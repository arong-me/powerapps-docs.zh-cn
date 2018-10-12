---
title: 在 PowerApps 中映射实体字段 | MicrosoftDocs
description: 了解如何映射实体字段
ms.custom: ''
ms.date: 05/29/2018
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
ms.assetid: 7c5aa1c3-bde9-43f1-a369-fdcdbf14dec0
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
ms.openlocfilehash: 7e84e10a824ea218063cb2dccdc15ed7ae2340da
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669311"
---
# <a name="map-entity-fields"></a>映射实体字段
 
可在具有实体关系的实体之间映射属性。 这样，即可为在另一记录的上下文中创建的记录设置默认值。 

## <a name="easier-way-to-create-new-records-in-model-driven-apps"></a>在模型驱动应用中新建记录的简便方法

假设想为特定帐户的员工创建新的联系人记录。 可通过两种不同的方式完成：  
  
### <a name="the-hard-way"></a>较麻烦的方式

可导航到该应用中，从头开始创建新的联系人记录。 但是，之后需要设置父级帐户，并输入地址和电话信息等多项信息（这些信息可能与父级帐户的信息相同）。 此操作可能非常耗时且容易产生错误。  
  
### <a name="the-easier-way"></a>较简便的方式

更简单的方法是首先操作帐户实体，然后通过表单上的“联系人”子网格，选择“+”以添加联系人。 这样，会先引导用户查找是否已存在相关的联系人，从而避免意外创建重复的记录。 如果找不到现有记录，可选择“新建”并创建新的联系人记录。 

在新的联系人记录表单中，从帐户映射的所有属性值（例如地址和电话信息）将作为默认值。 用户可在保存记录之前编辑这些值。

## <a name="how-this-works"></a>运行原理

在映射一对多实体关系的实体字段时，主要实体记录中的某些数据项将复制到新的相关实体表单用于设置默认值，用户在保存之前可编辑这些值。
 
  
> [!NOTE]
> 这些映射仅设置记录在保存之前的默认值。 用户可在保存之前编辑这些值。 此时的数据就是所转换的数据。 如果数据源之后出现更改，则它不进行同步。
>   
> 这些映射不用于使用工作流或对话流程创建的相关记录。 它们不自动应用到使用代码创建的新记录，不过开发人员可使用名为 `InitializeFrom`（[InitializeFrom 函数](/dynamics365/customer-engagement/web-api/initializefrom?view=dynamics-ce-odata-9)或 [InitializeFromRequest 类](/dotnet/api/microsoft.crm.sdk.messages.initializefromrequest?view=dynamics-general-ce-9)）的特殊消息创建使用可用映射的新纪录。  

## <a name="open-solution-explorer"></a>打开解决方案资源管理器

要映射实体字段，只能使用解决方案资源管理器。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]
  
字段映射操作是在一对多或多对一的实体关系中完成的，因此首先需要[查看一对多或多对一实体关系](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships)。

## <a name="view-mappable-fields"></a>查看可映射的字段

实际上，字段映射并不是在实体关系中定义的，而是在关系用户界面中公开的。 并非每个一对多实体关系都具有字段映射。 在查看实体的一对多（或多对一）实体关系列表时，可按类型筛选所显示的关系。 可选择“全部”、“自定义”、“可自定义”或“可映射”。 通过可映射的实体关系，可映射实体字段。 

![查看可映射的实体关系](media/mappable-entity-relationships.png) 

在打开可映射的实体关系时，请选择左侧导航栏中的“映射”。

![为实体关系选择“映射”](media/map-entity-fields-ui-solution-explorer.png)

## <a name="delete-mappings"></a>删除映射

如果存在不想应用的映射，可将其选中并单击 ![“删除”图标](media/delete.gif) 图标。

## <a name="add-new-mappings"></a>添加新映射

要新建映射，请单击工具栏中的“新建”。 这将打开“创建字段映射”对话框。

![“创建字段映射”对话框](media/create-field-mapping-dialog.png)

选择具有要映射的值的源实体字段和目标实体字段。 

![配置字段映射](media/configure-field-mapping.png)

然后选择“确定”以关闭该对话框。

下述规则说明了可映射哪些类型的数据。  
  
- 源字段和目标字段的类型和格式必须一致。  
- 目标字段的长度必须等于或大于源字段的长度。  
- 目标字段不能是已映射到其他字段的字段。  
- 源字段必须是表单上的可见字段。  
- 目标字段必须是用户能输入数据的字段。  
- 地址 ID 值不可映射。
- 如果映射中的源字段或目标字段未在表单上显示，则仅在将未显示的字段添加到表单后，才能完成映射。
- 如果字段是选项集，则每个选项的整数值必须相同。  
  
> [!NOTE]
>  如果需要映射选项集字段，建议将两个字段配置为使用同一个全局选项集。 否则，难以手动同步这两个单独的选项集。 如果每个选项的整数值未正确映射，则数据可能出现问题。 详细信息：[为 Common Data Service for Apps 创建和编辑全局选项集（选择列表）](create-edit-global-option-sets.md)  
  
## <a name="automatically-generate-field-mappings"></a>自动生成字段映射  

还可通过选择“更多操作”菜单中的“生成映射”来自动生成映射。

在对系统实体执行此操作时需小心谨慎。 在创建自定义实体并希望使用映射时，请执行此操作。 

> [!WARNING]
> 这会删除所有现有映射，并将其替换为所推荐的映射，即仅基于具有相似名称和数据类型的字段的映射。 如果对系统实体执行此操作，可能会丢失一些预期映射。 对于自定义实体，这有助于节省时间，因为可更轻松地删除不必要的所有映射，并添加生成映射操作不会创建的其他映射。  


## <a name="publish-customizations"></a>发布自定义项 

字段映射不是元数据，因此必须在更改生效之前发布它们。 
<!-- TODO Need a general topic about publishing to link to in situations like this -->

### <a name="see-also"></a>另请参阅
[使用解决方案资源管理器创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships-solution-explorer.md)<br />
[开发人员文档：自定义实体和属性映射](/dynamics365/customer-engagement/developer/customize-entity-attribute-mappings)<br />
[开发人员文档：Web API 基于另一实体创建新实体](/dynamics365/customer-engagement/developer/webapi/create-entity-web-api#create-a-new-entity-from-another-entity)
