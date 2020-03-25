---
title: Common Data Service 中的实体和元数据 | MicrosoftDocs
description: 了解 Common Data Service 中的实体和元数据
ms.custom: ''
ms.date: 05/30/2018
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
ms.assetid: 88b18946-474c-4c94-8e4c-27532f930757
caps.latest.revision: 28
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3aeb07c29178570ca17426cca46dd7cbc73a2aca
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "3108042"
---
# <a name="entities-and-metadata-in-common-data-service"></a>Common Data Service 中的实体和元数据

Common Data Service 的设计是让您可以快速轻松地为您的应用程序创建数据模型。 通常，您应该不必担心本主题将介绍的元数据的一些详细信息。 但是，如果要深入了解使用 Common Data Service 的应用如何工作，或您在评估可能性，了解 Common Data Service 使用的元数据可能为您提供见解。

*元数据*指的是有关数据的数据。 Common Data Service 为您提供了一个灵活的平台，因为它在编辑环境要使用的数据定义上相对容易。 在 Common Data Service 中，元数据是一个实体的集合。 实体描述存储在数据库中的数据种类。  每个实体对应于一个数据库表，实体中的每个字段（也称为属性）代表该表中的一列。 实体元数据可以控制您能创建的记录种类以及可以对记录执行的操作种类。 在使用自定义工具创建或编辑实体、字段和实体关系时，您在编辑此元数据。 
  
用户用于与环境中的数据交互的不同客户端会依赖实体元数据，并随元数据的自定义进行调整。 但是，这些客户端要依赖其他数据来控制要显示的可视元素、要应用的自定义逻辑以及安全性应用方式。 此系统数据也存储在实体中，但实体本身不可用于自定义。

您可以查看[实体引用](/powerapps/developer/common-data-service/reference/about-entity-reference)，了解默认包括在 Common Data Service 中的标准实体、属性和实体关系。

> [!TIP]
> 可用于编辑元数据的设计器无法显示在元数据中找到的所有详细信息。 您可以安装名为**元数据浏览器**的模型驱动应用程序，这让您可以查看在系统中找到的所有实体和元数据属性。 详细信息：[浏览您的环境的元数据](https://docs.microsoft.com/dynamics365/customer-engagement/developer/browse-your-metadata)。
  
<a name="BKMK_CreateNewOrUseExistingMetadata"></a>

## <a name="create-new-metadata-or-use-existing-metadata"></a>新建元数据或使用现有元数据？

Common Data Service 附带了一些支持核心业务应用程序功能的标准实体。 例如，有关客户或潜在客户的数据可使用客户或联系人实体存储。  
  
每个实体还包含一些字段，这些字段代表系统可能需要为相应实体存储的通用数据。  
  
对于大多数组织而言，将标准实体和属性用于其既定用途对您有利。 
  
如果安装解决方案，您可以预期解决方案开发人员已经利用了标准实体和属性。 创建代替系统实体或属性的新自定义实体意味着某些可用的解决方案可能无法用于您的组织。  
  
由于以上原因，我们建议您查找并使用提供的标准实体、字段和实体关系（如果它们对您的组织有意义）。 如果它们没有意义，并且无法通过编辑来满足您的需求，则应评估是否需要创建新实体、字段或实体关系。 

<!--  Can we say this yet? 
    
> [!NOTE]
> The [Common Data Model](/powerapps/common-data-model/overview) will provide a capability to add additional standard entities. 

-->

请记住，您可以更改实体的显示名称，使其与您的组织采用的命名法匹配。 例如，人们经常会将客户实体的显示名称更改为*公司*，或者将联系人实体的显示名称更改为*个人*。 无需更改实体的行为就能对实体或属性执行此操作。 有关重命名实体的详细信息，请参阅[更改实体名称](edit-entities.md#change-the-name-of-an-entity)。
  
无法删除标准实体、字段或实体关系。 它们被视为系统解决方案的一部分，并且每个组织都应该有它们。 如果要隐藏标准实体，可以更改您的组织的安全角色权限以删除对该实体的读取权限。 这将从应用程序的大部分地方移除实体。 如果存在您不需要的系统字段，可将其从使用它的窗体或任何视图移除。 更改字段和实体关系定义中的**可搜索**值，使其不会出现在高级查找中。 
  
<a name="BKMK_LimitationsOnMetadata"></a>   

## <a name="limitations-on-creating-metadata-items"></a>针对创建元数据项目的限制  

对可以创建的实体数量有限制。 可以在**[设置](../model-driven-apps/advanced-navigation.md#settings)** > **管理** > **使用中的资源**页面上找到有关最大数量的信息。 如果需要更多自定义实体，请与技术支持人员联系。 可以调整此上限。  
  
在每个实体中，对您可以创建的字段数量有上限限制。 该限制基于对可在数据库表的一行中存储的数据量的技术限制。 很难提供一个具体的数目，因为每种类型的字段可以使用的空间量不同。 上限取决于实体的所有字段占用的空间总量。  
  
大多数人创建的自定义字段不足以达到该限制，但是，如果您打算向实体中添加数百个自定义字段，则应考虑这是不是最佳设计。 您计划添加的所有字段是否描述该实体的一个记录的属性？ 您是否真的期望使用您的组织的人可以在一个包含如此大量的字段的窗体中进行管理？ 您添加到窗体中的字段数量会增加每次编辑记录时必须传输的数量量，从而会影响系统的性能。 在向实体中添加自自定义字段时，请考虑这些因素。  
  
选项集字段提供一组选项，在使用高级查找时，这些选项将会显示在窗体上的下拉列表控件中，或者显示在选择列表控件中。 您的环境可以支持一个选项集中有数千或数万个选项，但不应将此视为上限。 可用性研究表明，当下拉控制提供大量的选项时，人们在使用系统时会遇到麻烦。 使用选项集字段可定义数据类别。 请勿使用选项集字段选择实际代表单独的数据项的类别。 例如，不要维护存储数百个某种类型的设备的可能制造商中的每个制造商的选项集字段，而应考虑创建一个实体来存储对每个制造商的引用，并使用查找字段代替选项集。  
  
## <a name="next-steps"></a>后续步骤 

[创建或编辑实体（记录类型）](create-edit-entities.md)<br />
[创建和编辑实体之间的关系](create-edit-entity-relationships.md)

