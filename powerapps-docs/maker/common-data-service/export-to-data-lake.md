---
title: 导出到数据湖 | MicrosoftDocs
description: 了解如何在 Power Apps 中将实体数据导出到 Azure Data Lake 中
ms.custom: ''
ms.date: 01/28/2020
ms.reviewer: Mattp123
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- powerapps
author: sabinn-msft
ms.assetid: ''
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6adf35a76df347ca8a99bd12620e7beea4b403d5
ms.sourcegitcommit: 97a36c9df2a7067a29fb6bd254975dadc2bc16fa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2020
ms.locfileid: "3072852"
---
# <a name="export-entity-data-to-azure-data-lake-storage-gen2"></a>将实体数据导出到 Azure Data Lake Storage Gen2

导出到 Data Lake 服务是将数据从 Common Data Service 连续导出到 Azure Data Lake Storage Gen2 的管道。 导出到 Data Lake 服务针对企业大数据分析设计，其通过灾难恢复功能提供可伸缩的高可用性。 数据以 Common Data Model 格式存储，因此可以确保应用和部署之间的语义一致性。 

![导出到数据湖概述](media/export-data-lake-overview.png "导出到 Data Lake 概述")

导出到 Data Lake 可提供以下功能： 

- 将 Common Data Service 环境与 Azure 订阅中的 Data Lake Storage Gen2 链接或解除两者之间的链接。 
- 将实体连续复制到 Data Lake Storage Gen2。
- 初始写入数据和元数据后进行增量写入。 
- 复制标准实体和自定义实体。 
- 复制创建、更新和删除 (CrUD) 事务。 
- 持续更新大型分析方案的快照。 
- 简化了元数据恢复和数据生产者与使用者（如 Power BI、Azure 数据工厂、Azure Databricks 和 Azure 机器学习）之间的互操作性。

## <a name="how-data-and-metadata-are-exported"></a>如何导出数据和元数据

导出到 Data Lake 服务支持对实体数据和元数据进行初始写入和增量写入。 将把 Common Data Service 中的所有数据或元数据更改自动推送到数据湖，无需再执行任何操作。 这是推送操作，不是拉取操作。 将把更改推送到目标，无需设置刷新时间间隔。 

可以导出标准实体和自定义实体。 请注意，Common Data Service 中的更改跟踪实体属性用于让数据有效地保持同步，方法是从最初解压缩或最后同步数据开始就监测被更改的数据。 

所有创建、更新和删除操作都将从 Common Data Service 导出到 Data Lake。 例如，如果用户删除 Common Data Service 中的一条客户实体记录，将把事务复制到数据湖。

## <a name="prerequisites"></a>先决条件

必须先创建和配置 Azure Storage v2（一般用途 v2）存储帐户，然后才能将 Common Data Service 数据导出到数据湖。 

请执行 [创建 Azure 存储帐户](/azure/storage/blobs/data-lake-storage-quickstart-create-account) 文章中的步骤，并记下以下要求： 

