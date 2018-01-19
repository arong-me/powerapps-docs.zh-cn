---
title: "饼图控件：参考 | Microsoft 文档"
description: "有关饼图控件的信息（包括属性和示例）"
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
ms.openlocfilehash: 1388eac45e5086f677cb83c8db9593fe01a9819f
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/12/2018
---
# <a name="pie-chart-control-in-powerapps"></a>PowerApps 中的饼图控件
该控件用于显示与其他内容相比较的相对值。

## <a name="description"></a>说明
如果要从最左侧列中包含标签的表中显示相对数据，以及显示左起第二列中的值，请添加“饼图”控件。

## <a name="key-properties"></a>关键属性
**[Items](properties-core.md)** - 控件中显示的数据源，如库、列表或图表。

**ShowLabels** - 饼图是否显示与每个其楔形相关联的值。

## <a name="additional-properties"></a>其他属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件边框的颜色。

**Explode** - 饼图中楔形间的距离。

**[Font](properties-text.md)** – 文本中所显示的字体系列的名称。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

**ItemBorderColor** - 饼图中每个楔形周围边框的颜色。

**ItemBorderThickness** - 饼图中每个楔形周围边框的粗细。

**ItemColorSet** – 图表中每个数据点的颜色。

**LabelPosition** - 饼图中标签相对于楔形的位置。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Max**( *DataSource*, *ColumnName* )](../functions/function-aggregates.md)

## <a name="example"></a>示例
1. 添加“**[按钮](control-button.md)**”控件，并将其 **[OnSelect](properties-core.md)** 属性设置为以下公式：<br>
   **收集 (Revenue2015，{产品:"木"，收入： 27000}，{产品:"木"，收入： 26300}，{产品:"Callisto"，收入： 29200})**
   
    不知道如何[添加和配置控件](../add-configure-controls.md)？
   
    想要了解有关 **[Collect](../functions/function-clear-collect-clearcollect.md)** 函数或[其他函数](../formula-reference.md)的详细信息？
2. 按 F5，单击或点击“[按钮](control-button.md)”控件，然后按 Esc 返回到默认工作区。
3. 添加**饼图**控件，然后将其 [Items](properties-core.md) 属性设置为 **Revenue2015**。
   
    **饼图**控件显示每个产品与其他产品之间相关的收入数据。

