---
title: 饼图控件：参考 | Microsoft 文档
description: 有关饼图控件的信息（包括属性和示例）
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
ms.openlocfilehash: 2037de5ab55839b5908fb4789ca3fcda6836f4d9
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650347"
---
# <a name="pie-chart-control-in-powerapps"></a>PowerApps 中的饼图控件
该控件用于显示与其他内容相比较的相对值。

## <a name="description"></a>描述
如果要从最左侧列中包含标签的表中显示相对数据，以及显示左起第二列中的值，请添加“饼图”控件。

此控件是包含三个控件的分组控件： **[标题标签](control-text-box.md)** 、图表图形和图例。

## <a name="chart-key-properties"></a>图表关键属性
**[Items](properties-core.md)** - 控件中显示的数据源，如库、列表或图表。

**ShowLabels** - 饼图是否显示与每个其楔形相关联的值。

## <a name="additional-chart-properties"></a>其他图表属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[DisabledBorderColor](properties-color-border.md)** – 控件的 [DisplayMode](properties-core.md) 属性设置为“Disabled”时，该控件边框的颜色。

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

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Max**( *DataSource*, *ColumnName* )](../functions/function-aggregates.md)

## <a name="example"></a>示例
1. 添加“ **[按钮](control-button.md)** ”控件，并将其 **[OnSelect](properties-core.md)** 属性设置为以下公式：<br>
   **Collect(Revenue2015, {Product:"Europa", Revenue:27000}, {Product:"Ganymede", Revenue:26300}, {Product:"Callisto", Revenue:29200})**
   
    不知道如何[添加和配置控件](../add-configure-controls.md)？
   
    想要了解有关 **[Collect](../functions/function-clear-collect-clearcollect.md)** 函数或[其他函数](../formula-reference.md)的详细信息？
2. 按 F5，单击或点击“[按钮](control-button.md)”控件，然后按 Esc 返回到默认工作区。
3. 添加**饼图**控件，然后将其 [Items](properties-core.md) 属性设置为 **Revenue2015**。
   
    **饼图**控件显示每个产品与其他产品之间相关的收入数据。


## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="color-contrast"></a>颜色对比度
在以下项之间必须有足够的颜色对比度：
* “ItemColorSet”中的每个项
* “ItemColorSet”中的所有项和背景色
* **[Color](properties-color-border.md)** 和背景色

### <a name="screen-reader-support"></a>屏幕阅读器支持
* “图表图形”前必须有一个便签作为 **[标题](control-text-box.md)** 。

    > [!NOTE]
  > “图表图形”和“图例”对屏幕阅读器用户隐藏。 作为替代方法，将向用户显示表格形式的数据。 他们还可以在用于在图表中选择数据的按钮之间循环。

### <a name="low-vision-support"></a>弱视支持
* “Legend”必须存在。
* 请考虑将“ShowLabels”设置为“true”。 这可以帮助弱视用户快速确定每个饼图扇区所表示的内容。
* 请考虑将“LabelPosition”设置为“LabelPosition.Outside”。 这样可以提高标签的易读性，因为颜色对比度更一致。

### <a name="keyboard-support"></a>键盘支持
* **[“TabIndex”](properties-accessibility.md)** 必须为零或更大，以便键盘用户可以导航到它。

    > [!NOTE]
  > 当键盘用户导航到图表时，可以在用于在图表中选择数据的按钮之间循环。
