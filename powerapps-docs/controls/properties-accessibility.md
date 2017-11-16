---
title: "Accessibility 属性 | Microsoft 文档"
description: "有关 TabIndex、Tooltip 等属性的参考信息"
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
ms.date: 01/26/2017
ms.author: anneta
ms.openlocfilehash: d8cc9d6c8586856dcaa27f67d3ea1fdc17fa0433
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="accessibility-properties-in-powerapps"></a>PowerApps 中的辅助功能属性
## <a name="overview"></a>概述
采用替代方法帮助视觉障碍用户与控件进行交互的属性的配置。

## <a name="properties"></a>属性
**Tooltip**：用户将鼠标悬停在控件上时显示的解释性文本。  辅助屏幕阅读器的 Aria 标签使用此文本。

* 适用于**[音频](control-audio-video.md)**、**[按钮](control-button.md)**、**[照相机](control-camera.md)**、**[复选框](control-check-box.md)**、**[下拉列表](control-drop-down.md)**、**[HTML 文本](control-html-text.md)**、**[图像](control-image.md)**、**[标签](control-text-box.md)**、**[列表框](control-list-box.md)**、**[麦克风](control-microphone.md)**、**[PDF 查看器](control-pdf-viewer.md)**、**[笔输入](control-pen-input.md)**、**[单选按钮](control-radio.md)**、**[评分](control-rating.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)**、**[计时器](control-timer.md)**、**[切换](control-toggle.md)**和**[视频](control-audio-video.md)**控件。

**TabIndex**：在运行时自定义控件的 Tab 键顺序。

默认值零根据控件的 XY 坐标指定默认 Tab 键顺序。  如果将值设置为大于零，则会将该控件的 Tab 键顺序移到所有采用默认值的控件的前面。  使用 Tab 键时，TabIndex 值为 2 的控件优先于 TabIndex 值大于等于 3 的控件。

请注意，窗体控件和库控件等容器始终先用 Tab 键访问其所有元素，然后才会访问容器外部的控件。  容器的 Tab 键顺序从具有最小 TabIndex 值的子控件开始。

将 TabIndex 设置为 -1 将禁止使用 tab 访问控件；图像、图标和形状也将对屏幕阅读器不可见。

* 适用于**[按钮](control-button.md)**、**[日期选取器](control-date-picker.md)**、**[下拉列表](control-drop-down.md)**、**[图像](control-image.md)**、**[导入](control-export-import.md)**、**[列表框](control-list-box.md)**、**[单选按钮](control-radio.md)**、**[评级](control-rating.md)**、**[滑块](control-slider.md)**、**[文本输入](control-text-input.md)**和**[切换](control-toggle.md)**控件。