- 您必须在存储帐户中被授予“负责人”角色。 
- 将存储类型设置为 **Storagev2（一般用途 v2）**。 
- 存储帐户必须启用了**分层命名空间**功能。 

 我们建议您将复制设置为读取访问异地冗余存储 (RA-GRS)。 详细信息：[读取访问异地冗余存储](/azure/storage/common/storage-redundancy-grs#read-access-geo-redundant-storage)

>   ![存储帐户属性](media/storage-account-properties.png "存储帐户属性")

> [!NOTE]
> - 必须在与 Power Apps 租户相同的 Azure Active Directory (Azure AD) 租户中创建存储帐户。  
> - 存储帐户必须在与您将在其中使用功能的 Power Apps 环境相同的区域中创建。  
> - 若要将 Common Data Service 环境链接到 Azure Data Lake Storage Gen2，您必须是 Common Data Service 管理员。 
> - 只能导出已启用了更改跟踪的实体。 

## <a name="select-and-export-common-data-service-entity-data-to-azure-data-lake-storage-gen2"></a>选择并将 Common Data Service 实体数据导出到 Azure Data Lake Storage Gen2

1. 登录 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，展开**数据**，然后选择**实体**。 
2. 在命令栏中选择**导出到数据湖**，然后在**导出到数据湖**页中选择**指向数据湖的新链接**。 
3. 选择下列设置中的每一个，然后选择**下一步**： 
   - **订购**。 选择您的 Azure 订阅。 
   - **资源组**。 选择其中包含 Storage v2（一般用途 v2）存储帐户的资源组。
   - **存储帐户**。 选择要用于导出的 Storage v2（一般用途 v2）存储帐户。 
4. 选择要导出到数据湖的实体，然后选择**保存**。 只能导出已启用了更改跟踪的实体。 详细信息：[启用更改跟踪](/dynamics365/customer-engagement/admin/enable-change-tracking-control-data-synchronization)

   > [!div class="mx-imgBorder"] 
   > ![选择要导出的实体](media/export-data-lake-select-entity.png "选择要导出的实体")

您的 Common Data Service 环境已链接到 Azure Data Lake Storage Gen2 帐户。 将在 Azure 存储帐户中为选择要复制到数据湖的每个实体创建文件系统和一个文件夹。 

## <a name="manage-entity-data-to-the-data-lake"></a>管理实体数据到数据湖的导出

为订阅中的 Azure Data Lake Storage Gen2 设置数据导出之后，可以通过两种方法之一管理实体数据到数据湖的导出： 

- 在 Power Apps 开发者门户的**导出到数据湖**区域中，选择命令栏中的**管理实体**添加或删除链接的一个或多个实体。
- 在 Power Apps 开发者门户的**实体**区域中，选择实体旁边的 **…**， 然后选择要将实体数据导出到的链接的数据湖。 

   ![选择要导出的实体](media/select-entity-export.png "选择要导出的实体")

若要取消链接所有链接的实体，请在 Power Apps 开发者门户的**导出到数据湖**区域中选择**取消链接数据湖**。

## <a name="view-your-data-in-azure-data-lake-storage-gen2"></a>在 Azure Data Lake Storage Gen2 中查看您的数据

1. 登录 [Azure](https://portal.azure.com)，选择存储帐户，然后在最左侧导航窗格中选择**存储资源管理器**。 
2. 展开**文件系统**，然后选择 commondataservice-*environmentName*-org-*Id*。 

model.json 文件和名称与版本一起提供已导出到数据湖的实体的列表。 model.json 文件中还包含初始同步状态和同步完成时间。 

将为导出到数据湖的每个实体显示一个包含快照的逗号分隔（CSV 格式）文件的文件夹。
   > [!div class="mx-imgBorder"] 
   > ![数据湖中的实体数据](media/entity-data-in-lake.png "数据湖中的实体数据") 

### <a name="continuous-snapshot-updates"></a>连续更新快照

可通过创建、更新和删除事务持续更改 Common Data Service 数据。 快照提供定期更新的数据的只读副本，此例中为每小时。 这样可以确保数据分析使用者随时可以可靠地使用湖中的数据。

![连续更新快照](media/snapshot-updates.png "连续更新快照")

如果在初始导出时添加实体，将把实体数据写入到数据湖中相应文件夹下的 entity.csv 文件中。 这是 T1 间隔，此时将创建一个快照只读文件，名称为 *entity*-T1.csv&mdash;例如 Account-T1.csv 或 Contacts-T1.csv。 此外，还将把 model.json 文件更新为指向这些快照文件。 可通过打开 model.json 查看快照详细信息。 

下面是数据湖中 Account.csv 分区文件和快照文件夹的示例。

![客户实体快照](media/export-data-lake-account-snapshots.png "客户实体快照") 

将使用稀疏源引擎把 Common Data Service 中的更改持续推送到相应的 CSV 文件中。 这是 T2 间隔，此时再创建一个快照。 将把*Entity*-T2.csv&mdash;例如 Accounts-T2.csv 或 Contacts-T2.csv（假设对该实体进行了更改）&mdash;和 model.json 更新到新的快照文件。 将把查看 T2 的快照数据的所有新用户继续定向到更新的快照文件。 这样，原始快照查看者就可以继续处理旧快照 T1 文件，而新查看者则可以读取最新更改。 这在具有较长运行时间的下游流程的方案中非常有用。 

下面是 model.json 文件的示例，该文件始终指向时间戳最新的客户快照文件。 

![快照 model.json 文件示例](media/sample-snapshot-json.png "快照 model.json 文件示例") 

## <a name="transporting-an-export-to-data-lake-configuration-across-environments"></a>在环境之间传输导出到 Data Lake 配置

在 Power Apps 中，解决方案被用来将应用和组件从一个环境传输到另一个环境，或将一组自定义项应用到现有应用。 若要让用户注意导出到 Data Lake 配置解决方案，请将“导出到 Data Lake Core”解决方案导入到环境中。 这将启用基本的应用程序生命周期管理 (ALM) 功能，如分发、备份和恢复导出到 Data Lake 配置。 

### <a name="import-the-export-to-data-lake-core-solution"></a>导入“导出到 Data Lake Core”解决方案

1.  从 Power Apps 开发者门户选择要将导出到 Data Lake 配置分发到的环境。
2.  在最左侧导航窗格中，选择**解决方案**，选择**打开 AppSource**，搜索名称为**导出到 Data Lake 核心**的解决方案，然后导入该解决方案。

### <a name="add-an-export-to-data-lake-configuration-to-a-solution"></a>向解决方案添加导出到 Data Lake 配置

> [!IMPORTANT]
> 必须先安装前面介绍的“导出到 Data Lake Core”解决方案，才能添加导出到 Data Lake 配置。 

1.  从 Power Apps 开发者门户选择要将导出到 Data Lake 配置分发到的环境，然后在最左侧导航窗格中选择**解决方案**。 
2.  选择**新建解决方案**，提供名称，选择发布商，然后指定版本号。  
3.  打开上一步中创建的解决方案，选择**添加现有的** > **其他** > **导出到数据湖配置**。 
4.  选择所需链接的数据湖配置，然后选择**添加**。 
5.  在**解决方案**区域中，选择解决方案，然后在命令栏中选择**导出**。 
6.  在**导出前**窗格中，选择**发布**发布导出前的所有更改，然后选择**下一步**。 

### <a name="import-the-solution-that-contains-the-export-to-data-lake-configuration"></a>导入其中包含导出到 Data Lake 配置的解决方案

在要将解决方案导入到的环境中，在 Power Apps 开发者门户的**解决方案**区域中导入解决方案。 

#### <a name="verify-the-export-to-data-lake-configuration"></a>验证导出到 Data Lake 配置

在导入了导出到 Data Lake 配置的环境中，从 Power Apps 开发者门户验证除了从其他环境传输的实体外，是否可查看链接的数据湖。

> [!div class="mx-imgBorder"] 
> ![已导入导出到 Data Lake 实体](media/imported-export-entities.png "已导入导出到 Data Lake 实体") 

### <a name="see-also"></a>另请参阅

[博客：将 CDS 数据导出到 Azure Data Lake](https://powerapps.microsoft.com/blog/exporting-cds-data-to-azure-data-lake-preview/)
