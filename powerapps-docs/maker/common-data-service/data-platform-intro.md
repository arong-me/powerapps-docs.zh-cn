---
title: Common Data Service for Apps | Microsoft 文档
description: 介绍 Common Data Service for Apps、实体和服务器端逻辑。
services: powerapps
documentationcenter: na
author: clwesene
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 3/21/2018
ms.author: clwesene
ms.openlocfilehash: 9a247ab22970538c56c8a1fb1578b197f9898f92
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="common-data-service-for-apps"></a>Common Data Service for Apps

Common Data Service 可以安全地存储和管理数据，这些数据在开发的应用或 Microsoft 和应用提供商提供的应用中使用。 Common Data Service 中的数据存储在一组标准实体和自定义实体中。 实体是一组字段，用于存储数据，类似于在数据库中存储表。 存储数据以后，即可通过 Microsoft PowerApps 使用数据生成丰富的应用程序：

* 利用现有标准实体或创建自定义实体，用于支持方案和应用程序。
* 创建直接针对 Common Data Service 的 PowerApps 和 Flow。
* 将自定义字段和关系添加到需要其他信息的标准实体。
* 为实体创建计算和汇总字段，以便在应用和分析中提供一致的计算。
* 定义业务规则以确保实体中的数据质量，而不必担心访问和编辑你的数据的应用。
* 创建工作流并利用与 Microsoft Flow 的集成来驱动针对数据的其他操作和业务流程。
* 将标准实体和自定义实体纳入正在开发的应用中，就像将数据导入其他源一样简单。
* 使用 Common Data Service 实用外接程序连接到 Microsoft Excel 中的数据。
* 使用 Power Query 轻松导入和同步数据。
* 对标准实体和自定义实体使用基于角色的安全措施，确保组织中数据的安全。
* 通过将实体和字段名称转换为用户的语言，为数据和应用提供全局支持。

每个实体均包含一组可由用户根据其权限创建、读取、更新和删除的记录。 可以创建各实体间的关系，以便在一个实体中可以基于其他实体中的记录查找信息。 例如，可以创建一个自定义实体，用于跟踪客户参加过的事件。 将“客户”作为查找字段添加到自定义实体即可在两个实体之间建立一种关系，这两个实体可以在应用和报告中利用。

若要了解如何购买 Common Data Service 使用套餐，请参阅[定价信息](../../administrator/pricing-billing-skus.md)。

## <a name="why-use-the-common-data-service-for-apps"></a>为何使用 Common Data Service for Apps？
Common Data Service 中的实体，包括标准实体和自定义实体，都可以为数据提供安全的基于云的存储选项。 可以通过实体创建以业务为中心的定义，对可以在应用中使用的数据进行定义。 如果不确定实体是否为最佳选择，请考虑以下优势：

* **易于管理** - 元数据和数据均存储在云中。 无需详细了解如何进行存储。
* **易于共享** - 轻松地与同事共享数据，由 PowerApps 管理权限。
* **易于保护** - 安全地存储数据，只有拥有访问权限的用户才能查看数据。 借助基于角色的安全性，可以控制组织内不同用户对实体的访问权限。
* **各种元数据** - 可直接在 PowerApps 中利用数据类型和关系。 例如，定义字段类型 URL 会以超链接的形式在应用中数显示据。
* **逻辑和验证** - 定义计算字段、业务规则、工作流和业务流程，以确保数据质量和驱动业务流程。
* **实用工具** - 实体适用于 Microsoft Excel 的外接程序，以提高工作效率，并确保数据可访问性。

开发应用时，可以使用标准实体、自定义实体或将两者一起使用。 如果标准实体在应用中具有特殊用途，则应当使用它，而不是开发一个执行同样操作的自定义实体。 如果标准实体需要进行几项更改才能发挥特殊用途，可以添加字段以适应需求。

