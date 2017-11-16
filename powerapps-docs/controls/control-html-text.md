---
title: "HTML 文本控件：参考 | Microsoft 文档"
description: "有关 HTML 文本控件的信息（包括属性和示例）"
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
ms.openlocfilehash: bb652f3ba6decad7cb6f93007eaec6340f230ca1
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="html-text-control-in-powerapps"></a>PowerApps 中的 HTML 文本控件
一个框，用于显示文本并将 HTML 标记转换为格式。

## <a name="description"></a>说明
**HTML 文本**控件不仅显示纯文本和数字，还会转换 HTML 标记，例如非换行空格。

## <a name="key-properties"></a>关键属性
**[Color](properties-color-border.md)** – 控件中文本的颜色。

**[Font](properties-text.md)** – 文本中所显示的字体系列的名称。

**HTMLText** - HTML 文本控件中显示且可能包含 HTML 标记的文本。

## <a name="additional-properties"></a>其他属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件边框的颜色。

[DisabledFill](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件的背景颜色。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[PaddingBottom](properties-size-location.md)** - 控件中的文本与该控件的下边缘之间的距离。

**[PaddingLeft](properties-size-location.md)** - 控件中的文本与该控件的左边缘之间的距离。

**[PaddingRight](properties-size-location.md)** - 控件中的文本与该控件的右边缘之间的距离。

**[PaddingTop](properties-size-location.md)** - 控件中的文本与该控件的上边缘之间的距离。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Find**( *FindString*, *WithinString* )](../functions/function-find.md)

## <a name="example"></a>示例
1. 添加一个“[标签](control-text-box.md)”控件，将它命名为“Source”，然后将“[Text](properties-core.md)”属性设置为下面的字符串：

\<p> We have done an unusually \&nbsp; \&quot; deep \&quot; globalization and localization. \<p>

不知道如何[添加、命名和配置控件](../add-configure-controls.md)？

1. 添加 **HTML 文本**控件，并将其 **HTMLText** 属性设置为下面的值：<br>
   **Source.Text**
   
     虽然“HTML 文本”控件显示与“[标签](control-text-box.md)”控件相同的文本，但会将这些标记转换成相应的字符。
