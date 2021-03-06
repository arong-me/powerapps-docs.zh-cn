---
title: 创建规则 | Microsoft 文档
description: 逐步介绍了如何创建规则，从而生成应用逻辑
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 52deddf87a1c3ee4604591110cfb08eb2d2680b8
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74672991"
---
# <a name="create-a-rule-in-canvas-apps"></a>在画布应用中创建规则
创建根据指定条件自动修改应用的规则。 例如，根据列表项状态以红色、黄色或绿色显示列表项，或仅对特定用户（如管理人员）显示批准按钮。 可以向各种控件添加规则。 本主题中添加的规则用于在滑块控件的值大于 70 时，更改标签控件的文字颜色。

> [!IMPORTANT]
> 2019年10月14日生效，画布应用中的规则功能已弃用。 详细信息：[博客：画布规则功能弃用](https://powerapps.microsoft.com/blog/canvas-rules-feature-deprecation/)。

## <a name="add-a-rule"></a>添加规则
1. 选择控件（或添加并选择控件）。

    在本主题中，[添加标签和滑块](add-configure-controls.md)，将标签的 Text 属性设置为 Slider1.Value，再选择滑块。

1. 在右侧面板中，依次单击或点击“规则”和“新建规则”。

    ![新建规则](./media/working-with-rules/new-rule.png)

    如果选择的控件已定义有一个或多个规则，可以单击或点击任意规则进行编辑。  

## <a name="add-a-condition"></a>添加条件
条件是计算结果为 true 或 false 的表达式，如值是否大于 70。 可以使用模板或从头开始编写表达式，并能根据 UI 中的指导 (Intellisense) 自定义表达式。

1. 单击或点击“添加条件”，再单击模板或“自定义条件”。

    在本主题中，单击或点击“大于”。

    ![添加条件](./media/working-with-rules/rule-conditions.png)

1. 将表达式更新为定义何时应用规则。

    对于本主题，将 0 更改为 70，生成如下表达式： <br>**Slider1.Value > 70**

## <a name="add-an-action"></a>添加操作
操作定义了在应用规则时会发生些什么。 Power Apps 可根据你对控件所做的更改自动创建操作。

1. 单击或点击“定义操作”。

    ![定义操作](./media/working-with-rules/rule-define-actions.png)

1. 在确认对话框中，单击或点击 "**转到**"，以便 Power Apps 捕获下一个或多个操作的更改或更改。

1. 配置一个或多个控件，以满足条件为 true 时的预期要求。

    在本主题中，更改标签颜色。

    ![捕获属性](./media/working-with-rules/rule-capture-properties.png)

1. （可选）单击或点击“显示操作”，预览所做的更改。

    ![预览操作](./media/working-with-rules/rule-review-actions.png)

1. 添加完操作后，单击或点击“完成”。

1. 检查规则的条件和操作。

    ![检查规则](./media/working-with-rules/rule-review.png)

## <a name="rename-the-rule"></a>重命名规则

1. 将鼠标悬停在“Rule1”之上，并单击或点击编辑按钮。

    ![将鼠标悬停在规则名称之上](./media/working-with-rules/hover-over-rules_name.png)

1. 输入规则的新名称。

    ![重命名规则](./media/working-with-rules/rename-rule.png)

1. 单击或点击“完成”，以消除编辑器。

## <a name="test-the-rule"></a>测试规则
1. 按 F5（或单击靠近右上角的播放按钮）预览应用。

    ![打开预览](./media/working-with-rules/open-preview.png)

1. 指定为 true 的条件，再确认操作是否符合预期。

    在本主题中，将滑块的值设置为大于 70，再确认标签文本的颜色是否变化。

## <a name="see-all-rules"></a>查看所有规则
默认情况下，“规则”选项卡仅显示选定控件的规则，以及规则条件或操作中使用的所有子控件的规则。 若要在应用中显示所有规则，请清除“仅显示此控件的规则”复选框。

![删除筛选器](./media/working-with-rules/rules-filter.png)

## <a name="known-limitations"></a>已知的限制
截至本文撰写之时：

* 无法在条件中指定窗体或库的 ThisItem 属性。
