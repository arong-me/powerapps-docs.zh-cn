---
title: 为 Common Data Service 创建和编辑全局选项集（选择列表）概述 | MicrosoftDocs
ms.custom: ''
ms.date: 05/26/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: f06b8941-8dca-4601-b965-341cfb6fc3b2
caps.latest.revision: 11
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 746f3b1677df7eb89ce35ef1161a291bfdb7d2be
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865859"
---
# <a name="create-and-edit-global-option-sets-overview"></a>创建和编辑全局选项集概述 

选项集（选择列表）是可以包含在实体内的字段类型。 它定义一组选项。 当一个选项集显示在窗体中时，将使用下拉列表控件。 在显示在**高级查找**中时，它使用*选择列表控件*。 有时，开发人员将选项集称为选择列表。  
  
可以定义一个选项集以使用其中定义的一组选项；选项集也可以使用其他地方（全局）定义的可供其他选项集字段使用的一组选项。 

当您有可应用于多个字段的一组标准类别时，全局选项集很有用。 维护两个包含相同值的单独选项集很难，并且，如果它们不同步，则可能会发生错误，当您在一对实体关系中映射实体字段时更是如此。 详细信息：[映射实体字段](map-entity-fields.md)

> [!NOTE]
> 如果您将每个选项集定义为全局选项集，您的全局选项集列表将增大并可能很难管理。 如果您知道这组选项只会在一个位置使用，请使用本地选项集。

有两个设计器您可以用于创建或编辑全局选项集：

|设计器| 说明|
|--|--|
|[Power Apps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|提供简单的简化体验，但是有些特殊设置不可用。<br />详细信息：[创建选项集](custom-picklists.md) |
|解决方案资源管理器|不那么简单，但提供更多灵活性可减少常见要求。 <br />详细信息：[使用解决方案资源管理器为 Common Data Service 创建和编辑全局选项集](create-edit-global-option-sets-solution-explorer.md) |

> [!NOTE]
> 您还可以使用以下方法在您的环境中创建全局选项集：
> - 导入包含全局选项集的定义的解决方案。
> - 开发人员可以编写程序来创建它们。 <br />详细信息：[开发人员文档：自定义全局选项集](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)。

本主题中的信息将帮助您选择可以使用的设计器。 

您应该使用 [Power Apps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)来处理全局选项集，除非您需要满足以下任何要求：

- 向选项分配颜色
- 更改选项的顺序
- 在除 Common Data Service 默认解决方案以外的解决方案中创建全局选项集
- 设置托管属性
- 设置用于虚拟实体的属性
- 查看依赖项

## <a name="see-also"></a>另请参阅

[创建选项集](custom-picklists.md)<br />
[使用解决方案资源管理器为 Common Data Service 创建和编辑全局选项集](create-edit-global-option-sets-solution-explorer.md)<br />
[开发人员文档：自定义全局选项集](/dynamics365/customer-engagement/developer/org-service/customize-global-option-sets)
  

 