* Common Data Service 在默认情况下提供标准实体。 这些实体根据最佳实践设计，为组织获取最基本的概念，如联系人、帐户和产品。 有关实体的完整列表，请参阅[标准实体](data-platform-intro.md#standard-entities)。
* 可以通过创建一个或多个自定义实体来扩展标准实体的功能，存储组织专用信息。 有关详细信息，请参阅[如何创建自定义实体](create-custom-entity.md)。

> [!NOTE]
> 如果可能，请使用标准实体（必要时，其中添加了自定义字段）。 这样可确保你能够受益于那些在未来利用这些实体的新功能或应用。

## <a name="interacting-with-entities"></a>与实体进行交互

当使用标准实体或创建自定义实体时，每个实体中都有多个可用的元素，并且可以执行不同的操作。 根据业务方案的简单或高级程度，将确定需要使用的功能。 若要查看环境中可用的实体，请登录到 [PowerApps](https://web.powerapps.com)，单击“数据”，然后单击左侧菜单中的“实体”。

### <a name="system-fields"></a>系统字段
所有实体（标准实体或自定义实体）均使用一组只读字段创建，不能对其进行更改、删除或设置为某值。 以下是最重要的系统字段：

* 每个字段可以定义要收集的信息片段，以及要显示的数据类型或格式。 字段类似于数据库或 Excel 中的列。
* 备用密钥可以在不使用标准唯一标识符时有效准确地搜索以及与实体中的记录进行交互。 在使用业务密钥或与外部系统集成时，这一点尤为重要。
* 每个实体可以与其他实体具有多个关系，以支持跨实体查找和查询。 关系可以创建，以支持多对一、一对多和多对多的关系。
* 视图使每个实体可以以多种方式呈现，包括显示的字段、数据的筛选和排序。 这些演示保存为视图，并且可以在不同的应用中使用，例如可能只想要查看应用中的活动帐户，因此可以使用预筛选的视图以仅显示活动帐户，以避免在每个正在使用的应用中重复筛选器。
* 业务规则可用于验证实体中正在创建和更新的数据，以确保数据质量。 每个业务规则都可以验证跨多个字段和实体的数据，提示警告和错误消息，而不考虑用于创建数据的应用。
* Common Data Service 中存储的数据可通过 PowerApps 门户、PowerApps、Microsoft Excel 和 Web API 为开发人员提供。

## <a name="logic-and-validation"></a>逻辑和验证

Common Data Service 中的实体可以利用丰富的服务器端逻辑和验证来确保数据质量，并减少在每个应用中创建和使用实体中的数据的重复代码。

* 业务规则可以跨多个字段和实体验证数据，提示警告和错误消息，而不考虑用于创建数据的应用。 有关详细信息，请参阅[创建业务规则](./data-platform-create-business-rule.md)。
* 业务流程指导用户确保数据输入一致，每次都执行同样的步骤。 业务流程目前仅支持模型驱动应用。 有关详细信息，请参阅[业务流程概述](/dynamics365/customer-engagement/customize/business-process-flows-overview)。
* 工作流可以在没有用户交互的情况下自动完成业务流程。 有关详细信息，请参阅[工作流概述](/dynamics365/customer-engagement/customize/workflow-processes)。
* 带有代码的业务逻辑支持更高级的开发人员方案，以便通过代码直接扩展应用程序。 有关详细信息，请参阅[使用代码应用业务逻辑](../../developer/common-data-service/apply-business-logic-with-code.md)。

## <a name="getting-data-into-the-common-data-service"></a>在 Common Data Service 中输入数据

有几种方法可以开始在 Common Data Service 中输入数据：

* 创建 PowerApp 或 Flow 以开始创建数据。
* 使用 Power Query 连接到联机或本地数据源并将其直接导入 Commmon Data Service。 Power Query 还可以在导入过程中基于源的架构创建实体，以及在导入过程中对数据执行转换。 有关详细信息，请参阅[使用 Power Query 将数据添加到 Common Data Service 中的实体](./data-platform-cds-newentity-pq.md)。

## <a name="developer-capabilities"></a>开发人员功能

除了通过 [PowerApps](https://web.powerapps.com) 门户提供的功能外，Common Data Service 还包括一些功能，供开发人员以编程方式访问元数据和数据，以创建实体和业务逻辑，以及与数据进行交互。 有关详细信息，请参阅 [Common Data Service for Apps 开发人员概述](../../developer/common-data-service/overview.md)

## <a name="get-started"></a>入门
可以通过使用标准实体创建应用来进行尝试，也可以先[创建自定义实体](create-custom-entity.md)，然后[创建使用该实体的应用](../canvas-apps/data-platform-create-app.md)。

## <a name="privacy-notice"></a>隐私声明
通过 Microsoft PowerApps 通用数据模型，我们收集自定义实体和字段名称并将其存储在诊断系统中。  我们利用这一知识来改进我们客户的通用数据模型。 创建者创建的实体和字段名称帮助我们了解 Microsoft PowerApps 社区中的常见方案，并确定服务标准实体范围中的缺口，如与组织相关的架构。 Microsoft 无法访问或使用数据库表中与这些实体相关联的数据，此类数据也无法在预配了数据库的区域之外进行复制。 不过，请注意，自定义实体和字段名称可能可以进行跨区域复制，并根据我们的数据保留策略进行删除。 Microsoft 致力于保护你的隐私安全，我们的[信任中心](https://www.microsoft.com/trustcenter/Privacy/default.aspx)对此进行了详述。

