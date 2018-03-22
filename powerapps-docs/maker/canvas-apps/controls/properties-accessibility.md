---
title: Accessibility 属性 | Microsoft 文档
description: 有关 TabIndex、Tooltip 等属性的参考信息
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
ms.date: 01/26/2017
ms.author: fikaradz
ms.openlocfilehash: d35b4bc7a6e479ce47ad0a0b841a6ed9ccfd1a52
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="accessibility-properties-in-powerapps"></a>PowerApps 中的辅助功能属性
配置有助于残障用户以其他合适方式与控件进行交互的属性。

### <a name="properties"></a>属性
**AccessiblityLabel** - 供屏幕阅读器读取的控件的说明。   如果“图像”、“图标”和“形状”控件采用空值，将导致这些控件对屏幕阅读器不可见，并被视为修饰。

* 适用于**[音频](control-audio-video.md)**、**[按钮](control-button.md)**、**[照相机](control-camera.md)**、**[复选框](control-check-box.md)**、**[下拉列表](control-drop-down.md)**、**[HTML 文本](control-html-text.md)**、**[图像](control-image.md)**、**[标签](control-text-box.md)**、**[列表框](control-list-box.md)**、**[麦克风](control-microphone.md)**、**[PDF 查看器](control-pdf-viewer.md)**、**[笔输入](control-pen-input.md)**、**[单选按钮](control-radio.md)**、**[评分](control-rating.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)**、**[计时器](control-timer.md)**、**[切换](control-toggle.md)**和**[视频](control-audio-video.md)**控件。

**TabIndex**：在运行时自定义控件的 Tab 键顺序。

默认值零根据控件的 XY 坐标指定默认 Tab 键顺序。  如果将值设置为大于零，则会将该控件的 Tab 键顺序移到所有采用默认值的控件的前面。  使用 Tab 键时，TabIndex 值为 2 的控件优先于 TabIndex 值大于等于 3 的控件。

请注意，窗体控件和库控件等容器始终先用 Tab 键访问其所有元素，然后才会访问容器外部的控件。  容器的 Tab 键顺序从具有最小 TabIndex 值的子控件开始。

如果将 TabIndex 设置为 -1，则禁用 tab 键访问控件；如果是“图像”、“图标”和“形状”控件，它们也会成为非交互式元素。

* 适用于**[按钮](control-button.md)**、**[日期选取器](control-date-picker.md)**、**[下拉列表](control-drop-down.md)**、**[图像](control-image.md)**、**[导入](control-export-import.md)**、**[列表框](control-list-box.md)**、**[单选按钮](control-radio.md)**、**[评级](control-rating.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)**和**[切换](control-toggle.md)**控件。
