---
title: 具有辅助功能的颜色 | Microsoft Docs
description: PowerApps 的颜色对比度准则
author: tahoon
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: anneta
ms.date: 04/23/2018
ms.author: tahoon
ms.openlocfilehash: 289026f18d341381d64423e76effb1abf586557c
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39014802"
---
# <a name="accessible-colors-in-powerapps"></a>PowerApps 中具有辅助功能的颜色
应用中使用的颜色应方便色盲和弱视用户使用。 默认情况下，所有 PowerApps 主题可让所有用户都轻松使用。 在修改应用中使用的颜色时，请遵循以下准则以确保它们方便用户使用。 有多种联机工具可以帮助确定颜色对比度问题。

## <a name="minimum-contrast-for-text"></a>文本最小对比度
* 文本及其背景必须至少有 4.5:1 的对比度
* 大型文本必须至少有 3:1 的对比度
* 已禁用的文本没有对比度要求

实际上，所有交互式控件之间都必须有足够的颜色对比度：
* [Color](controls/properties-color-border.md) 和 [Fill](controls/properties-color-border.md)
* [PressedColor](controls/properties-color-border.md) 和 [PressedFill](controls/properties-color-border.md)
* [HoverColor](controls/properties-color-border.md) 和 [HoverFill](controls/properties-color-border.md)

## <a name="minimum-contrast-for-non-text"></a>非文本最小对比度

> [!NOTE]
> 在 [WCAG 2.0](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-contrast.html) 标准下，对比度要求仅适用于文本。 如需更出色的辅助功能，请考虑即将推出的面向图标按钮等基本用户界面组件的 [WCAG 2.1 对比度准则](https://www.w3.org/TR/WCAG21/#non-text-contrast)。 建议对这些组件使用最小对比度 3:1。 本部分所述的指导原则可供选择，符合 WCAG 2.0 标准。

### <a name="user-interface-components"></a>用户界面组件
所有交互式控件之间都必须有足够的颜色对比度：
* [FocusedBorderColor](controls/properties-color-border.md) 和控件范围之外的颜色

其他颜色对比度检查适用于其中整个区域为交互式或信息性的控件。 例如，[按钮](controls/control-button.md)或用作按钮的[图标](controls/control-shapes-icons.md)。 这可确保控件边界清晰，并确保用户知道他们可以在哪个位置单击或点击。

如果没有此类控件边框，则在以下项之间应有足够的颜色对比度：
* [BorderColor](controls/properties-color-border.md) 和控件范围之外的颜色
* [PressedBorderColor](controls/properties-color-border.md) 和控件范围之外的颜色
* [HoverBorderColor](controls/properties-color-border.md) 和控件范围之外的颜色

如果没有边框，则在以下项之间应有足够的颜色对比度：
* [Fill](controls/properties-color-border.md) 和控件范围之外的颜色
* [PressedFill](controls/properties-color-border.md) 和控件范围之外的颜色
* [HoverFill](controls/properties-color-border.md) 和控件范围之外的颜色

### <a name="graphical-objects"></a>图形对象
如果图像传达重要信息，请考虑检查其对比度问题。 这适用于可在其中显示图像的控件：[音频](controls/control-audio-video.md)、[图像](controls/control-image.md)、[麦克风](controls/control-microphone.md)和[视频](controls/control-audio-video.md)。

有关视频内容，请考虑检查其对比度问题。 或者另外提供[隐藏式字幕](controls/control-audio-video.md)来描述视频。

## <a name="provide-other-visual-cues"></a>提供其他视觉提示
确保应用不仅仅使用颜色来传达信息。 例如，红绿色盲用户将无法从绿色成功消息中区分红色错误消息。

其他提示，如[图标](controls/control-shapes-icons.md)或[斜体](controls/properties-text.md)和[下划线](controls/properties-text.md)之类的文本样式有助于传达含义。

## <a name="next-steps"></a>后续步骤
了解 PowerApps 控件中的[辅助功能属性](controls/properties-accessibility.md)并尝试[使用辅助功能检查器](accessibility-checker.md)。
