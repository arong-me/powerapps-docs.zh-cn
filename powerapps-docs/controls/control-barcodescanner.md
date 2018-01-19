---
title: "条码扫描器控件：参考 | Microsoft 文档"
description: "有关条码扫描器控件的信息（包括属性和示例）"
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
ms.openlocfilehash: c27a2319d74db9a50acff84e40ea7df83dc1c126
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/12/2018
---
# <a name="barcode-scanner-control-in-powerapps"></a>PowerApps 中的条码扫描器控件
通过在设备上使用条码扫描器，用户可用来拍摄照片的控件。

## <a name="description"></a>说明
如果添加此控件，用户可从应用运行的任何位置使用一张或多张照片更新数据源。

## <a name="key-properties"></a>关键属性
**barcode scanner** - 在具有多个条码扫描器的设备上，应用使用的条码扫描器的数字 ID。

## <a name="additional-properties"></a>其他属性
**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**Brightness** - 用户在图像中可能感知到的光线强度。

**Contrast** - 用户可区分图像中相似颜色的轻松程度。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**OnStream** - 更新 **Stream** 属性时应用的响应方式。

**Photo** - 用户拍摄照片时捕获的图像。

**Stream** - 基于 **StreamRate** 属性自动更新的图像。

**StreamRate** - 在 **Stream** 属性上更新图像的频率（以毫秒为单位）。  此值的范围介于 100（1/10 秒）到 3,600,000（1 小时）之间。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

**Zoom** - 放大来自条码扫描器的图像百分比或 PDF 查看器中文件的视图百分比。

## <a name="related-functions"></a>相关函数
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>示例
### <a name="add-photos-to-an-image-gallery-control"></a>向图像库控件添加照片
1. 添加**条码扫描器**控件，将其命名为 **Mybarcode scanner**
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
2. 添加一个“标签”控件，然后将输出设置为条形码的值。  
3. 扫描 BarcodeType 属性下设置的类型的条形码。
4. 标签将显示扫描的条形码。

