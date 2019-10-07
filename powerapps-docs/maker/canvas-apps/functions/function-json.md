---
title: JSON 函数 |Microsoft Docs
description: PowerApps 中 JSON 函数的参考信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/02/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ba852093da05c3fa69cc47b219a0bef65908c170
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71992621"
---
# <a name="json-function-in-powerapps"></a>PowerApps 中的 JSON 函数

为表、记录或值生成 JSON 文本字符串。

## <a name="description"></a>描述

**JSON**函数以文本的形式返回数据结构的 JAVASCRIPT 对象表示法（JSON）表示形式，以便它适合在网络中进行存储或传输。 [ECMA-404](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf)和[IETF RFC 8259](https://tools.ietf.org/html/rfc8259)介绍了 JavaScript 和其他编程语言广泛使用的格式。

画布应用支持此表列出的[数据类型](data-types.md)以及有关其文本表示形式的详细信息：

| 数据类型 | 描述 | 结果示例 |
|-----------|-------------|---------|
| **变量** | *true*或*false*。 | `true` |
| 颜色 | 包含颜色的8位十六进制表示形式的字符串。 此表示形式采用的格式为 #*rrggbbaa*，其中*rr*为红色分量， *gg*为绿色， *bb*为蓝色， *aa*为 alpha 通道。 对于 alpha 通道， **00**是完全透明的，而**ff**是完全不透明的。 可以将字符串传递给[**ColorValue**](function-colors.md)函数。  | `"#102030ff"` |
| **货币** | 对用户语言使用适当的小数点分隔符的数字。 如果需要，使用科学记数法。 | `1.345` |
| **日期** | 包含 ISO 8601 **yyyy-mm-dd**格式的日期的字符串。 | `"2019-03-31"` |
| **型** | 包含 ISO 8601 日期/时间的字符串。 日期/时间值采用 UTC 格式，因为结束的 "Z" 指示。  | `"2019-03-31T22:32:06.822Z"`  |
| **GUID.EMPTY** | 包含 GUID 值的字符串。 字母小写。 | `"751b58ac-380e-4a04-a925-9f375995cc40"`
| **图像、媒体** | 如果指定了**IncludeBinaryData** ，则媒体文件将以字符串的形式进行编码。 使用 http：或 https 的 Web 引用：未修改 URL 方案。 对内存中二进制数据的引用将用["data：*mimetype*; base64,..."](https://en.wikipedia.org/wiki/Data_URI_scheme)格式进行编码。 内存中数据包括用户使用[**照相机**](../controls/control-camera.md)控件捕获的图像，以及 appres：和 blob 的任何其他引用：URL 方案。| `"data:image/jpeg;base64,/9j/4AA..."` |
| **多种** | 对用户语言使用适当的小数点分隔符的数字。 如果需要，使用科学记数法。 | `1.345` |
| **选项 @ no__t-1set** | 选项集的数值，而不是用于显示的标签。 使用数值是因为它是独立于语言的。  | `1001` |
| **阶段** | 包含 ISO 8601 *hh： mm： ss*格式的字符串。  | `"23:12:49.000"` |
| **记录** | 以逗号分隔的列表，介于 **{** 和 **}** 之间，字段及其值之间。 此表示法类似于画布应用中的记录，但名称始终在双引号之间。 此格式不支持基于多对一关系的记录。  | `{ "First Name": "Fred", "Age": 21 }` |
| **数据表** | 记录的以逗号分隔的列表，介于 **[** 和 **]** 之间。 此格式不支持基于一对多关系的表。  | `[ { "First Name": "Fred", "Age": 21 }, { "First Name": "Jean", "Age": 20 } ]` |
| **两个 @ no__t-1option** | 这两个选项的布尔值（ *true*或*false*），而不是用于显示的标签。 使用布尔值，因为它是独立于语言的。 | `false` |
| **超链接、文本** | 双引号。 函数使用反斜杠转义嵌入的双引号，将换行符替换为 "\n"，并进行其他标准 JavaScript 替换。 | `"This is a string."` |

指定可选的*格式*参数以控制结果的可读性，以及如何处理不受支持的和二进制数据类型。 默认情况下，输出尽可能简洁，无需空格或换行符，不允许使用不受支持的数据类型和二进制数据。 如果指定 **&** 运算符，则可以组合多种格式。

| JSONFormat 枚举 | 描述 |
|-----------------|-------------|
| **Compact** | 默认值。  输出尽可能简洁，无添加空格或换行符。 |
| **IndentFour** | 为提高可读性，输出包含每个列和嵌套级别的一个换行符，并为每个缩进级别使用四个空格。 |
| **IncludeBinaryData** | 结果包括图像、视频和音频剪辑列。 此格式会大幅增加结果的大小并降低应用程序的性能。 |
| **IgnoreBinaryData** | 结果不包括图像、视频或音频剪辑列。 如果既没有指定**IncludeBinaryData**也没有指定**IgnoreBinaryData**，则在遇到二进制数据时，该函数将生成错误。 |
| **IgnoreUnsupportedTypes** | 允许使用不受支持的数据类型，但结果不会包括它们。 默认情况下，不支持的数据类型产生错误。 |

使用[ **ShowColumns**和**DropColumns** ](function-table-shaping.md)函数来控制结果所包含的数据并删除不支持的数据类型。

由于**JSON**可能会占用大量内存和计算计算，因此只能在[行为函数](../working-with-formulas-in-depth.md)中使用此函数。 可以将**JSON**中的结果捕获到变量中，然后可以在数据流中使用该[变量](../working-with-variables.md)。

如果列同时具有显示名称和逻辑名称，则结果将包含逻辑名称。 显示名称反映了应用用户的语言，因此不适合用于将数据传输到公共服务。

## <a name="syntax"></a>语法

**JSON**（ *DataStructure* [， *Format* ]）

* *DataStructure* –必需。 要转换为 JSON 的数据结构。  支持、任意嵌套表、记录和基元值。
* *格式*-可选。  **JSONFormat**枚举值。 默认值为**Compact**，此值不会添加换行符或空格，也不会阻止二进制数据和不受支持的列。

## <a name="examples"></a>示例

### <a name="hierarchical-data"></a>分层数据

1. 插入[**按钮**](../controls/control-button.md)控件，并将其**OnSelect**属性设置为此公式。

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

1. 按住 Alt 键的同时选择该按钮。

    **CitiesByCountry**集合是使用此数据结构创建的，通过在 "**文件**" 菜单上选择 "**集合**"，然后选择集合的名称，可以显示该集合。

    > [!div class="mx-imgBorder"]
    > ![CitiesByCountry collection @ no__t-1

    你还可以通过以下方式显示此集合：选择 "**文件** > **应用设置**"  >  "**高级 @no__t 设置**"。**启用公式栏结果视图**，在编辑栏中选择集合名称，然后选择公式栏下的集合名称旁的向下箭头。

    > [!div class="mx-imgBorder"]
    > 在公式栏的结果视图中 ![Collection @ no__t-1

1. 插入另一个按钮，并将其**OnSelect**属性设置为以下公式：

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON( CitiesByCountry ) )
    ```

    此公式将全局变量**CitiesByCountryJSON**设置为**CitiesByCountry**的 JSON 表示形式。

1. 按住 Alt 键的同时选择该按钮。

1. 插入 "[**标签**](../controls/control-text-box.md)" 控件，并将 " **Text** " 属性设置为此变量。

    ```powerapps-dot
    CitiesByCountryJSON
    ```

    标签显示此结果，所有内容都在无空格的单个行上，适用于跨网络传输：

    ```json
    [{"Cities":[{"City":"London","Population":8615000}],"Country":"United Kingdom"},{"Cities":[{"City":"Berlin","Population":3562000},{"City":"Hamburg","Population":1760000},{"City":"Munich","Population":1494000}],"Country":"Germany"},{"Cities":[{"City":"Madrid","Population":3165000},{"City":"Barcelona","Population":1602000}],"Country":"Spain"}]
    ```

1. 更改第二个按钮的公式，使输出更具可读性。

    ```powerapps-dot
    Set( CitiesByCountryJSON, JSON(CitiesByCountry, JSONFormat.IndentFour ))
    ```

1. 按住 Alt 键的同时选择第二个按钮。

    标签显示可读性更强的结果。

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

### <a name="images-and-media-in-base64"></a>Base64 中的图像和媒体

1. 添加[**图像**](../controls/control-image.md)控件。

    此控件将**SampleImage** 。

1. 添加一个[**按钮**](../controls/control-button.md)控件，并将其**OnSelect**属性设置为此公式。

    ```powerapps-dot
    Set( ImageJSON, JSON( SampleImage, JSONFormat.IncludeBinaryData ) )
    ```

1. 按住 Alt 键的同时选择该按钮。

1. 添加一个标签，并将其**Text**属性设置为此变量。

    ```powerapps-dot
    ImageJSON
    ```

1. 调整控件的大小并根据需要减小字体大小，以显示大部分结果。

    标签显示**JSON**函数捕获的文本字符串。

    ```json
    "data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4NCjxzdmcgdmVyc2lvbj0iMS4xIg0KCSB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHhtbG5zOnhsaW5rPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5L3hsaW5rIiB4bWxuczphPSJodHRwOi8vbnMuYWRvYmUuY29tL0Fkb2JlU1ZHVmlld2VyRXh0ZW5zaW9ucy8zLjAvIg0KCSB4PSIwcHgiIHk9IjBweCIgd2lkdGg9IjI3MHB4IiBoZWlnaHQ9IjI3MHB4IiBlbmFibGUtYmFja2dyb3VuZD0ibmV3IDAgMCAyNzAgMjcwIiB4bWw6c3BhY2U9InByZXNlcnZlIj4NCgk8ZyBjbGFzcz0ic3QwIj4NCgkJPHJlY3QgeT0iMC43IiBmaWxsPSIjRTlFOUU5IiB3aWR0aD0iMjY5IiBoZWlnaHQ9IjI2OS4zIi8+DQoJCTxwb2x5Z29uIGZpbGw9IiNDQkNCQ0EiIHBvaW50cz0iMjc3LjksMTg3LjEgMjQ1LDE0My40IDE4OC42LDIwMi44IDc1LDgwLjUgLTQuMSwxNjUuMyAtNC4xLDI3MiAyNzcuOSwyNzIiLz4NCgkJPGVsbGlwc2UgZmlsbD0iI0NCQ0JDQSIgY3g9IjIwMi40IiBjeT0iODQuMSIgcng9IjI0LjQiIHJ5PSIyNC4zIi8+DQoJPC9nPg0KPC9zdmc+"
    ```
