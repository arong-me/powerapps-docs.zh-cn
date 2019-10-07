---
title: Power BI 磁贴控件：参考 | Microsoft 文档
description: 有关 Power BI 磁贴控件的信息（包括属性和示例）
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/07/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f258beee317fcdad46d71b504f9c8a3046bb3641
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993363"
---
# <a name="power-bi-tile-control-in-powerapps"></a>PowerApps 中的 Power BI 磁贴控件

在应用内显示 [Power BI](https://powerbi.microsoft.com) 磁贴的控件。

没有 Power BI？ [注册](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi)。

## <a name="description"></a>描述

通过在应用内显示 **[Power BI 磁贴](https://docs.microsoft.com/power-bi/service-dashboard-tiles)** 来利用现有数据分析和报告。 在选项面板的“数据”选项卡中，设置磁贴的 Workspace、Dashboard 和 Tile 属性，指定要显示的磁贴。

## <a name="sharing-and-security"></a>共享和安全性

共享包含 Power BI 内容的应用时，不仅要共享应用本身，还必须共享磁贴所在的[仪表板](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports)。 否则，即使对于打开应用的用户，也不会显示 Power BI 内容。 包含 Power BI 内容的应用遵从该内容的权限。

## <a name="performance"></a>性能

建议不要在应用内同时加载三个以上的 Power BI 磁贴。 可通过设置 LoadPowerBIContent 属性，控制磁贴加载和卸载。

## <a name="pass-a-parameter"></a>传递参数

通过从应用传递单个参数，可以筛选 Power BI 磁贴中显示的结果。 但是，仅支持字符串值和 equals 运算符，并且如果表名或列名包含空格，筛选器可能不起作用。

若要传递单个筛选器值，请修改**TileURL**属性的值，该属性遵循以下语法：

```
"https://app.powerbi.com/embed?dashboardId=<DashboardID>&tileId=<TileID>&config=<SomeHash>"
```

对于该值，附加以下语法：

```
&$filter=<TableName>/<ColumnName> eq '<Value>'
```

参数将筛选图块所源自的报表的数据集中的值。

## <a name="key-properties"></a>关键属性

**Workspace** – 磁贴所在的 Power BI 工作区。

**Dashboard** – 磁贴所在的 Power BI 仪表板。

**Tile** - 要显示的 Power BI 磁贴的名称。

**LoadPowerBIContent** - 设置为 true 时，加载和显示 Power BI 内容。 设置为 false 时，卸载 Power BI 内容，这将释放内存并优化性能。

## <a name="additional-properties"></a>其他属性

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。 默认情况下，将打开与磁贴关联的 Power BI 报表。

TileUrl – 从 Power BI 服务请求磁贴所使用的 URL。 可以通过向 URL 追加参数将单个参数传递到 Power BI 磁贴中（例如：… & "&$filter=Town/Province eq '" & ListBox1.Selected.Abbr & "'"）。 在参数中只能使用等于运算符。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="example"></a>示例

1. 从“插入”选项卡的“控件”菜单中添加“Power BI 磁贴”控件。

    不知道如何[添加和配置控件](../add-configure-controls.md)？

2. 在“选项”面板的“数据”选项卡中，单击或点击“我的工作区”以打开“工作区”设置。

3. 在仪表板列表中选择仪表板，然后在磁贴列表中选择磁贴。

    控件将显示该 Power BI 磁贴。

## <a name="accessibility-guidelines"></a>辅助功能准则

Power BI 磁贴只是 Power BI 内容的容器。 了解如何使用这些 [Power BI 辅助功能提示](https://docs.microsoft.com/power-bi/desktop-accessibility)创建可访问的内容。

如果 Power BI 内容没有标题，请考虑使用 **[标签](control-text-box.md)** 控件添加标题，以便为屏幕阅读器提供支持。 可将标签直接置于 Power BI 磁贴前。
