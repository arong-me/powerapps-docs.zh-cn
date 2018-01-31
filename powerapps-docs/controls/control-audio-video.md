---
title: "音频和视频控件：参考 | Microsoft 文档"
description: "有关音频和视频控件的信息（包括属性和示例）"
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
ms.openlocfilehash: 7aa3c2e2e6b0e6baaaec9666fc7b4e56c9568317
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="audio-and-video-controls-in-powerapps"></a>PowerApps 中的音频和视频控件
一个控件，用于播放 YouTube 上的音频文件、视频文件或视频。

## <a name="description"></a>说明
“音频”控件播放文件中的声音剪辑、“[麦克风](control-microphone.md)”控件中的录制内容或视频文件中的音轨。 “视频”控件播放文件或 YouTube（如果指定 URL）中的视频剪辑。

## <a name="key-properties"></a>关键属性
**Loop** - 音频或视频剪辑是否在播放完后自动重新开始。

**Media** – 音频或视频控件播放的剪辑的标识符。

**ShowControls** - 音频或视频播放器是否显示播放按钮和音量滑块等内容，以及笔控件是否显示绘图、擦除和清除等图标。

## <a name="additional-properties"></a>其他属性
**AutoPause** - 用户导航到另一屏幕时音频或视频剪辑是否自动暂停。

**AutoStart** - 用户导航到包含音频或视频控件的屏幕时，该控件是否自动开始播放剪辑。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[Image](properties-visual.md)** - 图像、音频或麦克风控件中显示的图像名称。

**[ImagePosition](properties-visual.md)** – 屏幕或控件大小与图像大小不同时，其中图像的位置（“填充”、“适应”、“拉伸”、“平铺”或“居中”）。

**OnEnd** - 音频或视频剪辑播放完成后应用如何响应。

**OnPause** - 用户暂停音频或视频控件播放的剪辑时应用如何响应。

**OnStart** - 用户使用麦克风控件开始录制时应用如何响应。

**Paused** - 如果媒体播放控件当前已暂停，则为 *True*；否则为 *false*。

**[Reset](properties-core.md)** - 是否还原控件的默认值。

**Start** – 音频或视频剪辑是否播放。

**StartTime** - 音频或视频剪辑开始播放之后的时间。

**Time** - 媒体控件的当前位置。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数
[**First**( *TableName* )](../functions/function-first-last.md)

## <a name="examples"></a>示例
### <a name="play-an-audio-or-video-file"></a>播放音频或视频文件
1. 在“文件”菜单上，依次单击或点击“媒体”、“视频”或“音频”、“浏览”。
2. 浏览到想要使用的文件，单击或点击它，然后单击或点击“打开”。
3. 按 Esc 返回默认工作区，添加“音频”或“视频”控件，并将其 **Media** 属性设置为已添加的文件。
   
    不知道如何[添加和配置控件](../add-configure-controls.md)？
4. 按 F5，然后通过单击或点击所添加的控件的播放按钮来播放剪辑。
   
    > [!TIP]
> 将鼠标悬停在“视频”控件之上时，便会看到此控件的播放按钮。
5. 按 Esc 返回默认工作区。

### <a name="play-a-youtube-video"></a>播放 YouTube 视频
1. 添加“视频”控件，并将其 **Media** 属性设置为 YouTube 视频的 URL（括在双引号内）。
2. 按 F5，然后通过单击或点击“视频”控件的播放按钮来播放剪辑。
3. 按 Esc 返回默认工作区。

