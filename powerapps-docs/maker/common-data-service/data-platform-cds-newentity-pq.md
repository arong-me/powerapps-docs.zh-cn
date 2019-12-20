---
title: 使用 Power Query 将数据添加到 Common Data Service 中的实体 | Microsoft Docs
description: 如何使用 Power Query 在 Common Data Service 中从其他数据源将数据添加到新的或现有实体的分步说明。
author: mllopis
manager: kfile
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: cds
ms.date: 03/21/2018
ms.author: millopis
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: cc5ce204047810704f01562a9a00668e51784769
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "2872878"
---
# <a name="add-data-to-an-entity-in-common-data-service-by-using-power-query"></a>使用 Power Query 将数据添加到 Common Data Service 中的实体
在本过程中，您将在 [Common Data Service](data-platform-intro.md) 中创建实体，并使用 Power Query 用来自 OData 源的数据填充该实体。 您可以使用相同的技巧集成这些联机和本地源的数据，其中包括：

* SQL Server
* 销售团队
* IBM DB2
* 访问
* Excel
* Web API
* OData 源
* 文本文件

在您将数据加载到新的或现有实体之前，您还可以筛选、转换和合并数据。

如果没有 Power Apps 的许可证，您可以[免费注册](../signup-for-powerapps.md)。

## <a name="prerequisites"></a>必备条件
要遵循本主题的做法，您必须切换到可以创建实体的[环境](../canvas-apps/working-with-environments.md)。

## <a name="specify-the-source-data"></a>指定源数据

1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后单击或点按左边缘附近的**数据**向下键。

    ![Power Apps 主页](./media/data-platform-cds-newentity-pq/sign-in.png)

1. 在显示的列表中，单击或点按**数据集成**，然后单击或点按窗口右上角附近的**新建项目**。

1. 在数据源列表中，单击或点按 **OData**。

    ![选择 OAuth 连接器](./media/data-platform-cds-newentity-pq/choose-odata.png)

1. 在**设置连接**下，键入或粘贴该 URL，然后选择**下一步**：<br>
`https://services.odata.org/V4/Northwind/Northwind.svc/`

1. 在表列表中，选择**客户**复选框，然后单击或点按**下一步**。

    ![选择“客户”表](./media/data-platform-cds-newentity-pq/select-table.png)

1. （可选）通过选择要包含的列，通过一种或多种方式转换此表，添加索引或条件列，或进行其他更改，来修改架构以满足您的需求。

1. 在右下角，单击或点按**下一步**。

## <a name="specify-the-target-entity"></a>指定目标实体
1. 在**加载设置**下，选择**加载到新实体**。

    ![指定新实体的名称](./media/data-platform-cds-newentity-pq/new-entity-name.png)

    您可以向新实体提供不同名称或显示名称，但保留默认值以准确按照本教程操作。

1. 在**主名称字段**列表中，单击或点按 **ContactName**，然后单击或点按右下角的**下一步**。

    您可以指定不同的主名称字段，将源表中的不同列映射到您在创建的实体中的每个字段，或同时执行这两项操作。 您还可以指定查询输出中的“文本”列在 Common Data Service 中是应作为“多行文本”还是“单行文本”创建。 要准确按照本教程操作，请保留默认列映射。

1. 在**加载状态**为**已完成**时，选择右下角的**完成**。

1. 左**数据**（左边缘附近），选择**实体**以显示数据库中的实体列表。

    您从 OData 源创建的**客户**实体将显示为自定义实体。

    ![标准和自定义实体的列表](./media/data-platform-cds-newentity-pq/entity-list.png)

> [!WARNING]
> 如果使用 Power Query 将数据添加到现有实体，该实体中的所有数据将被覆盖。

如果选择**加载到现有实体**，可指定一个您可以从**客户**表向其添加数据的实体。 例如，您可以将数据添加到附带 Common Data Service 的**客户**实体。 在**源列**下，您可以进一步指定**客户**表的 **ContactName** 列中的数据应被添加到**客户**实体中的**名称**列。

![指定新实体的名称](./media/data-platform-cds-newentity-pq/existing-entity.png)

我们对此功感到很兴奋，热切盼望能听到您的反馈。 请[向我们发送有关此功能的建议和反馈](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)！

如果出现[有关权限的错误消息](data-platform-cds-newentity-troubleshooting-mashup.md)，请联系您的管理员。

> [!WARNING]
> 使用此功能可以加载的每个运行和每个项目有 500,000 行限制。
