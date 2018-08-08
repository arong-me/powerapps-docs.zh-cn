---
title: 使用通用数据模型进行开发 | Microsoft Docs
description: 提供有关如何使用通用数据模型开发应用和解决方案的信息。
author: RobertBruckner
ms.service: powerapps
ms.topic: article
ms.date: 07/24/2018
ms.author: robruc
ms.openlocfilehash: 6e99fbe13d9b6e3acdd0cfdd08662676a321471c
ms.sourcegitcommit: abe4d4728db7f56088f618af5b820af78e7099c9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/28/2018
ms.locfileid: "39332056"
---
# <a name="how-to-use-the-common-data-model"></a>如何使用 Common Data Service

借助通用数据模型 (CDM)，可以将数据设置为表示常用概念和活动并得到广泛使用和理解的格式，这样便可以查询并重复使用这些数据，与其他使用这种格式的业务和应用程序进行交互操作。 类似于了解五号电池的大小和形状，让所有遥控器都可以使用，CDM 定义了（例如）“联系人”的大小和形状，因此便于应用程序开发人员和业务合作伙伴了解如何轻松灵活地获取数据并生成自己的应用（或互操作）。 由于 CDM 是标准实体的开源定义，对此感兴趣的开发人员社区可以轻松理解并参与架构定义。

如今，CDM 可在 Common Data Service (CDS) for Apps 中使用，它支持 Dynamics 和 PowerApps，以及 Power BI 的数据准备功能（可以在 Azure Data Lake 中创建架构化文件）。

![通用数据模型和 CDS for Apps](media/cdm-with-cds.png)

可以通过以下方式使用 CDM 和 CDS for Apps：

-   **以 CDM 格式安全存储和管理数据**：可使用 CDS for Apps 以 CDM 格式安全存储和管理数据。 由此，你可以访问和使用 Dynamics、Power Apps、Flow、Power BI 等 Microsoft 应用和服务中或自定义应用程序中的数据。

-   **创建自定义 CDM 实体**：CDM 是可扩展的，因此可以创建特定于组织的尚未采用 CDM 格式的实体，并通过 Power Query 使用现有数据填充这些实体。 这样可以充分利用 CDM，还能根据业务需要进行自定义。

-   **创建自己的数据存储库**：可以构建遵循通用数据模型 (CDM) 架构的数据存储库，并使用 Microsoft 数据连接器连接到这些数据源。 这样可以生成使用或共享 CDM 数据的自定义业务线应用程序，而不考虑数据源或存储的位置。

-   **使用 Power BI 快速获取并分发见解**：可以在 Power BI 中使用访问 CDM 数据存储（例如已放入 CDS for Apps 中的数据）的高级数据准备服务来创建报表和仪表板，然后创建生成报表的应用，这些应用自动将 CDM 数据提取到组织内个人和组的自定义见解中。

-   **在 Power BI 中生成自定义但属于组织范围内的报表**：可以使用自动生成自定义报表的应用，这些报表会放置到组织内用户及其他用户的 Power BI 工作区中。

随着 Microsoft 在 CDM 领域的不断拓展，以及与众多合作伙伴和主题专家的合作，医疗保健等新兴行业将能够从 CDM 和支持它的平台中受益。

## <a name="data-integration-and-power-query-online"></a>数据集成和 Power Query Online

目前支持 CDM 的两个平台还通过 Power Query Online 提供数据集成体验，让用户可以从各种源引入数据、必要时进行转换，然后映射到标准 CDM 实体或创建自定义实体。 Power Query Online 采用与 Excel 中的 Power Query 以及 Power BI Desktop 相同的可视化、自助式数据准备体验，因此现有用户可以快速上手。

![通过采用 CDM 格式的实体映射数据](media/cdm-map-entities.png)

## <a name="common-data-service-for-apps"></a>Common Data Service for Apps

通过 CDS for Apps，可使用具有内置业务逻辑、安全性和集成的 CDM 快速启动应用。 通过该平台，可以：

-   **利用打包的商业应用程序**：许多 Microsoft Dynamics 解决方案和第三方应用程序都是基于（或至少利用）CDS for Apps 生成的。 当数据采用 CDM 格式时，你可以利用这些打包的应用程序。

-   **访问自定义解决方案**：扩展和完整应用程序的生态系统，由了解和处理 CDM 格式数据的开发人员创建。 有关详细信息，请参阅[解决方案简介](https://docs.microsoft.com/powerapps/developer/common-data-service/introduction-solutions)。

无论你的目的是什么，CDM 都会将数据设置为通用格式，这样你便可以更加轻松地使用、共享和分析数据。

**CDS for Apps 资源**

-   [什么是 CDS for Apps？](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-intro)

-   [使用 Power Query 将数据添加到 CDS for Apps 中的实体](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-cds-newentity-pq)

-   [解决方案简介](https://docs.microsoft.com/powerapps/developer/common-data-service/introduction-solutions)

-   [生成模型驱动应用](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

-   [生成画布应用](https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started)

-   [创建使用 CDS for Apps 的流](https://docs.microsoft.com/flow/common-data-model-intro)

