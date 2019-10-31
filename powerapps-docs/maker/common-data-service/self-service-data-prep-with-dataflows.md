---
title: 在 PowerApps 中使用数据流自助准备数据 | MicrosoftDocs
description: 了解如何在 PowerApps 中使用数据流准备数据。
ms.custom: ''
ms.date: 08/05/2019
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


<!--note from editor: I think "dataflows" should be lowercase based on this entry in the Microsoft style guide (scroll down to find dataflows): https://styleguides.azurewebsites.net/Styleguide/Read?id=2696&topicid=42299 -->



# <a name="self-service-data-prep-with-dataflows"></a>使用数据流准备自助服务数据
[!INCLUDE [cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

随着数据量不断上升，将这些数据塑造为结构良好的可行信息的挑战也随之上升。 您可以为应用程序、AI 工作负载或分析准备好数据，以便将大量数据转换为可行见解。 通过在 PowerApps 中自助准备数据，点击数次即可转换数据并加载到 Common Data Service 或您的组织的 Azure Data Lake Storage Gen2 帐户中。

引入数据流是为了帮助组织整合来自不同来源的数据，并准备使用。 可使用熟悉的自助服务工具轻松创建数据流，以便吸收、转换、集成和丰富大量数据。 创建数据流时，将定义数据源连接、ETL（提取、转换、加载）逻辑和生成的数据要加载到的目标。 创建后，可配置数据流的刷新日程安排以指示其运行频率。 此外，新的模型驱动计算引擎可以让数据准备流程对数据流客户而言更容易管理，确定性更高，更简洁。 通过数据流，即使非数据科学家（如应用程序创建者、业务分析人员和报表创建者）现在点击数次即可处理曾经需要数据 IT 组织（使用大量时间）才能创建和监视的任务。


数据流将数据存储到实体中。 实体是一组用于存储数据的记录，类似于表在数据库中存储数据。 客户可以定义自定义实体架构或利用 Common Data Model 的标准实体。
Common Data Model 是可供业务和分析应用程序使用的共享数据语言。 Common Data Model 元数据系统可以实现数据及其含义在各应用程序和业务流程（如 PowerApps、Power BI、某些 Dynamics 365 应用程序（模型驱动应用程序）和 Azure）中一致，这些应用程序和业务流程按照 Common Data Model 存储数据。 然后，可以按照下面的一种方式存储数据流生成的实体：

-   **Common Data Service。** 让您可以安全地存储和管理使用 PowerApps 和 Microsoft Flow 生成的业务应用程序使用的数据。

-   **Azure Data Lake Storage Gen2。** 让您可以使用 Power BI、Azure Data 和 AI 服务或从湖中读取数据的自定义构建业务线应用程序与组织中的人员协作。 将数据加载到 Azure Data Lake Storage Gen2 帐户的数据流将数据存储在 [Common Data Model 文件夹](https://go.microsoft.com/fwlink/?linkid=2045304)中。 **Common Data Model 文件夹**中包含标准化格式的架构化数据和元数据，以便更容易交换数据，以及在生成或使用作为共享存储层存储在组织的 Azure Data Lake Storage 帐户中的数据的服务之间实现完全互操作性。

可使用数据流从一组不断增多的大量受支持本地部署数据源和基于云的数据源（包括 Excel、Azure SQL Database、SharePoint、Azure Data Explorer、Salesforce、Oracle 数据库等）吸收数据。

选择数据源之后，可使用 Power Query 低码/无码体验转换数据和将其映射到 Common Data Model 中的标准实体或创建自定义实体。 高级用户可直接编辑数据流的 M 语言以充分自定义数据流，类似无数 Power BI Desktop 和 Excel 用户已经了解的 Power Query 体验。

创建和保存数据流之后，需要在云中运行。
可以选择触发数据源以手动运行，或为您安排 Power Platform 数据流服务的运行频率。 工作流完成运行时，可使用其数据。 若要将数据流数据加载到 Common Data Service 中，可在 PowerApps、Microsoft Flow、Excel 和其他所有支持 Common Data Service 连接器的应用程序中使用 Common Data Service 连接器。 若要从组织的 Azure Data Lake Storage Gen2 帐户中存储的数据流获取，可使用 Power BI Desktop 中的 Power Platform 数据流连接器或直接在湖中访问文件。

## <a name="how-to-use-dataflows"></a>如何使用数据流
上一部分提供数据流技术的背景。 此部分中，将介绍如何在组织中使用数据流。

> [!NOTE]
> 您必须有付费 PowerApps 套餐才能使用数据流，但是不为因为使用数据流而单独向您收费。 

### <a name="load-data-to-common-data-service"></a>将数据加载到 Common Data Service
可使用数据流在 [Common Data Service](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/data-platform-intro) 中填充以后要在 PowerApps 中使用的实体。 点击数次即可集成来自在线源数据源和本地部署源数据源的数据。

<!--from editor: In the last sentence above, should it change to "...on-premises data sources." ? -->


### <a name="extend-the-common-data-model-for-your-business-needs"></a>针对业务需要扩展 Common Data Model
对于要扩展和基于 Common Data Model 构建的组织，业务智能专业人士可使用数据流自定义标准实体或创建新的标准实体。 然后可使用数据流和这种用于自定义数据模型的自助服务方法构建针对组织度身定制的 Power BI 仪表板。

### <a name="extend-your-capabilities-with-azure-data-and-ai-services"></a>使用 Azure Data 和 AI 服务扩展您的能力
可将 Power Platform 数据流配置为把数据流数据存储到组织的 Azure Data Lake Storage Gen2 帐户中。 如果将环境连接到组织的 Data Lake，则数据科学家和开发人员可利用强大的 Azure 产品（如 Azure 机器学习、Azure Databricks、Azure 数据工厂等）。

有关 Azure Data Lake Storage Gen2 和数据流集成的详细信息（包括如何创建组织的 Azure Data Lake 中驻留的数据流），请参阅[数据流与 Azure Data Lake 集成（预览）](/power-bi/service-dataflows-azure-data-lake-integration)。

## <a name="summary-of-self-service-data-prep-for-big-data-in-powerapps"></a>PowerApps 中的大数据自助数据准备摘要
提供了多种方案和示例，在这些方案和示例中，您可以使用数据流通过业务数据增强控制和更快获取见解。 组织中的其他人员可通过 Common Data Service、Power BI 中的 Power Platform 数据流连接器或通过直接访问数据流在组织的 Azure Data Lake Storage Gen2 帐户中的 **Common Data Service** 文件夹利用数据流。 如果使用 Common Data Model 定义的标准数据模型（架构），业务应用程序可依赖实体的架构，也可以从数据的创建方法或从数据源提取。 数据源完成计划的运行之后，数据即准备就绪，可用于迅速建模和创建应用程序、流或 BI 建议，过去需要数月甚至更长时间才能创建。

组织中的人员可使用 Common Data Model 的标准化格式创建应用程序以生成快速、轻松、自动化的视觉效果和报表。 其中包括但不限于：

-   将各种来源的数据映射到 Common Data Model 中的标准实体以整合数据并利用已知架构驱动现成的应用程序。

-   创建自己的自定义实体以整合组织中的数据。

-   创建利用数据流数据的 Power BI 报表和仪表板。

-   通过组织的 Azure Data Lake Storage Gen2 帐户创建与 Azure Data 和 AI 服务的集成。

## <a name="next-steps"></a>后续步骤

本文概述 PowerApps 门户中的自助数据准备及其使用方法。 以下主题更详细地介绍数据流的常见使用方案：

-   [在 PowerApps 中创建和使用工作流](https://go.microsoft.com/fwlink/?linkid=2100076)

-   [在 Common Data Service 中向实体添加数据](https://go.microsoft.com/fwlink/?linkid=2100075)

-   [连接 Azure Data Lake Storage Gen2 以存储数据流](https://go.microsoft.com/fwlink/?linkid=2099973)

-   [结合本地部署数据源使用数据流](https://go.microsoft.com/fwlink/?linkid=2100077)

有关 Power Query 和计划刷新的详细信息，可阅读以下文章：

-   [Power BI Desktop 中的查询概述](/power-bi/desktop-query-overview)

-   [配置计划刷新](/power-bi/refresh-scheduled-refresh)

有关 Common Data Model 的详细信息，可阅读以下概述文章：

-   [Common Data Model - 概述](/powerapps/common-data-model/overview)

