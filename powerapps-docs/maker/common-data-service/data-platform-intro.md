---
title: 什么是 Common Data Service？ | Microsoft Docs
description: Common Data Service、实体、服务器端逻辑、安全和开发人员功能简介。
author: clwesene
manager: kvivek
ms.service: powerapps
ms.topic: overview
ms.component: cds
ms.date: 06/21/2019
ms.reviewer: matp
ms.author: matp
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8c912ca78a15f080801d841e4dbbb03ad5d193df
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755519"
---
# <a name="what-is-common-data-service"></a>什么是 Common Data Service？
Common Data Service 让您可以安全地存储和管理业务应用程序使用的数据。 Common Data Service 内的数据存储在一组实体中。 *实体*是一组用于存储数据的记录，类似于表在数据库中存储数据。 Common Data Service 包括一组覆盖典型情形的标准实体，但是，您还可以创建针对您的组织的自定义实体，并使用 Power Query 用数据填充它们。 应用制造者随后可以利用 PowerApps 使用此数据生成丰富的应用程序。

![显示业务应用程序平台的概述的屏幕截图。](./media/data-platform-cds-intro/platform.png "平台概述")

有关购买计划以使用 Common Data Service 的信息，请参阅[定价信息](../../administrator/pricing-billing-skus.md)。

## <a name="why-use-common-data-service"></a>为什么使用 Common Data Service？
Common Data Service 内的标准和自定义实体为您的数据提供基于云的安全存储选项。 实体允许您创建在应用程序内使用的组织数据的专注于业务的定义。 如果不确定实体是否是您的最佳选项，请考虑以下好处：

* **易于管理** &ndash; 元数据和数据都存储在云中。 不需要担心存储方式的细节。
* **易于保护** &ndash; 数据安全存储，以便用户只能在您授予他们访问权限时查看。 基于角色的安全性使您可以控制对组织内其他用户的实体的访问。
* **访问您的 Dynamics 365 数据** &ndash; 来自 Dynamics 365 应用程序的数据也存储在 Common Data Service 内，让您可以快速生成利用 Dynamics 365 数据的应用并使用 PowerApps 扩展您的应用。
* **丰富的元数据** &ndash; 数据类型和关系直接在 PowerApps 中加以利用。
* **验证和逻辑** &ndash; 定义计算字段、业务规则、工作流和业务流程以确保数据质量并推动业务流程。
* **生产工具** &ndash; 实体在 Microsoft Excel 的加载项内提供，以提高效率并确保数据的可访问性。

## <a name="dynamics-365-and-common-data-service"></a>Dynamics 365 和 Common Data Service

Dynamics 365 应用程序（例如 Dynamics 365 Sales、Dynamics 365 Customer Service 或 Dynamics 365 Talent）也使用 Common Data Service 存储和保护应用程序使用的数据。 这使您能够直接根据 Dynamics 365 内已经使用的核心业务数据使用 PowerApps 和 Common Data Service 生成应用，不需要集成。

* **基于您的 Dynamics 365 数据生成应用** &ndash; 基于 PowerApps 内的业务数据或使用 Pro Developer SDK 快速生成应用。
* **管理可重复使用的业务逻辑和规则** &ndash; 已在 Dynamics 365 实体中定义的业务规则和逻辑应用于您的 PowerApps 以确保数据的一致性，不管您的用户如何访问数据或通过哪个应用访问。
* **可跨 Dynamics 365 和 PowerApps 重复使用的技能** &ndash; 具有 PowerApps 或 Dynamics 365 中以前的技能的用户现在可以跨新的 Common Data Service 平台利用这些技能。 创建实体、窗体、图表等现在在各个应用程序中是公用的。

    > [!NOTE]
    > Finance and Operations 应用当前需要配置[数据集成器](/power-platform/admin/data-integrator)来让您的 Finance and Operations 应用中的业务数据在 Common Data Service 内可用。

## <a name="integrating-data-into-the-common-data-service"></a>将数据集成到 Common Data Service 中

生成应用程序通常涉及来自多个源的数据，虽然这有时可以在应用程序级别进行，但也存在其他一些情况，将此数据一起集成到通用存储，以实现更简单的应用程序生成体验，并集成一组逻辑以维护数据并对数据进行操作。 Common Data Service 允许数据从多个源集成到随后可以在 PowerApps、Flow 和 Power BI 中使用的单个存储，一同集成的还有 Dynamics 365 应用程序已经提供的数据。

