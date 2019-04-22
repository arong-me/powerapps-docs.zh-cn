---
title: Char 函数 | Microsoft 文档
description: PowerApps 中 Char 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/01/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1b598cc863ec01bcb2a66a9510cb48ec5203e679
ms.sourcegitcommit: f84095d964fe1fe5cc5290e5edbee284bd768e1e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59042609"
---
# <a name="char-function-in-powerapps"></a>PowerApps 中的 Char 函数

将字符代码转换为字符串。

## <a name="description"></a>描述

**Char**函数会将数字转换为具有相应的 ASCII 字符的字符串。

## <a name="syntax"></a>语法

**Char**( *CharacterCode* )

- *CharacterCode* - 必需。 要转换的 ASCII 字符代码。

## <a name="examples"></a>示例

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Char( 65 )** |返回 ASCII 代码 65 对应的字符。 |"A" |
| **Char( 105 )** |返回 ASCII 代码 105 对应的字符。 |"i" |
| **Char( 35 )** |返回 ASCII 代码 35 对应的字符。 |"#" |

### <a name="display-a-character-map"></a>显示字符映射表

1. 在平板电脑应用中的空屏幕上，添加[**库**](../controls/control-gallery.md)与控制**空白水平**布局，然后设置这些属性：

    - **项**: `[0,1,2,3,4,5,6,7]`
    - **宽度**:800
    - **高度**:500
    - **TemplateSize**:100
    - **TemplatePadding**:0

1. 在该库中，添加**库**控件替换**空白垂直**布局，然后设置这些属性：

    - **项**: `ForAll( [0,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 )`
    - **宽度**:100
    - **高度**:500
    - **TemplateSize**:30
    - **TemplatePadding**:0

    值**项**属性将提供的值列的列数为 16 相乘**项**从第一个库的属性 (0-7 `ThisItem.Value`)。 该公式从第二个库中然后将结果添加到一个行号 (0 至 15 中记录作用域[ **ForAll** ](function-forall.md)函数提供了)。

1. 在第二个 （垂直） 库中，添加**标签**控件，并设置这些属性：

    - **文本**: `ThisItem.Value`
    - **宽度**:50

1. 在第二个 （垂直） 库中，添加另一个**标签**控件，并设置这些属性：

    - **文本**: `Char( ThisItem.Value )`
    - **宽度**:50
    - **X**:50

你已创建的前 128 个 ASCII 字符的图表。 显示为不能打印的小正方形的字符。

![第一次 128 个 ASCII 字符](media/function-char/chart-lower.png)

若要显示扩展的 ASCII 字符，将**项**的第二个库为此公式，将 128 添加到每个字符值的属性：

`ForAll( [0,2,3,4,5,6,7,8,9,10,11,12,13,14,15], Value + ThisItem.Value * 16 + 128)`

![扩展的 ASCII 字符](media/function-char/chart-higher.png)

若要在不同的字体显示字符，请设置**字体**属性的值，如到第二个标签**跳舞脚本**。

![跳舞脚本](media/function-char/chart-higher-dancing-script.png)
