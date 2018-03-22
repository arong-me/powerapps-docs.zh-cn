---
title: "照相机控件：参考 | Microsoft 文档"
description: "有关照相机控件的信息，包括属性和示例"
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
ms.openlocfilehash: a3a724ad42082962ec8aea4e616f1d75aa7299ec
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/12/2018
---
# <a name="camera-control-in-powerapps"></a>PowerApps 中的照相机控件
一个控件，用户通过此控件可使用设备上的照相机拍照。

## <a name="description"></a>说明
如果添加此控件，用户可从应用运行的任何位置使用一张或多张照片更新数据源。

## <a name="key-properties"></a>关键属性
**Camera** - 在具有多个照相机的设备上，应用所使用的照相机的数字 ID。

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

**Zoom** – 相机中图像被放大的百分比或 PDF 查看器中文件的视图百分比。

## <a name="related-functions"></a>相关函数
[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>示例
### <a name="add-photos-to-an-image-gallery-control"></a>向图像库控件添加照片
1. 添加“照相机”控件，将其命名为 **MyCamera**，并将其 **[OnSelect](properties-core.md)** 属性设置为以下公式：<br>
   **Collect(MyPix, MyCamera.Photo)**
   
    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？
   
    想要了解有关 **[Collect](../functions/function-clear-collect-clearcollect.md)** 函数或[其他函数](../formula-reference.md)的详细信息？
2. 按 F5，然后单击或点击 **MyCamera** 进行拍照。
3. 添加**[图像库](control-gallery.md)**控件，然后重新调整其**[图像](control-image.md)**控件、其模板以及“图像库”控件本身的大小，以适应屏幕大小。
4. 将“图像库”控件的 **[Items](properties-core.md)** 属性设置为以下表达式：<br>**MyPix.Url**。
5. 将库中的“图像”控件的 **[Image](properties-visual.md)** 属性设置为以下表达式：<br>
   **ThisItem.Url**
   
    拍摄的照片将在“图像库”控件中显示。
6. 拍摄所需数量的照片，然后按 Esc 返回默认工作区。
7. （可选）将“图像库”控件中“图像”控件的 **OnSelect** 属性设置为 **Remove(MyPix, ThisItem)**，按 F5，然后单击或点击照片将其删除。

使用 **[SaveData](../functions/function-savedata-loaddata.md)** 函数本地保存照片或使用 **[Patch](../functions/function-patch.md)** 函数更新数据源。

