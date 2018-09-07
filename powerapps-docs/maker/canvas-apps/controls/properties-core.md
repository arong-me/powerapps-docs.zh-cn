---
title: Core 属性 | Microsoft 文档
description: 有关 Disabled、Visible 和 ReadOnly 属性的参考信息
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 16065dc29d74655cbede25cea20148b343b790e6
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42853998"
---
# <a name="core-properties-in-powerapps"></a>PowerApps 中的核心属性
配置用户是否能看到控件并与之交互。

### <a name="properties"></a>属性
**Default**：用户更改控件前的初始值。

* 适用于**[卡片](control-card.md)**、**[复选框](control-check-box.md)**、**[下拉列表](control-drop-down.md)**、**[库](control-gallery.md)**、**[列表框](control-list-box.md)**、**[单选按钮](control-radio.md)**、**[评级](control-rating.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)** 和**[切换](control-toggle.md)** 控件。

**DelayOutput**：设置为 true，可在文本输入期间延迟操作。

* 适用于**[文本输入](control-text-input.md)**、**[卡片](control-card.md)**

**DisplayMode** – 值可以是 Edit、View 或 Disabled。 配置控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。  在 View 模式时，输入控件（如[文本输入](control-text-input.md)、[下拉列表](control-drop-down.md)、[日期选取器](control-date-picker.md)）将仅显示文本值，不会呈现任何交互元素或修饰。  这使它们适合以表单形式或可读输出形式进行显示。

* 适用于**[添加图片](control-add-picture.md)**、**[音频](control-audio-video.md)**、**[按钮](control-button.md)**、**[照相机](control-camera.md)**、**[复选框](control-check-box.md)**、**[柱形图](control-column-line-chart.md)**、**[日期选取器](control-date-picker.md)**、**[下拉列表](control-drop-down.md)**、**[导出](control-export-import.md)**、**[库](control-gallery.md)**、**[HTML 文本](control-html-text.md)**、**[图标](control-shapes-icons.md)**、**[图像](control-image.md)**、**[导入](control-export-import.md)**、**[标签](control-text-box.md)**、**[折线图](control-column-line-chart.md)**、**[列表框](control-list-box.md)**、**[麦克风](control-microphone.md)**、**[PDF 查看器](control-pdf-viewer.md)**、**[笔输入](control-pen-input.md)**、**[饼图](control-pie-chart.md)**、**[单选按钮](control-radio.md)**、**[评分](control-rating.md)**、**[形状](control-shapes-icons.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)**、**[计时器](control-timer.md)**、**[切换](control-toggle.md)** 和**[视频](control-audio-video.md)** 控件。

**Items**：在库、列表或图表等控件中显示的数据的源。

* 适用于**[柱形图](control-column-line-chart.md)**、**[下拉列表](control-drop-down.md)**、**[库](control-gallery.md)**、**[折线图](control-column-line-chart.md)**、**[列表框](control-list-box.md)**、**[饼图](control-pie-chart.md)** 和**[单选按钮](control-radio.md)** 控件。

**OnChange** - 用户更改控件的值（例如，通过调整滑块）时应用的响应方式。

* 适用于**[添加图片](control-add-picture.md)**、**[下拉列表](control-drop-down.md)**、**[列表框](control-list-box.md)**、**[单选按钮](control-radio.md)**、**[评级](control-rating.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)** 和**[切换](control-toggle.md)** 控件。

**OnSelect**：用户点击或单击控件时应用的响应方式。

