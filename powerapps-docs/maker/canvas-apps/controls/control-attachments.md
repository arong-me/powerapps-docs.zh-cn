---
title: 附件控件：参考 | Microsoft 文档
description: 有关附件控件的信息（包括属性和示例）
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.date: 03/09/2020
ms.author: chmoncay
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 35e4107934134a229817deb258bacf5e36c9dbb6
ms.sourcegitcommit: a02b20113164acb11955d27ef4ffa421ee0fba9d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "78970981"
---
# <a name="attachments-control-in-power-apps"></a>Power Apps 中的附件控件
允许用户将文件下载到其设备，以及上传和删除 SharePoint 列表或 Common Data Service 实体中的文件的控件。

## <a name="limitations"></a>限制
附件控件具有以下限制：
1. SharePoint 列表和 Common Data Service 实体支持附件。

1. 上载和删除功能只能在窗体中使用。 在编辑模式下而不是在窗体中时，附件控件将显示为禁用状态。 若要保存文件添加和删除，应用程序用户必须保存窗体。 由于存在此限制，因此无法从 "**插入**" 选项卡访问 "附件" 控件，但当在 SharePoint 或 Common Data Service 窗体中启用了附件窗体字段时，该控件将显示在窗体中。

1. 仅当文件为 10 MB 或更小时，才能上载文件。  

## <a name="description"></a>说明
使用 "**附件**" 控件，可以打开、添加和删除 SharePoint 列表或 Common Data Service 实体中的文件。

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
1. 向应用程序添加窗体，并将 SharePoint 列表设置为其数据源。

2. 在左侧的树视图中选择 "**显示窗体**" 控件。 您还可以改用 "**编辑表单**"。

3. 在右侧 "选项" 面板的 "属性" 选项卡中选择 "**数据源**"，并选择连接到的 SharePoint 列表。

4. 选择 "**编辑**字段 *"* 部分，然后选择 "**添加字段**"。 

5. 选择 "**附件**" 字段并选择 "**添加**"。

    与 SharePoint 列表相关联的“附件”字段将显示在窗体中。

[了解如何添加和配置控件](../add-configure-controls.md)


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
* 焦点指示器必须清晰可见。 可以使用 **[“FocusedBorderColor”](properties-color-border.md)** 和 **[“FocusedBorderThickness”](properties-color-border.md)** 来实现此目的。
