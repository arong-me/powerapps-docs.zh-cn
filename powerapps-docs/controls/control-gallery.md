---
title: "库控件：参考 | Microsoft 文档"
description: "了解库控件（包括属性和示例）"
services: 
suite: powerapps
documentationcenter: na
author: RickSaling
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/25/2017
ms.author: ricksal
ms.openlocfilehash: a85c0f3e0468c249641e40c3a0b7fb7f1d32a916
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="gallery-control-in-powerapps"></a>PowerApps 中的库控件
包含其他控件并显示一组数据的控件。

## <a name="description"></a>说明
“库”控件可以显示数据源中的多条记录，每条记录都能包含多种类型的数据。 例如，“库”控件可以显示多个联系人，其中每一项都用于显示联系人信息，包括每个联系人的姓名、地址和电话号码。 每个数据字段显示在“库”控件的单独控件内，可以在库模板中配置这些控件。 此模板显示为库中的第一项，如果库为水平/横向，此模板显示在“库”控件的左边缘；如果库为垂直/纵向，此模板显示在“库”控件的上边缘。 在模板中执行的任何更改都会反映在整个“库”控件中。

不仅可以预定义库模板来显示图像、文本，还可以使用库来显示高度不同的项。

## <a name="key-properties"></a>关键属性
[Default](properties-core.md) - 应用启动时，要在库中选择的数据源项或记录。

**[Items](properties-core.md)** – 控件中显示的数据源，如库、列表或图表。

Selected - 选定项。

## <a name="additional-properties"></a>其他属性
AllItems - 库中的所有项，其中包括属于库模板的附加控件值。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

Layout - 用户在滚动浏览库时是从上向下（**垂直**）还是从左向右（**水平**）滚动滑块。

NavigationStep - 当库的“ShowNavigation”属性设为“true”，且用户选择库任意一端的导航箭头时，库的滚动距离。

ShowNavigation - 是否在库的每一端显示一个箭头，以便用户可以通过单击或点击箭头滚动浏览库中的项。

ShowScrollbar - 当用户将鼠标悬停在库之上时，是否显示滚动条。

Snap - 当用户滚动浏览库时，库是否会自动对齐，以便完整显示下一项。

TemplateFill - 库的背景色。

TemplatePadding - 库中各项之间的距离。

TemplateSize - 当库为垂直/纵向时，模板的高度；当库为水平/横向时，模板的宽度。

Transition - 当用户将鼠标悬停在库中一项之上时的视觉效果（“Pop”、“Push”或“None”）。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

WrapCount - 每行或每列（具体取决于是水平布局还是垂直布局）显示的项数。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**Filter**( *DataSource*, *Formula* )](../functions/function-filter-lookup.md)

## <a name="examples"></a>示例
### <a name="show-and-filter-data"></a>显示和筛选数据
* [显示文本](control-text-box.md#show-data-in-a-gallery)
* [显示图像](control-image.md#show-a-set-of-images-from-a-data-source)
* [通过选择列表选项筛选数据](control-drop-down.md#example)
* [通过调整滑块筛选数据](control-slider.md#example)

### <a name="get-data-from-the-user"></a>从用户获取数据
* [获取文本](control-text-input.md#collect-data)
* [获取图像](control-add-picture.md#add-images-to-an-image-gallery-control)
* [获取照片](control-camera.md#example)
* [获取声音](control-microphone.md#example)
* [获取绘图](control-pen-input.md#create-a-set-of-images)

