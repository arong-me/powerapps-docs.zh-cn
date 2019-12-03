---
title: IfError 函数 | Microsoft Docs
description: PowerApps 中 IfError 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/21/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8d9916c3fa62aab947315b7c31daa96f7e528acd
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74680273"
---
# <a name="iferror-function-in-powerapps"></a>PowerApps 中的 IfError 函数

检测错误并提供替代值或执行操作。

## <a name="description"></a>描述

> [!NOTE]
> 此函数是试验性功能的一部分，并可能会发生变化。 本主题描述的行为仅在 "*公式级别错误管理*" 功能打开时可用。 此应用级设置默认情况下处于关闭状态。 若要启用此功能，请打开 "*文件*" 选项卡，在左侧菜单中选择 "*应用设置*"，然后选择 "*实验性功能*"。 你的反馈对我们非常有用-请告诉我们你在[Power Apps 社区论坛](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To)中的看法。

**IfError**函数将测试一个或多个值，直到它找到错误结果。 如果函数发现错误，该函数将返回相应的值。 否则，该函数将返回默认值。 在任一情况下，函数可能会返回要显示的字符串、要计算的公式或其他形式的结果。 **IfError**函数类似于**If**函数： **IfError**测试错误，但**如果**测试为**true**，则为。

使用**IfError**将错误值替换为有效值。 例如，如果用户输入可能会导致被零除，则使用此函数。 生成一个公式，将结果替换为0或另一个适用于应用的值，以便可以继续下游计算。 公式可以像以下示例那样简单：

```powerapps-dot
IfError( 1/x, 0 )
```

如果**x**的值不为零，则该公式将返回**1/x**。 否则， **1/x**生成错误，公式改为返回0。

在执行其他操作之前，在[行为公式](../working-with-formulas-in-depth.md)中使用**IfError**来执行操作并检查错误，如下所示：

```powerapps-dot
IfError(
    Patch( DS1, ... ), Notify( "problem in the first action" ),
    Patch( DS2, ... ), Notify( "problem in the second action" )
)
```

如果第一个修补程序遇到问题，则第一个**通知**将会运行，而不会进行进一步的处理，且第二个修补程序不会运行。 如果第一个修补程序成功，则第二个修补程序将运行，并在遇到问题时运行第二个**通知**。

如果公式找不到任何错误，并且您指定了可选的*DefaultResult*参数，则该公式将返回您为该参数指定的值。 如果公式找不到任何错误，并且未指定该参数，则该公式将返回计算的最后一个*值*参数。

## <a name="syntax"></a>语法

**IfError**（ *Value1*， *Fallback1* [， *Value2*， *Fallback2*，.。。[， *DefaultResult* ]])

* *Value （s）* -必需。 测试错误值的公式。
* *Fallback(s)* - 必需。 如果匹配的*值*参数返回错误，则为要计算的公式和要返回的值。
* DefaultResult - 可选。  要计算公式是否找不到任何错误的公式。

## <a name="examples"></a>示例

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **IfError( 1, 2 )** |第一个参数不是错误。 函数没有其他要检查的错误，也没有默认的返回值。 函数返回计算的最后一个*值*参数。   | 1 |
| **IfError( 1/0, 2 )** | 第一个参数将返回一个错误值（由于被零除）。 函数计算第二个参数，并将其作为结果返回。 | 2 |
| **IfError( 1/0, Notify( "There was an internal problem", NotificationType.Error ) )** | 第一个参数将返回一个错误值（由于被零除）。 函数计算第二个参数，并向用户显示一条消息。 Notify 的返回值是 ShowError 的返回值，强制转换为与 IfError 的第一个参数相同的类型（一个数字）。 | 1 |
| **IfError （1，2，3，4，5）** | 第一个参数不是错误，因此该函数不会计算该参数的相应回退。 第三个参数不是错误，因此该函数不会计算该参数的相应回退。 第五个参数没有对应的回退，并且是默认结果。 函数返回该结果，因为该公式不包含错误。 | 5 |

### <a name="step-by-step"></a>分步操作

1. 添加“[文本输入](../controls/control-text-input.md)”控件，将它命名为“TextInput1”（如果默认名称不是这样）。

2. 添加“[标签](../controls/control-text-box.md)”控件，将它命名为“Label1”（如果默认名称不是这样）。

3. 将 Label1 的文本属性的公式设置为：

    **IfError( Value( TextInput1.Text ), -1 )**

4. 在“TextInput1”中键入“1234”。  

    Label1 将显示值“1234”，因为这是对 Value 函数的有效输入。

5. 在“TextInput1”中键入“ToInfinity”。

    Label1 将显示值“-1”，因为这是对 Value 函数的无效输入。  在未使用 IfError 包装 Value 函数的情况下，标签将不会显示任何值，因为错误值被视为空白。 