* **安排的与其他系统的集成** &ndash; 保留在其他应用程序内的数据可以与 Common Data Service 定期同步，以允许您利用 PowerApps 中的其他应用程序数据。
* **使用 PowerQuery 转换和导入数据** &ndash; 在导入到 Common Data Service 时转换数据可以通过 PowerQuery 从很多联机数据源进行，这是一项跨 Excel 和 Power BI 使用的通用工具。
* **一次性导入数据** &ndash; 简单的 Excel 和 CSV 文件导入和导出可一次性使用或用于少有的 Common Data Service 数据导入。

有关将数据集成到 Common Data Service 的详细信息，请参阅[使用 Power Query 将数据添加到 Common Data Service 中的实体](data-platform-cds-newentity-pq.md)。

## <a name="interacting-with-entities"></a>与实体交互
在开发应用程序时，可以使用标准实体、自定义实体或混合使用。 Common Data Service 默认情况下提供标准实体。 这些内容根据最佳实践进行了设计，以获取组织内最常见的概念和情形。

![显示实体列表的屏幕截图。](./media/data-platform-cds-intro/entitylist.png "实体列表")

要获取完整的实体列表，请参阅[实体引用](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/about-entity-reference)。

您可以通过创建一个或多个自定义实体存储组织的唯一信息来扩展标准实体的功能。 有关详细信息，请参阅[如何创建自定义实体](create-custom-entity.md)。

## <a name="logic-and-validation"></a>验证和逻辑
Common Data Service 内的实体利用丰富的服务器端逻辑和验证来确保数据质量，并减少在实体中创建和使用数据的每个应用程序中的重复代码。

* **业务规则**验证多个字段和实体中的数据并提供警告和错误消息，不论用于创建数据的应用程序是什么。 有关详细信息，请参阅[创建业务规则](./data-platform-create-business-rule.md)。
* **业务流程**指导用户确保一致地输入数据并且每次遵循相同的步骤。 目前仅模型驱动应用程序支持业务流程。 有关详细信息，请参阅[业务流程概述](/dynamics365/customer-engagement/customize/business-process-flows-overview)。
* **工作流**让您可以实现无需用户干预的业务流程自动化。 有关详细信息，请参阅[工作流概述](/dynamics365/customer-engagement/customize/workflow-processes)。
* **使用代码的业务逻辑**支持在高级开发人员情形下直接通过代码扩展应用程序。 有关详细信息，请参阅[应用使用代码的业务逻辑](../../developer/common-data-service/apply-business-logic-with-code.md)。

## <a name="security"></a>安全性
Common Data Service 具有丰富的安全模型来保护数据的完整性和用户的隐私，同时还能够促进高效的数据访问和协作。 您可以结合业务部门、基于角色的安全性、基于记录的安全性和基于字段的安全性来定义用户在 Common Data Service 环境中所具有的总体信息访问权限。 详细信息：[Common Data Service 中的安全性](/power-platform/admin/wp-security) 

## <a name="developer-capabilities"></a>开发人员功能
除了通过 [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 门户提供的功能外，Common Data Service 还包括支持开发人员以编程方式访问元数据和数据以创建实体和业务逻辑并与数据交互的功能。 有关详细信息，请参阅 [Common Data Service 开发人员概述](../../developer/common-data-service/overview.md)

## <a name="next-steps"></a>后续步骤
开始使用 Common Data Service：
- [使用 Common Data Service 数据库创建区域应用](../canvas-apps/data-platform-create-app-scratch.md)。
- [创建自定义实体](create-custom-entity.md)，然后[创建使用该实体的区域应用](../canvas-apps/data-platform-create-app.md)。
- 基于 Common Data Service [创建模型驱动应用](/powerapps/maker/model-driven-apps/build-first-model-driven-app)。
- [使用 Power Query](./data-platform-cds-newentity-pq.md) 连接到联机或本地数据源，并将数据直接导入到 Common Data Service。

## <a name="privacy-notice"></a>隐私声明
通过 Microsoft PowerApps 通用数据模型，Microsoft 收集并在我们的诊断系统中存储自定义实体和字段名称。 我们使用此知识来改进我们客户的通用数据模型。 应用创建者创建的实体和字段名称帮助我们了解 Microsoft PowerApps 社区常见的情形，以及服务的标准实体功能存在的确定空白区，如与组织相关的架构。 与这些实体关联的数据库表中的数据不由 Microsoft 访问或使用，也不会在数据库配置地区以外复制。 但是，请注意，自定义实体和字段名称可以跨地区复制，并根据我们的数据保留策略删除。 Microsoft 承诺保护您的隐私，如我们的[信任中心](https://www.microsoft.com/trustcenter/Privacy/default.aspx)的详细叙述。
