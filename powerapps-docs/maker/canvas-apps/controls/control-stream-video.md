---
title: Microsoft Stream 视频控件：参考 |Microsoft Docs
description: 有关 Microsoft Stream 视频控件的信息（包括属性和示例）
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/26/2019
ms.author: fikaradz
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c9d3594ecf338c6cfa93786f56a09606b2de6296
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732018"
---
# <a name="microsoft-stream-video-control-in-power-apps"></a>在 Power Apps 中 Microsoft Stream 视频控制
视频播放器 Microsoft Stream 视频和频道。

## <a name="description"></a>描述
该控件将允许应用用户播放视频并浏览 Microsoft Stream 服务的频道。

## <a name="key-properties"></a>关键属性
**StreamUrl** –要在控件中显示的 Microsoft Stream 视频或通道的 URL。

**ShowControls** –视频播放控件是否向最终用户显示。

## <a name="additional-properties"></a>其他属性
**[AccessibleLabel](properties-accessibility.md)** – 屏幕阅读器标签。 应为视频或音频剪辑的标题。

**AutoStart** – 用户导航到包含音频或视频控件的屏幕时，该控件是否自动开始播放剪辑。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Fill](properties-color-border.md)** – 控件的背景色。

**[FocusedBorderColor](properties-color-border.md)** – 当聚焦到控件时，控件的边框颜色。

**[FocusedBorderThickness](properties-color-border.md)** – 当聚焦到控件时，控件的边框粗细。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**StartTime** - 音频或视频剪辑开始播放之后的时间。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

**[Tooltip](properties-core.md)** – 用户将鼠标悬停在控件上时显示的解释性文本。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="example"></a>示例

### <a name="play-an-audio-or-video-file-from-microsoft-stream"></a>播放 Microsoft Stream 的音频或视频文件

1. 在 "**文件**" 菜单上，选择 "**插入**"，然后单击 "打开**媒体**" 下拉菜单。 
2. 从媒体控件列表中选择 " **Microsoft Stream** "：

    ![Microsoft Stream](./media/control-stream-video/stream-icon.png "Microsoft Stream")

3. 将视频链接粘贴到左侧的 "**流 URL** " 属性中：

    ![自定义 StreamUrl 属性](./media/control-stream-video/stream-url.png "自定义 StreamUrl 属性")

4. 按 F5，选择您所添加的控件的 "播放" 按钮。

    > [!NOTE]
   > **Microsoft Stream**要求身份验证才能播放视频。 请确保应用用户具有所需的权限。
5. 按 Esc 退出预览模式。

## <a name="browser-considerations"></a>浏览器注意事项

### <a name="ios"></a>iOS
Power Apps iOS 播放器不支持直接播放嵌入在应用中的视频。  若要观看视频，请单击 "流" 图标以全屏模式启动视频播放器。

### <a name="safari"></a>免费

若要在 Safari 浏览器中查看应用 Microsoft Stream 视频，需要关闭[阻止跨站点跟踪](https://support.apple.com/guide/safari/sfri40732/mac)的选项。

## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="audio-and-video-alternatives"></a>视频和音频替代项
* “ShowControls”必须为“true”，以便用户可以按照自己的节奏收听或观看多媒体。 此外，还允许用户在视频播放器上切换隐藏式字幕和全屏模式。
* 必须为视频提供隐藏式字幕。
 * 考虑使用下列方法之一提供音频或视频脚本：
  1. 将文本放入 **[Label ](control-text-box.md)** 并将其置于多媒体播放器旁边。 （可选）创建 **[按钮](control-button.md)** 切换文本显示。
  2. 将文本置于不同屏幕中。 创建导航到屏幕的 **[按钮](control-button.md)** ，并将按钮置于多媒体播放器旁边。
  3. 如果描述很短，可以将其放入 **[AccessibleLabel](properties-accessibility.md)** 。

### <a name="color-contrast"></a>颜色对比度
在以下项之间必须有足够的颜色对比度：
* **[FocusedBorderColor](properties-color-border.md)** 和外部颜色
* **[Fill](properties-color-border.md)** 和多媒体播放器控件（如果填充可见）

如果视频内容颜色对比度有问题，则提供隐藏式字幕和/或脚本。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* **[“AccessibleLabel”](properties-accessibility.md)** 必须存在。

### <a name="keyboard-support"></a>键盘支持
* **[“TabIndex”](properties-accessibility.md)** 必须为零或更大，以便键盘用户可以导航到它。
* 焦点指示器必须清晰可见。 可以使用 **[“FocusedBorderColor”](properties-color-border.md)** 和 **[“FocusedBorderThickness”](properties-color-border.md)** 来实现此目的。
* “AutoStart”应为“false”，因为它可能会使键盘用户难以快速停止播放。