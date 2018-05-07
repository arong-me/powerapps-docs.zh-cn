---
title: 条码扫描器控件：参考 | Microsoft 文档
description: 有关条码扫描器控件的信息（包括属性和示例）
documentationcenter: na
author: fikaradz
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.openlocfilehash: 8cd0c84f508c13e8064b0e5bc93b01024cf22120
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="barcode-scanner-control-experimental-in-powerapps"></a>PowerApps 中的条形码扫描程序控件（实验性）
通过在设备上使用条形码扫描程序，用户可用来拍摄照片的实验性控件。

## <a name="description"></a>描述
如果添加此控件，用户可从应用运行的任何位置使用一张或多张照片更新数据源。

## <a name="key-properties"></a>关键属性
**barcode scanner** - 在具有多个条码扫描器的设备上，应用使用的条码扫描器的数字 ID。

## <a name="additional-properties"></a>其他属性
**[AccessibleLabel](properties-accessibility.md)** – 屏幕阅读器标签。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**Brightness** - 用户在图像中可能感知到的光线强度。

**Contrast** - 用户可区分图像中相似颜色的轻松程度。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**OnStream** - 更新 **Stream** 属性时应用的响应方式。

**Photo** - 用户拍摄照片时捕获的图像。

**ShowLiveBarcodeDetection** – 是否显示视觉提示以指示条形码检测的状态。 黄色矩形表示正在检查的区域。 跨矩形的绿色线条表示成功的条形码标识。

**Stream** - 基于 **StreamRate** 属性自动更新的图像。

**StreamRate** - 在 **Stream** 属性上更新图像的频率（以毫秒为单位）。  此值的范围为 100（1/10 秒）到 3,600,000（1 小时）。

Text – 上次由扫描仪识别的条形码值。

**[Tooltip](properties-core.md)** – 用户将鼠标悬停在控件上时显示的解释性文本。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

**Zoom** - 放大来自条码扫描器的图像百分比或 PDF 查看器中文件的视图百分比。

## <a name="related-functions"></a>相关函数
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>示例
### <a name="add-photos-to-an-image-gallery-control"></a>向图像库控件添加照片
1. 添加**条码扫描器**控件，将其命名为 **Mybarcode scanner**

    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 添加“标签”控件，然后将输出设置为条形码的“Text”。  
3. 扫描 BarcodeType 属性下设置的类型的条形码。
4. 标签将显示扫描的条形码。


## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="video-alternatives"></a>视频替代项
* 请考虑添加标签**[](control-text-box.md)**，并将其 Text**[](properties-core.md)** 设置为条形码扫描仪的“Text”。 由于条形码扫描仪未显示标识的条形码值，执行上述操作将使所有人都可访问扫描仪，而不仅仅是那些有视觉障碍的用户。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* **[“AccessibleLabel”](properties-accessibility.md)** 必须存在。

    > [!NOTE]
> 发现新条形码时，屏幕阅读器将公布此条码形。 不会公布值。 只要条形码在视图中，屏幕阅读器就会每隔 5 秒提醒一次，指示仍在识别相同的条形码。
