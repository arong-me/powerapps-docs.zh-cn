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
ms.assetid: ''
caps.latest.revision: ''
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: d7957f048613045a64af0caf5696e540dbb8f883
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2754771"
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
在使用 Azure Data Lake Storage Gen2 帐户配置您的环境之前，必须创建和配置存储帐户。 以下是 Power Platform 数据流的要求：
1.  必须在与 PowerApps 租户相同的 Azure Active Directory 租户中创建存储帐户。
2.  我们建议在与您打算在其中使用帐户的 PowerApps 环境相同的区域中创建存储帐户。 要确定 PowerApps 环境在哪里，请与环境管理员联系。
3.  存储帐户必须启用了分层命名空间功能。
4.  您必须在存储帐户中被授予“负责人”角色。

以下各节逐步介绍了配置 Azure Data Lake Storage Gen2 帐户所需的步骤。

## <a name="create-the-storage-account"></a>创建存储帐户
请按照[创建 Azure Data Lake Storage Gen2 存储帐户](https://docs.microsoft.com/azure/storage/blobs/data-lake-storage-quickstart-create-account)中的步骤操作。
1.  确保选择与环境相同的区域，并将存储设置为 StorageV2（常规用途 v2）。
2.  确保启用分层命名空间功能。 
3.  我们建议您将复制设置设置为“读取访问异地冗余存储 (RA-GRS)”。

## <a name="connect-your-azure-data-lake-storage-gen2-to-powerapps"></a>将 Azure Data Lake Storage Gen2 连接到 PowerApps
在 Azure 门户中设置 Azure Data Lake Storage Gen2 帐户后，即可将其连接到特定的数据流或 PowerApps 环境。 将湖连接到环境后，环境中的其他开发者和管理员可以创建将其数据也存储在组织的湖中的数据流。 

要将您的 Azure Data Lake Storage Gen2 帐户与数据流连接，请按照下列步骤操作：
1.  登录到 [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后验证您所在的环境。 环境切换器位于标头的右侧。 
2. 在左侧导航窗格中，选择**数据**旁边的向下箭头。

   ![PowerApps 开发者门户“数据”选项卡](media/powerapps-portal-data.png)

3. 在显示的列表中，选择**数据流**，然后在命令栏上选择**新建数据流**。

   ![创建新数据流](media/new-dataflow.png) 

4. 选择所需的分析实体。 这些实体指示您要存储在组织的 Azure Data Lake Store Gen2 帐户中的数据。 

   ![选择分析实体](media/select-analytical-entities.png)

## <a name="select-the-storage-account-to-use-for-dataflow-storage"></a>选择用于数据流存储的存储帐户
如果尚未将存储帐户与环境关联，则会显示**链接到 Data Lake** 对话框。 您将需要登录并找到在先前步骤中创建的 Data Lake。 在此示例中，没有 Data Lake 与环境关联，因此将提示添加一个 Data Lake。 


1. 选择存储帐户。

    **选择存储帐户**屏幕将出现。
    
    ![选择存储帐户](media/select-storage-account.png)
    
2. 选择存储帐户的**订阅 ID**。
3. 选择创建存储帐户的**资源组名称**。
4. 输入**存储帐户名称**。
5. 选择**保存**。

成功完成这些步骤后，您的 Azure Data Lake Storage Gen2 帐户已连接到 Power Platform 数据流，您可以继续创建数据流。

## <a name="considerations-and-limitations"></a>注意事项和限制
使用数据流存储时，需要牢记一些注意事项和限制：
- 在默认环境中，不支持链接 Azure Data Lake Store Gen2 帐户进行数据流存储。
- 为数据流配置数据流存储位置后，将无法更改它。
- 默认情况下，环境的任何成员都可以使用 Power Platform 数据流连接器访问数据流数据。 但是，只有数据流的负责人才能直接在 Azure Data Lake Storage Gen2 中访问其文件。 要授权其他人直接在湖中访问数据流数据，您必须为他们授予数据湖中数据流的 **CDM 文件夹**或数据湖本身的权限。
- 删除数据流后，其在湖中的 **CDM 文件夹**也将被删除。 

> [!IMPORTANT]
> 您不应该在组织的湖中更改由数据流创建的文件，也不应该将文件添加到数据流的 **CDM 文件夹**中。 更改文件可能会损坏数据流或更改其行为，因此不支持。 Power Platform 数据流仅授予对其在湖中创建的文件的读取访问权限。 如果您向其他人或服务授予 Power Platform 数据流使用的文件系统的权限，则仅授予他们对该文件系统中文件或文件夹的读取权限。

## <a name="frequently-asked-questions"></a>常见问题
*如果我以前在组织的 Azure Data Lake Storage Gen2 中创建了数据流并且想要更改其存储位置怎么办？*

   创建数据流后，您将无法更改其存储位置。

*什么时候可以更改环境的数据流存储位置？*

   当前不支持更改环境的数据流存储位置。 

## <a name="next-steps"></a>后续步骤
本文提供了有关如何连接 Azure Data Lake Storage Gen2 帐户进行数据流存储的指南。 

有关数据流、Common Data Model 和 Azure Data Lake Storage Gen2 的详细信息，请参阅以下文章：
- [使用数据流准备自助服务数据](https://go.microsoft.com/fwlink/?linkid=2099972)
- [在 PowerApps 中创建和使用工作流](https://go.microsoft.com/fwlink/?linkid=2100076)
- [连接 Azure Data Lake Storage Gen2 以存储数据流](https://go.microsoft.com/fwlink/?linkid=2099973)
- [在 Common Data Service 中向实体添加数据](https://go.microsoft.com/fwlink/?linkid=2100075)

有关 Azure 存储的更多信息，请参阅此文章：
- [Azure 存储安全指南](https://docs.microsoft.com/azure/storage/common/storage-security-guide)

有关 Common Data Model 的详细信息，请参阅以下文章：
- [Common Data Model - 概述](https://docs.microsoft.com/powerapps/common-data-model/overview) 
- [Common Data Model 文件夹](https://go.microsoft.com/fwlink/?linkid=2045304)
- [CDM 模型文件定义](https://go.microsoft.com/fwlink/?linkid=2045521)

您可以在 [PowerApps 社区](https://go.microsoft.com/fwlink/?linkid=2099971)中提问。
