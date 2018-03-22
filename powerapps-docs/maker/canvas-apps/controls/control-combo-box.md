---
title: 组合框控件：参考 | Microsoft 文档
description: 了解组合框控件（包括属性和示例）
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
ms.date: 09/13/2017
ms.author: fikaradz
ms.openlocfilehash: 4d298e24ea967cbf5cb47638d4296f6efbd758c7
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="combo-box-control-in-powerapps"></a>PowerApps 中的组合框控件
用户可以在其中提供的选项之间进行选择的控件。  支持搜索和多重选择。

## <a name="description"></a>说明
使用组合框控件，可以搜索要选择的项。  由于搜索是在服务器端对 SearchField 属性执行，因此性能不受非常大的数据源影响。  

单选或多重选择模式是通过 SelectMultiple 属性进行配置。

搜索要选择的项时，可以对所有项修改“数据”窗格中的“布局”设置，选择是显示一个数据值、两个数据值，还是一张图片和两个值（“人员”模板）。

## <a name="people-picker"></a>人员选取器
若要将组合框用作人员选取器，请从“数据”窗格的“布局”设置中选择“人员”模板，并配置要显示的如下人员相关数据属性。

## <a name="key-properties"></a>关键属性
**[Items](properties-core.md)** - 提供待选选项的数据源。

**DefaultItems** - 用户与控件交互前的初始选定项。

**SelectedItems** - 用户交互后的选定项列表。

**SelectMultiple** - 用户是能选择一个项，还是能选择多个项。

**IsSearchable** - 用户能否在选择前先搜索项。

## <a name="additional-properties"></a>其他属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[Default](properties-core.md)** - 单选模式下用户更改选项前的初始选定项。

**DisplayFields** - 针对搜索返回的每个项显示的字段列表。  通过“属性选项”选项卡中的“数据”窗格进行配置最为简单。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**InputTextPlaceholder** - 在用户未选中项时向最终用户显示的说明文字。

**OnChange** - 在用户更改选项时，应用如何响应。

**OnNavigate** - 在用户单击项时，应用如何响应。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="example"></a>示例
1. 使用“插入”选项卡中的“控件”菜单，添加组合框控件。  
2. 在“属性选项”选项卡中，单击“数据”。  
3. 在下面选择数据源、布局和相关属性。
4. 在“高级”选项卡中设置 SelectMultiple 属性。

    正常运行的组合框将会在应用中显示。

    不知道如何[添加和配置控件](../add-configure-controls.md)？
