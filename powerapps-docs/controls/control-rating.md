---
title: "评分控件 | Microsoft 文档"
description: "有关评分控件的信息（包括属性和示例）"
services: 
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: 4dd23b8c94ee4760e40b4513e7a88667f85c3a4b
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="rating-control-in-powerapps"></a>PowerApps 中的评分控件
用户可以用于指示介于 1 和你指定的最大数之间的值的控件。

## <a name="description"></a>说明
例如，用户可以在此控件中通过选择一定数量的星星来表示他们对某些内容所喜爱的程度。

## <a name="key-properties"></a>关键属性
**[Default](properties-core.md)** – 用户更改控件前的初始值。

**Max** – 用户可对滑块或评分设置的最大值。

## <a name="additional-properties"></a>其他属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[FocusedBorderThickness](properties-color-border.md)** - 控件具有键盘焦点时，该控件边框的粗细。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[OnChange](properties-core.md)** – 用户更改控件的值（例如，通过调整滑块）时应用的响应方式。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**RatingFill** – 评分控件中星星的颜色。

**ReadOnly** – 用户是否可以更改滑块或评分控件的值。

**[Reset](properties-core.md)** - 控件是否还原为其默认值。

**ShowValue** – 用户更改滑块或评分的值或将鼠标悬停在控件上时，是否显示该值。

**[TabIndex](properties-accessibility.md)** - 设置为非零值时，在运行时自定义控件的选项卡顺序。

**[Tooltip](properties-core.md)** – 用户将鼠标悬停在控件上时显示的解释性文本。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Average**( *Value1*, *Value2,* ... )](../functions/function-aggregates.md)

## <a name="example"></a>示例
1. 添加“评分”控件，并将其命名为“定量”。
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 添加**[“文本输入”](control-text-input.md)**控件，将其命名为“定性”，并将其移至“评分”控件下。
3. 将**[“文本输入”](control-text-input.md)**控件的**[“Default”](properties-core.md)**属性设置为 **""**，并将其“HintText”设置为以下公式：
   <br>**If(Quantitative.Value > 3, "What did you especially like?", "How might we do better?")**
   
    想要了解有关 **[If](../functions/function-if.md)** 函数或[其他函数](../formula-reference.md)的详细信息？
4. 按 F5，然后在“评分”控件中单击或点击四颗或五颗星。
   
    **[文本输入](control-text-input.md)**控件中的提示文本将发生变化以体现高评分。
5. 在“定量”中单击或点击少于四颗星。
   
    **[Text input](control-text-input.md)** 控件中的提示文本将发生变化以体现低评分。
6. 若要返回默认工作区，请按 Esc。

