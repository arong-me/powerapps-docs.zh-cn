---
title: 连接 Azure Data Lake Storage Gen2 以存储数据流 | MicrosoftDocs
description: 了解如何连接 Azure Data Lake Storage Gen2 以存储数据流
ms.custom: ''
ms.date: 09/05/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: null
caps.latest.revision: null
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="connect-azure-data-lake-storage-gen2-for-dataflow-storage"></a>连接 Azure Data Lake Storage Gen2 以存储数据流

[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

您可以配置数据流以将其数据存储在组织的 Azure Data Lake Storage Gen2 帐户中。 本文介绍了这样做所必需采取的一般步骤，并提供全程指导和最佳实践。 

配置数据流以将其定义和数据文件存储在您的 Data Lake 中有一些优点，包括：
- Azure Data Lake Storage Gen2 提供了高度可扩展的数据存储设施。
- 您的 IT 部门的开发人员可以利用数据流数据和定义文件来利用 Azure 数据和人工智能 (AI) 服务，如 Azure 数据服务的 GitHub 示例中所示。
- 它使组织中的开发人员可以使用数据流和 Azure 的开发人员资源将数据流数据集成到内部应用程序和业务线解决方案中。

## <a name="requirements"></a>要求
要将 Azure Data Lake Storage Gen2 用于数据流，您需要具备以下条件：
- PowerApps 环境。 任何 PowerApps 计划都将允许您以 Azure Data Lake Storage Gen2 作为目标来创建数据流。 您需要在环境中获得开发者的授权。 
- Azure 订阅。 您需要 Azure 订阅才能使用 Azure Data Lake Storage Gen2。
- 资源组。 使用已有的资源组，或创建一个新资源组。
- Azure 存储帐户。 存储帐户必须启用了 Data Lake Storage Gen2 功能。

> [!TIP]
> 如果您没有 Azure 订阅，请在开始之前[创建一个免费试用帐户](https://azure.microsoft.com/free/)。

## <a name="prepare-your-azure-data-lake-storage-gen2-for-power-platform-dataflows"></a>为 Power Platform 数据流准备 Azure Data Lake Storage Gen2
在使用 Azure Data Lake Storage Gen2 帐户配置 Power BI 之前，必须创建和配置存储帐户。 以下是 Power Platform 数据流的要求：
1.  必须在与 PowerApps 租户相同的 Azure Active Directory 租户中创建存储帐户。
2.  我们建议在与您打算在其中使用帐户的 PowerApps 环境相同的区域中创建存储帐户。 要确定 PowerApps 环境在哪里，请与环境管理员联系。
3.  存储帐户必须启用了分层命名空间功能。
4.  您必须在存储帐户中被授予“负责人”角色。

以下各节逐步介绍了配置 Azure Data Lake Storage Gen2 帐户所需的步骤。

## <a name="create-the-storage-account"></a>创建存储帐户
请按照[创建 Azure Data Lake Storage Gen2 存储帐户](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account)中的步骤操作。
1.  确保选择与 Power BI 租户相同的位置，并将存储设置为 StorageV2（常规用途 v2）。
2.  确保启用分层命名空间功能。 
3.  我们建议您将复制设置设置为“读取访问异地冗余存储 (RA-GRS)”。



<!--from editor: I haven't heard of Athena before. Is it the Amazon service, https://aws.amazon.com/athena/? If so, it probably should be identified as Amazon at first mention. -->


## <a name="create-a-cross-origin-resource-sharing-cors-rule-for-the-athena-service"></a>为 Athena 服务创建跨源资源共享 (CORS) 规则

> [!NOTE]
> Power Platform 数据流利用 Athena 服务将 Data Lake 连接到 PowerApps 环境。 在本节中，需要向 Athena 服务授予存储帐户角色，以便可以将其配置为用于数据流。

接下来，您需要启用 Athena 服务以通过 Web 浏览器和 PowerApps 门户访问存储帐户。 Web 浏览器实施称为[同源策略](http://www.w3.org/Security/wiki/Same_Origin_Policy)的安全限制，该限制可阻止网页在其他域中调用 API；CORS 提供了一种允许一个域（原始域）调用另一个域中的 API 的安全方法。 有关 CORS 的详细信息，请参阅 [CORS 规范](http://www.w3.org/TR/cors/)。

请按照您刚刚在 Azure 门户的设置页面上创建的存储帐户中的步骤进行操作。 在 CORS 菜单项中，选择“BLOB 服务”分区，然后输入这些详细信息。 

|设置  |Value  |
|---------|---------|
|允许的源   | https://athena-ui-prod.trafficmanager.net     |
|允许的方法   |  DELETE、GET、HEAD、MERGE、POST、OPTIONS、PUT、PATCH   |
|允许的标头   | *    |
|显示的标头   | *    |
|最大时间 |   *  |


下图显示了为 Athena 服务配置的 CORS 规则。

![CORS 规则](media/dataflows-cores-rule.png)

## <a name="connect-your-azure-data-lake-storage-gen2-to-powerapps"></a>将 Azure Data Lake Storage Gen2 连接到 PowerApps
在 Azure 门户中设置 Azure Data Lake Storage Gen2 帐户后，即可将其连接到特定的数据流或 PowerApps 环境。 将湖连接到环境后，环境中的其他开发者和管理员可以创建将其数据也存储在组织的湖中的数据流。 

要将您的 Azure Data Lake Storage Gen2 帐户与数据流连接，请按照下列步骤操作：
1.  登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后验证您所在的环境。 环境切换器位于标头的右侧。 
2. 在左侧导航窗格中，选择**数据**旁边的向下箭头。

   ![PowerApps 开发者门户“数据”选项卡](media/powerapps-portal-data.png)

3. 在显示的列表中，选择**数据流**，然后在命令栏上选择**新建数据流**。

   ![创建新数据流](media/new-dataflow.png) 

4. 选择所需的分析实体。 这些实体指示您要存储在组织的 Azure Data Lake Store Gen2 帐户中的数据。 

   ![选择分析实体](media/select-analytical-entities.png)

## <a name="select-the-storage-account-to-use-for-dataflow-storage"></a>选择用于数据流存储的存储帐户
如果尚未将存储帐户与环境关联，则会显示**链接到 Data Lake** 对话框。 您将需要登录并找到在先前步骤中创建的 Data Lake。 在此示例中，没有 Data Lake 与环境关联，因此将提示添加一个 Data Lake。 



<!--from editor: Should "storage account" be in bold because it's something the user has to select? --"

1. Select storage account.

    The **Select Storage Account** screen appears.
    
    ![Select storage account](media/select-storage-account.png)
    
2. Select the **Subscription ID** of the storage account.
3. Select the **Resource group name** in which the storage account was created.
4. Enter the **Storage account name**.
5. Select **Save**.

Once these steps are successfully completed, your Azure Data Lake Storage Gen2 account is connected to Power Platform Dataflows and you can continue to create a dataflow.

## Considerations and limitations
There are a few considerations and limitations to keep in mind when working with your dataflow storage:
- Linking an Azure Data Lake Store Gen2 account for dataflow storage is not supported in the default environment.
- Once a dataflow storage location is configured for a dataflow, it can't be changed.
- By default, any member of the environment can access dataflow data using the Power Platform Dataflows Connector. However, only the owners of a dataflow can access its files directly in Azure Data Lake Storage Gen2. To authorize additional people to access the dataflows data directly in the lake, you must authorize them to the dataflow’s CDM folder in the data lake or the data lake itself.
- When a dataflow is deleted, its CDM folder in the lake will also be deleted. 

> [!IMPORTANT]
> You shouldn't change files created by dataflows in your organization’s lake or add files to a dataflow’s CDM folder. Changing files might damage dataflows or alter their behavior and is not supported. Power Platform Dataflows only grants read access to files it creates in the lake. If you authorize other people or services to the filesystem used by Power Platform Dataflows, only grant them read access to files or folders in that filesystem.

## Frequently asked questions
*What if I had previously created dataflows in my organization’s Azure Data Lake Storage Gen2 and would like to change their storage location?*

   You can't change the storage location of a dataflow after it was created.

*When can I change the dataflow storage location of an environment?*

   Changing the environment's dataflow storage location is not currently supported. 

## Next steps
This article provided guidance about how to connect an Azure Data Lake Storage Gen2 account for dataflow storage. 

For more information about dataflows, the Common Data Model, and Azure Data Lake Storage Gen2, see these articles:
- [Self-service data prep with dataflows](https://go.microsoft.com/fwlink/?linkid=2099972)
- [Creating and using dataflows in PowerApps](https://go.microsoft.com/fwlink/?linkid=2100076)
- [Connect Azure Data Lake Storage Gen2 for dataflow storage](https://go.microsoft.com/fwlink/?linkid=2099973)
- [Add data to an entity in Common Data Service](https://go.microsoft.com/fwlink/?linkid=2100075)

For more information about Azure storage, see this article:
- [Azure Storage security guide](https://docs.microsoft.com/azure/storage/common/storage-security-guide)

For more information about the Common Data Model, see these articles:
- [Common Data Model - overview](https://docs.microsoft.com/powerapps/common-data-model/overview) 
- [Common Data Model folders](https://go.microsoft.com/fwlink/?linkid=2045304)
- [CDM model file definition](https://go.microsoft.com/fwlink/?linkid=2045521)

You can ask questions in the [PowerApps Community](https://go.microsoft.com/fwlink/?linkid=2099971).
