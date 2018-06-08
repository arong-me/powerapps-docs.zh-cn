---
title: 创建提供辅助功能的应用 | Microsoft Docs
description: 如何确保残障人士能够访问应用
author: fikaradz
ms.service: powerapps
ms.topic: conceptual
ms.component: canvas
ms.date: 04/03/2018
ms.author: fikaradz
ms.openlocfilehash: 8a7139f6dbc39bc1585156802e30236aa2b68359
ms.sourcegitcommit: 7354a0c61578fcc0b9965bf557b9d7c553c73e96
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2018
ms.locfileid: "34803066"
---
# <a name="create-accessible-apps"></a>创建提供辅助功能的应用
如果应用提供辅助功能，有视力障碍、听力障碍和其他障碍的用户就可以成功使用应用。  除了遵守许多政府和组织的要求外，遵守下面的指南可以让所有用户都用起来更加方便，无论他们是否有残障。

## <a name="layout-and-color"></a>布局和颜色
符合常理的不复杂设计有助于确保所有用户都能更轻松地使用应用。  若要大量自定义应用，请遵循以下建议。  默认情况下，PowerApps 主题可方便所有用户都轻松使用。
- 确保所有元素都清晰可见，且文本大小适当。  所有内容都必须可用肉眼轻松阅读和理解。
- 避免使用项的可见性属性来显示元素。  如果需要有条件地显示内容，请在新屏幕中创建内容，并来回导航到它。
- 确保输入元素在屏幕上有标签。 [AccessibilityLabel](controls/properties-accessibility.md) 属性定义了屏幕阅读器将读出的内容。
- 若要自定义颜色，请确保文本和背景的对比度不小于 4.5:1。  可随时使用软件工具来协助此过程。
- 确保布局符合从上到下、从左到右阅读时的逻辑流。


## <a name="keyboard-support"></a>键盘支持
测试应用的辅助功能时，请确保应用只能与键盘结合使用，且辅助功能模式同时适用于 iOS 和 Android，以及在启用屏幕阅读器后能够成功导航。

对于键盘导航（启用或未启用屏幕阅读器），请确保在使用 TAB 键时按一定逻辑顺序导航到输入字段，具体是通过设置每个控件的 [TabIndex](controls/properties-accessibility.md) 属性：
- 标签、图像、图标、形状控件 - 如果它们表示交互元素（即按钮），将 TabIndex 设置为 0；如果它们是装饰性元素或文本，将 TabIndex 设置为 -1。
- 避免将选项卡索引值设置为大于零。

## <a name="screen-reader-support"></a>屏幕阅读器支持
若要结合使用 PowerApps 和屏幕阅读器，支持的软件组合如下：

- **Windows**：Edge/讲述人
- **macOS**：Safari/VoiceOver
- **Android**：PowerApps 应用/Talkback
- **iOS**：PowerApps 应用/VoiceOver

为了确保令人满意的屏幕阅读器使用体验，建议执行以下操作：

- 确保所有输入控件均已设置 [AccessibilityLabel](controls/properties-accessibility.md)属性。
- 对于图像，将 [AccessibilityLabel](controls/properties-accessibility.md) 设置为相应说明。
  - 如果图片不用作按钮或链接（即图标只用作装饰），且不得由屏幕阅读器阅读，请确保 [AccessibilityLabel](controls/properties-accessibility.md) 为空或未设置。
  - 如果图片或图标用作按钮，请将 [TabIndex](controls/properties-accessibility.md) 设置为 0，并将 [AccessibilityLabel](controls/properties-accessibility.md) 设置为链接说明。


## <a name="multimedia"></a>多媒体
请确保所有视频都有字幕，且全部录音的解说词都可供用户查看。  视频控件支持 WebVTT 格式的隐藏式字幕（通过 ClosedCaptionsUrl 属性实现）。

请注意，启用屏幕阅读器后，计时器读出的不是按钮文本，而是所耗时长。  无法禁用读出功能，即使计时器隐藏且不透明度低，也不例外。

## <a name="working-with-signatures"></a>使用签名
若有签名字段使用笔输入控件，需要启用签名输入备用方法。  推荐方法是，显示可供用户键入姓名的文本输入控件。  请确保 [AccessibilityLabel](controls/properties-accessibility.md) 属性中有签名说明，且文本输入控件靠近笔输入位置（即在笔输入右侧或正下方）。



相关：[辅助功能属性](controls/properties-accessibility.md)
