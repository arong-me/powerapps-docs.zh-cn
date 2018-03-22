---
title: Power BI 磁贴控件：参考 | Microsoft 文档
description: 有关 Power BI 磁贴控件的信息（包括属性和示例）
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
ms.date: 07/07/2016
ms.author: fikaradz
ms.openlocfilehash: 1f351877e3c05b83b4bd9cfa104a7eb22cef5028
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="power-bi-tile-control-in-powerapps"></a>PowerApps 中的 Power BI 磁贴控件
在应用内显示 [Power BI ](https://powerbi.microsoft.com) 磁贴的控件。

## <a name="description"></a>说明
通过在应用内显示 **[Power BI 磁贴](https://docs.microsoft.com/power-bi/service-dashboard-tiles)**来利用现有数据分析和报告。  通过在选项面板的“数据”选项卡设置磁贴的“Workspace”、“Dashboard”和“Tile”属性来选择想要显示的磁贴。

## <a name="sharing-and-security"></a>共享和安全性
共享后，有权访问 PowerApp 的所有用户均可访问此应用。  但是，若要使 Power BI 内容对这些用户可见，需要将磁贴所在的仪表板与 Power BI 上的用户[共享](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports)。  这样可确保在应用中访问 Power BI 内容时 Power BI 共享权限受到尊重。

## <a name="key-properties"></a>关键属性
**Workspace** – 磁贴所在的 Power BI 工作区。

**Dashboard** – 磁贴所在的 Power BI 仪表板。

**Tile** – 想要显示的 Power BI 磁贴的名称。

## <a name="additional-properties"></a>其他属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。 默认行为会将用户转到此磁贴关联的 Power BI 报表。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="example"></a>示例
1. 从“插入”选项卡的“控件”菜单中添加“Power BI 磁贴”控件。  
2. 在“选项”面板的“数据”选项卡中，为“工作区”设置选择“我的工作区”。  从仪表板列表中选择一个仪表板，并从磁贴列表中选择一个磁贴。
   
    控件将显示该 Power BI 磁贴。
   
    不知道如何[添加和配置控件](../add-configure-controls.md)？
   
   没有 Power BI？ [注册](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi)。

