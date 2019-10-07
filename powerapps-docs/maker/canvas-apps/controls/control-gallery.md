---
title: 库控件：参考 | Microsoft 文档
description: 了解库控件（包括属性和示例）
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/25/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 964f57c427b8e9e2e2f7a50e3d6e149ddea8e8b0
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71986665"
---
# <a name="gallery-control-in-canvas-apps"></a>画布应用中的库控件

包含其他控件并显示一组数据的控件。

## <a name="description"></a>描述

“库”控件可以显示数据源中的多条记录，每条记录都能包含多种类型的数据。 例如，“库”控件可以显示多个联系人，其中每一项都用于显示联系人信息，包括每个联系人的姓名、地址和电话号码。 每个数据字段显示在“库”控件的单独控件内，可以在库模板中配置这些控件。 此模板显示为库中的第一项，如果库为水平/横向，此模板显示在“库”控件的左边缘；如果库为垂直/纵向，此模板显示在“库”控件的上边缘。 在模板中执行的任何更改都会反映在整个“库”控件中。

提供了用于在库中显示图像和文本的预定义模板，以及可变高度项的库。

## <a name="limitations"></a>限制

如果用户在加载所有项之前滚动 "**灵活的高度**库" 控件，则在数据加载完成后，可能会向下或向外推送当前正在查看的项。 若要避免此问题，请使用标准**库**控件，而不是**灵活的高度**变体。

## <a name="key-properties"></a>关键属性

[Default](properties-core.md) - 应用启动时，要在库中选择的数据源项或记录。

**[Items](properties-core.md)** – 控件中显示的数据源，如库、列表或图表。

Selected - 选定项。

## <a name="additional-properties"></a>其他属性

**["Accessiblelabel"](properties-accessibility.md)** –屏幕阅读器的库（不是其包含的项）的标签。 应描述项列表是什么。

AllItems - 库中的所有项，其中包括属于库模板的附加控件值。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Fill](properties-color-border.md)** – 控件的背景色。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**ItemAccessibleLabel** –屏幕阅读器的每个库项的标签。 应说明每个项的内容。

NavigationStep - 当库的“ShowNavigation”属性设为“true”，且用户选择库任意一端的导航箭头时，库的滚动距离。

**可选**–是否可以选择库项。 当设置为**true**时，屏幕阅读器会将库标识为可选列表，并通过单击或点击该项来选择项。 当设置为**false**时，屏幕读取器将库标识为常规列表，单击或点击项并不选中。

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

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

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

## <a name="accessibility-guidelines"></a>辅助功能准则

### <a name="color-contrast"></a>颜色对比度

如果在库项中单击任何位置都是要选择它，那么在以下项之间必须有足够的颜色对比度：

* **[BorderColor](properties-color-border.md)** 和库外的颜色（如果没有边框）
* **[Fill](properties-color-border.md)** 和库范围之外的颜色（如果没有边框）

### <a name="screen-reader-support"></a>屏幕阅读器支持

* **[“AccessibleLabel”](properties-accessibility.md)** 必须存在。

    > [!NOTE]
    > 屏幕阅读器将在库中的项目更改时公布。 还将提到“AccessibleLabel”。 这为公告提供上下文，甚至在同一个屏幕上有多个库的情况下更为重要。

* 如果库项包含多个控件，请使用**ItemAccessibleLabel**汇总库项的内容。

* 如果希望用户选择库**项，请**将值设置为**true** 。 否则，将该值设置为**false**。

* 如果库项包含多个控件，请使用**ItemAccessibleLabel**提供库项的内容的摘要。

* **应根据**用户是否打算选择库项，相应地设置可选择。

### <a name="keyboard-support"></a>键盘支持

* 请考虑将“ShowScrollbar”设置为“true”。 在大多数触摸屏设备上，在开始滚动之前，不会显示滚动条。
* 如果在库项中单击任何位置都是要选择它，还必须为键盘用户提供选择库项的方法。 例如，添加一个 **[按钮](control-button.md)** ，并将其“OnSelect”属性设置为“Select(Parent)”。

    > [!NOTE]
  > 库内的键盘导航顺序不考虑库外控件。 库内控件的 **[TabIndex](properties-accessibility.md)** 具有范围限制。 请参阅[辅助功能属性](properties-accessibility.md)了解详细信息。
