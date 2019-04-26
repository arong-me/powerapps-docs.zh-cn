---
title: Web 条码扫描器控件： 引用 |Microsoft Docs
description: 包括属性和示例，条码扫描器控件有关的信息
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 10/25/2016
ms.author: fikaradz
ms.reviewer: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 787fa34bdfcabf6103fefd82f66e976b680544e2
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61544582"
---
# <a name="web-barcode-scanner-control-experimental-in-powerapps"></a>（实验） 在 PowerApps 中的 web 条码扫描器控件

旧条形码扫描控件，这已过时，但可能适用于扫描的 web 浏览器中的代码。

## <a name="description"></a>描述

此控件显示相机源应用程序中，以便用户可以扫描条形码，在所有设备上。 该控件是由于性能不佳和移动版已过时**[条码扫描器](control-new-barcode-scanner.md)** 控件所替换此控件。

## <a name="key-properties"></a>关键属性

**barcode scanner** - 在具有多个条码扫描器的设备上，应用使用的条码扫描器的数字 ID。

## <a name="additional-properties"></a>其他属性

**[AccessibleLabel](properties-accessibility.md)** – 屏幕阅读器标签。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**ShowLiveBarcodeDetection** – 是否显示视觉提示以指示条形码检测的状态。 黄色矩形表示正在检查的区域。 跨矩形的绿色线条表示成功的条形码标识。

**Stream** - 基于 **StreamRate** 属性自动更新的图像。

**StreamRate** - 在 **Stream** 属性上更新图像的频率（以毫秒为单位）。  此值的范围为 100（1/10 秒）到 3,600,000（1 小时）。

Text – 上次由扫描仪识别的条形码值。

**[Tooltip](properties-core.md)** – 用户将鼠标悬停在控件上时显示的解释性文本。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="related-functions"></a>相关函数

[**Patch**( *DataSource*, *BaseRecord*, *ChangeRecord* )](../functions/function-patch.md)

## <a name="example"></a>示例

### <a name="add-photos-to-an-image-gallery-control"></a>向图像库控件添加照片

1. 添加**条码扫描器**控件，将其命名为 **Mybarcode scanner**

    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？

1. 添加**标签**控件，并将其输出设置为条形码扫描仪**文本**属性。

1. 扫描设置下的类型的条形码**BarcodeType**属性。

    标签将显示扫描的条形码。

## <a name="accessibility-guidelines"></a>辅助功能准则

### <a name="video-alternatives"></a>视频替代项

* 请考虑添加 **[标签](control-text-box.md)**，并将其 **[Text](properties-core.md)** 设置为条形码扫描仪的“Text”。 由于条形码扫描仪未显示标识的条形码值，执行上述操作将使所有人都可访问扫描仪，而不仅仅是那些有视觉障碍的用户。

### <a name="screen-reader-support"></a>屏幕阅读器支持

* **[“AccessibleLabel”](properties-accessibility.md)** 必须存在。

    > [!NOTE]
  > 已发现新条形码时，屏幕阅读器将公布。 不会公布值。 只要条形码在视图中，屏幕阅读器就会每隔 5 秒提醒一次，指示仍在识别相同的条形码。
