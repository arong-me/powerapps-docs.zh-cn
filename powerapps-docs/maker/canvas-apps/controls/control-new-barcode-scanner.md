---
title: 条码扫描器控件： 引用 |Microsoft Docs
description: 包括属性和示例，条码扫描器控件有关的信息
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 11/25/2018
ms.author: fikaradz
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9a4b2c941b5e28c462b85d3c6d54404746e22d04
ms.sourcegitcommit: 8d0ba2ec0c97be91d1350180dd6881c14dec8f2d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2019
ms.locfileid: "65517342"
---
# <a name="barcode-scanner-control-for-canvas-apps"></a>画布应用的条码扫描器控件

扫描条形码、 QR 码和 Android 或 iOS 设备上的数据矩阵代码。 不支持在 web 浏览器中。

## <a name="description"></a>描述

在 Android 或 iOS 设备上的本机扫描仪，控件将打开。 扫描程序会自动检测条形码、 QR 代码或当视图中的数据矩阵代码。 该控件不支持扫描 web 浏览器中。

控件支持 QR 代码、 数据矩阵代码和这些类型的条形码：

- UPC A
- UPC E
- EAN 8
- EAN 13
- 代码 39
- 代码 128
- ITF
- PDF 417

## <a name="key-properties"></a>关键属性

**值**– 输出包含已扫描最新的代码的文本值的属性。

**文本**-激活扫描程序按钮显示的文本。

**OnScan** -已成功扫描条形码时应用的响应方式。

## <a name="additional-properties"></a>其他属性

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**FlashlightEnabled** -是否打开扫描程序时自动启用手电筒。

**[高度](properties-size-location.md)** – 激活扫描程序按钮的高度。

**PreferFrontCamera** -是否前置照相机，如果可用，请使用进行扫描。

**[Tooltip](properties-core.md)** – 用户将鼠标悬停在控件上时显示的解释性文本。

**类型**-的最近成功扫描中检测到的代码类型。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[宽度](properties-size-location.md)** – 激活扫描程序按钮的宽度。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="accessibility-guidelines"></a>辅助功能准则
相同准则 **[按钮](control-button.md)** 控制将应用于**条码扫描器**控制，因为它是用于启动扫描的按钮。

### <a name="visual-alternatives"></a>视频替代
* 条形码扫描程序是不会显示扫描结果的按钮。 请考虑将显示扫描结果与 **[标签](control-text-box.md)** 控件。 设置的标签 **[文本](properties-core.md)** 属性设置为条形码扫描仪**值**属性。 设置的标签 **[Live](properties-accessibility.md)** 属性设置为**礼貌**，以便更改的通知屏幕阅读器用户。 此更改使扫描生成的值可供所有人，而不考虑视觉功能。

* Visual 和汽车残障人士可能倾向于不指向条形码的照相机。 请考虑添加另一种形式的输入，如 **[文本输入](control-text-input.md)** 控件，用户输入的条形码。
