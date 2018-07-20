---
title: 形状控件和图标控件：参考 | Microsoft 文档
description: 有关形状控件和图标控件的信息（包括属性和示例）
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: 12865bf432ed31f0964add63fa024182680fb7aa
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39022392"
---
# <a name="shape-controls-and-icon-controls-in-powerapps"></a>PowerApps 中的形状控件和图标控件
你可以为其配置外观和行为属性的图形。

## <a name="description"></a>描述
这些控件包括箭头、几何形状、操作图标和符号，你可以为其配置诸如 fill、size 和 location 之类的属性。 此外，还可以配置其 **[OnSelect](properties-core.md)** 属性，以便应用在用户单击或点击控件时作出响应。

## <a name="key-properties"></a>关键属性
**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

## <a name="additional-properties"></a>其他属性
**[AccessibleLabel](properties-accessibility.md)** – 屏幕阅读器标签。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[FocusedBorderColor](properties-color-border.md)** – 当聚焦到控件时，控件的边框颜色。

**[FocusedBorderThickness](properties-color-border.md)** – 当聚焦到控件时，控件的边框粗细。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景色。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数

[**Navigate**( *ScreenName*, *ScreenTransition* )](../functions/function-navigate.md)

## <a name="example"></a>示例

1. 将默认“[屏幕](control-screen.md)”控件命名为“Target”，添加“[标签](control-text-box.md)”控件，然后将“[Text](properties-core.md)”属性设置为显示“Target”。

    不知道如何[添加和配置控件](../add-configure-controls.md)？

2. 添加**[屏幕](control-screen.md)** 控件，然后将其命名为“Source”。
3. 在“Source”中，添加“形状”控件，并将其 **[OnSelect](properties-core.md)** 属性设置为以下公式：<br>**Navigate(Target, ScreenTransition.Fade)**
4. 按 F5，然后单击或点击“形状”控件。

    将会出现“Target”屏幕。

5. （可选）按 Esc 返回默认工作区，向“Target”添加“形状”控件，并将“形状”控件的 **[OnSelect](properties-core.md)** 属性设置为以下公式：
   <br>Navigate(Source, ScreenTransition.Fade)


## <a name="accessibility-guidelines"></a>辅助功能准则

### <a name="color-contrast"></a>颜色对比度

以下仅适用于用作按钮的图形，或者不只是用于修饰。

对于图标：
* **[Color](properties-color-border.md)** 和 **[Fill](properties-color-border.md)**
* 其他[标准颜色对比度要求](../accessible-apps-color.md)适用（如果用作按钮）

对于带边框的形状：
* **[BorderColor](properties-color-border.md)** 和控件范围之外的颜色
* **[FocusedBorderColor](properties-color-border.md)** 和控件范围之外的颜色（如果用作按钮）

对于没有边框的形状：
* **[Fill](properties-color-border.md)** 和控件范围之外的颜色
* **[PressedFill](properties-color-border.md)** 和控件范围之外的颜色（如果用作按钮）
* **[HoverFill](properties-color-border.md)** 和控件范围之外的颜色（如果用作按钮）

### <a name="screen-reader-support"></a>屏幕阅读器支持
* 如果图形用作按钮或者不仅仅用于修饰，则**[“AccessibleLabel”](properties-accessibility.md)** 必须存在。
* 如果图形纯粹用于修饰作用，**[AccessibleLabel](properties-accessibility.md)** 必须为空或空字符串 ""。 这将导致屏幕阅读器忽略图形。
* 如果图形提供冗余信息，**[AccessibleLabel](properties-accessibility.md)** 可以为空或空字符串 ""。

    例如，“设置”图标将其 **[AccessibleLabel](properties-accessibility.md)** 设置为“Settings”。 此图标不用作按钮。 它位于同样显示“Setting”的**[标签](control-text-box.md)** 旁边。 屏幕阅读器将图标读作“Setting”，并再次将标签读作“Setting”。 没必要对此进行详细说明。 在此情况下，该图标不需要**[“AccessibleLabel”](properties-accessibility.md)**。

    > [!IMPORTANT]
    > 屏幕阅读器将始终读取 **[TabIndex](properties-accessibility.md)** 为零或更大的图标或形状，即使 **[AccessibleLabel](properties-accessibility.md)** 为空。 这是因为它们以按钮形式呈现。 如果没有提供 **[AccessibleLabel](properties-accessibility.md)**，屏幕阅读器只需将图形读作“按钮”。

### <a name="keyboard-support"></a>键盘支持
* 如果图形用作按钮，**[TabIndex](properties-accessibility.md)** 必须为零或更大。 这允许键盘用户导航到它。
* 如果图形用作按钮，焦点指示器必须清楚显示。 可以使用**[“FocusedBorderColor”](properties-color-border.md)** 和**[“FocusedBorderThickness”](properties-color-border.md)** 来实现此目的。

    > [!NOTE]
  > 当**[“TabIndex”](properties-accessibility.md)** 为零或更大，图标或形状将以按钮形式呈现。 可视外观没有变化，但屏幕阅读器将正确识别作为按钮的图像。 当 **[TabIndex](properties-accessibility.md)** 小于零时，图标或形状将被标识为图像。
