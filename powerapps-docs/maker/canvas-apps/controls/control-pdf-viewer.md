---
title: "PDF 查看器控件：参考 | Microsoft 文档"
description: "有关 PDF 查看器控件的信息，包括属性和示例"
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
ms.openlocfilehash: c3ed17faae5963f71531b2fdc2ef9b08ee2569cc
ms.sourcegitcommit: c76ec82db5d261be1fb7fdeeec3e119cdfada57f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2018
---
# <a name="pdf-viewer-control-experimental-in-powerapps"></a>PowerApps 中的 PDF 查看器控件（实验性）
显示 PDF 文件内容的实验性控件。

## <a name="description"></a>说明
通过添加此类型的控件并将其 **Document** 属性设置为要显示的文件的 URL（用双引号括住），来显示 PDF 文件中的文本、图形和其他内容。

## <a name="limitations"></a>限制
请注意，由于 PowerApps 的安全体系结构，PDF 查看器仅支持 HTTPS 链接，而不支持 HTTP。  
如果 PDF 文档所在的服务器具有限制 CORS 的设置，则无法在应用程序中进行查看。  托管 PDF 文档的服务器必须允许来自 powerapps.com 的跨源请求 (CORS)，才能解决此问题。

如果文档无法在 PowerApps 中打开，则在外部浏览器中打开文档的选项会显示给最终用户。  所有外部文档的控件菜单中也有此选项。

## <a name="key-properties"></a>关键属性
**Document** - 用双引号括住的 PDF 文件的 URL。

## <a name="additional-properties"></a>其他属性
**ActualZoom** - 控件的实际缩放量，可能与 **Zoom** 属性请求的缩放量不同。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**CurrentFindText** - 当前正在使用的搜索词。

**CurrentPage** - 实际显示的 PDF 文件中的页码。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为 Disabled 时，该控件边框的颜色。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**FindNext** - 在文档中查找 **FindText** 的下一个实例。

**FindPrevious** - 在文档中查找 **FindText** 的上一个实例。

**FindText** - 要在文档中查找的搜索词。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**OnStateChange** - 控件状态发生更改时应用响应的方式。

**[PaddingBottom](properties-size-location.md)** – 控件中的文本与该控件下边缘之间的距离。

**[PaddingLeft](properties-size-location.md)** - 控件中的文本与该控件的左边缘之间的距离。

**[PaddingRight](properties-size-location.md)** - 控件中的文本与该控件的右边缘之间的距离。

**[PaddingTop](properties-size-location.md)** – 控件中的文本与该控件上边缘之间的距离。

**Page** - 要显示的页码。

**PageCount** - 文档中的页数。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**ShowControls** – 音频或视频播放器是否显示播放按钮和音量滑块等组件，笔控件是否显示绘图、擦除和清除图标等。

**[Tooltip](properties-core.md)** - 用户将鼠标悬停在控件上时显示的解释性文本。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

**Zoom** – 相机中图像被放大的百分比或 PDF 查看器中文件的视图百分比。

## <a name="example"></a>示例
* 添加 **PDF 查看器**控件，并将其 **Document** 属性设置为 PDF 文件的 URL（用双引号括住），如下例所示：<br>
  **"http://www.who.int/gho/publications/world_health_statistics/EN_WHS2015_TOC.pdf?ua=1"**

    此控件显示 PDF 文件。

    不知道如何[添加和配置控件](../add-configure-controls.md)？