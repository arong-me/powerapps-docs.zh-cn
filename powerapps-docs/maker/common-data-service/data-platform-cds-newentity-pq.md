---
title: 使用 Power Query 将数据添加到 Common Data Service 中的实体的快速入门 | Microsoft 文档
description: 本快速入门分步说明如何使用 Power Query 将来自另一个数据源的数据添加到 Common Data Service for Apps 中的新实体或现有实体。
services: ''
suite: powerapps
documentationcenter: na
author: AFTOwen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: anneta
ms.openlocfilehash: def53153d3db75b0f56d7878324fa1391c8c58a8
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="quickstart-add-data-to-an-entity-in-the-common-data-service-by-using-power-query"></a>快速入门：使用 Power Query 将数据添加到 Common Data Service 中的实体
在此过程中，将在 [Common Data Service for Apps](data-platform-intro.md) 中创建实体，并使用 Power Query 将来自 OData 源的数据填充到该实体。 可以使用相同的技术来集成来自这些联机和本地源的数据，其中包括：

* SQL Server
* Salesforce
* IBM DB2
* Access
* Excel
* Web API
* OData 源
* 文本文件

还可以在将数据加载到新实体或现有实体之前对其进行筛选、转换和合并。

如果没有适用于 PowerApps 的许可证，可以[免费注册](../signup-for-powerapps.md)。

## <a name="prerequisites"></a>先决条件
若要遵循本主题，请务必切换到可以创建实体的[环境](../canvas-apps/working-with-environments.md)。

## <a name="specify-the-source-data"></a>指定源数据

1. 登录 [PowerApps](https://web.powerapps.com)，然后单击或点击左边缘附近的“数据”的下箭头。

    ![PowerApps 主页](./media/data-platform-cds-newentity-pq/sign-in.png)

1. 在显示的列表中，单击或点击“数据集成”，然后在窗口右上角附近单击或点击“新建项目”。

1. 在数据源列表中，单击或点击“OData”。

    ![选择 OAuth 连接器](./media/data-platform-cds-newentity-pq/choose-odata.png)

1. 在“连接设置”下，键入或粘贴此 URL，然后选择“下一步”：<br>
`http://services.odata.org/V4/Northwind/Northwind.svc/`

1. 在表列表中，选择“客户”复选框，然后单击或点击“下一步”。

    ![选择客户表](./media/data-platform-cds-newentity-pq/select-table.png)

1. （可选）通过选择包含的列、以一种或多种方式转换表、添加索引或条件列或进行其他更改来修改架构以满足需要。

1. 在右下角单击或点击“下一步”。

## <a name="specify-the-target-entity"></a>指定目标实体
1. 在“加载设置”下，选择“加载到新实体”。

    ![指定新实体的名称](./media/data-platform-cds-newentity-pq/new-entity-name.png)

    可以为新实体提供不同的名称或显示名称，但请保留默认值以完全按照本教程进行操作。

1. 在“主名称字段”列表中，单击或点击“联系人姓名”，然后在右下角单击或点击“下一步”。

    可以指定不同的主名称字段，将源表中的不同列映射到正在创建的实体中的每个字段或者两者上。 若要完全遵循本教程，请保留默认列映射。

1. 当“加载状态”为“已完成”时，选择右下角的“完成”。

1. 在“数据”（左边缘附近）下，选择“实体”以显示数据库中的实体列表。

    从 OData 源创建的“客户”实体显示为自定义实体。

    ![标准和自定义实体列表](./media/data-platform-cds-newentity-pq/entity-list.png)

> [!WARNING]
> 如果使用 Power Query 向现有实体添加数据，将覆盖该实体中的所有数据。

如果选择“加载到现有实体”，则可以指定从“客户”表中添加数据的实体。 例如，可以将数据添加到 Common Data Service 附带的“帐户”实体中。 在“源列”下，可以进一步指定来自“客户”表的“联系人姓名”列中的数据应该添加到“帐户”实体中的“名称”列。

![指定新实体的名称](./media/data-platform-cds-newentity-pq/existing-entity.png)

我们非常高兴地宣布推出此功能，很想听到大家的反馈。 请[向我们发送对此功能的建议和反馈](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)！

