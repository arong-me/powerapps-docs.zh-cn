---
title: Color 和 border 属性 | Microsoft 文档
description: 有关 BorderColor、HoverBorderColor 和 PressedBorderColor 等属性的参考信息
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 69b15887894bba576364ced8bab9f47eceeb8f96
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731912"
---
# <a name="color-and-border-properties-in-power-apps"></a>Power Apps 中的颜色和边框属性

## <a name="overview"></a>概述

根据用户与控件交互的方式来配置控件的样式。

可以通过多种方式指定颜色：

- [**颜色**](../functions/function-colors.md)枚举：指定级联样式表中的颜色名称，如以下示例中所示：

  - **Color.Red**
  - **Color.Indigo**

- [**ColorValue**](../functions/function-colors.md)函数：指定文本字符串，如级联样式表和十六进制代码表示法（ **#** ）中的颜色名称，如以下示例中所示：

  - **ColorValue （"AliceBlue"）**
  - **ColorValue("#ff00ff")**

- [**ColorFade**](../functions/function-colors.md)函数：指定颜色的褪色程度（从完全黑色（-100%）为完全空白（100%），如本示例所示：

  - **ColorFade （红灯，50%）**

- [**RGBA**](../functions/function-colors.md)函数：指定颜色从0到255的红色、绿色和蓝色分量，并指定从0% （完全透明）到100% （完全不透明）的 alpha 通道，如以下示例中所示：

  - **RGBA （255，0，255，25%）**

颜色属性还可以引用其他颜色属性。 例如， **PressedColor**可以设置为公式**Label1。颜色**，自动将更改从一个属性级联到另一个属性。

## <a name="normal"></a>一般

以下属性一般在用户不与控件交互时起作用。

BorderColor — 控件边框的颜色。

