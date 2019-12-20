---
title: 在 Power Apps 中映射实体字段 | MicrosoftDocs
description: 了解如何映射实体字段
ms.custom: ''
ms.date: 05/29/2018
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
ms.assetid: 7c5aa1c3-bde9-43f1-a369-fdcdbf14dec0
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: a5da8b9ecfb2bbba2a4e03fbc0d28301c41e2a7c
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2860883"
---
# <a name="map-entity-fields"></a>映射实体字段
 
您可以在具有实体关系的实体之间映射属性。 这样就可以为在另一条记录的上下文中创建的记录设置默认值。 

## <a name="easier-way-to-create-new-records-in-model-driven-apps"></a>在模型驱动应用程序中创建新记录的更简单方法

假设用户要为属于特定客户的员工的某个人添加一个新的联系人记录。 他们可以通过两种方式完成此事：  
  
### <a name="the-hard-way"></a>困难方法

用户在应用中导航即可从头开始创建新的联系人记录。 但是，随后他们需要设置上级单位，并输入可能与上级单位相同的多个信息项（如地址和电话信息）。 这可能会很耗时间，并会增加出错的机会。  
  
### <a name="the-easier-way"></a>更简单的方法

最简单的方法是从客户实体入手，然后使用窗体上的**联系人**子网格，选择 **+** 来添加联系人。 它将先指引用户查找现有的相关联系人，因此不会无意中创建重复的记录。 如果没有找到现有记录，则可以选择**新建**，创建一个新的联系人记录。 

新的联系人记录窗体将包含客户的任何映射属性值（如地址和电话信息）作为默认值。 用户可以在保存记录前编辑这些值。

## <a name="how-this-works"></a>工作原理

当映射 1:N 实体关系的实体字段时，主要实体记录中数据的某些项目将被复制到新的相关实体窗体以设置用户在保存前可以编辑的默认值。
 
  
> [!NOTE]
> 这些映射仅在保存记录之前设置记录的默认值。 用户可以在保存之前编辑值。 传输的数据是该时间点的数据。 如果源数据之后改变，将不会同步。
>   
> 这些映射不会应用于使用工作流或对话流程创建的相关记录。 它们不会自动应用于使用代码创建的新记录，但开发人员可以使用一条名为 `InitializeFrom`（[InitializeFrom 函数](/dynamics365/customer-engagement/web-api/initializefrom?view=dynamics-ce-odata-9)或 [InitializeFromRequest 类](/dotnet/api/microsoft.crm.sdk.messages.initializefromrequest?view=dynamics-general-ce-9)）的特殊消息，使用可用映射来创建新记录。  

## <a name="open-solution-explorer"></a>打开解决方案资源管理器

映射实体字段的唯一方法是使用解决方案资源管理器。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]
  
映射字段在 1:N 或 N:1 实体关系的上下文中进行，因此，您首先需要[查看 1:N 或 N:1 实体关系](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships)。

## <a name="view-mappable-fields"></a>查看可映射字段

字段映射不在实体关系中实际定义，但它们显示在关系用户界面中。 并非每个 1:N 实体关系都有它们。 在查看某个实体的 1:N（或 N:1）实体实体列表时，可以按类型筛选显示的关系。 您可以选择**全部**、**自定义**、**可自定义**或**可映射**。 “可映射”实体关系提供的访问权限允许映射实体字段。 

![查看可映射实体关系](media/mappable-entity-relationships.png) 

在打开可映射实体关系时，选择左侧导航中的**映射**。

![选择实体关系的“映射”](media/map-entity-fields-ui-solution-explorer.png)

## <a name="delete-mappings"></a>删除映射

如果存在您不希望应用的任何映射，您可以选择它们并单击 ![“删除图标”](media/delete.gif) 图标。

## <a name="add-new-mappings"></a>添加新映射

若要创建新映射，在工具栏上单击**新建**。 这将打开**创建字段映射**对话框。

![创建字段映射对话框](media/create-field-mapping-dialog.png)

选择一个源实体字段和一个包含您要映射的值的目标实体字段。 

![配置字段映射](media/configure-field-mapping.png)

然后选择**确定**关闭对话框。

下列规则显示了可以映射的数据种类。  
  
- 两个字段必须属于同一类型，而且必须采用相同的格式。  
- 目标字段的长度必须等于或大于源字段的长度。  
- 目标字段不能已映射到其他字段。  
- 源字段必须在表单上可见。  
- 目标字段必须是一个可供用户在其中输入数据的字段。  
- 不能映射地址 ID 值。
- 如果映射到未在表单中显示的字段或从其进行映射，则在将该字段添加到表单前，映射不会完成。
- 如果字段是选项集，则每个选项的整数值应完全相同。  
  
> [!NOTE]
>  如果需要映射选项集字段，建议您将两个字段都配置为使用相同的全局选项集。 否则，可能难以手动让两个单独的选项集保持同步。 如果每个选项的整数值未正确映射，则可能是数据中出现了问题。 详细信息：[为 Common Data Service 创建和编辑全局选项集（选择列表）](create-edit-global-option-sets.md)  
  
## <a name="automatically-generate-field-mappings"></a>自动生成字段映射  

您还可以通过从**其他操作**菜单选择**生成映射**来自动生成映射。

在使用系统实体进行操作时应该小心。 请在创建自定义实体并要使用映射时使用此选项。 

> [!WARNING]
> 这会删除所有现有的映射，并代这以建议的映射；这些建议的映射基于具有类似名称和数据类型的字段。 如果对系统实体使用此方法，则可能会丢失一些应有的映射。 对于自定义实体，这有助于节省时间，因为您可以更轻松地删除您不需要的任何映射，并可添加生成映射操作不会创建的其他任何映射。  


## <a name="publish-customizations"></a>发布自定义项 

由于字段映射不属于元数据，必须在更改生效前发布它们。 
<!-- TODO Need a general topic about publishing to link to in situations like this -->

### <a name="see-also"></a>另请参阅
[使用解决方案资源管理器创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships-solution-explorer.md)<br />
[开发人员文档：自定义实体和属性映射](/dynamics365/customer-engagement/developer/customize-entity-attribute-mappings)<br />
[开发人员文档：Web API 从另一个实体创建新实体](/dynamics365/customer-engagement/developer/webapi/create-entity-web-api#create-a-new-entity-from-another-entity)
