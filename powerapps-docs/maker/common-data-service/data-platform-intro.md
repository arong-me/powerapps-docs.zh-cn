---
title: 什么是 Common Data Service for Apps？ | Microsoft Docs
description: 介绍 Common Data Service (CDS) for Apps、实体和服务器端逻辑。
author: clwesene
manager: kfile
ms.service: powerapps
ms.topic: overview
ms.component: cds
ms.date: 05/01/2018
ms.author: matp
ms.openlocfilehash: 6a8bc8f24ce0f772f5c98852838095f233c4317f
ms.sourcegitcommit: 0b051bba173353d7ceda3b60921e7e009eb00709
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2018
ms.locfileid: "39218064"
---
# <a name="what-is-common-data-service-for-apps"></a>什么是 Common Data Service for Apps？
使用 Common Data Service (CDS) for Apps，可安全地存储和管理业务应用程序使用的数据。 CDS for Apps 中的数据存储在一组实体中。 实体是一组用于存储数据的记录，类似于表存储数据库中数据的方式。 CDS for Apps 带有一组基本的标准实体（包含典型解决方案），但用户也可创建组织特定的自定义实体，并使用 Power Query 向其填充数据。 应用创建者随后可以使用 PowerApps 通过此数据生成大量应用程序。

![显示商业应用程序平台概述的屏幕截图](./media/data-platform-cds-intro/platform.png "平台概述")

有关购买套餐以使用 CDS for Apps 的详细信息，请参阅[定价信息](../../administrator/pricing-billing-skus.md)。

## <a name="why-use-common-data-service-for-apps"></a>为何使用 Common Data Service for Apps？
CDS for Apps 中的标准实体和自定义实体都可以为数据提供基于云的安全存储选项。 可以通过实体创建以业务为中心的定义，对可以在应用中使用的组织的数据进行定义。 如果不确定实体是否为最佳选择，请考虑以下优势：

* **易于管理** &ndash; 元数据和数据均存储在云中。 无需详细了解如何进行存储。
* **易于保护** &ndash; 安全地存储数据，只有拥有访问权限的用户才能查看数据。 借助基于角色的安全性，可以控制组织内不同用户对实体的访问权限。
* **访问 Dynamics 365 数据** &ndash; Dynamics 365 应用程序中的数据也存储在 Common Data Service for Apps.中，后者可利用 Dynamics 365 数据快速构建应用并使用 PowerApps 对应用进行扩展。
* **各种元数据** &ndash; 可直接在 PowerApps 中利用数据类型和关系。
* **逻辑和验证** &ndash; 定义计算字段、业务规则、工作流和业务流程，以确保数据质量和驱动业务流程。
* **实用工具** &ndash; 实体适用于 Microsoft Excel 的外接程序，以提高工作效率，并确保数据可访问性。

## <a name="dynamics-365-and-the-common-data-service-for-apps"></a>Dynamics 365 和 Common Data Service for Apps

Dynamics 365 应用程序（例如 Dynamics 365 for Sales、Dynamics 365 for Service 或 Dynamics 365 for Talent）也使用 Common Data Service for Apps 存储和保护这些应用程序使用的数据。 这使你可针对 Dynamics 365 中已使用的核心商业数据直接使用 PowerApps 和 Common Data Service for Apps 构建应用，而无需集成。

* **针对 Dynamics 365 数据构建应用** &ndash; 针对企业数据使用 PowerApps 或专业开发人员 SDK 快速构建应用。
* **管理可重用的业务逻辑和规则** &ndash; 在 Dynamics 365 实体上已定义的业务规则和逻辑已应用到 PowerApps，确保在用户使用不同的访问方式或通过不同的应用访问时数据的一致性。
* **Dynamics 365 和 PowerApps 中可重用的技能** &ndash; 熟悉 PowerApps 或 Dynamics 365 技能的用户现在可以在新的 Common Data Service for Apps 平台内利用这些技能。 现在跨应用程序创建实体、表单、图表等已十分常见。

    > [!NOTE]
    > Dynamics 365 for Finance and Operations 当前需要配置数据集成器才能使 Finance and Operations 中的业务数据在 Common Data Service for Apps 中可用。

## <a name="integrating-data-into-the-common-data-service"></a>将数据集成到 Common Data Service

