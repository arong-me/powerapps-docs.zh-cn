---
title: 预览功能：将 Azure Cosmos DB for SQL API 数据提供程序与 Common Data Service for Apps 结合使用 | MicrosoftDocs
description: 了解如何配置 Azure Cosmos DB for SQL API 数据提供程序，以便将其与虚拟实体结合使用。
keywords: SQL API
ms.date: 06/27/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: d0031ffc-8754-4a12-b8c1-e08edc49ff73
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: ''
topic-status: Drafting
ms.openlocfilehash: fa45376dff85205a0dfbf28334c678293528d00e
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669285"
---
# <a name="preview-feature-azure-cosmos-db-sql-api-data-provider-requirements"></a>预览功能：Azure Cosmos DB SQL API 数据提供程序要求

本主题介绍 Azure Cosmos DB for SQL API 数据提供程序的要求，以及将 Azure Cosmos DB for SQL API 数据提供程序与虚拟实体结合使用时的配置方式和建议的最佳做法。 

> [!IMPORTANT]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-no-ms-support.md)]


## <a name="what-is-azure-cosmos-db"></a>什么是 Azure Cosmos DB？

Azure Cosmos DB 是 Microsoft 的全球分布式多模式数据库服务，适用于任务关键型应用程序。 它提供了丰富且熟悉的 SQL 查询功能，在传输无架构 JSON 数据过程中可保持较低的延迟。 详细信息：[Azure Cosmos DB 简介：SQL API](https://docs.microsoft.com/azure/cosmos-db/sql-api-introduction)

## <a name="requirements"></a>要求

- 包含 Azure Cosmos DB 的 Azure 订阅。
- Azure Cosmos DB SQL API 集合。
- Azure Cosmos DB 数据库类型应为 SQL。 

## <a name="data-type-mapping"></a>数据类型映射

假设你在名为“订单”的集合中具有 Azure Cosmos DB 文档，该集合的 JSON 结构如下。

![SQL API 文档的 JSON 示例。](media/documentdbexample.png)

此表指示“订单”集合中的 SQL API 文档和 Common Data Service for Apps 的数据类型映射。

|SQL API 数据|CDS for Apps|
|--|--|
|`id`|主要密钥|
|`name`|单行文本|
|`quantity`|整数|
|`orderid`|单行文本|
|`ordertype`|选项集|
|`amount`|小数或货币|
|`delivered`|两个选项|
|`datetimeoffset`|日期和时间|

> [!NOTE]
> - 带有下划线 (_) 前缀的属性由 SQL API 生成。
> - 在 SQL API 文档中配置为可选并在 CDS for Apps 中映射为“业务必需”的属性将导致出现运行时错误。
> - id 属性的值必需为 GUID。
> - 若要详细了解如何使用 SQL API 中的日期，请参阅[在 Azure Cosmos DB 中使用日期](https://azure.microsoft.com/blog/working-with-dates-in-azure-documentdb-4/)。

## <a name="supported-sql-query-filtering"></a>支持的 SQL 查询筛选

SQL 查询筛选支持以下运算符。 

- 比较运算符：`<`、`>`、`<=`、`>=` 和 `!=`
- 逻辑运算符：`and` 和 `or` 
- 集合运算符：`in` 和 `not in`
- 字符串运算符：`like`、`contains`、b`egins with` 和 `ends with`

> [!NOTE]
> like 运算符的使用将转换为等效的 `contains`/`begins with`/`ends with` 运算符。 SQL API 不支持模式参数，如主题 [Like (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql) 中所述。 Azure Cosmos DB for SQL API 数据提供程序可将单个特殊的 `Like('[aA]%')` 转换为 `BeginsWith('a')` 或 `BeginsWith('A')`。 请注意，SQL API 中的字符串比较需区分大小写。

## <a name="add-a-data-source-using-the-azure-cosmos-db-for-sql-api-data-provider"></a>使用 Azure Cosmos DB for SQL API 数据提供程序添加数据源

1. 转到 [AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.documentdb_data_provider?tab=Overview)，选择“立即获取”，然后按照说明使用 v9x 或更高版本将应用程序添加到环境中。
2. 安装解决方案后，登录到环境并转到“设置” > “管理” > “虚拟实体数据源”。
3. 在“操作”工具栏上选择“新建”，并在“选择数据提供程序”对话框中选择“Azure Cosmos DB for SQL API 数据提供程序”，然后选择“确定”。
![选择“Azure Cosmos DB for SQL API 数据提供程序”。](media/createdatasource.png)
1. 输入以下信息，并选择“保存并关闭”。

    |字段|描述|
    |--|--|
    |**名称**|键入描述数据源的名称。|
    |**集合名称**|Azure Cosmos DB 数据库集合（其中包含要在虚拟实体中显示的数据）的 ID。  |
    |**授权密钥**|Azure Cosmos DB 帐户的主要或辅助密钥。 可在 Azure 管理门户中，Azure Cosmos DB 帐户下的“密钥”设置中找到该密钥。|
    |**URI**|Azure Cosmos DB 集合所在资源组的 URI。 URI 的格式类似于 `https://contoso/documents.azure.com:443`。 可在 Azure 管理门户中，Azure Cosmos DB 帐户的“密钥”设置下找到该 URI。 |
    |**超时（以秒为单位）**。|输入在数据请求超时前等待 Azure Cosmos DB 服务响应的秒数。例如，输入 30 秒，则最长等待 30 秒后便发生超时。 默认超时为 120 秒。|

    ![使用 SQL API 数据提供程序创建数据源。](media/cosmosdb-datasource.png)

## <a name="best-practices-and-limitations"></a>最佳做法和限制

- 在将 Azure Cosmos DB 用作数据源时，请注意以下事项：
   - 每个 Azure Cosmos DB 数据源只能与一个虚拟实体关联。
   - 可将多个数据源与 Azure Cosmos DB 中的同一集合连接。
- 不能按实体细分集合中的数据。
- Azure Cosmos DB 数据库不需要架构，但必须使用可预测架构对 Azure Cosmos DB 中的数据进行结构化。 
- 尽管 Azure Cosmos DB for SQL API 数据提供程序可实现投影、筛选和排序运算符的查询转换，但不支持联接操作。
- 使用 SQL API 只能按单个列进行筛选。

## <a name="see-also"></a>另请参阅

[创建和编辑包含外部数据源数据的虚拟实体](create-edit-virtual-entities.md)
