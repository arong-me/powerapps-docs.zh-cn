---
title: Excel 连接概述 | Microsoft 文档
description: 通过在云存储帐户中存储工作簿，然后从应用连接到数据，以在 Excel 中显示和更新数据。
services: ''
suite: powerapps
documentationcenter: na
author: archnair
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/02/2016
ms.author: archanan
ms.openlocfilehash: d57d279670bf49c330b68a30bcd99a4578d3bbf9
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="connect-to-excel-from-powerapps"></a>从 PowerApps 连接到 Excel
![Excel](./media/connection-excel/excelicon.png)

Excel *类似*一种连接。 在应用中显示 Excel 数据：

1. [将 Excel 数据设置为表格格式](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664)。
2. 在云存储帐户（例如 Box、Dropbox、Google Drive、OneDrive 和 OneDrive for Business）中存储 Excel 文件。
3. [连接到云存储帐户](../add-manage-connections.md)，然后将 Excel 表格作为数据源添加。
4. 通过[自动生成应用](../get-started-create-from-data.md)或添加和配置**库**控件等内容，在应用中显示此信息。

> [!NOTE]
> 在用户从 PowerApps 连接到 Excel 表后，PowerApps 会立即新建 \_PowerAppsId_**** 列，并且 Excel 表的每一行都有唯一 ID。

[云存储连接概述](cloud-storage-blob-connections.md)中介绍了如何添加连接、将 Excel 表格作为数据源添加以及在应用中使用 Excel 数据。

有关如何连接到其他数据类型的信息，请参阅 [PowerApps 的连接列表](../connections-list.md)。

### <a name="known-limitations"></a>已知的限制
若要了解如何在组织内共享 Excel 数据，请[查看这些限制](cloud-storage-blob-connections.md#sharing-excel-tables)。