- 适用于 **[添加图片](control-add-picture.md)** 、 **[音频](control-audio-video.md)** 、 **[按钮](control-button.md)** 、 **[照相机](control-camera.md)** 、 **[卡片](control-card.md)** 、 **[复选框](control-check-box.md)** 、 **[柱形图](control-column-line-chart.md)** 、 **[日期选取器](control-date-picker.md)** 、 **[显示窗体](control-form-detail.md)** 、 **[下拉](control-drop-down.md)** 列表、 **[编辑窗体](control-form-detail.md)** 、 **[导出](control-export-import.md)** 、 **[库](control-gallery.md)** 、 **[HTML 文本](control-html-text.md)** 、 **[图像](control-image.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[折线图](control-column-line-chart.md)** 、 **[列表框](control-list-box.md)** 、 **[麦克风](control-microphone.md)** 、 **[PDF 查看器](control-pdf-viewer.md)** 、 **[笔输入](control-pen-input.md)** 、 **[饼图](control-pie-chart.md)** 、 **[广播](control-radio.md)** 、 **[分级](control-rating.md)** 、 **[滑块](control-slider.md)** 、 **[文本输入](control-text-input.md)** 、 **[计时器](control-timer.md)** 、 **[切换](control-toggle.md)** 和 **[视频](control-audio-video.md)** 控件。

BorderStyle – 控件边框是“实线”、“虚线”、“点线”还是“无”。

- 适用于 **[添加图片](control-add-picture.md)** 、 **[音频](control-audio-video.md)** 、 **[按钮](control-button.md)** 、 **[照相机](control-camera.md)** 、 **[卡片](control-card.md)** 、 **[复选框](control-check-box.md)** 、 **[柱形图](control-column-line-chart.md)** 、 **[日期选取器](control-date-picker.md)** 、 **[显示窗体](control-form-detail.md)** 、 **[下拉](control-drop-down.md)** 列表、 **[编辑窗体](control-form-detail.md)** 、 **[导出](control-export-import.md)** 、 **[库](control-gallery.md)** 、 **[HTML 文本](control-html-text.md)** 、 **[图像](control-image.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[折线图](control-column-line-chart.md)** 、 **[列表框](control-list-box.md)** 、 **[麦克风](control-microphone.md)** 、 **[PDF 查看器](control-pdf-viewer.md)** 、 **[笔输入](control-pen-input.md)** 、 **[饼图](control-pie-chart.md)** 、 **[广播](control-radio.md)** 、 **[分级](control-rating.md)** 、 **[滑块](control-slider.md)** 、 **[文本输入](control-text-input.md)** 、 **[计时器](control-timer.md)** 、 **[切换](control-toggle.md)** 和 **[视频](control-audio-video.md)** 控件。

**BorderThickness** – 控件边框的粗细。

- 适用于 **[添加图片](control-add-picture.md)** 、 **[音频](control-audio-video.md)** 、 **[按钮](control-button.md)** 、 **[照相机](control-camera.md)** 、 **[卡片](control-card.md)** 、 **[复选框](control-check-box.md)** 、 **[柱形图](control-column-line-chart.md)** 、 **[日期选取器](control-date-picker.md)** 、 **[显示窗体](control-form-detail.md)** 、 **[下拉](control-drop-down.md)** 列表、 **[编辑窗体](control-form-detail.md)** 、 **[导出](control-export-import.md)** 、 **[库](control-gallery.md)** 、 **[HTML 文本](control-html-text.md)** 、 **[图像](control-image.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[折线图](control-column-line-chart.md)** 、 **[列表框](control-list-box.md)** 、 **[麦克风](control-microphone.md)** 、 **[PDF 查看器](control-pdf-viewer.md)** 、 **[笔输入](control-pen-input.md)** 、 **[饼图](control-pie-chart.md)** 、 **[广播](control-radio.md)** 、 **[分级](control-rating.md)** 、 **[滑块](control-slider.md)** 、 **[文本输入](control-text-input.md)** 、 **[计时器](control-timer.md)** 、 **[切换](control-toggle.md)** 和 **[视频](control-audio-video.md)** 控件。

**Color** – 控件中文本的颜色。

- 适用于 **[添加图片](control-add-picture.md)** 、 **[按钮](control-button.md)** 、 **[复选框](control-check-box.md)** 、 **[柱形图](control-column-line-chart.md)** 、 **[日期选取器](control-date-picker.md)** 、 **[下拉](control-drop-down.md)** 列表 **[、导出](control-export-import.md)** 、 **[HTML 文本](control-html-text.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[折线图](control-column-line-chart.md)** 、 **[列表框](control-list-box.md)** 、 **[麦克风](control-microphone.md)** 、 **[笔输入](control-pen-input.md)** 、 **[饼图](control-pie-chart.md)** 、 **[收音机](control-radio.md)** 、 **[文本输入](control-text-input.md)** 和 **[计时器](control-timer.md)** 控件。

Fill – 控件的背景色。

- 适用于 **[添加图片](control-add-picture.md)** 、 **[音频](control-audio-video.md)** 、 **[按钮](control-button.md)** 、 **[卡片](control-card.md)** 、 **[复选框](control-check-box.md)** 、 **[日期选取器](control-date-picker.md)** 、 **[显示窗体](control-form-detail.md)** 、 **[下拉](control-drop-down.md)** 列表、 **[编辑窗体](control-form-detail.md)** 、 **[导出](control-export-import.md)** 、 **[库](control-gallery.md)** 、 **[HTML 文本](control-html-text.md)** 、 **[图标](control-shapes-icons.md)** 、 **[图像](control-image.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[列表框](control-list-box.md)** 、 **[麦克风](control-microphone.md)** 、 **[PDF 查看器](control-pdf-viewer.md)** 、 **[笔输入](control-pen-input.md)** 、 **[收音机](control-radio.md)** 、 **[分级](control-rating.md)** 、 **[屏幕](control-screen.md)** 、 **[形状](control-shapes-icons.md)** 、 **[文本输入](control-text-input.md)** 、 **[计时器](control-timer.md)** 、 **[切换](control-toggle.md)** 和 **[视频](control-audio-video.md)** 控件。

## <a name="focused"></a>Focused

以下属性在控件聚焦时起作用。

**FocusedBorderColor** – 聚焦时控件的边框颜色。

**FocusedBorderThickness** – 聚焦时控件的边框粗细。

- 这些属性适用于 **[添加图片](control-add-picture.md)** 、 **[附件](control-attachments.md)** 、 **[音频](control-audio-video.md)** 、 **[按钮](control-button.md)** 、 **[照相机](control-camera.md)** 、 **[复选框](control-check-box.md)** 、 **[组合框](control-combo-box.md)** 、 **[日期选取器](control-date-picker.md)** 、 **[下拉](control-drop-down.md)** 列表、 **[导出](control-export-import.md)** 、 **[库](control-gallery.md)** 、 **[图标](control-shapes-icons.md)** 、 **[图像](control-image.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[列表框](control-list-box.md)** 、 **[麦克风](control-microphone.md)** 、 **[广播](control-radio.md)** 、 **[分级](control-rating.md)** 、 **[形状](control-shapes-icons.md)** 、 **[滑块](control-slider.md)** 、 **[文本输入](control-text-input.md)** 、 **[计时器](control-timer.md)** 、 **[切换](control-toggle.md)** 和 **[视频](control-audio-video.md)** 控件。

## <a name="disabled"></a>Disabled

以下属性在控件被禁用时起作用。  如果 [Disabled](properties-core.md) 属性设置为“true”，则可以禁用控件。

**DisabledBorderColor** – 控件的 **[“DisplayMode”](properties-core.md)** 属性设置为 **“Disabled”** 时，该控件边框的颜色。

- 适用于 **[添加图片](control-add-picture.md)** 、 **[按钮](control-button.md)** 、 **[复选框](control-check-box.md)** 、 **[柱形图](control-column-line-chart.md)** 、 **[日期选取器](control-date-picker.md)** 、 **[下拉](control-drop-down.md)** 列表 **[、导出](control-export-import.md)** 、 **[HTML 文本](control-html-text.md)** 、 **[图像](control-image.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[折线图](control-column-line-chart.md)** 、 **[列表框](control-list-box.md)** 、 **[麦克风](control-microphone.md)** 、 **[PDF 查看器](control-pdf-viewer.md)** 、 **[饼图](control-pie-chart.md)** 、 **[广播](control-radio.md)** 、 **[滑块](control-slider.md)** 、 **[文本输入](control-text-input.md)** 、 **[计时器](control-timer.md)** 和 **[切换](control-toggle.md)** 控件。

DisabledColor – 控件的 [DisplayMode](properties-core.md) 属性设置为“Disabled” 时，该控件中的文本颜色。

- 适用于[添加图片](control-add-picture.md)、[按钮](control-button.md)、[复选框](control-check-box.md)、[日期选取器](control-date-picker.md)、[下拉列表](control-drop-down.md)、[导出](control-export-import.md)、[导入](control-export-import.md)、[标签](control-text-box.md)、[列表框](control-list-box.md)、[麦克风](control-microphone.md)、[单选](control-radio.md)、[文本输入](control-text-input.md)和[计时器](control-timer.md)控件。

DisabledFill– 控件的 [DisplayMode](properties-core.md) 属性设置为“Disabled”时，该控件的背景色。

- 适用于[添加图片](control-add-picture.md)、[按钮](control-button.md)、[复选框](control-check-box.md)、[日期选取器](control-date-picker.md)、[下拉列表](control-drop-down.md)、[导出](control-export-import.md)、[HTML 文本](control-html-text.md)、[图像](control-image.md)、[导入](control-export-import.md)、[标签](control-text-box.md)、[列表框](control-list-box.md)、[麦克风](control-microphone.md)、[单选](control-radio.md)、[文本输入](control-text-input.md)和[计时器](control-timer.md)控件。

## <a name="hover"></a>Hover

以下属性在用户将鼠标悬停在控件上时起作用。

HoverBorderColor – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

- 适用于 **[添加图片](control-add-picture.md)** 、 **[按钮](control-button.md)** 、 **[复选框](control-check-box.md)** 、 **[柱形图](control-column-line-chart.md)** 、 **[下拉](control-drop-down.md)** 列表、 **[导出](control-export-import.md)** 、 **[HTML 文本](control-html-text.md)** 、 **[图像](control-image.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[折线图](control-column-line-chart.md)** 、 **[列表框](control-list-box.md)** 、 **[麦克风](control-microphone.md)** 、 **[PDF 查看器](control-pdf-viewer.md)** 、 **[饼图](control-pie-chart.md)** 、 **[滑块](control-slider.md)** 、 **[文本输入](control-text-input.md)** 、 **[计时器](control-timer.md)** 和 **[切换](control-toggle.md)** 控件。

HoverColor – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

- 适用于[添加图片](control-add-picture.md)、[按钮](control-button.md)、[复选框](control-check-box.md)、[下拉列表](control-drop-down.md)、[导出](control-export-import.md)、[导入](control-export-import.md)、[标签](control-text-box.md)、[列表框](control-list-box.md)、[麦克风](control-microphone.md)、[单选](control-radio.md)、[文本输入](control-text-input.md)和[计时器](control-timer.md)控件。

HoverFill – 用户将鼠标指针停留在控件上时，该控件的背景色。

- 适用于[添加图片](control-add-picture.md)、[按钮](control-button.md)、[复选框](control-check-box.md)、[下拉列表](control-drop-down.md)、[导出](control-export-import.md)、[图标](control-shapes-icons.md)、 **[图像](control-image.md)** 、[导入](control-export-import.md)、[标签](control-text-box.md)、[列表框](control-list-box.md)、[麦克风](control-microphone.md)、[单选](control-radio.md)、[形状](control-shapes-icons.md)、[文本输入](control-text-input.md)和[计时器](control-timer.md)控件。

## <a name="pressed"></a>Pressed

以下属性在按下按钮或图像控件时起作用。

PressedBorderColor – 用户在点击或单击控件时，该控件边框的颜色。

- 适用于 **[添加图片](control-add-picture.md)** 、 **[按钮](control-button.md)** 、 **[复选框](control-check-box.md)** 、 **[柱形图](control-column-line-chart.md)** 、 **[下拉](control-drop-down.md)** 列表、 **[导出](control-export-import.md)** 、 **[图标](control-shapes-icons.md)** 、 **[图像](control-image.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[折线图](control-column-line-chart.md)** 、 **[列表框](control-list-box.md)** 、 **[麦克风](control-microphone.md)** 、 **[PDF 查看器](control-pdf-viewer.md)** 、 **[饼图](control-pie-chart.md)** 、 **[形状](control-shapes-icons.md)** 、 **[滑块](control-slider.md)** 、 **[文本输入](control-text-input.md)** 、 **[计时器](control-timer.md)** 和 **[切换](control-toggle.md)** 控件。

PressedColor – 用户在点击或单击控件时，该控件中的文本颜色。

- 适用于[添加图片](control-add-picture.md)、[按钮](control-button.md)、[复选框](control-check-box.md)、[下拉列表](control-drop-down.md)、[导出](control-export-import.md)、[导入](control-export-import.md)、[标签](control-text-box.md)、[列表框](control-list-box.md)、[麦克风](control-microphone.md)、[单选](control-radio.md)、[文本输入](control-text-input.md)和[计时器](control-timer.md)控件。

PressedFill – 用户在点击或单击控件时，该控件的背景色。

- 适用于[添加图片](control-add-picture.md)、[按钮](control-button.md)、[复选框](control-check-box.md)、[下拉列表](control-drop-down.md)、[导出](control-export-import.md)、[图像](control-image.md)、[导入](control-export-import.md)、[标签](control-text-box.md)、[列表框](control-list-box.md)、[麦克风](control-microphone.md)、[单选](control-radio.md)、[文本输入](control-text-input.md)和[计时器](control-timer.md)控件。

## <a name="selection"></a>Selection

以下属性在用户选定控件中的某项时起作用。

SelectionColor – 列表中选定项的文本颜色或笔控件中选择工具的颜色。

- 适用于[下拉列表](control-drop-down.md)、[列表框](control-list-box.md)和[笔输入](control-pen-input.md)控件。

SelectionFill – 列表中选定项的背景色或笔控件中选定区域的背景色。

- 适用于[下拉列表](control-drop-down.md)和[列表框](control-list-box.md)控件。