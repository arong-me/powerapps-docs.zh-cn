---
title: "了解实体 | Microsoft 文档"
description: "实体、字段、关系和数据库简介。"
services: powerapps
documentationcenter: na
author: clwesene
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/20/2017
ms.author: kfend
ms.openlocfilehash: bbc501542e634fab925654734cf709fe87248883
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="understand-entities-in-the-common-data-service"></a>了解 Common Data Service 中的实体

可以使用 Common Data Service 在一组标准实体和自定义实体中安全地存储和管理数据。 实体是一组字段，用于存储数据，类似于在数据库中存储表。 存储数据以后，即可通过 Microsoft PowerApps 使用数据生成丰富的应用程序：

* 将数据导入标准实体或自定义实体中。
* 创建自定义实体，用于支持方案和应用程序。
* 将自定义字段添加到在其中需要其他信息的标准实体。
* 将标准实体和自定义实体纳入正在开发的应用中，就像将数据导入其他源一样简单。
* 利用生产力外接程序，从 Microsoft Excel 和 Outlook 访问数据。
* 对标准实体和自定义实体使用基于角色的安全措施，确保组织中数据的安全。
* 包括预定义数据的选择列表，例如 Country、Salutation 或 Currency。
* 通过对实体和字段名称进行转换，为数据和应用程序提供全局支持。

每个实体均包含一组可由用户创建、读取、更新和删除的记录。 可以创建各实体间的关系，以便在一个实体中可以基于其他实体中的记录查找信息。 例如，可以创建一个自定义实体，用于跟踪客户参加过的事件。 将“客户”作为查找字段添加到自定义实体即可在两个实体之间建立一种关系，这两个实体可以在应用和报告中利用。

若要了解如何购买 Common Data Service 使用套餐，请参阅[定价信息](pricing-billing-skus.md)。

## <a name="why-use-entities"></a>为什么使用实体？
Common Data Service 中的实体，包括标准实体和自定义实体，都可以为数据提供安全的基于云的存储选项。 可以通过实体创建以业务为中心的定义，对可以在应用中使用的数据进行定义。 如果不确定实体是否为最佳选择，请考虑以下优势：

* **易于管理** - 元数据和数据均存储在云中。 无需详细了解如何进行存储。
* **易于共享** - 轻松地与同事共享数据，由 PowerApps 管理权限。
* **易于保护** - 安全地存储数据，只有拥有访问权限的用户才能查看数据。 借助基于角色的安全性，可以控制组织内不同用户对实体的访问权限。
* **各种元数据** - 可直接在 PowerApps 中利用数据类型和关系。 例如，定义字段类型 URL 会以超链接的形式在应用中数显示据。
* **实用工具** - 实体适用于 Microsoft Excel 和 Outlook 的外接程序，以提高工作效率，并确保数据可访问性。
* **选项列表** - 包含一系列的标准选择列表，可在实体和应用中实现快速下拉。

## <a name="standard-and-custom-entities"></a>标准和自定义实体
开发应用时，可以使用标准实体、自定义实体或将两者一起使用。 如果标准实体在应用中具有特殊用途，则应当使用它，而不是开发一个执行同样操作的自定义实体。 如果标准实体需要进行几项更改才能发挥特殊用途，可以添加字段以适应需求。

