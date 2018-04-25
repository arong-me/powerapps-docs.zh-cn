---
title: IfError 函数 | Microsoft Docs
description: PowerApps 中 IfError 函数的参考信息（包括语法和示例）
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: gregli
ms.openlocfilehash: c0da6a00f1176c8f44db6e508cca92b0cbf99beb
ms.sourcegitcommit: a9d33322228c398d29964429602dc3fe19fa67d2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2018
---
# <a name="iferror-function-in-powerapps"></a>PowerApps 中的 IfError 函数
检测错误并提供替代值或执行操作。

## <a name="description"></a>说明
> [!NOTE]
> 此函数是试验性功能的一部分，并可能会发生变化。  此处描述的行为仅在开启公式级错误管理功能时可用。  默认情况下关闭此应用级别设置。  若要启用此功能，请导航到“文件”选项卡左侧菜单中的“应用设置”，然后导航到“试验性功能”。  你的反馈对我们非常重要，请通过 [PowerApps 社区论坛](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To)提供反馈。

IfError 函数测试其每个参数以寻找错误值，并在找到首个非错误值后停止。  找到非错误值后，参数将被忽略不计。

使用 IfError 将错误值替换为有效值。  例如，用户输入可能会导致除数为零，将其替换为 0 或适合应用的其他有效值，这样下游计算可以继续。

在[行为公式](../working-with-formulas-in-depth.md)中使用 IfError 执行操作，检查结果是否有错误，以及是否需要采取进一步的操作或通过 [ShowError](function-showerror.md) 向用户显示错误消息。

如果 IfError 的所有参数均导致错误，则返回最后一个参数值（它将是一个错误值）。 

## <a name="syntax"></a>语法
IfError( Value, Fallback1 [, Fallback2, ... ] )

* *Value* - 必需。 测试错误值的公式。 
* 回退 - 必需。 如果先前的参数返回错误，要求值的公式和要返回的值。  计算回退参数直到找到非错误值。

## <a name="examples"></a>示例

| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **IfError( 1, 2 )** |第一个参数不是错误。  返回该参数，且不计算后续参数。   | 1 |
| **IfError( 1/0, 2 )** | 第一个参数返回一个错误值（由于除数为零）。  计算第二个参数，返回生成的非错误值。 | 2 | 
| **IfError( 1/0, ShowError( "Division by Zero" ) )** | 第一个参数返回一个错误值（由于除数为零）。  计算第二个参数，向用户显示消息。  IfError 的返回值是 ShowError 的返回值，强制转换为与 IfError 的第一个参数相同的类型（一个数字）。 | 1 |
| **IfError( 1/0, 1/0, 2, 1/0, 3 )** | 第一个参数返回一个错误值（由于除数为零）。  计算第二个参数，生成一个错误值（另一个除数为零）。  计算第三个参数，不返回返回的错误值。  第四和第五个参数将被忽略。  | 2 |

### <a name="step-by-step"></a>分步操作

1. 添加“[文本输入](../controls/control-text-input.md)”控件，将它命名为“TextInput1”（如果默认名称不是这样）。

2. 添加“[标签](../controls/control-text-box.md)”控件，将它命名为“Label1”（如果默认名称不是这样）。

3. 将 Label1 的文本属性的公式设置为：

    **IfError( Value( TextInput1.Text ), -1 )**

4. 在“TextInput1”中键入“1234”。  

    Label1 将显示值“1234”，因为这是对 Value 函数的有效输入。

5. 在“TextInput1”中键入“ToInfinity”。

    Label1 将显示值“-1”，因为这是对 Value 函数的无效输入。  在未使用 IfError 包装 Value 函数的情况下，标签将不会显示任何值，因为错误值被视为空白。 
