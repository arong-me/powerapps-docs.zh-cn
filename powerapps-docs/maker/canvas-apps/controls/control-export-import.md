---
title: 导出控件和导入控件：参考 | Microsoft 文档
description: 有关导出控件和导入控件的信息（包括属性和示例）
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b78f88941fce85b9e63427635cb946f944aa120a
ms.sourcegitcommit: e2a9d1a6090cdd8aa78515b49f38ed2365217ea6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/17/2018
ms.locfileid: "49384262"
---
# <a name="export-control-and-import-control-in-powerapps"></a>PowerApps 中的导出控件和导入控件
该控件用于将数据导出到本地文件，然后将该数据导入到 PowerApps 中的其他应用。

## <a name="description"></a>描述
如果要创建多个应用（该应用使用相同数据，但不在其外部共享该数据），可以使用**导出**控件和**导入**控件将其导出和导入。 导出数据时，创建一个可以复制到其他计算机的压缩文件，但不能在 PowerApps 以外的任何程序中读取该文件。

## <a name="warning"></a>警告
在应用中启用此功能可能会使该应用遭受安全漏洞和数据泄漏的威胁。  建议让用户仅导入已认可和受信任的文件，并仅导出不属于机密或敏感内容的数据。

## <a name="limitations"></a>限制
Web 浏览器中不支持导出功能。

## <a name="key-properties"></a>关键属性
**Data** – 想要导出到本地文件的集合的名称。

* **Data** 属性对**导出**控件可用，但对**导入**控件不可用。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

## <a name="additional-properties"></a>其他属性
**[Align](properties-text.md)** – 文本相对于其控件的水平居中的位置。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[DisabledBorderColor](properties-color-border.md)** – 控件的 [DisplayMode](properties-core.md) 属性设置为“Disabled”时，该控件边框的颜色。

**[DisabledColor](properties-color-border.md)** – 控件的 **[DisplayMode](properties-core.md)** 属性设置为 Disabled**Disabled** 时，该控件中的文本颜色。

**[DisabledFill](properties-color-border.md)** – 控件的“DisplayMode”**[Display Mode](properties-core.md)** 属性设置为“Disabled”**Disabled**时，该控件的背景色。

**[Fill](properties-color-border.md)** – 控件的背景色。

**[FocusedBorderColor](properties-color-border.md)** – 当聚焦到控件时，控件的边框颜色。

**[FocusedBorderThickness](properties-color-border.md)** – 当聚焦到控件时，控件的边框粗细。

[Font](properties-text.md) – 文本中所显示的字体系列的名称。

**[FontWeight](properties-text.md)** – 控件中文本的粗细：**粗体**、**半粗体**、**正常**或**细体**。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

[HoverColor](properties-color-border.md) – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景色。

**[Italic](properties-text.md)** – 控件中的文本是否为斜体。

**[Padding](properties-size-location.md)** – 导入或导出按钮上的文本和该按钮边缘之间的距离。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件中的文本的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

**[RadiusBottomLeft](properties-size-location.md)** – 控件左下角圆角的程度。

**[RadiusBottomRight](properties-size-location.md)** – 控件右下角圆角的程度。

**[RadiusTopLeft](properties-size-location.md)** – 控件左上角圆角的程度。

[RadiusTopRight](properties-size-location.md) – 控件右上角圆角的程度。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

[Strikethrough](properties-text.md) – 通过文本显示的线是否在控件上显示。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

**[Text](properties-core.md)** – 在控件上显示或用户键入到控件中的文本。

[Underline](properties-text.md) – 在文本下方显示的线是否在控件上显示。

[VerticalAlign](properties-text.md) – 控件上的文本相对于该控件垂直居中的位置。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="example"></a>示例
1. 添加“**[按钮](control-button.md)**”控件，并将其 **[OnSelect](properties-core.md)** 属性设置为以下公式：
   <br>**ClearCollect(Products, {Name:"Europa", Price:"10.99"}, {Name:"Ganymede", Price:"12.49"}, {Name:"Callisto", Price:"11.79"})**
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
   
    想要了解有关 **[ ClearCollect](../functions/function-clear-collect-clearcollect.md)** 函数或[其他函数](../formula-reference.md)的详细信息？
2. 按 F5，单击或点击“**[按钮](control-button.md)**”控件，然后按 Esc。
3. 添加“**导出**”控件，并将其 **Data** 属性设置为“**产品**”。
4. 按 F5，单击或点击“**导出**”控件，然后指定要将数据导出的文件名称。
5. 单击或点击“**保存**”，然后按 Esc 返回默认工作区。
6. 在新的或现有应用中，添加“**导入**”控件，将其命名为 **MyData**，并将其 **[OnSelect](properties-core.md)** 属性设置以下此公式：<br>
   **Collect(ImportedProducts, MyData.Data)**
7. 按 F5，单击或点击 **MyData**，再单击或点击导出的文件，然后单击或点击“**打开**”。
8. 按 Esc，单击或点击“**文件**”菜单上的“**集合**”，并确认当前应用中包含你导出的数据。


## <a name="accessibility-guidelines"></a>辅助功能准则
适用 **[按钮](control-button.md)** 的相同准则，因为“导出”和“导入”是专用按钮。
