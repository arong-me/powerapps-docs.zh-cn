---
title: "附件控件：参考 | Microsoft 文档"
description: "有关附件控件的信息（包括属性和示例）"
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
ms.date: 09/29/2017
ms.author: fikaradz
ms.openlocfilehash: 2fd5db380eead5403d4cc7d927da5a24aa24abc9
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/12/2018
---
# <a name="attachments-control-in-powerapps"></a>PowerApps 中的附件控件
使用该控件用户可将文件下载到其自己的设备。  上传功能即将推出。

## <a name="description"></a>说明
“附件”控件可让用户打开存储在数据源上的文件。

## <a name="key-properties"></a>关键属性
[Items](properties-core.md) – 描述可下载文件的源。

MaxAttachments – 控件将接受的文件数上限。

OnAttach – 当用户添加新的文件附件时，应用的响应方式。

OnRemove – 当用户删除现有附件时，应用的响应方式。

[OnSelect](properties-core.md) – 当用户单击附件时，应用的响应方式。

## <a name="additional-properties"></a>其他属性
AddAttachmentText – 用于添加新附件的按钮的标签文本。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是**实线**、**虚线**、**点线**还是**无**。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

[DisplayMode](properties-core.md) – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

NoAttachmentsText – 当没有要显示的附件时，向用户显示的说明文本。

[Visible](properties-core.md) – 控件可见还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

[Y](properties-size-location.md) - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。


## <a name="example"></a>示例
1. 使用 SharePoint 列表作为数据源从数据中创建一个应用。  或者，在你的应用中添加一个窗体，并设置 SharePoint 列表作为其数据源。

2. 在左侧树视图中选择“窗体”控件。

3. 单击右侧选项面板中“属性”选项卡中的“数据”。

4. 在“字段”下，启用“附件”字段。

    与 SharePoint 列表相关联的“附件”字段将显示在窗体中。

不知道如何[添加和配置控件](../add-configure-controls.md)？
