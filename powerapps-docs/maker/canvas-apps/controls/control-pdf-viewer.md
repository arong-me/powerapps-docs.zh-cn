---
title: PDF 查看器控件：参考 | Microsoft 文档
description: 有关 PDF 查看器控件的信息，包括属性和示例
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 9fdd7f25a729fa71111e1fd5d82e04b7cea874f3
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71986420"
---
# <a name="pdf-viewer-control-experimental-in-powerapps"></a>PowerApps 中的 PDF 查看器控件（实验性）
显示 PDF 文件内容的实验性控件。

## <a name="description"></a>描述
通过添加此类型的控件并将其“Document”属性设置为要显示的文件的 URL（用双引号括住），来显示 PDF 文件中的文本、图形和其他内容。

## <a name="limitations"></a>限制
1. PowerApps 的安全体系结构要求 PDF 查看器仅支持 HTTPS 链接，而不支持 HTTP。  

2. **文档**属性必须直接链接到 PDF 文件。 不支持服务器重定向或文档的 HTML 视图。

3. 承载文档的服务器不得要求身份验证。

4. 如果文档驻留在具有限制性的跨域资源共享（CORS）设置的服务器上，则您可能无法在应用程序中查看 PDF 文档。 若要解决此问题，承载 PDF 文档的服务器必须允许来自 powerapps.com 的跨源请求。

如果控件无法打开文档，应用程序用户可以在外部浏览器中打开 PDF 文档来解决这些限制。 所有外部文档的控件菜单中也有此选项。

应用程序制造商可以通过在应用中包含 PDF 文档作为媒体资源来解决这些限制。 这样，PDF 查看器控件即可始终显示文档。

## <a name="key-properties"></a>关键属性
Document – 用双引号括住的 PDF 文件的 URL。

## <a name="additional-properties"></a>其他属性
ActualZoom – 控件的实际缩放量，可能与“Zoom”属性请求的缩放量不同。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

CurrentFindText – 当前正在使用的搜索词。

**CurrentPage** – 实际显示的 PDF 文件中的页码。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

[DisabledBorderColor](properties-color-border.md) – 控件的 [DisplayMode](properties-core.md) 属性设置为“Disabled”时，该控件边框的颜色。

**[Fill](properties-color-border.md)** – 控件的背景色。

FindNext – 在文档中查找 FindText 的下一个实例。

FindPrevious – 在文档中查找 FindText 的上一个实例。

FindText – 要在文档中查找的搜索词。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

OnStateChange – 控件状态发生更改时应用响应的方式。

[PaddingBottom](properties-size-location.md) – 控件中的文本与该控件的下边缘之间的距离。

[PaddingLeft](properties-size-location.md) – 控件中的文本与该控件的左边缘之间的距离。

[PaddingRight](properties-size-location.md) – 控件中的文本与该控件的右边缘之间的距离。

**[PaddingTop](properties-size-location.md)** – 控件中的文本与该控件的上边缘之间的距离。

Page – 要显示的页码。

PageCount – 文档中的页数。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

ShowControls – 音频或视频播放器是否显示播放按钮和音量滑块等组件，笔控件是否显示绘图、擦除和清除图标等。

**[Tooltip](properties-core.md)** – 用户将鼠标悬停在控件上时显示的解释性文本。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

Zoom – 相机中图像被放大的百分比或 PDF 查看器中文件的视图百分比。

## <a name="example"></a>示例

添加“PDF 查看器”控件，并将其“Document”属性设置为 PDF 文件的 URL（用双引号括住），如下例所示：

  "https://blog.mozilla.org/security/files/2015/05/HTTPS-FAQ.pdf"

此控件显示 PDF 文件。

不知道如何[添加和配置控件](../add-configure-controls.md)？

## <a name="accessibility-guidelines"></a>辅助功能准则

并不支持 PDF 文档的所有辅助功能，因为“PDF 查看器”仍处于实验阶段。 因此，“ShowControls”应设置为“true”，以允许用户在外部应用程序中打开文档。

了解如何通过 [WCAG 2.0](https://www.w3.org/TR/WCAG-TECHS/pdf.html) 和 [PDF/UA](https://www.pdfa.org/pdfua-the-iso-standard-for-universal-accessibility/) 标准创建可访问的 PDF 文档。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* 如果 PDF 文档没有标题，请考虑使用 **[标签](control-text-box.md)** 添加标题。 标题会立即置于“Power BI 查看器”前。
