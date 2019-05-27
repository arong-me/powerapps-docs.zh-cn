---
title: IfError 函数 | Microsoft Docs
description: PowerApps 中 IfError 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 03/21/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 63a837eff2944569f5f66223690b11ddcfd399f6
ms.sourcegitcommit: aa9f78c304fe46922aecfe3b3fadb6bda72dfb23
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2019
ms.locfileid: "66215930"
---
# <a name="iferror-function-in-powerapps"></a>PowerApps 中的 IfError 函数

检测错误并提供替代值或执行操作。

## <a name="description"></a>描述

> [!NOTE]
> 此函数是试验性功能的一部分，并可能会发生变化。 本主题介绍的行为是时才可用*公式级错误管理*功能已打开。 默认情况下，此应用程序级设置处于关闭状态。 若要启用此功能，请打开*文件*选项卡上，选择*应用程序设置*在左侧菜单中，然后选择*实验性功能*。 你的反馈对我们非常重要，请通过 [PowerApps 社区论坛](https://powerusers.microsoft.com/t5/Expressions-and-Formulas/bd-p/How-To)提供反馈。

**IfError**函数测试一个或多个值，直到它找到一个错误结果。 如果该函数发现错误，该函数将返回相应的值。 否则，该函数返回默认值。 在任一情况下，该函数可能会返回要显示的公式或另一种形式的结果的字符串。 **IfError**函数类似于**如果**函数：**IfError**测试是否有错误，尽管**如果**测试**true**。

使用**IfError**错误值替换为与有效的值。 如果用户输入可能会导致除数为零，例如，使用此函数。 生成的公式将替换为 0 或适合您的应用程序，以便下游计算可以继续执行的另一个值的结果。 公式可以像此示例中一样简单：

```powerapps-dot
IfError( 1/x, 0 )
```

如果的值**x**不为零，该公式将返回**1 / x**。 否则为**1 / x**会生成错误，并且公式将改为返回 0。

使用**IfError**中[行为公式](../working-with-formulas-in-depth.md)错误执行的操作和检查，然后再执行其他操作，如这种模式中所示：

```powerapps-dot
IfError(
    Patch( DS1, ... ), Notify( "problem in the first action" ),
    Patch( DS2, ... ), Notify( "problem in the second action" )
)
```

如果第一个修补程序遇到问题，第一个**通知**发生运行时，不进行其他处理，并且第二个修补程序不会运行。 如果第一个修补程序成功，将在运行第二个修补程序和遇到问题，第二个**通知**运行。

如果公式找不到任何错误并且已指定可选*DefaultResult*参数，该公式将返回为该参数指定的值。 如果该公式找不到任何错误，并且没有指定该参数，该公式将返回上次*值*求值的参数。

## <a name="syntax"></a>语法

**IfError**( *Value1*, *Fallback1* [, *Value2*, *Fallback2*, ... [, *DefaultResult* ] ] )

* *值*-必需。 测试错误值的公式。
* *Fallback(s)* - 必需。 要计算的公式和值如果匹配，则返回*值*的参数返回错误。
* DefaultResult - 可选。  若要评估公式不会发现任何错误时这些公式。

## <a name="examples"></a>示例

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **IfError( 1, 2 )** |第一个参数不是错误。 该函数具有其他错误检查和返回值无默认值。 该函数将返回上次*值*求值的参数。   | 1 |
| **IfError( 1/0, 2 )** | 第一个参数返回错误值 （由于除数为零）。 函数计算第二个参数，并将其作为结果返回。 | 2 |
| **IfError( 1/0, Notify( "There was an internal problem", NotificationType.Error ) )** | 第一个参数返回错误值 （由于除数为零）。 函数计算第二个参数，并向用户显示一条消息。 Notify 的返回值是 ShowError 的返回值，强制转换为与 IfError 的第一个参数相同的类型（一个数字）。 | 1 |
| **IfError( 1, 2, 3, 4, 5 )** | 第一个参数不是错误，因此该函数才会计算参数的相应回退。 第三个参数不出现错误，因此该函数才会计算参数的相应回退。 第五个参数没有相应的回退，它是默认结果。 该函数返回该结果，因为该公式不包含任何错误。 | 5 |

### <a name="step-by-step"></a>分步操作

1. 添加“[文本输入](../controls/control-text-input.md)”控件，将它命名为“TextInput1”（如果默认名称不是这样）。

2. 添加“[标签](../controls/control-text-box.md)”控件，将它命名为“Label1”（如果默认名称不是这样）。

3. 将 Label1 的文本属性的公式设置为：

    **IfError( Value( TextInput1.Text ), -1 )**

4. 在“TextInput1”中键入“1234”。  

    Label1 将显示值“1234”，因为这是对 Value 函数的有效输入。

5. 在“TextInput1”中键入“ToInfinity”。

    Label1 将显示值“-1”，因为这是对 Value 函数的无效输入。  在未使用 IfError 包装 Value 函数的情况下，标签将不会显示任何值，因为错误值被视为空白。 

