---
title: 麦克风控件：参考 | Microsoft 文档
description: 有关麦克风控件的信息（包括属性和示例）
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/16/2020
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 353485baf6726314f6009c57838b3aa68d145fa0
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79436752"
---
# <a name="microphone-control-in-power-apps"></a>Power Apps 中的麦克风控件

使应用程序用户可以从其设备记录声音的控件。

## <a name="description"></a>说明

使用 "**麦克风**" 控件，通过设备的麦克风捕获音频。  设备必须具有麦克风，并且用户必须授权应用程序使用麦克风。  在 web 浏览器中运行时，支持麦克风控件。  

最近录制的音频剪辑可通过**音频**属性获得。 对于此属性，录制的音频可以是：

- **播放音频控件。**  使用 "[音频](control-audio-video.md)" 控件侦听录制。 有关详细信息，请参阅[示例](#examples)。
- **临时放入变量或集合。**  使用 "[设置](../functions/function-set.md)" 或 "[收集](../functions/function-clear-collect-clearcollect.md)函数" 将音频剪辑存储到变量或集合中。  使用设备的有限内存同时对一个集合中的多个音频剪辑使用时务必小心。  使用[SaveData](../functions/function-savedata-loaddata.md)和[LoadData](../functions/function-savedata-loaddata.md)函数将音频剪辑移动到设备上的本地存储和[脱机方案](../offline-apps.md)。
- **存储在数据库中。**  使用[Patch](../functions/function-patch.md)函数可在数据库中存储音频剪辑。
- **作为 base64 编码文本字符串传输。**  使用[JSON](../functions/function-json.md)函数对音频剪辑进行 base64 编码。

录制的音频的格式：

- 适用于*Android*的*3gp*格式。
- 适用于*iOS*的*AAC*格式。
- *Web 浏览器*的*OGG*格式。

捕获的媒体由文本字符串 URI 引用。 有关详细信息，请参阅[数据类型文档](../functions/data-types.md#uris-for-images-and-other-media)。

## <a name="key-properties"></a>关键属性

**音频**–当用户与设备的麦克风一起记录时捕获的音频剪辑。 

**Mic** –设备上具有多个麦克风的麦克风的数字 ID。

**OnStop** – 用户使用麦克风控件停止录制时应用的响应方式。

## <a name="additional-properties"></a>其他属性

[AccessibleLabel](properties-accessibility.md) – 屏幕阅读器标签。 应描述麦克风的用途。

[BorderColor](properties-color-border.md) — 控件边框的颜色。

[BorderStyle](properties-color-border.md) – 控件边框是“实线”、“虚线”、“点线”还是“无”。

[BorderThickness](properties-color-border.md) – 控件边框的粗细。

[Color](properties-color-border.md) – 控件中文本的颜色。

[DisplayMode](properties-core.md) –控件是允许用户输入（**Edit**）、仅显示数据（**View**），还是已禁用（**disabled**）。

[DisabledBorderColor](properties-color-border.md) –控件的[DisplayMode](properties-core.md)属性设置为 " **Disabled**" 时，该控件边框的颜色。

[DisabledColor](properties-color-border.md) –控件的[DisplayMode](properties-core.md)属性设置为**Disabled**时，该控件中的文本颜色。

[DisabledFill](properties-color-border.md) –控件的[DisplayMode](properties-core.md)属性设置为**Disabled**时，该控件的背景色。

[Fill](properties-color-border.md) – 控件的背景色。

[FocusedBorderColor](properties-color-border.md) –控件聚焦时控件边框的颜色。

[FocusedBorderThickness](properties-color-border.md) –控件聚焦时控件边框的粗细。

[Height](properties-size-location.md) - 控件上边缘和下边缘之间的距离。

[HoverBorderColor](properties-color-border.md) – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

[HoverColor](properties-color-border.md) – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

[HoverFill](properties-color-border.md) – 用户将鼠标指针停留在控件上时，该控件的背景色。

[Image](properties-visual.md) - 在图像、音频或麦克风控件中显示的图像名称。

[ImagePosition](properties-visual.md) - 屏幕或控件大小与图像大小不同时，其中图像的位置（“填充”、“适应”、“拉伸”、“平铺”或“居中”）。

[OnSelect](properties-core.md) -用户选择控件时应用的响应方式。

**OnStart** - 用户使用麦克风控件开始录制时应用如何响应。

[PressedBorderColor](properties-color-border.md) –用户选择控件时，该控件边框的颜色。

[PressedColor](properties-color-border.md) -用户选择控件时控件中文本的颜色。

[PressedFill](properties-color-border.md) -当用户选择控件时，该控件的背景色。

[Reset](properties-core.md) - 控件是否还原为其默认值。

[TabIndex](properties-accessibility.md) –相对于其他控件的键盘导航顺序。

[Tooltip](properties-core.md)：用户将鼠标悬停在控件上时显示的解释性文本。

[Visible](properties-core.md)：控件显示还是隐藏。

[Width](properties-size-location.md) - 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) –控件左边缘与其父容器或屏幕左边缘之间的距离。

[Y](properties-size-location.md) -控件上边缘和父容器或屏幕上边缘之间的距离。

## <a name="examples"></a>示例

### <a name="simple-direct-playback"></a>简单直接播放

在此示例中，我们将使用**音频**控制直接连接**麦克风**控件，以便立即播放：

1. [向](../add-configure-controls.md)应用程序添加**麦克风**控件。
1. 在出现提示时，授权应用使用设备的麦克风。
1. 向应用程序添加**音频**控件。
1. 将**音频**控件的**Media**属性设置为公式：

    ```powerapps-dot
    Microphone1.Audio
    ```

    > [!NOTE]
    > 根据需要替换麦克风控件名称*Microphone1* 。

1. 预览应用程序。
1. 选择 "**麦克风**" 控件开始录制。
1. 录音录音。
1. 再次选择**麦克风**控件结束录制。
1. 选择**音频**控件收听记录。  

### <a name="add-sounds-to-a-gallery-control"></a>向库控件添加声音

在此示例中，我们将创建一个存储在集合中的音频剪辑库，该集合可单独选择播放：

1. [添加](../add-configure-controls.md)**麦克风**控件。

1. 使用[Collect](../functions/function-clear-collect-clearcollect.md)函数将其**OnStop**属性设置为此公式：

    ```powerapps-dot
    Collect( MySounds, MyMic.Audio )
    ```

1. 添加**库**控件，将其移到**MyMic**下。

1. 将库的[Items](properties-core.md)属性设置为以下公式：

    ```powerapps-dot
    MySounds
    ```

1. 在 "**自定义库**" 控件的模板中，添加 "[音频](control-audio-video.md)" 控件。

1. 将音频控件的**媒体**属性设置为以下公式：

    ```powerapps-dot
    ThisItem.Url
    ```

1. 按 F5 预览应用程序。

1. 选择**MyMic**开始录制，并再次选择它以停止录制。

1. 在 "**库**" 控件中，选择 "**音频**" 控件中的 "播放" 按钮播放录制。

1. 添加所需数量的录制，然后按 Esc 键返回到默认工作区。

1. 可有可无在**库**控件的模板中，添加一个[按钮](control-button.md)控件。

1. 将其[OnSelect](properties-core.md)属性设置为公式：

    ```powerapps-dot
    Remove( MySounds, ThisItem )
    ```

1. 按 F5，然后通过选择相应的**按钮**控件删除记录。

使用[SaveData](../functions/function-savedata-loaddata.md)函数在本地保存记录，或使用[Patch](../functions/function-patch.md)函数更新数据源。

## <a name="accessibility-guidelines"></a>辅助功能准则

因为**麦克风**只是专用按钮，所以适用于[按钮](control-button.md)的准则同样适用。 另外，请考虑：

### <a name="audio-alternatives"></a>音频替代项

请考虑为有语言障碍或没有麦克风的用户添加另一种输入形式。 例如，允许用户输入文本的[文本输入](control-text-input.md)。

### <a name="color-contrast"></a>颜色对比度

- 阅读[标准颜色对比度要求](../accessible-apps-color.md)。
- 确保[图像](properties-visual.md)与按钮文本和图标（如果适用）具有足够的颜色对比度。

### <a name="screen-reader-support"></a>屏幕阅读器支持

- ["Accessiblelabel"](properties-accessibility.md)必须存在。
