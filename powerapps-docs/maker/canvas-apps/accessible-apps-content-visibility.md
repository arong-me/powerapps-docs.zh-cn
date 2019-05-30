---
title: 显示或隐藏从画布应用中的辅助技术的内容 |Microsoft Docs
description: 仅向视力正常用户或仅向屏幕阅读器用户仅对画布应用中显示的内容的方法
author: tahoon-ms
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.date: 10/22/2018
ms.author: tahoon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c680767bc6a56f0596eba03dd555c1c9a0205346
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61550079"
---
# <a name="show-or-hide-content-from-assistive-technologies-for-canvas-apps"></a>显示或隐藏的画布应用的辅助技术中的内容

在大多数情况下，所有用户都应该能够访问所有内容，但有时可能需要仅向视力正常用户或仅向屏幕阅读器用户显示的内容。 例如，可能希望仅屏幕阅读器用户访问的图表是为视力正常用户明显的趋势说明。 您可能想要隐藏屏幕阅读器用户从一个图标，如果相邻标签描述它。 将不必要地详细的图标上的另一个描述。

## <a name="hide-content-from-all-users"></a>隐藏所有用户内容

* 设置 **[Visible](controls/properties-core.md)** 为 false。

## <a name="hide-content-from-sighted-users-and-show-it-to-screen-reader-users"></a>隐藏视力正常用户中的内容并显示到屏幕阅读器用户

使用这些方法之一：

* 设置 **[大小](controls/properties-text.md)** 为 0。
* 设置 **[宽度](controls/properties-size-location.md)** 并 **[高度](controls/properties-size-location.md)** 为 1。
* 设置 **[X](controls/properties-size-location.md)** ，  **[Y](controls/properties-size-location.md)** ，或这两个属性，该控件为屏幕外。
* 设置 **[颜色](controls/properties-color-border.md)** 和相关属性为透明。
* 定位矩形 **[形状](controls/control-shapes-icons.md)** 上面的内容，并设置 **[填充](controls/properties-color-border.md)** 为屏幕的背景色相同的颜色。

> [!NOTE]
> 用户仍可以使用键盘来访问交互式控制，例如 **[按钮](controls/control-button.md)** ，即使使用一种技术在上一列表中隐藏它。 设置 **[TabIndex](controls/properties-accessibility.md)** 为-1，如果你想要防止用户通过按 Tab 键访问控件。

## <a name="hide-content-from-screen-reader-users-and-show-it-to-sighted-users"></a>隐藏屏幕阅读器用户中的内容并显示为视力正常用户

* 有关 **[映像](controls/control-image.md)** ， **[图标](controls/control-shapes-icons.md)** ，并 **[形状](controls/control-shapes-icons.md)** 控件，设置 **[Accessiblelabel](controls/properties-accessibility.md)** 为空字符串""。

## <a name="next-steps"></a>后续步骤

了解如何[辅助功能属性](controls/properties-accessibility.md)画布应用中的控件。
