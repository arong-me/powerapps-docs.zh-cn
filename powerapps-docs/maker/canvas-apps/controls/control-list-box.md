---
title: 列表框控件：参考 | Microsoft 文档
description: 有关列表框控件的信息（包括属性和示例）
services: ''
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: 71f3493064e7b877a501f9b91f93adedb0c68f6a
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="list-box-control-in-powerapps"></a>PowerApps 中的列表框控件
用户可以选择一个或多个项的列表。

## <a name="description"></a>说明
**列表框**控件始终显示所有可用的选项（不同于**[下拉](control-drop-down.md)**控件），用户可以一次选择多个项（不同于**[单选](control-radio.md)**控件）。

## <a name="key-properties"></a>关键属性
**[Default](properties-core.md)** - 用户更改控件前的初始值。

**[Items](properties-core.md)** - 控件中显示的数据源，如库、列表或图表。

[!INCLUDE [long-items](../../../includes/long-items.md)]

## <a name="additional-properties"></a>其他属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[FocusedBorderThickness](properties-color-border.md)** – 控件具有键盘焦点时的边框粗细。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件边框的颜色。

[DisabledColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件中的文本颜色。

[DisabledFill](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件的背景颜色。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Font](properties-text.md)** – 文本中所显示的字体系列的名称。

**[FontWeight](properties-text.md)** – 控件中文本的粗细：**粗体**、**半粗体**、**正常**或**细体**。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

**[HoverColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景颜色。

**[Italic](properties-text.md)** – 控件中的文本是否为斜体。

**ItemPaddingLeft** – 列表框中的文本与其左边缘之间的距离。

**[LineHeight](properties-text.md)** - 文本行之间或列表中项之间的距离。

**[OnChange](properties-core.md)** - 用户更改控件的值（例如，通过调整滑块）时应用的响应方式。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[PaddingBottom](properties-size-location.md)** – 控件中的文本与该控件下边缘之间的距离。

**[PaddingLeft](properties-size-location.md)** - 控件中的文本与该控件的左边缘之间的距离。

**[PaddingRight](properties-size-location.md)** - 控件中的文本与该控件的右边缘之间的距离。

**[PaddingTop](properties-size-location.md)** - 控件中的文本与该控件的上边缘之间的距离。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件中的文本的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

**[Reset](properties-core.md)** - 是否还原控件的默认值。

**[SelectionColor](properties-color-border.md)** – 所选项目或列表中项目的文本颜色，或笔控件中选择工具的颜色。

**[SelectionFill](properties-color-border.md)** – 所选项目、列表中项目或笔控件中选定区域的背景颜色。

**SelectMultiple** – 用户是否可以选择列表框中的多个项目。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**[Strikethrough](properties-text.md)** – 通过文本显示的线是否在控件上显示。

**[TabIndex](properties-accessibility.md)** - 设置为非零值时，在运行时自定义控件的选项卡顺序。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**[Underline](properties-text.md)** – 在文本下方显示的线是否在控件上显示。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Distinct**( *DataSource*, *ColumnName* )](../functions/function-distinct.md)

## <a name="example"></a>示例
1. 添加“列表框”控件，将其命名为“CategoryList”，并将其 **[Items](properties-core.md)** 属性设置为以下公式：<br>
   **["Carpet","Hardwood","Tile"]**
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
   
    ![列表框中的地板类别](./media/control-list-box/category-listbox.png)
2. 添加三个**[下拉](control-drop-down.md)**控件，将它们移动到“CategoryList”下，并分别命名为“CarpetList”、“HardwoodList”和“TileList”。
3. 将每个**[下拉](control-drop-down.md)**控件的  **[Items](properties-core.md)** 属性设置为以下值之一：
   
   * CarpetList：**["Caserta Stone Beige","Ageless Beauty Clay", "Lush II Tundra"]**
   * HardwoodList：**["Golden Teak","Natural Hickory", "Victoria Mahogany"]**
   * TileList：**["Honey Onyx Marble","Indian Autumn Slate", "Panaria Vitality Ceramic"]**
     
     ![下拉列表中的地板名称](./media/control-list-box/flooring-names.png)
4. 将每个**[下拉](control-drop-down.md)**控件的 **[Visible](properties-core.md)** 属性设置为以下值之一：
   
   * CarpetList：**If("Carpet" in CategoryList.SelectedItems.Value, true)**
   * HardwoodList：**If("Hardwood" in CategoryList.SelectedItems.Value, true)**
   * TileList：**If("Tile" in CategoryList.SelectedItems.Value, true)**
     
     想要详细了解 **[If](../functions/function-if.md)** 函数或[其他函数](../formula-reference.md)吗？
5. 按 F5，然后在“CategoryList”中选择一个或多个项。
   
    根据你的选择，将显示相应的一个或多个**[下拉](control-drop-down.md)**控件。
   
    ![下拉列表中的地板名称](./media/control-list-box/selected-lists.png)
6. （可选）按 Esc 返回默认工作区。
