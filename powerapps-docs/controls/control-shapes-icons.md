---
title: "形状控件和图标控件：参考 | Microsoft 文档"
description: "有关形状控件和图标控件的信息（包括属性和示例）"
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
ms.openlocfilehash: 7a71695460453816dd5c63dad8477cb7ccc703d7
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="shape-controls-and-icon-controls-in-powerapps"></a>PowerApps 中的形状控件和图标控件
你可以为其配置外观和行为属性的图形。

## <a name="description"></a>说明
这些控件包括箭头、几何形状、操作图标和符号，你可以为其配置诸如 fill、size 和 location 之类的属性。 此外，还可以配置其 **[OnSelect](properties-core.md)** 属性，以便应用在用户单击或点击控件时作出响应。

## <a name="key-properties"></a>关键属性
**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

## <a name="additional-properties"></a>其他属性
[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景颜色。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[FocusedBorderThickness](properties-color-border.md)** – 控件具有键盘焦点时的边框粗细。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Navigate**( *ScreenName*, *ScreenTransition* )](../functions/function-navigate.md)

## <a name="example"></a>示例
1. 将默认“[屏幕](control-screen.md)”控件命名为“Target”，添加“[标签](control-text-box.md)”控件，然后将“[Text](properties-core.md)”属性设置为显示“Target”。
   
    不知道如何[添加和配置控件](../add-configure-controls.md)？
2. 添加**[屏幕](control-screen.md)**控件，然后将其命名为“Source”。
3. 在“Source”中，添加“形状”控件，并将其 **[OnSelect](properties-core.md)** 属性设置为以下公式：
   <br>**Navigate(Target, ScreenTransition.Fade)**
4. 按 F5，然后单击或点击“形状”控件。
   
    将会出现“Target”屏幕。
5. （可选）按 Esc 返回默认工作区，向“Target”添加“形状”控件，并将“形状”控件的 **[OnSelect](properties-core.md)** 属性设置为以下公式：
   <br>**Navigate(Source, ScreenTransition.Fade)**

