---
title: 柱形图和折线图控件：参考 | Microsoft 文档
description: 了解柱形图和折线图控件（包括属性和示例）
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9c290d28db7ae35d33f4ceb2cd56c3a3ad79b01c
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42832827"
---
# <a name="column-chart-and-line-chart-controls-in-powerapps"></a>PowerApps 中的柱形图和折线图控件
用包含 x 轴和 y 轴的图显示数据的控件。

## <a name="description"></a>描述
“柱形图”和“折线图”为分组控件。 每组包含三个控件：标题[标签](control-text-box.md)、图表图形和图例。

## <a name="chart-key-properties"></a>图表关键属性
**[Items](properties-core.md)** - 控件中显示的数据源，如库、列表或图表。

NumberOfSeries - 柱形图或折线图中反映了多少列的数据。

## <a name="additional-chart-properties"></a>其他图表属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

**[DisabledBorderColor](properties-color-border.md)** – 控件的 [DisplayMode](properties-core.md) 属性设置为“Disabled”时，该控件边框的颜色。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[Font](properties-text.md) – 文本中所显示的字体系列的名称。

GridStyle - 柱形图或折线图是显示 x 轴和/或 y 轴，还是两者都不显示。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

ItemColorSet - 图表中每个数据点的颜色。

ItemsGap - 柱形图中各柱形之间的距离。

* “ItemsGap”属性适用于“柱形图”控件，但不适用于“折线图”控件。

Markers - 柱形图或折线图是否显示每个数据点的值。

MarkerSuffix - 在“Markers”属性设为“true”的柱形图中，每个值后显示的文本。

* “MarkerSuffix”属性适用于“柱形图”控件，但不适用于“折线图”控件。

MinimumBarWidth - 柱形图中的柱形宽度下限。

* “MinimumBarWidth”属性适用于“柱形图”控件，但不适用于“折线图”控件。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

[PaddingBottom](properties-size-location.md) – 控件中的文本与该控件的下边缘之间的距离。

[PaddingLeft](properties-size-location.md) – 控件中的文本与该控件的左边缘之间的距离。

[PaddingRight](properties-size-location.md) – 控件中的文本与该控件的右边缘之间的距离。

[PaddingTop](properties-size-location.md) – 控件中的文本与该控件的上边缘之间的距离。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

SeriesAxisMax - 柱形图或折线图 y 轴的最大值。

* “SeriesAxisMax”属性适用于“柱形图”控件，但不适用于“折线图”控件。

SeriesAxisMin - 柱形图 y 轴的最小值。

* “SeriesAxisMin”属性适用于“柱形图”控件，但不适用于“折线图”控件。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

XLabelAngle - 柱形图或折线图的 x 轴下方的标签角度。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

YAxisMax - 折线图 y 轴的最大值。

* “YAxisMax”属性适用于折线图控件，但不适用于柱形图控件。

YAxisMin - 折线图 y 轴的最小值。

* “YAxisMin” 属性适用于折线图控件，但不适用于柱形图控件。

YLabelAngle - 折线图或柱形图 y 轴旁边标签的角度。

## <a name="related-functions"></a>相关函数
[**Max**( *DataSource*, *ColumnName* )](../functions/function-aggregates.md)

## <a name="example"></a>示例
1. 添加“**[按钮](control-button.md)**”控件，并将其 **[OnSelect](properties-core.md)** 属性设置为以下公式：<br>
   **Collect(Revenue, {Year:"2013", Europa:24000, Ganymede:22300, Callisto:21200}, {Year:"2014", Europa:26500, Ganymede:25700, Callisto:24700},{Year:"2014", Europa:27900, Ganymede:28300, Callisto:25600})**
   
    不知道如何[添加和配置控件](../add-configure-controls.md)？
   
    想要了解有关 **[Collect](../functions/function-clear-collect-clearcollect.md)** 函数或[其他函数](../formula-reference.md)的详细信息？
2. 按 F5 键，单击或点击**[“按钮”](control-button.md)** 控件，然后按 Esc 键返回到默认工作区。
3. 添加“柱形图”或“折线图”控件，将其**[“Items”](properties-core.md)** 属性设为“Revenue”，并将其“NumberOfSeries”属性设为“3”。
   
    此控件将显示每个产品超过三年的收入数据。


## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="color-contrast"></a>颜色对比度
在以下项之间必须有足够的颜色对比度：
* “ItemColorSet”中的每个项
* “ItemColorSet”中的所有项和背景色
* **[Color](properties-color-border.md)** 和背景色

### <a name="screen-reader-support"></a>屏幕阅读器支持
* “图表图形”前必须有一个**[便签](control-text-box.md)** 作为标题。
* 请考虑添加图表图形的摘要。 例如，“折线图显示本年度 3 月和 8 月之间销售额的稳定增长”。

    > [!NOTE]
  > 图表图形和图例对屏幕阅读器用户隐藏。 作为替代方法，将向用户显示表格形式的数据。 他们还可以在用于在图表中选择数据的按钮之间循环。

### <a name="low-vision-support"></a>弱视支持
* 如果显示多个序列，则必须有图例。
* 请考虑将“GridStyle”设置为“GridStyle.All”，以显示两个轴。 这可以帮助所有用户准确地确定数据的规模。
* 对于柱形图，请考虑将“Markers”设置为“true”。 这有助于弱视用户确定柱形的值。

### <a name="keyboard-support"></a>键盘支持
* **[“TabIndex”](properties-accessibility.md)** 必须为零或更大，以便键盘用户可以导航到它。

    > [!NOTE]
  > 当键盘用户导航到图表时，可以在用于在图表中选择数据的按钮之间循环。
