---
title: "创建规则 | Microsoft 文档"
description: "逐步介绍了如何创建规则，从而生成应用逻辑"
services: 
suite: PowerApps
documentationcenter: na
author: karthik-1
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/14/2017
ms.author: karthikb
ms.openlocfilehash: c6b7141c20591c1fdbb5278b1fe4d75bfb6a4ebb
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="create-a-rule-in-powerapps"></a>在 PowerApps 中创建规则
创建根据指定条件自动修改应用的规则。 例如，根据列表项状态以红色、黄色或绿色显示列表项，或仅对特定用户（如管理人员）显示批准按钮。

可以向各种控件添加规则。 本主题中添加的规则用于在滑块控件的值大于 70 时，更改标签控件的文字颜色。

## <a name="add-a-rule"></a>添加规则
1. 选择控件（或添加并选择控件）。
   
    在本主题中，[添加标签和滑块](add-configure-controls.md)，将标签的 Text 属性设置为 Slider1.Value，再选择滑块。
2. 在右侧面板中，依次单击或点击“规则”和“新建规则”。
   
    ![新建规则](./media/working-with-rules/new-rule.png)
   
    如果选择的控件已定义有一个或多个规则，可以单击或点击任意规则进行编辑。  

## <a name="add-a-condition"></a>添加条件
条件是计算结果为 true 或 false 的表达式，如值是否大于 70。 可以使用模板或从头开始编写表达式，并能根据 UI 中的指导 (Intellisense) 自定义表达式。

1. 单击或点击“添加条件”，再单击模板或“自定义条件”。
   
    在本主题中，单击或点击“大于”。
   
    ![添加条件](./media/working-with-rules/rule-conditions.png)
2. 完成表达式，定义规则何时适用。
   
    本主题使用以下表达式： <br>**Value(Slider1.Value) > 70**
   
    **注意**：截至本文撰写之时，必须指定待比较的控件属性。 在今后推出的版本中，PowerApps 可能就会推断出控件的常见属性（如 Text 或 Value）。

## <a name="add-an-action"></a>添加操作
操作定义了在应用规则时会发生些什么。 PowerApps 可根据用户做出的控件更改自动创建操作。

1. 单击或点击“定义操作”。
   
    ![定义操作](./media/working-with-rules/rule-define-actions.png)
2. 在确认对话框中，单击或点击“开始吧”，这样 PowerApps 就会捕获接下来的更改（一个或多个）作为一项或多项操作。
3. 配置一个或多个控件，以满足条件为 true 时的预期要求。
   
    在本主题中，更改标签颜色。
   
    ![捕获属性](./media/working-with-rules/rule-capture-properties.png)
4. （可选）单击或点击“显示操作”，预览所做的更改。
   
    ![预览操作](./media/working-with-rules/rule-review-actions.png)
5. 添加完操作后，单击或点击“完成”。
6. 检查规则的条件和操作，再单击或点击“完成”进行保存。
   
    ![检查规则](./media/working-with-rules/rule-review.png)

## <a name="test-the-rule"></a>测试规则
1. 按 F5（或单击靠近右上角的播放按钮）预览应用。
   
    ![打开预览](./media/working-with-rules/open-preview.png)
2. 指定为 true 的条件，再确认操作是否符合预期。
   
    在本主题中，将滑块的值设置为大于 70，再确认标签文本的颜色是否变化。

## <a name="known-limitations"></a>已知的限制
截至本文撰写之时：

* 无法重命名规则。
* 无法在条件中指定窗体或库的 ThisItem 属性。

