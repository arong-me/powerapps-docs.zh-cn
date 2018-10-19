---
title: 预览功能：通过面向应用程序的 Common Data Service 使用 Azure Cosmos DB for SQL API 数据提供程序 | MicrosoftDocs
description: 了解如何配置 Azure Cosmos DB for SQL API 数据提供程序以与虚拟实体结合使用。
keywords: SQL API
ms.date: 06/27/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: d0031ffc-8754-4a12-b8c1-e08edc49ff73
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: null
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="preview-feature-azure-cosmos-db-sql-api-data-provider-requirements"></a>预览功能：Azure Cosmos DB SQL API 数据提供程序的要求

本主题介绍 Azure Cosmos DB for SQL API 数据提供程序的要求，以及在您将 Azure Cosmos DB for SQL API 数据提供程序用于虚拟实体时如何配置和建议最佳实践。 

> [!IMPORTANT]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-no-ms-support.md)]


## <a name="what-is-azure-cosmos-db"></a>Azure Cosmos DB 是什么？

Azure Cosmos DB 是 Microsoft 全球分发的用于任务关键型应用程序的多模型数据库服务。 它提供丰富且熟悉的 SQL 查询功能，在架构灵活的 JSON 数据中具有一致的低延迟。 详细信息：[Azure Cosmos DB 简介：SQL API](https://docs.microsoft.com/azure/cosmos-db/sql-api-introduction)

## <a name="requirements"></a>要求

- 包含 Azure Cosmos DB 的 Azure 订阅。
- Azure Cosmos DB SQL API 集合。
- Azure Cosmos DB 的数据库类型应为 SQL。 

## <a name="data-type-mapping"></a>数据类型映射

假定您在名为*订单*的集合中有一个 Azure Cosmos DB 文档，此集合具有以下 JSON 结构。

![SQL API 文档的示例 JSON。](media/documentdbexample.png)

此表指示使用面向应用程序的 Common Data Service 的*订单*集合中 SQL API 文档的数据类型映射。

|SQL API 数据|面向应用程序的 CDS|
|--|--|
|`id`|主键|
|`name`|单行文本|
|`quantity`|整数|
|`orderid`|单行文本|
|`ordertype`|选项集|
|`amount`|十进制数字或货币|
|`delivered`|两个选项|
|`datetimeoffset`|日期和时间|

> [!NOTE]
> - 带下划线 (_) 前缀的属性由 SQL API 生成。
> - 在 SQL API 文档中配置为可选并在面向应用程序的 CDS 中作为**必需业务**映射的属性会导致运行时错误。
> - ID 属性值必须是 guid。
> - 有关使用 SQL API 中的日期的更多信息，请参阅[使用 Azure Cosmos DB 中的日期](https://azure.microsoft.com/blog/working-with-dates-in-azure-documentdb-4/)。

## <a name="supported-sql-query-filtering"></a>支持的 SQL 查询筛选

SQL 查询筛选支持以下运算符。 

- 比较运算符：`<`、`>`、`<=`、`>=`、`!=`
- 逻辑运算符：`and`、`or` 
- 设置运算符：`in`、`not in`
- 字符串运算符：`like`、`contains`、b`egins with`、`ends with`

> [!NOTE]
> 使用 like 运算符将转换为等效的 `contains`/`begins with`/`ends with` 运算符。 SQL API 不支持模式参数，如主题 [Like (Transact-SQL)](/sql/t-sql/language-elements/like-transact-sql) 中所述。 Azure Cosmos DB for SQL API 数据提供程序可以将单个特殊案例 `Like('[aA]%')` 转换为 `BeginsWith('a')` 或 `BeginsWith('A')`。 请注意，SQL API 中的字符串比较区分大小写。

## <a name="add-a-data-source-using-the-azure-cosmos-db-for-sql-api-data-provider"></a>使用 Azure Cosmos DB for SQL API 数据提供程序添加数据源

1. 转到 [AppSource](https://appsource.microsoft.com/product/dynamics-365/mscrm.documentdb_data_provider?tab=Overview)，选择**立即获取**，然后使用 v9x 或更高版本按照说明将应用程序添加到环境中。
2. 在安装解决方案后，登录到环境并转到**设置** > **管理** > **虚拟实体数据源**。
3. 在“操作”工具栏上，选择**新建**，在**选择数据提供程序**对话框中选择 **Azure Cosmos DB for SQL API 数据提供程序**，然后选择**确定**。
![选择 Azure Cosmos DB for SQL API 数据提供程序。](media/createdatasource.png)
1. 输入以下信息，然后选择**保存并关闭**。

    |字段|说明|
    |--|--|
    |**名称**|键入用于描述数据源的名称。|
    |**集合名称**|包含您要在虚拟实体中显示的数据的 Azure Cosmos DB 数据库集合的 ID。  |
    |**授权密钥**|Azure Cosmos DB 帐户的主要密钥或辅助密钥。 您可以从您的 Azure Cosmos DB 帐户下**密钥**设置下的 Azure 管理门户找到密钥。|
    |**Uri**|Azure Cosmos DB 集合所在的资源组的 URI。 URI 的格式类似于 `https://contoso/documents.azure.com:443`。 您可以从您的 Azure Cosmos DB 帐户下**密钥**设置下的 Azure 管理门户找到 URI。 |
    |**超时(以秒为单位)**|输入数据请求超时前等待 Azure Cosmos DB 服务响应的秒数。例如，输入 30 将最多等待 30 秒才超时。 默认超时为 120 秒。|

    > [!div class="mx-imgBorder"] 
    > ![使用 SQL API 数据提供程序创建数据源。](media/cosmosdb-datasource.png)

## <a name="best-practices-and-limitations"></a>最佳实践和限制

- 使用 Azure Cosmos DB 作为数据源时请注意以下问题：
   - 每个 Azure Cosmos DB 数据源只能与一个虚拟实体关联。
   - 您可以将多个数据源连接到 Azure Cosmos DB 中的同一个集合。
- 无法按实体细分集合中的数据。
- Azure Cosmos DB 数据库不需要架构，但是 Azure Cosmos DB 内的数据必须使用可预测数据结构化。 
- 虽然 Azure Cosmos DB for SQL API 数据提供程序实施投射、筛选和排序运算符的查询转换，但它不支持联接操作。
- 您只能通过 SQL API 按单个列筛选。

## <a name="see-also"></a>另请参阅

[创建和编辑包含来自外部数据源的数据的虚拟实体](create-edit-virtual-entities.md)
