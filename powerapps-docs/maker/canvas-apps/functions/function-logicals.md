---
title: And、Or 和 Not 函数 | Microsoft 文档
description: PowerApps 中 And、Or 和 Not 函数的参考信息，包括语法和示例
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 438076c5e1b3e0643af809755078fbc491cea9c5
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61562804"
---
# <a name="and-or-and-not-functions-in-powerapps"></a>PowerApps 中的 And、Or 和 Not 函数
布尔逻辑函数，常用于操作比较结果和测试结果。

## <a name="description"></a>描述
如果 **And** 函数的所有参数均为 **true**，则此函数返回 **true**。  **&&** [运算符](operators.md)等效于 **And**。

如果 **Or** 函数的任何参数为 **true**，则此函数返回 **true**。  **||** 运算符等效于 **Or**。

如果 **Not** 函数的参数为 **false**，则此函数返回 **true**；如果其参数为 **true**，则返回 **false**。  **!** 运算符等效于 **Not**。

这些函数使用逻辑值。 不能直接向这些函数传递数字或字符串；而是必须执行比较或测试。 例如，诸如 **x > 1** 的比较是一个逻辑公式，如果 **x** 大于 **1**，则计算结果为布尔值 **true**。 如果 **x** 小于 **1**，则此公式的计算结果为 **false**。

## <a name="syntax"></a>语法
**And**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Or**( *LogicalFormula1*, *LogicalFormula2* [, *LogicalFormula3*, ... ] )<br>
**Not**( *LogicalFormula* )

* *LogicalFormula(s)* - 必需。  要计算和运算的逻辑公式。

## <a name="examples"></a>示例
### <a name="step-by-step"></a>分步操作
使用此函数确定滑块的值是否在 50 到 100 范围之外：

**Or(Slider1.Value < 50, Slider1.Value> 100)**

如果[表](../working-with-tables.md)中包含“部门”[列](../working-with-tables.md#columns)和“薪水”列，则可在“结果”列中使用此函数在所有符合条件的行中显示 **true**，其中“部门”列中的值为“人力资源”或“薪水”列中的值大于 **200000**：

**Or(Dept = HR, Salary >= 200000)**

或者，使用 || 运算符来获得与之前的公式相同的结果：

**Slider1.Value < 50 || Slider1.Value> 100**

**Dept = "HR" || Salary > 200000**