* Common Data Service 在默认情况下提供标准实体。 这些实体根据最佳实践设计，为组织获取最基本的概念，如联系人、帐户和产品。 有关实体的完整列表，请参阅[标准实体](data-platform-intro.md#standard-entities)。
* 可以通过创建一个或多个自定义实体来扩展标准实体的功能，存储组织专用信息。 有关详细信息，请参阅[如何创建自定义实体](data-platform-create-entity.md)。

> [!NOTE]
> 如果可能，请使用标准实体（必要时，其中添加了自定义字段）。 这样可确保你能够受益于那些在未来利用这些实体的新功能或应用。


## <a name="fields"></a>字段
每个字段均包含名称、显示名称、数据类型和一些简单的验证。 数据类型包括多种类型，例如 **text**、**date** 或 **number**。 验证可确保必填字段所含数据和记录是唯一的（如果实体对其要求如此）。 每个字段均包含以下三个类别之一：系统字段、标准字段或自定义字段。

### <a name="system-fields"></a>系统字段
所有实体（标准实体或自定义实体）均使用一组只读字段创建，不能对其进行更改、删除或设置为某值。 有关详细信息，请参阅 [系统和记录标题字段](data-platform-create-entity.md#system-fields-and-the-record-title-field)。 以下是最重要的系统字段：

* **创建记录日期** - 创建记录的日期和时间。
* **创建者** - 创建记录的用户。
* **修改记录日期** - 最近修改记录的日期和时间。
* **上次修改者** - 最近修改记录的用户。

### <a name="standard-fields"></a>标准字段
每个标准实体均包含一组默认字段，不能对其进行更改或删除。 如需实体及其字段的列表，以及选择列表的列表，请参阅 [Standard entities](https://docs.microsoft.com/common-data-service/entity-reference/standard-entities)（标准实体）。

### <a name="custom-fields"></a>自定义字段
可以在标准实体或自定义实体中创建自定义字段。 必须指定每个自定义字段的名称、显示名称和数据类型。 有关受支持类型的完整列表，请参阅 [Entity field data types](https://docs.microsoft.com/en-us/common-data-service/entity-reference/field-data-types)（实体字段数据类型）。

## <a name="lookup-relationships"></a>查找关系
可以在实体中的记录间导航，前提是它们具有被定义为 **Lookup** 数据类型的字段的关系。 若要创建查找关系，请在一个实体中添加数据类型为 **Lookup** 的字段，并指向要在其中查找信息的实体。 有关详细信息，请参阅 [通过查找字段的实体关系](data-platform-entity-lookup.md)。

## <a name="standard-entities"></a>标准实体
如需实体及其字段的列表，以及枚举的列表，请参阅 [Standard entities](https://docs.microsoft.com/common-data-service/entity-reference/standard-entities)（标准实体）。

| 功能组 | 说明 |
| --- | --- |
| 客户服务 |“客户服务”实体负责管理客户遇到的问题，包括跟踪、升级和文档处理。 |
| 基金会 |基金会实体所含信息几乎与每个其他实体组相关。 该组包含诸如地址和货币等实体。 |
| 人员、组织和组 |这些实体包含一组可以与之进行交互的大量人员和组织，包括员工、承办商、捐赠者、志愿者、爱好者、校友和家庭。 |
| 采购 |可通过采购实体创建采购解决方案。 |
| 销售热线 |借助“销售”实体，可以创建端到端销售解决方案，包括跟踪潜在客户和商机、跟进联系人、接受并提交订单以及发送发票。 |

## <a name="get-started"></a>入门
可以通过使用标准实体创建应用来进行尝试，也可以先[创建自定义实体](data-platform-create-entity.md)，然后[创建使用该实体的应用](data-platform-create-app.md)。

<!--TODO - Add Link for Standard entity app - Template? -->

## <a name="privacy-notice"></a>隐私声明
通过 Microsoft PowerApps 通用数据模型，我们收集自定义实体和字段名称并将其存储在诊断系统中。  我们利用这一知识来改进我们客户的通用数据模型。 创建者创建的实体和字段名称帮助我们了解 Microsoft PowerApps 社区中的常见方案，并确定服务标准实体范围中的缺口，如与组织相关的架构。 Microsoft 无法访问或使用数据库表中与这些实体相关联的数据，此类数据也无法在预配了数据库的区域之外进行复制。 不过，请注意，自定义实体和字段名称可能可以进行跨区域复制，并根据我们的数据保留策略进行删除。 Microsoft 致力于保护你的隐私安全，我们的[信任中心](https://www.microsoft.com/trustcenter/Privacy/default.aspx)对此进行了详述。

