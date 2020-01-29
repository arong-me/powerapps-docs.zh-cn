---
title: Assert 函数 | Microsoft Docs
description: 提供 Power Apps Test Studio 中 Assert 函数的参考信息（包括语法）
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/19/2018
ms.author: aheneay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e4319c3685db46f4277109e385a640e744402edc
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541281"
---
# <a name="assert-function-in-power-apps-test-studio"></a>Power Apps Test Studio 的 Assert 函数

断言是测试中计算结果为 True 或 False 的条件或表达式。 如果表达式返回 False，则测试用例将失败。 断言用于验证测试或测试步骤的实际结果是否符合预期结果，并且如果条件为 False，则会使测试失败。 断言可用于验证应用中控件的状态，如标签值、列表框选择和其他控件属性。  

通过和失败断言的断言消息也包含在 TestCaseResult 记录的 Traces 表中。 

## <a name="syntax"></a>语法

Assert(expression, message) 

- expression - 必需  。 计算结果为 True 或 False 的表达式。
- message - 非必需  。 描述断言失败的消息。 


## <a name="examples"></a>示例

```Assert(lblResult.Text = "Success", "lblResult value Expected : Success , Actual : " & lblResult.Text)```<br>
```Assert(ListBox1.Selected.Value = "Success", "ListBox1 selection Expected : Success,  Actual : " & ListBox1.Selected.Value)```<br>
```Assert(kudosAfterTest = kudosBeforeTest + 1, "Kudos count. Expected : " & kudosBeforeTest + 1  & " Actual :" & kudosAfterTest)```

### <a name="see-also"></a>另请参阅

[Test Studio 概述](../test-studio.md) <br>
[使用 Test Studio](../working-with-test-studio.md)
