---
title: JSON 函数 |Microsoft Docs
description: 参考信息，包括在 PowerApps 中 JSON 函数的语法，
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/02/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 74e10a5b073e16ba9f35139441c94e9911446a0f
ms.sourcegitcommit: 2084789802fc5134dbeb888e759cced46019a017
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/06/2019
ms.locfileid: "66736390"
---
# <a name="json-function-in-powerapps"></a>在 PowerApps 中的 JSON 函数

生成表、 一个记录或值的 JSON 文本字符串。

## <a name="description"></a>描述

**JSON**函数返回的数据结构的 JavaScript 对象表示法 (JSON) 表示形式为文本，以便它适合用于存储或通过网络传输。 [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf)并[IETF RFC 8259](https://tools.ietf.org/html/rfc8259)介绍 JavaScript 和其他编程语言广泛使用的格式。

画布应用支持[数据类型](data-types.md)，此表列出了有关其文本表示形式的详细信息：

| 数据类型 | 描述 | 结果示例 |
|-----------|-------------|---------|
| **Boolean** | *true*或*false*。 | `true` |
|  颜色 | 包含颜色的 8 位十六进制表示形式的字符串。 这种表示形式会采用格式 #*rrggbbaa*，其中*rr*是红色分量*gg*为绿色， *bb*是蓝色，并*aa*是 alpha 通道。 Alpha 通道**00**是完全透明的并且**ff**是完全不透明的。 您可以将字符串传递给[ **ColorValue** ](function-colors.md)函数。  | `"#102030ff"` |
| **货币** | 为用户的语言使用相应的小数分隔符的数字。 如果需要则使用科学记数法。 | `1.345` |
| **日期** | 字符串，其中包含以 ISO 8601 日期**年-月-日**格式。 | `"2019-03-31"` |
| **DateTime** | 包含的 ISO 8601 日期/时间的字符串。 日期/时间值均是 UTC 时间，因为结束的"Z"指示。  | `"2019-03-31T22:32:06.822Z"`  |
| **GUID** | 包含 GUID 值的字符串。 字母均为小写。 | `"751b58ac-380e-4a04-a925-9f375995cc40"`
| **图中媒体** | 如果**IncludeBinaryData**媒体文件格式进行编码字符串的指定。 Web 引用，使用 http： 或 https:URL 方案不会被修改。 对内存中二进制数据的引用进行编码["的数据：*mimetype*; base64，..."](https://en.wikipedia.org/wiki/Data_URI_scheme)格式。 内存中数据包括用户通过使用捕获的映像[**照相机**](../controls/control-camera.md)控件和任何其他引用与 appres： 和 blob:URL 方案。| `"data:image/jpeg;base64,/9j/4AA..."` |
| **数量** | 为用户的语言使用相应的小数分隔符的数字。 如果需要则使用科学记数法。 | `1.345` |
| **选项&nbsp;设置** | 数字值的选项的设置，不用于进行显示的标签。 使用数字值是因为它与语言无关。  | `1001` |
| **时间** | 字符串，其中包含 ISO 8601 *hh:mm:ss.fff*格式。  | `"23:12:49.000"` |
| **记录** | 以逗号分隔列表，之间 **{** 并 **}** 、 字段和其值。 此表示法类似的画布应用中的记录，但该名称始终是两个双引号之间。 此格式不支持基于多对一关系的记录。  | `{ "First Name": "Fred", "Age": 21 }` |
| **Table** | 以逗号分隔列表，之间 **[** 并 **]** 的记录。 此格式不支持基于一个对多关系的表。  | `[ { "First Name": "Fred", "Age": 21 }, { "First Name": "Jean", "Age": 20 } ]` |
| **两个&nbsp;选项** | 布尔值的两个选项，则为 *，则返回 true*或*false*，不用于进行显示的标签。 因为它是独立于语言，则使用布尔值。 | `false` |
| **超链接的文本** | 两个双引号之间的字符串。 函数对嵌入的双引号以反斜杠进行转义，换行符替换为"\n"，并使其他标准 JavaScript 替换内容。 | `"This is a string."` |

指定可选*格式*参数来控制如何可读的结果是，如何不受支持和二进制数据类型进行处理。 默认情况下，输出为不带任何不必要的空格或换行符，尽可能紧凑，不允许使用不受支持的数据类型和二进制数据。 如果指定，可以组合多个格式 **&** 运算符。

| JSONFormat 枚举 | 描述 |
|-----------------|-------------|
| **Compact** | 默认值。  输出是没有添加的空格或换行符尽可能紧凑。 |
| **IndentFour** | 若要提高可读性，输出包含每个列和嵌套级别的新行并为每个缩进级别使用四个空格。 |
| **IncludeBinaryData** | 结果包括图像、 视频和音频剪辑列。 此格式可以大幅提高结果的大小，并会降低应用程序的性能。 |
| **IgnoreBinaryData** | 结果不包括图像、 视频或音频剪辑列。 如果未指定**IncludeBinaryData**也不**IgnoreBinaryData**，如果遇到二进制数据，该函数将产生错误。 |
| **IgnoreUnsupportedTypes** | 允许使用不支持的数据类型，但结果不包含它们。 默认情况下，不受支持的数据类型会生成错误。 |

使用[ **ShowColumns**并**DropColumns** ](function-table-shaping.md)函数，则结果将包括哪些数据的控制以及删除不支持的数据类型。

因为**JSON**可以是内存和计算密集型，可以使用此函数仅在[的行为函数](../working-with-formulas-in-depth.md)。 您可以捕获的结果**JSON**成[变量](../working-with-variables.md)，然后可以在数据流中使用。

如果某个列的显示名称和逻辑名称，则结果包含的逻辑名称。 显示名称反映应用程序用户和语言中，因此不适合于数据传输到一个公共服务。

## <a name="syntax"></a>语法

**JSON**( *DataStructure* [, *Format* ] )

* *DataStructure* – 必需。 要将转换为 JSON 的数据结构。  表、 记录和基元值支持，任意嵌套。
* *格式*-可选。  **JSONFormat**枚举值。 默认值是**Compact**，这不会添加换行符或空格和二进制数据和不支持的列会阻止。

## <a name="examples"></a>示例

### <a name="hierarchical-data"></a>分层数据

1. 插入[**按钮**](../controls/control-button.md)控件，并设置其**OnSelect**属性设为此公式。

    ```powerapps-dot
    ClearCollect( CityPopulations,
        { City: "London",    Country: "United Kingdom", Population: 8615000 },
        { City: "Berlin",    Country: "Germany",        Population: 3562000 },
        { City: "Madrid",    Country: "Spain",          Population: 3165000 },
        { City: "Hamburg",   Country: "Germany",        Population: 1760000 },
        { City: "Barcelona", Country: "Spain",          Population: 1602000 },
        { City: "Munich",    Country: "Germany",        Population: 1494000 }
    );
    ClearCollect( CitiesByCountry, GroupBy( CityPopulations, "Country", "Cities" ) )
    ```

1. 在按住 Alt 键的同时选择按钮。

    **CitiesByCountry**使用此数据结构，可以通过选择显示创建集合**集合**上**文件**菜单，然后选择的名称集合。

    > [!div class="mx-imgBorder"]
    > ![CitiesByCountry 集合](media/function-json/cities-grouped.png)

    此外可以通过选择显示此集合**文件** > **应用设置** > **高级设置** >  **启用公式栏结果视图**，在公式栏中选择的集合的名称，然后选择公式栏下的集合的名称旁边的向下箭头。

    > [!div class="mx-imgBorder"]
    > ![在编辑栏结果视图中的集合](media/function-json/cities-grouped-resultview.png)

1. 将插入另一个按钮，并设置其**OnSelect**属性设为此公式：

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON( CitiesByCountry ) )
    ```

    此公式设置全局变量**CitiesByCountryJSON**到的 JSON 表示形式**CitiesByCountry**。

1. 在按住 Alt 键的同时选择按钮。

1. 插入[**标签**](../controls/control-text-box.md)控件，并设置其**文本**向此变量的属性。

    ```powerapps-dot
    CitiesByCountryJSON
    ```

    标签显示所有内容位于一行 （不含空格） 的此结果，适用于跨网络传输：

    ```json
    [{"Cities":[{"City":"London","Population":8615000}],"Country":"United Kingdom"},{"Cities":[{"City":"Berlin","Population":3562000},{"City":"Hamburg","Population":1760000},{"City":"Munich","Population":1494000}],"Country":"Germany"},{"Cities":[{"City":"Madrid","Population":3165000},{"City":"Barcelona","Population":1602000}],"Country":"Spain"}]
    ```

1. 更改第二个按钮的公式，以使输出更具可读性。

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON(CitiesByCountry, JSONFormat.IndentFour ))
    ```

1. 在按住 Alt 键的同时选择第二个按钮。

    标签显示更具可读性的结果。

    ```json
    [
        {
            "Cities": [
                {
                    "City": "London",
                    "Population": 8615000
                }
            ],
            "Country": "United Kingdom"
        },
        {
            "Cities": [
                {
                    "City": "Berlin",
                    "Population": 3562000
                },
                {
                    "City": "Hamburg",
                    "Population": 1760000
                },
                {
                    "City": "Munich",
                    "Population": 1494000
                }
            ],
            "Country": "Germany"
        },
        {
            "Cities": [
                {
                    "City": "Madrid",
                    "Population": 3165000
                },
                {
                    "City": "Barcelona",
                    "Population": 1602000
                }
            ],
            "Country": "Spain"
        }
    ]
    ```

### <a name="images-and-media-in-base64"></a>图像和采用 base64 格式的媒体

1. 添加[**映像**](../controls/control-image.md)控件。

    此控件带来**SampleImage**使用它。

1. 添加[**按钮**](../controls/control-button.md)控件，并设置其**OnSelect**属性设为此公式。

    ```powerapps-dot
    Set( ImageJSON, JSON( SampleImage, JSONFormat.IncludeBinaryData ) )
    ```

1. 在按住 Alt 键的同时选择按钮。

1. 添加一个标签，并设置其**文本**向此变量的属性。

    ```powerapps-dot
    ImageJSON
    ```

1. 调整控件的大小和减小字体大小，以显示结果的大多数。

    此时，标签显示的文本字符串**JSON**函数捕获。

    ```json
    "data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjxzdmcgdmVyc2lvbj0iMS4xIg0KCSB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4bWxuczphPSJodHRwOi8vbnMuYWRvYmUuY29tL0Fkb2JlU1ZHVmlld2VyRXh0ZW5zaW9ucy8zLjAvIg0KCSB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjI3MHB4IiBoZWlnaHQ9IjI3MHB4IiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCAyNzAgMjcwIiB4bWw6c3BhY2U9InByZXNlcnZlIj4NCgk8ZyBjbGFzcz0ic3QwIj4NCgkJPHJlY3QgeT0iMC43IiBmaWxsPSIjRTlFOUU5IiB3aWR0aD0iMjY5IiBoZWlnaHQ9IjI2OS4zIi8+DQoJCTxwb2x5Z29uIGZpbGw9IiNDQkNCQ0EiIHBvaW50cz0iMjc3LjksMTg3LjEgMjQ1LDE0My40IDE4OC42LDIwMi44IDc1LDgwLjUgLTQuMSwxNjUuMyAtNC4xLDI3MiAyNzcuOSwyNzIiLz4NCgkJPGVsbGlwc2UgZmlsbD0iI0NCQ0JDQSIgY3g9IjIwMi40IiBjeT0iODQuMSIgcng9IjI0LjQiIHJ5PSIyNC4zIi8+DQoJPC9nPg0KPC9zdmc+"
    ```
