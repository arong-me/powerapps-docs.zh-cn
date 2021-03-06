---
title: 形状控件和图标控件：参考 | Microsoft 文档
description: 有关形状控件和图标控件的信息（包括属性和示例）
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f46199d0265cf042ebae5dd27ae308fad7eca8e6
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732050"
---
# <a name="shape-controls-and-icon-controls-in-power-apps"></a>Power Apps 中的形状控件和图标控件
你可以为其配置外观和行为属性的图形。

## <a name="description"></a>描述
这些控件包括箭头、几何形状、操作图标和符号，你可以为其配置诸如 fill、size 和 location 之类的属性。 还可以配置其 **[OnSelect](properties-core.md)** 属性，以便在用户选择控件时应用程序做出响应。

## <a name="key-properties-icons-and-shapes"></a>键属性（图标和形状）
**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[OnSelect](properties-core.md)** -用户选择控件时应用的响应方式。

## <a name="key-properties-icons-only"></a>键属性（仅图标）

**Icon** -要显示的图标类型（例如， **ArrowDown**或**ShoppingCart**）。 

**旋转**-要将图标旋转的度数。 

**Color** ：按名称或 RGBA 值的图标的颜色。

## <a name="additional-properties"></a>其他属性
[AccessibleLabel](properties-accessibility.md) – 屏幕阅读器标签。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[FocusedBorderColor](properties-color-border.md) – 当聚焦到控件时，控件的边框颜色。

[FocusedBorderThickness](properties-color-border.md) – 当聚焦到控件时，控件的边框粗细。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景颜色。

**[PressedBorderColor](properties-color-border.md)** –用户选择控件时，该控件边框的颜色。

**[PressedFill](properties-color-border.md)** -当用户选择控件时，该控件的背景色。

**[TabIndex](properties-accessibility.md)** - 相对于其他控件的键盘导航顺序。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

[Width](properties-size-location.md) – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数

[**Navigate**( *ScreenName*, *ScreenTransition* )](../functions/function-navigate.md)

## <a name="example"></a>示例

1. 将默认“[屏幕](control-screen.md)”控件命名为“Target”，添加“[标签](control-text-box.md)”控件，然后将“[Text](properties-core.md)”属性设置为显示“Target”。

    不知道如何[添加和配置控件](../add-configure-controls.md)？

1. 添加 **[屏幕](control-screen.md)** 控件，然后将其命名为“Source”。

1. 在“Source”中，添加“形状”控件，并将其 **[OnSelect](properties-core.md)** 属性设置为以下公式：

  `Navigate(Target, ScreenTransition.Fade)`
  
1. 按 F5，然后选择**形状**控件。

    将会出现“Target”屏幕。

1. （可选）按 Esc 返回默认工作区，向“Target”添加“形状”控件，并将“形状”控件的 **[OnSelect](properties-core.md)** 属性设置为以下公式：

  `Navigate(Source, ScreenTransition.Fade)`

## <a name="accessibility-guidelines"></a>辅助功能准则

### <a name="color-contrast"></a>颜色对比度

以下仅适用于用作按钮的图形，或者不只是用于修饰。

对于图标：
- **[Color](properties-color-border.md)** 和 **[Fill](properties-color-border.md)**
- 其他[标准颜色对比度要求](../accessible-apps-color.md)适用（如果用作按钮）

对于带边框的形状：
- **[BorderColor](properties-color-border.md)** 和控件范围之外的颜色
- **[FocusedBorderColor](properties-color-border.md)** 和控件范围之外的颜色（如果用作按钮）

对于没有边框的形状：
- **[Fill](properties-color-border.md)** 和控件范围之外的颜色
- **[PressedFill](properties-color-border.md)** 和控件范围之外的颜色（如果用作按钮）
- **[HoverFill](properties-color-border.md)** 和控件范围之外的颜色（如果用作按钮）

### <a name="screen-reader-support"></a>屏幕阅读器支持
- 如果图形用作按钮，则必须将 **["accessiblelabel"](properties-accessibility.md)** 设置为非空字符串，否则不能仅将其用于修饰。

- 如果图形提供冗余信息或纯粹用于修饰，则 **["accessiblelabel"](properties-accessibility.md)** 必须为空或空字符串 **""** 。 此值会使屏幕阅读器忽略图形。

例如，可以将 "**设置**" 图标的 " **[" accessiblelabel "](properties-accessibility.md)** " 属性设置为 "**设置**"。 此图标不用作按钮。 它位于同样显示 "**设置**" 的 **[标签](control-text-box.md)** 旁边。 屏幕阅读器将图标和标签作为 "**设置**" 进行读取，这是不必要的。 在这种情况下，图标不需要 **["accessiblelabel"](properties-accessibility.md)** 。

> [!IMPORTANT]
> 如果将图标或形状的 **["accessiblelabel"](properties-accessibility.md)** 设置为空字符串，并且其 **[TabIndex](properties-accessibility.md)** 设置为零或更大，屏幕阅读器会将其作为**按钮**读取。 此类图标或形状以按钮形式呈现。 

### <a name="keyboard-support"></a>键盘支持
- 如果图形用作按钮，则 **[TabIndex](properties-accessibility.md)** 必须为零或更大。 如果为图标或形状设置此值，则键盘用户可以导航到它。

- 如果图形用作按钮，则焦点指示器必须清晰可见。 使用 **[FocusedBorderColor](properties-color-border.md)** 和 **[FocusedBorderThickness](properties-color-border.md)** 实现此结果。

    > [!NOTE]
    > 当 **[“TabIndex”](properties-accessibility.md)** 为零或更大，图标或形状将以按钮形式呈现。 其外观不会改变，但屏幕阅读器会将图像正确地标识为按钮。 当 **[TabIndex](properties-accessibility.md)** 小于零时，图标或形状将被标识为图像。
