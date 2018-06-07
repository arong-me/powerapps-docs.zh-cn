---
title: 大小和位置属性 | Microsoft 文档
description: Height 和 Width 等属性的参考资料
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 10/25/2016
ms.author: gregli
ms.openlocfilehash: 7df2782bc18d1c999383226e31033035fb59cea1
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "31839076"
---
# <a name="size-and-location-properties-in-powerapps"></a>PowerApps 中的大小和位置属性
## <a name="overview"></a>概述
配置控件（或控件元素）的大小及其在所在屏幕中的位置。

## <a name="position"></a>位置
**X**控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。 对于多列容器中的“[数据卡](control-card.md)”控件，此属性将确定数据卡出现在哪一列。

* 适用于**[添加图片](control-add-picture.md)**、**[音频](control-audio-video.md)**、**[按钮](control-button.md)**、**[照相机](control-camera.md)**、**[卡片](control-card.md)**、**[复选框](control-check-box.md)**、**[柱形图](control-column-line-chart.md)**、**[日期选取器](control-date-picker.md)**、**[显示窗体](control-form-detail.md)**、**[下拉列表](control-drop-down.md)**、**[编辑窗体](control-form-detail.md)**、**[导出](control-export-import.md)**、**[库](control-gallery.md)**、**[HTML 文本](control-html-text.md)**、**[图标](control-shapes-icons.md)**、**[图像](control-image.md)**、**[导入](control-export-import.md)**、**[标签](control-text-box.md)**、**[折线图](control-column-line-chart.md)**、**[列表框](control-list-box.md)**、**[麦克风](control-microphone.md)**、**[PDF 查看器](control-pdf-viewer.md)**、**[笔输入](control-pen-input.md)**、**[饼图](control-pie-chart.md)**、**[单选按钮](control-radio.md)**、**[评分](control-rating.md)**、**[形状](control-shapes-icons.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)**、**[计时器](control-timer.md)**、**[切换](control-toggle.md)** 和**[视频](control-audio-video.md)** 控件。

**Y** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。 对于多行容器中的[数据卡](control-card.md)控件，此属性将确定数据卡出现在哪一行。

* 适用于**[添加图片](control-add-picture.md)**、**[音频](control-audio-video.md)**、**[按钮](control-button.md)**、**[照相机](control-camera.md)**、**[卡片](control-card.md)**、**[复选框](control-check-box.md)**、**[柱形图](control-column-line-chart.md)**、**[日期选取器](control-date-picker.md)**、**[显示窗体](control-form-detail.md)**、**[下拉列表](control-drop-down.md)**、**[编辑窗体](control-form-detail.md)**、**[导出](control-export-import.md)**、**[库](control-gallery.md)**、**[HTML 文本](control-html-text.md)**、**[图标](control-shapes-icons.md)**、**[图像](control-image.md)**、**[导入](control-export-import.md)**、**[标签](control-text-box.md)**、**[折线图](control-column-line-chart.md)**、**[列表框](control-list-box.md)**、**[麦克风](control-microphone.md)**、**[PDF 查看器](control-pdf-viewer.md)**、**[笔输入](control-pen-input.md)**、**[饼图](control-pie-chart.md)**、**[单选按钮](control-radio.md)**、**[评分](control-rating.md)**、**[形状](control-shapes-icons.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)**、**[计时器](control-timer.md)**、**[切换](control-toggle.md)** 和**[视频](control-audio-video.md)** 控件。

## <a name="size"></a>大小
**Height** - 控件上边缘和下边缘之间的距离。

* 适用于**[添加图片](control-add-picture.md)**、**[音频](control-audio-video.md)**、**[按钮](control-button.md)**、**[照相机](control-camera.md)**、**[卡片](control-card.md)**、**[复选框](control-check-box.md)**、**[柱形图](control-column-line-chart.md)**、**[日期选取器](control-date-picker.md)**、**[显示窗体](control-form-detail.md)**、**[下拉列表](control-drop-down.md)**、**[编辑窗体](control-form-detail.md)**、**[导出](control-export-import.md)**、**[库](control-gallery.md)**、**[HTML 文本](control-html-text.md)**、**[图标](control-shapes-icons.md)**、**[图像](control-image.md)**、**[导入](control-export-import.md)**、**[标签](control-text-box.md)**、**[折线图](control-column-line-chart.md)**、**[列表框](control-list-box.md)**、**[麦克风](control-microphone.md)**、**[PDF 查看器](control-pdf-viewer.md)**、**[笔输入](control-pen-input.md)**、**[饼图](control-pie-chart.md)**、**[单选按钮](control-radio.md)**、**[评分](control-rating.md)**、**[形状](control-shapes-icons.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)**、**[计时器](control-timer.md)**、**[切换](control-toggle.md)** 和**[视频](control-audio-video.md)** 控件。

**AutoHeight** - 标签是否会在“[Text](properties-core.md)”属性包含超过控件可显示的字符数时自动变高。  

* 适用于**[标签](control-text-box.md)**

**Width** - 控件左边缘和右边缘之间的距离。