构建应用程序通常涉及多个源中的数据，而这有时可以在应用程序级别中实现，还存在将此数据集成到通用存储的情况，这种方法使应用构建更加容易并能获取维持和操作数据的一组逻辑。 Common Data Service for Apps 支持将数据从多个源集成到单个存储中，然后在 PowerApps、Flow 和 Power BI 中结合 Dynamics 365 应用程序已提供的数据一起使用。

* **与其他系统的计划集成** &ndash; 另一个应用程序中保留的数据可以定期与 Common Data Service for Apps 进行同步，以便在 PowerApps 中利用其他应用程序的数据。
* **使用 PowerQuery 转换和导入数据** &ndash; 导入到 Common Data Service 时转换数据可通过许多在线数据源（Excel 和 Power BI 中使用的一种通用工具）实现。
* **一次性导入数据** &ndash; 对于一次性或很少时间将数据导入 Common Data Service for Apps 的情况，可使用简单的导入和导出 Excel 和 CSV 文件操作。


## <a name="interacting-with-entities"></a>与实体进行交互
开发应用时，可以使用标准实体、自定义实体或将两者一起使用。 CDS for Apps 在默认情况下提供标准实体。 这些实体根据最佳做法设计，可在组织中获取最基本的概念和方案。

![显示实体列表的屏幕截图。](./media/data-platform-cds-intro/entitylist.png "实体列表")

有关实体的完整列表，请参阅[实体引用](https://docs.microsoft.com/powerapps/developer/common-data-service/reference/about-entity-reference)。

可以通过创建一个或多个自定义实体来扩展标准实体的功能，存储组织专用信息。 有关详细信息，请参阅[如何创建自定义实体](create-custom-entity.md)。

## <a name="logic-and-validation"></a>逻辑和验证
CDS for Apps 中的实体可利用丰富的服务器端逻辑和验证来确保数据质量，并减少每个应用中用于创建和使用实体数据的重复代码。

* 业务规则跨多个字段和实体验证数据，提供警告和错误消息，而不考虑用于创建数据的应用。 有关详细信息，请参阅[创建业务规则](./data-platform-create-business-rule.md)。
* 业务流程指导用户确保数据输入一致，每次都执行同样的步骤。 业务流程目前仅支持模型驱动应用。 有关详细信息，请参阅[业务流程概述](/dynamics365/customer-engagement/customize/business-process-flows-overview)。
* 工作流可以在没有用户交互的情况下自动完成业务流程。 有关详细信息，请参阅[工作流概述](/dynamics365/customer-engagement/customize/workflow-processes)。
* 带有代码的业务逻辑支持高级的开发人员方案，以便通过代码直接扩展应用程序。 有关详细信息，请参阅[使用代码应用业务逻辑](../../developer/common-data-service/apply-business-logic-with-code.md)。

## <a name="developer-capabilities"></a>开发人员功能
除了提供可通过 [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 门户使用的功能外，CDS for Apps 还包含一些功能，可方便开发人员以编程方式访问元数据和数据，从而创建实体和业务逻辑，以及与数据进行交互。 有关详细信息，请参阅 [Common Data Service for Apps 开发人员概述](../../developer/common-data-service/overview.md)

## <a name="next-steps"></a>后续步骤
开始使用 CDS for Apps：
* [使用 Common Data Service 数据库创建应用](../canvas-apps/data-platform-create-app-scratch.md)。
* [创建自定义实体](create-custom-entity.md)然后[创建使用该实体的应用](../canvas-apps/data-platform-create-app.md)。
* [使用 Power Query](./data-platform-cds-newentity-pq.md) 连接到在线或本地数据源，并将该数据直接导入 CDS for Apps。

## <a name="privacy-notice"></a>隐私声明
通过 Microsoft PowerApps 通用数据模型，Microsoft 可收集自定义实体和字段名称，并将其存储在诊断系统中。 我们利用这一知识来改进我们客户的通用数据模型。 应用创建者创建的实体和字段名称帮助我们了解 Microsoft PowerApps 社区中的常见方案，并确定服务标准实体范围中的缺口，如与组织相关的架构。 Microsoft 无法访问或使用数据库表中与这些实体相关联的数据，此类数据也无法在预配了数据库的区域之外进行复制。 不过，请注意，自定义实体和字段名称可能可以进行跨区域复制，并根据我们的数据保留策略进行删除。 Microsoft 致力于保护你的隐私安全，我们的[信任中心](https://www.microsoft.com/trustcenter/Privacy/default.aspx)对此进行了详述。
