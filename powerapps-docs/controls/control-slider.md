---
title: "滑块控件：参考 | Microsoft 文档"
description: "有关滑块控件的信息，包括属性和示例"
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
ms.openlocfilehash: dc10ac44c1c14f182c39176a6b0216f3ede3816d
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="slider-control-in-powerapps"></a>PowerApps 中的滑块控件
一个控件，用户可通过拖动图柄使用该控件指定值。

## <a name="description"></a>说明
用户可通过左右或上下拖动滑块图柄来指示介于指定的最小值和最大值之间的值，具体取决于所选方向。

## <a name="key-properties"></a>关键属性
**[Default](properties-core.md)** – 用户更改控件前的初始值。

**Max** - 用户可对滑块或评分设置的最大值。

**Min** - 用户可对滑块设置的最小值。

**[Value](properties-core.md)** - 输入控件的值。

## <a name="additional-properties"></a>其他属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[FocusedBorderThickness](properties-color-border.md)** - 控件具有键盘焦点时，该控件边框的粗细。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件边框的颜色。

**HandleActiveFill** - 用户更改滑块值时，该滑块图柄的颜色。

**HandleFill** - 切换控件或滑块控件中的图柄（用于更改位置的元素）颜色。

**HandleHoverFill** - 用户将鼠标指针停留在滑块上时，该滑块中的图柄颜色。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

**Layout** - 用户是滚动浏览库还是从上至下（**垂直**）或从左至右（**水平**）调整滑块。

**[OnChange](properties-core.md)** - 用户更改控件的值（例如，通过调整滑块）时应用的响应方式。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**RailFill** - 切换控件的值为 **false** 时该控件中矩形的背景色，或滑块控件中图柄右侧线条的颜色。

**RailHoverFill** - 将鼠标悬停在切换控件或滑块上时，切换控件（其值为 **false**）中矩形的背景色，或滑块控件中图柄右侧线条的颜色。

**ReadOnly** - 用户是否可以更改滑块或评分控件的值。

**[Reset](properties-core.md)** - 控件是否还原为其默认值。

**ShowValue** – 用户更改滑块或评分的值或将鼠标悬停在控件上时，是否显示该值。

**[TabIndex](properties-accessibility.md)** - 设置为非零值时，在运行时自定义控件的选项卡顺序。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**ValueFill** - 切换控件的值为 **true** 时该控件中矩形的背景色，或滑块控件中图柄左侧线条的颜色。

**ValueHoverFill** - 将鼠标指针停留在切换控件或滑块上时，切换控件（其值为 **true**）中矩形的背景色，或滑块控件中图柄左侧线条的颜色。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Sum**( *Value1*, *Value2* )](../functions/function-aggregates.md)

## <a name="example"></a>示例
1. 添加一个按钮，然后将其 **[OnSelect](properties-core.md)** 属性设置为以下公式：
   <br>**ClearCollect(CityPopulations, {City:"London", Country:"United Kingdom", Population:8615000}, {City:"Berlin", Country:"Germany", Population:3562000}, {City:"Madrid", Country:"Spain", Population:3165000}, {City:"Rome", Country:"Italy", Population:2874000}, {City:"Paris", Country:"France", Population:2273000}, {City:"Hamburg", Country:"Germany", Population:1760000}, {City:"Barcelona", Country:"Spain", Population:1602000}, {City:"Munich", Country:"Germany", Population:1494000}, {City:"Milan", Country:"Italy", Population:1344000})**
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
   
    想要了解有关**[ ClearCollect](../functions/function-clear-collect-clearcollect.md)** 函数或[其他函数](../formula-reference.md)的详细信息？
2. 按 F5，选择该按钮，然后按 Esc。
3. 添加一个滑块，将其移动到按钮下方，然后将滑块命名为 **MinPopulation**。
4. 将滑块的 **Max** 属性设置为 **5000000**，**Min** 属性设置为 **1000000**。
5. 在垂直方向/纵向添加一个文本库，将其移动到滑块下方，然后将该库的 **[Items](properties-core.md)** 属性设置为以下公式：<br>
   **Filter(CityPopulations, Population > MinPopulation)**
6. 在库的第一个项中，将顶部标签的“[Text](properties-core.md)”属性设置为“ThisItem.City”，然后将底部标签的“[Text](properties-core.md)”属性设置为以下公式：<br> **Text(ThisItem.Population, "##,###")**
7. 按 F5，然后调整 **MinPopulation** 以仅显示人口数大于所指定值的城市。
8. 若要返回到默认工作区，请按 Esc。

