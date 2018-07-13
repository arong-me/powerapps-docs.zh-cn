---
title: 附件控件：参考 | Microsoft 文档
description: 有关附件控件的信息（包括属性和示例）
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 04/23/2018
ms.author: fikaradz
ms.reviewer: anneta
ms.openlocfilehash: d8e195ad3e4f59b9f07e23e17a685d9d1f55bef4
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39022024"
---
# <a name="attachments-control-in-powerapps"></a>PowerApps 中的附件控件
方便用户将文件下载到设备，并在 SharePoint 列表中上传和删除文件的控件。

## <a name="limitations"></a>限制
附件控件具有以下临时限制：
1. 仅支持在 SharePoint 自定义列表窗体中，从 Internet Explorer 下载附件。

1. 附件上传仅适用于 SharePoint 列表数据源。  将逐步递增对其他数据源的支持，首先是对 CDS 的支持。

1. 上传和删除功能仅在表单内部有效。  在编辑模式下，如果不在表单内部，附件控件会处于禁用状态。   请注意，最终用户必须保存表单，才能将文件添加和删除操作保存到后端。

1. 最大只能上传 10 MB 文件。  

1. 目前，iOS 设备只能将从文档和云存储帐户上传文件。 若要附加照片/视频，请在你的 iOS 设备上使用 Web 浏览器运行应用程序。

## <a name="description"></a>描述
使用“附件”控件，可以打开在数据源中存储的文件，并能在 SharePoint 列表中添加和删除文件。

## <a name="key-properties"></a>关键属性
[Items](properties-core.md) – 描述可下载文件的源。

MaxAttachments – 控件将接受的文件数上限。

MaxAttachmentSize – 每个新附件的文件大小上限（以 MB 为单位）。  暂不得超过 10 MB。

OnAttach – 当用户添加新的文件附件时，应用的响应方式。

OnRemove – 当用户删除现有附件时，应用的响应方式。

[OnSelect](properties-core.md) – 当用户单击附件时，应用的响应方式。

## <a name="additional-properties"></a>其他属性
**[AccessibleLabel](properties-accessibility.md)** – 屏幕阅读器标签。 应描述附件的用途。

AddAttachmentText – 用于添加新附件的链接的标签文本。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

[DisplayMode](properties-core.md) – 控件是允许添加和删除文件 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[FocusedBorderColor](properties-color-border.md)** – 当聚焦到控件时，控件的边框颜色。

**[FocusedBorderThickness](properties-color-border.md)** – 当聚焦到控件时，控件的边框粗细。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

MaxAttachmentsText – 当控件中的文件数达到上限时，用于替换“附加文件”链接的文本。

**NoAttachmentsText** – 在未附加任何文件时向用户显示的说明文本。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

[Visible](properties-core.md) – 控件可见还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

[Y](properties-size-location.md) – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。


## <a name="example"></a>示例
1. 使用 SharePoint 列表作为数据源从数据中创建一个应用。  或者，在你的应用中添加一个窗体，并设置 SharePoint 列表作为其数据源。

2. 在左侧树视图中选择“窗体”控件。

3. 单击右侧选项面板中“属性”选项卡中的“数据”。

4. 在“字段”下，启用“附件”字段。

    与 SharePoint 列表相关联的“附件”字段将显示在窗体中。

[了解如何添加和配置控件]。(../add-configure-controls.md)


## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="color-contrast"></a>颜色对比度
在以下项之间必须有足够的颜色对比度：
* ItemColor 和 ItemFill
* ItemHoverColor 和 ItemHoverFill
* ItemPressedColor 和 ItemPressedFill
* AddedItemColor 和 AddedItemFill
* RemovedItemColor 和 RemovedItemFill
* ItemErrorColor 和 ItemErrorFill
* AddAttachmentColor 和 Fill
* MaxAttachmentsColor 和 Fill
* NoAttachmentsColor 和 Fill

这是除[标准颜色对比度](../accessible-apps-color.md)以外的要求。

### <a name="screen-reader-support"></a>屏幕阅读器支持
必须存在以下属性：
* [AccessibleLabel](properties-accessibility.md)
* AddAttachmentsText
* MaxAttachmentsText
* NoAttachmentsText

### <a name="keyboard-support"></a>键盘支持
* **[“TabIndex”](properties-accessibility.md)** 必须为零或更大，以便键盘用户可以导航到它。
* 焦点指示器必须清晰可见。 可以使用**[“FocusedBorderColor”](properties-color-border.md)** 和**[“FocusedBorderThickness”](properties-color-border.md)** 来实现此目的。
