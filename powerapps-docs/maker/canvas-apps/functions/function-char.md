---
title: Char 函数 | Microsoft 文档
description: Power Apps 中 Char 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/01/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 578e196bfa55f33416de1ee551d1e63e106a612a
ms.sourcegitcommit: ed583eb94720a9645bfd79776311792a958077b8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/01/2020
ms.locfileid: "78204360"
---
# <a name="char-function-in-power-apps"></a>Power Apps 中的 Char 函数

将字符代码转换为字符串。

## <a name="description"></a>说明

**Char**函数使用对应的 ASCII 字符将数字转换为字符串。

## <a name="syntax"></a>语法

**Char**( *CharacterCode* )

- *CharacterCode* - 必需。 要转换的 ASCII 字符代码。

## <a name="examples"></a>示例

| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **Char( 65 )** |返回 ASCII 代码 65 对应的字符。 |的 |
| **Char( 105 )** |返回 ASCII 代码 105 对应的字符。 |看到 |
| **Char( 35 )** |返回 ASCII 代码 35 对应的字符。 |"#" |

### <a name="display-a-character-map"></a>显示字符映射表

1. 在 tablet 应用中的空屏幕上，添加一个具有**空白水平**布局的[**库**](../controls/control-gallery.md)控件，然后设置以下属性：

    - **项**： `[0,1,2,3,4,5,6,7]`
    - **宽度**：800
    - **高度**：500
    - **TemplateSize**：100
    - **TemplatePadding**：0

1. 在该库中，添加一个具有**空白垂直**布局的**库**控件，然后设置以下属性：

    - **项**： `ForAll( [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 )`
    - **宽度**：100
    - **高度**：500
    - **TemplateSize**：30
    - **TemplatePadding**：0

    **Items**属性的值与第一个库中**Items**属性的 value 列所提供的列号（`ThisItem.Value`中的0-7）相乘。 然后，该公式将结果添加到第二个库中的行号之一（0-15 在[**ForAll**](function-forall.md)函数提供的记录范围内）。

1. 在第二个（垂直）库中，添加 "**标签**" 控件，并设置以下属性：

    - **文本**： `ThisItem.Value`
    - **宽度**：50

1. 在第二个（垂直）库中，添加另一个 "**标签**" 控件，并设置以下属性：

    - **文本**： `Char( ThisItem.Value )`
    - **宽度**：50
    - **X**：50

您已经创建了一个图表，其中的前128个 ASCII 字符。 不能打印以小正方形显示的字符。

![前128个 ASCII 字符](media/function-char/chart-lower.png)

若要显示扩展的 ASCII 字符，请将第二个库的**Items**属性设置为此公式，这会将128添加到每个字符值：

`ForAll( [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 + 128)`

![扩展的 ASCII 字符](media/function-char/chart-higher.png)

若要以不同的字体显示字符，请将第二个标签的 "**字体**" 属性设置为 **"跳舞 Script"** 之类的值。

![跳舞脚本](media/function-char/chart-higher-dancing-script.png)
