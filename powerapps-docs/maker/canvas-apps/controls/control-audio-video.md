---
title: 音频和视频控件：参考 | Microsoft 文档
description: 有关音频和视频控件的信息（包括属性和示例）
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: aab2b0bb7b236fe8cc6d7f18beb7a5c8ea8246ae
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71993847"
---
# <a name="audio-and-video-controls-in-powerapps"></a>PowerApps 中的音频和视频控件
一个控件，用于播放 YouTube 上的音频文件、视频文件或视频。

## <a name="description"></a>描述
“音频”控件播放文件中的声音剪辑、“[麦克风](control-microphone.md)”控件中的录制内容或视频文件中的音轨。

“视频”控件播放文件或 YouTube 或 Azure 媒体服务中的视频剪辑。  如果指定，也可以显示隐藏式字幕。

## <a name="key-properties"></a>关键属性
**Loop** - 音频或视频剪辑是否在播放完后自动重新开始。

**Media** – 音频或视频控件播放的剪辑的标识符。

**ShowControls** - 音频或视频播放器是否显示播放按钮和音量滑块等内容，以及笔控件是否显示绘图、擦除和清除等图标。

## <a name="additional-properties"></a>其他属性
**[AccessibleLabel](properties-accessibility.md)** – 屏幕阅读器标签。 应为视频或音频剪辑的标题。

**AutoPause** - 用户导航到另一屏幕时音频或视频剪辑是否自动暂停。

**AutoStart** - 用户导航到包含音频或视频控件的屏幕时，该控件是否自动开始播放剪辑。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

ClosedCaptionsUrl – 仅视频控件适用。  WebVTT 格式的隐藏式字幕文件的 URL。  视频和标题的 URL都必须是 HTTPS。 托管视频和字幕文件的服务器需要启用 CORS。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Fill](properties-color-border.md)** – 控件的背景色。

**[FocusedBorderColor](properties-color-border.md)** – 当聚焦到控件时，控件的边框颜色。

**[FocusedBorderThickness](properties-color-border.md)** – 当聚焦到控件时，控件的边框粗细。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[Image](properties-visual.md)** - 图像、音频或麦克风控件中显示的图像名称。

**[ImagePosition](properties-visual.md)** – 屏幕或控件大小与图像大小不同时，其中图像的位置（“填充”、“适应”、“拉伸”、“平铺”或“居中”）。

**OnEnd** - 音频或视频剪辑播放完成后应用如何响应。

**OnPause** - 用户暂停音频或视频控件播放的剪辑时应用如何响应。

**OnStart** - 用户使用麦克风控件开始录制时应用如何响应。

**Paused** - 如果媒体播放控件当前已暂停，则为 *True*；否则为 *false*。

[Reset](properties-core.md) – 是否还原控件的默认值。

**Start** – 音频或视频剪辑是否播放。

**StartTime** - 音频或视频剪辑开始播放之后的时间。

**Time** - 媒体控件的当前位置。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

**[Tooltip](properties-core.md)** – 用户将鼠标悬停在控件上时显示的解释性文本。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

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
1. 添加“视频”控件，并将其“Media”属性设置为 YouTube 视频的 URL（括在双引号内）。
2. 按 F5，然后通过单击或点击“视频”控件的播放按钮来播放剪辑。
3. 按 Esc 返回默认工作区。

### <a name="play-a-video-from-azure-media-services"></a>从 Azure 媒体服务播放视频
1. 在 AMS 上发布视频后，复制清单 URL。 启动服务的流式处理终结点（如果尚未启动）。
1. 添加“视频”控件，并将其“Media”属性设置为 AMS 视频的 URL（括在双引号内）。
2. 按 F5，然后通过单击或点击“视频”控件的播放按钮来播放剪辑。
3. 按 Esc 返回默认工作区。


## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="audio-and-video-alternatives"></a>视频和音频替代项
* “ShowControls”必须为“true”，以便用户可以按照自己的节奏收听或观看多媒体。 此外，还允许用户在视频播放器上切换隐藏式字幕和全屏模式。
* 必须为视频提供隐藏式字幕。
  *  对于 YouTube 视频，使用 YouTube 提供的创作工具添加字幕。
  *  对于其他视频，创建 WebVTT 格式的字幕，将其上传，然后将“ClosedCaptionsUrl”设置为 url 位置。 有几个限制。 托管视频和字幕的服务器需启用 CORS，并使用 HTTPS 协议为它们提供服务。 隐藏式字幕在 Internet Explorer 上无效。
* 考虑使用下列方法之一提供音频或视频脚本：
  1. 将文本放入 **[Label ](control-text-box.md)** 并将其置于多媒体播放器旁边。 （可选）创建 **[按钮](control-button.md)** 切换文本显示。
  2. 将文本置于不同屏幕中。 创建导航到屏幕的 **[按钮](control-button.md)** ，并将按钮置于多媒体播放器旁边。
  3. 如果描述很短，可以将其放入 **[AccessibleLabel](properties-accessibility.md)** 。

### <a name="color-contrast"></a>颜色对比度
在以下项之间必须有足够的颜色对比度：
* **[FocusedBorderColor](properties-color-border.md)** 和外部颜色
* **[Image](properties-visual.md)** 和多媒体播放器控件（如果适用）
* **[Fill](properties-color-border.md)** 和多媒体播放器控件（如果填充可见）

如果视频内容颜色对比度有问题，则提供隐藏式字幕和/或脚本。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* **[“AccessibleLabel”](properties-accessibility.md)** 必须存在。

### <a name="keyboard-support"></a>键盘支持
* **[“TabIndex”](properties-accessibility.md)** 必须为零或更大，以便键盘用户可以导航到它。
* 焦点指示器必须清晰可见。 可以使用 **[“FocusedBorderColor”](properties-color-border.md)** 和 **[“FocusedBorderThickness”](properties-color-border.md)** 来实现此目的。
* “AutoStart”应为“false”，因为它可能会使键盘用户难以快速停止播放。