* 适用于**[添加图片](control-add-picture.md)**、**[音频](control-audio-video.md)**、**[按钮](control-button.md)**、**[照相机](control-camera.md)**、**[卡片](control-card.md)**、**[复选框](control-check-box.md)**、**[柱形图](control-column-line-chart.md)**、**[日期选取器](control-date-picker.md)**、**[显示窗体](control-form-detail.md)**、**[下拉列表](control-drop-down.md)**、**[编辑窗体](control-form-detail.md)**、**[导出](control-export-import.md)**、**[库](control-gallery.md)**、**[HTML 文本](control-html-text.md)**、**[图标](control-shapes-icons.md)**、**[图像](control-image.md)**、**[标签](control-text-box.md)**、**[导入](control-export-import.md)**、**[折线图](control-column-line-chart.md)**、**[列表框](control-list-box.md)**、**[麦克风](control-microphone.md)**、**[PDF 查看器](control-pdf-viewer.md)**、**[笔输入](control-pen-input.md)**、**[饼图](control-pie-chart.md)**、**[单选按钮](control-radio.md)**、**[评分](control-rating.md)**、**[形状](control-shapes-icons.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)**、**[计时器](control-timer.md)**、**[切换](control-toggle.md)** 和**[视频](control-audio-video.md)** 控件。

**WidthFit** - 控件是否会自动水平变宽，以填充容器控件（如“[编辑表单](control-form-detail.md)”控件）的所有空白空间。 如果多张数据卡将此属性设置为“true”，那么空白空间会被这些数据卡均分。 有关详细信息，请参阅[了解数据表单布局](../working-with-form-layout.md)。

* 适用于[数据卡](control-card.md)

## <a name="padding"></a>填充
**Padding** - 导入或导出按钮上的文本和该按钮边缘之间的距离。

* 适用于**[添加图片](control-add-picture.md)**、**[导出](control-export-import.md)** 和**[导入](control-export-import.md)** 控件。

**PaddingBottom** - 控件中的文本与该控件的下边缘之间的距离。

* 适用于**[按钮](control-button.md)**、**[复选框](control-check-box.md)**、**[柱形图](control-column-line-chart.md)**、**[日期选取器](control-date-picker.md)**、**[下拉列表](control-drop-down.md)**、**[HTML 文本](control-html-text.md)**、**[图像](control-image.md)**、**[标签](control-text-box.md)**、**[折线图](control-column-line-chart.md)**、**[列表框](control-list-box.md)**、**[PDF 查看器](control-pdf-viewer.md)**、**[单选按钮](control-radio.md)** 和**[文本输入](control-text-input.md)** 控件。

**PaddingLeft** - 控件中的文本与该控件的左边缘之间的距离。

* 适用于**[按钮](control-button.md)**、**[复选框](control-check-box.md)**、**[柱形图](control-column-line-chart.md)**、**[日期选取器](control-date-picker.md)**、**[下拉列表](control-drop-down.md)**、**[HTML 文本](control-html-text.md)**、**[图像](control-image.md)**、**[标签](control-text-box.md)**、**[折线图](control-column-line-chart.md)**、**[列表框](control-list-box.md)**、**[PDF 查看器](control-pdf-viewer.md)**、**[单选按钮](control-radio.md)** 和**[文本输入](control-text-input.md)** 控件。

**PaddingRight** - 控件中的文本与该控件的右边缘之间的距离。

* 适用于**[按钮](control-button.md)**、**[复选框](control-check-box.md)**、**[柱形图](control-column-line-chart.md)**、**[日期选取器](control-date-picker.md)**、**[下拉列表](control-drop-down.md)**、**[HTML 文本](control-html-text.md)**、**[图像](control-image.md)**、**[标签](control-text-box.md)**、**[折线图](control-column-line-chart.md)**、**[列表框](control-list-box.md)**、**[PDF 查看器](control-pdf-viewer.md)**、**[单选按钮](control-radio.md)** 和**[文本输入](control-text-input.md)** 控件。

**PaddingTop** - 控件中的文本与该控件的上边缘之间的距离。

* 适用于**[按钮](control-button.md)**、**[复选框](control-check-box.md)**、**[柱形图](control-column-line-chart.md)**、**[日期选取器](control-date-picker.md)**、**[下拉列表](control-drop-down.md)**、**[HTML 文本](control-html-text.md)**、**[图像](control-image.md)**、**[标签](control-text-box.md)**、**[折线图](control-column-line-chart.md)**、**[列表框](control-list-box.md)**、**[PDF 查看器](control-pdf-viewer.md)**、**[单选按钮](control-radio.md)** 和**[文本输入](control-text-input.md)** 控件。

## <a name="radius"></a>半径
**RadiusBottomLeft** - 控件左下角圆角的程度。

* 适用于**[按钮](control-button.md)**、**[导出](control-export-import.md)**、**[图像](control-image.md)**、**[导入](control-export-import.md)** 和**[文本输入](control-text-input.md)** 控件。

**RadiusBottomRight** - 控件右下角圆角的程度。

* 适用于**[按钮](control-button.md)**、**[导出](control-export-import.md)**、**[图像](control-image.md)**、**[导入](control-export-import.md)** 和**[文本输入](control-text-input.md)** 控件。

**RadiusTopLeft** - 控件左上角圆角的程度。

* 适用于**[按钮](control-button.md)**、**[导出](control-export-import.md)**、**[图像](control-image.md)**、**[导入](control-export-import.md)** 和**[文本输入](control-text-input.md)** 控件。

**RadiusTopRight** - 控件右上角圆角的程度。

* 适用于**[按钮](control-button.md)**、**[导出](control-export-import.md)**、**[图像](control-image.md)**、**[导入](control-export-import.md)** 和**[文本输入](control-text-input.md)** 控件。

