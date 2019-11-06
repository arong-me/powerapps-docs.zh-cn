---
title: 条形码扫描器控件：参考 |Microsoft Docs
description: 有关条形码扫描器控件的信息（包括属性和示例）
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/25/2018
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c7c3079ebbdeea0097f50acc2ce7f5d4e4089947
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73650419"
---
# <a name="barcode-scanner-control-for-canvas-apps"></a>用于画布应用的条形码扫描器控制

扫描 Android 或 iOS 设备上的条码、QR 码和数据矩阵代码。 在 web 浏览器中不受支持。

## <a name="description"></a>描述

控件打开 Android 或 iOS 设备上的本机扫描仪。 在视图中时，扫描器会自动检测条形码、QR 码或数据矩阵代码。 控件不支持在 web 浏览器中进行扫描。

此控件支持 QR 码、数据矩阵代码和以下类型的条码：

- UPC A
- UPC E
- EAN 8
- EAN 13
- 代码39
- 代码128
- ITF
- PDF 417

## <a name="key-properties"></a>关键属性

**值**– Output 属性，其中包含最近扫描的代码的文本值。

**文本**-在激活扫描仪的按钮上显示的文本。

**OnScan** -成功扫描条形码后应用的响应方式。

## <a name="additional-properties"></a>其他属性

[BorderColor](properties-color-border.md) – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**FlashlightEnabled** -打开扫描仪时是否自动启用闪光灯。

**[高度](properties-size-location.md)** –激活扫描仪的按钮的高度。

**PreferFrontCamera** -用于扫描的正面照相机（如果可用）。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**类型**-在最近成功完成的扫描中检测到的代码类型。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** –激活扫描仪的按钮的宽度。

**[X](properties-size-location.md)** - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="accessibility-guidelines"></a>辅助功能准则
**[按钮](control-button.md)** 控件的相同准则适用于**条形码扫描器**控件，因为它是启动扫描的按钮。

### <a name="visual-alternatives"></a>直观替代项
* 条形码扫描器是不显示扫描结果的按钮。 请考虑使用 " **[标签](control-text-box.md)** " 控件显示扫描结果。 将标签的 " **[Text](properties-core.md)** " 属性设置为条形码扫描器的**Value**属性。 将标签的 **[Live](properties-accessibility.md)** 属性设置为 "**礼貌**"，以便通知屏幕阅读器用户发生更改。 此更改使每个用户都可以访问扫描的值，而不考虑视觉对象的能力。

* 具有视觉障碍和伤残障碍的用户可能不会将相机指向条形码。 请考虑为用户添加另一种形式的输入（如 **[文本输入](control-text-input.md)** 控件），以供用户输入条形码。
