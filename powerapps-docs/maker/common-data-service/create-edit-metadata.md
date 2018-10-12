---
title: Common Data Service for Apps 中的实体和元数据 | MicrosoftDocs
description: 了解 Common Data Service for Apps 中的实体和元数据
ms.custom: ''
ms.date: 05/30/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 88b18946-474c-4c94-8e4c-27532f930757
caps.latest.revision: 28
ms.author: matp
manager: kvivek
ms.openlocfilehash: ef2f92865205fa7c97ada356edc70ac69a637e0f
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669610"
---
# <a name="entities-and-metadata-in-common-data-service-for-apps"></a>Common Data Service for Apps 中的实体和元数据

Common Data Service for Apps 旨在让用户可快速轻松地为应用程序创建数据模型。 通常，不必关心本主题将介绍的有关元数据的一些细节。 但是，如果希望更深入地了解使用 CDS for Apps 的应用如何工作，或者正在评估可能出现的情况，那么了解 CDS for Apps 使用的元数据能够提供见解。

元数据是指有关数据的数据。 CDS for Apps 提供了一个灵活的平台，因为编辑环境将使用的数据定义相对容易。 在 CDS for Apps 中，元数据是实体的集合。 实体描述存储在数据库中的数据类型。  每个实体对应一个数据库表，实体中的每个字段（也称为属性）表示该表中的一列。 实体元数据控制着可创建的记录类型以及可对它们执行的操作类型。 使用自定义工具创建或编辑实体、字段和实体关系时，就是在编辑此元数据。 
  
用来与环境中的数据进行交互的不同客户端取决于实体元数据，并会在自定义元数据时进行调整。 但是这些客户端还依赖于其他数据来控制要显示的视觉元素，要应用的任何自定义逻辑以及如何应用安全性。 此系统数据也存储在实体中，但实体本身不可用于自定义。

通过查看[实体引用](/powerapps/developer/common-data-service/reference/about-entity-reference)，可了解默认情况下 CDS for Apps 中包含的标准实体、属性和实体关系。

> [!TIP]
> 可用于编辑元数据的设计器无法显示在元数据中找到的所有详细信息。 可安装名为“元数据浏览器”的模型驱动应用，这样就可以查看在系统中找到的所有实体和元数据属性。 详细信息：[浏览环境的元数据](https://docs.microsoft.com/dynamics365/customer-engagement/developer/browse-your-metadata)。
  
<a name="BKMK_CreateNewOrUseExistingMetadata"></a>

## <a name="create-new-metadata-or-use-existing-metadata"></a>新建元数据还是使用现有元数据？

CDS for Apps 附带了许多支持核心商务应用程序功能的标准实体。 例如，打算使用帐户或联系人实体存储的客户或潜在客户的相关数据。  
  
这些实体中的每一个都包含许多字段，这些字段表示系统可能需要为相应实体存储的公共数据。  
  
对于大多数组织而言，可使用标准实体和属性所提供的用途来获得优势。 
  
如果安装解决方案，可预期解决方案开发人员利用标准实体和属性。 创建替换系统实体或属性的新自定义实体意味着可用的任何解决方案都可能不适用于组织。  
  
出于这些原因，我们建议在提供的标准实体、字段和实体关系对组织有意义时查找并使用它们。 如果它们没有意义且无法进行编辑以满足需求，则应评估是否需要创建新的实体、字段或实体关系。 

<!--  Can we say this yet? 
    
> [!NOTE]
> The [Common Data Model](/powerapps/common-data-model/overview) will provide a capability to add additional standard entities. 

-->

请记住，可以更改实体的显示名称，使其与组织使用的命名法相匹配。 例如，将 Account 实体的显示名称更改为 Company 或将 Contact 实体的名称更改为 Individual 是很常见的情况。 这可以在不更改实体行为的情况下对实体或属性进行操作。 有关重命名实体的详细信息，请参阅[更改实体名称](edit-entities.md#change-the-name-of-an-entity)。
  
无法删除标准实体、字段或实体关系。 它们作为系统解决方案的一部分，每个组织都应该拥有。 如果要隐藏标准实体，请更改组织的安全角色特权，以删除该实体的读取特权。 这将从应用程序的大多数部分中删除实体。 如果存在不需要的系统字段，请将其从窗体和使用它的任何视图中删除。 更改字段和实体关系定义中的“可搜索”值，以便它们不会出现在高级查找中。 
  
<a name="BKMK_LimitationsOnMetadata"></a>   

## <a name="limitations-on-creating-metadata-items"></a>创建元数据项的限制  

可创建的实体数量有限。 可在“[设置](../model-driven-apps/advanced-navigation.md#settings)” > “管理” > “正在使用的资源”页面中找到有关最大数量的信息。 如果需要更多自定义实体，请联系技术支持。 可以调整该上限。  
  
在每个实体中，可创建的字段数有上限。 此限制基于可存储在数据库表行中的数据量的技术限制。 很难提供特定的数字，因为每种类型的字段都可以使用不同的空间量。 上限取决于实体所有字段使用的总空间。  
  
大多数人未创建足够的自定义字段来达到限制，但如果发现自己计划向实体添加数百个自定义字段，则应考虑这是否是最佳设计。 计划添加的所有字段是否都描述了该实体的记录属性？ 是否确实希望使用组织的人员能够管理包含庞大数量字段的窗体？ 添加到窗体的字段数会增加每次编辑记录时必须传输的数据量，并会影响系统的性能。 在向实体添加自定义字段时，请考虑这些因素。  
  
选项集字段提供了一组选项，这些选项将在使用高级查找时显示在窗体的下拉列表控件或选择列表控件中。 环境可以在选项集中支持数千个选项，但不应将此视为上限。 可用性研究表明，下拉列表控件提供大量选项时，使用系统会遇到问题。 使用选项集字段定义数据类别。 不要使用选项集字段来选择实际代表数据单独项的类别。 例如，与其维护存储一类设备的数百个可能制造商中每一个的选项集字段，不如考虑创建存储对每个制造商的引用并使用查找字段而非选项集的实体。  
  
## <a name="next-steps"></a>后续步骤 

[创建或编辑实体（记录类型）](create-edit-entities.md)<br />
[创建和编辑实体之间的关系](create-edit-entity-relationships.md)