* 适用于**[添加图片](control-add-picture.md)**、**[按钮](control-button.md)**、**[照相机](control-camera.md)**、**[复选框](control-check-box.md)**、**[柱形图](control-column-line-chart.md)**、**[日期选取器](control-date-picker.md)**、**[下拉列表](control-drop-down.md)**、**[导出](control-export-import.md)**、**[HTML 文本](control-html-text.md)**、**[图标](control-shapes-icons.md)**、**[图像](control-image.md)**、**[导入](control-export-import.md)**、**[标签](control-text-box.md)**、**[折线图](control-column-line-chart.md)**、**[列表框](control-list-box.md)**、**[麦克风](control-microphone.md)**、**[PDF 查看器](control-pdf-viewer.md)**、**[笔输入](control-pen-input.md)**、**[饼图](control-pie-chart.md)**、**[单选按钮](control-radio.md)**、**[评分](control-rating.md)**、**[形状](control-shapes-icons.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)**、**[计时器](control-timer.md)** 和**[切换](control-toggle.md)** 控件。

**Reset** - 控件是否还原为其默认值。  另请参阅 [Reset](../functions/function-reset.md) 函数。

* 适用于**[音频](control-audio-video.md)**、**[复选框](control-check-box.md)**、**[下拉列表](control-drop-down.md)**、**[列表框](control-list-box.md)**、**[麦克风](control-microphone.md)**、**[单选按钮](control-radio.md)**、**[评级](control-rating.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)**、**[计时器](control-timer.md)**、**[切换](control-toggle.md)** 和**[视频](control-audio-video.md)** 控件。

**Text**：在控件上显示或用户键入到控件中的文本。

* 适用于**[添加图片](control-add-picture.md)**、**[按钮](control-button.md)**、**[复选框](control-check-box.md)**、**[导出](control-export-import.md)**、**[导入](control-export-import.md)**、**[标签](control-text-box.md)**、**[文本输入](control-text-input.md)** 和**[计时器](control-timer.md)** 控件。

**Tooltip**：用户将鼠标悬停在控件上时显示的解释性文本。

* 适用于**[音频](control-audio-video.md)**、**[按钮](control-button.md)**、**[照相机](control-camera.md)**、**[复选框](control-check-box.md)**、**[下拉列表](control-drop-down.md)**、**[HTML 文本](control-html-text.md)**、**[图像](control-image.md)**、**[标签](control-text-box.md)**、**[列表框](control-list-box.md)**、**[麦克风](control-microphone.md)**、**[PDF 查看器](control-pdf-viewer.md)**、**[笔输入](control-pen-input.md)**、**[单选按钮](control-radio.md)**、**[评分](control-rating.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)**、**[计时器](control-timer.md)**、**[切换](control-toggle.md)** 和**[视频](control-audio-video.md)** 控件。

**Value**：输入控件的值。

* 适用于**[复选框](control-check-box.md)**、**[单选按钮](control-radio.md)**、**[滑块](control-slider.md)** 和**[切换](control-toggle.md)** 控件。

**Visible**：控件显示还是隐藏。

* 适用于 **[添加图片](control-add-picture.md)** 、**[音频](control-audio-video.md)**、**[按钮](control-button.md)**、**[照相机](control-camera.md)**、**[卡片](control-card.md)**、**[复选框](control-check-box.md)**、**[柱形图](control-column-line-chart.md)**、**[日期选取器](control-date-picker.md)**、**[显示窗体](control-form-detail.md)**、**[下拉列表](control-drop-down.md)**、**[编辑窗体](control-form-detail.md)**、**[导出](control-export-import.md)**、**[库](control-gallery.md)**、**[HTML 文本](control-html-text.md)**、**[图标](control-shapes-icons.md)**、**[图像](control-image.md)**、**[导入](control-export-import.md)**、**[标签](control-text-box.md)**、**[折线图](control-column-line-chart.md)**、**[列表框](control-list-box.md)**、**[麦克风](control-microphone.md)**、**[PDF 查看器](control-pdf-viewer.md)**、**[笔输入](control-pen-input.md)**、**[饼图](control-pie-chart.md)**、**[单选按钮](control-radio.md)**、**[评分](control-rating.md)**、**[形状](control-shapes-icons.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)**、**[计时器](control-timer.md)**、 **[切换](control-toggle.md)** 和 **[视频](control-audio-video.md)** 控件。

