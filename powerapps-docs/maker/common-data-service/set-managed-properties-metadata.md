---
title: 在 Common Data Service 元数据中设置托管属性 | MicrosoftDocs
description: 了解如何在解决方案中为元数据项目设置托管属性。
ms.custom: ''
ms.date: 03/03/2020
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
ms.assetid: edaa7d4a-a95f-4d66-a9d9-2ad6051332f7
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0f75c9c38b3fbd74f330de5e80a2c0f7df8d6e13
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "3124945"
---
# <a name="set-managed-properties-in-common-data-service-metadata"></a>在 Common Data Service 元数据中设置托管属性 
可以使用托管属性来控制哪些托管解决方案组件可自定义。 ISV 应该允许在有意义时对解决方案组件进行自定义。 这样，组织可以根据其特殊需要自定义您的解决方案。 限制或消除提供解决方案核心功能的关键解决方案组件的自定义，以便您可以按可预见的方式支持和维护它。 对于大多数非 ISV 开发环境，我们建议您不要允许自定义托管解决方案组件。 

托管属性旨在保护解决方案免遭可能导致它中断的修改。 托管属性不提供数字版权管理 (DRM) 或者用于许可解决方案或控制谁可以安装它的功能。

当解决方案在开发环境的非托管层处于非托管状态时，您将应用托管属性。 托管属性将在您打包托管解决方案并将它安装在不同环境中后生效。 导入托管解决方案后，只能使用原始发布者的解决方案更新来更新托管属性。 

在查看解决方案组件列表时，大多数解决方案组件提供**托管属性**菜单项。 当您导入包含这些组件的托管解决方案时，可以查看但不能更改其托管属性。

## <a name="view-and-edit-entity-managed-properties"></a>查看和编辑实体托管属性
1.  登录 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后从左侧窗格中选择**解决方案**。 
2.  打开所需的解决方案。 
3.  从解决方案中的组件列表选择要查看或编辑其托管属性的非托管实体旁边的 **…**， 在要查看其托管属性的实体旁边，然后选择**托管属性**。 

    > [!div class="mx-imgBorder"] 
    > ![实体托管属性命令](media/entity-managed-properties.png "实体托管属性命令")

    将显示托管属性页。 

    > [!div class="mx-imgBorder"] 
    > <img src="media/managed-properties-dialog.png" alt="Managed properties pane" height="572" width="300">

实体具有的托管属性比其他任何类型的解决方案组件都多。 如果实体可以自定义，则可设置以下选项。  

|选项|说明|
|--|--|
|**允许自定义项** |控制所有其他选项。 如果此选项为 `False`，则其他设置都不适用。 如果这是 `True`，则可指定其他自定义选项。 当为 `False` 时，等同于将所有其他选项设置为 false。|
|**可以修改显示名称**|是否能修改实体显示名称。|
|**可以更改其他属性** |适用于其他选项包含的任何项目。|
|**可以创建新表单**|能否为此实体创建新窗体。|
|**可以创建新图表**|能否为此实体创建新图表。|
|**可以创建新视图** |能否为此实体创建新视图。|
|**可以更改分层关系**|“分层关系”设置是否可更改。 详细信息：[定义和查询层次上相关的数据](define-query-hierarchical-data.md)|
|**是否可以启用更改跟踪** |实体**更改跟踪**属性是否可更改。|
|**可启用到外部搜索索引的同步** |实体是否可以配置为启用相关性搜索"。 详细信息：[配置相关性搜索以改进搜索结果和性能](/dynamics365/customer-engagement/admin/configure-relevance-search-organization) |

## <a name="view-and-edit-field-managed-properties"></a>查看和编辑字段托管属性
在解决方案中的自定义字段旁边，选择 **…** 然后选择**托管属性**。

这将打开**托管属性**窗格。
> [!div class="mx-imgBorder"] 
> <img src="media/field-managed-prop.png" alt="Field managed properties" height="525" width="295">

**允许自定义**选项控制其他所有选项。 如果此选项被禁用，则其他设置都不适用。 如果启用，则可指定其他自定义选项。  
  
如果字段可以自定义，您可以启用以下选项。  
  
- **可以修改显示名称**
- **可以更改其他属性**：此属性控制没有特定托管属性的任何其他自定义项。 
- **可以创建新表单** 
- **可以创建新图表** 
- **可以创建新视图** 
- **可以更改分层关系** 
- **可以启用更改跟踪** 
- **支持同步到外部搜索索引**

禁用所有单个选项等同于禁用**允许自定义**。  

应用您的选择，然后选择**完成**关闭窗格。

> [!NOTE]
> 如果此字段是**日期和时间**字段，另外的**可更改日期和时间行为**属性可用。 详细信息：[日期及时间字段的行为和格式](behavior-format-date-time-field.md) 

有关如何编辑字段的信息，请参阅[使用 Power Apps 解决方案资源管理器创建和编辑 Common Data Service 的字段](create-edit-field-solution-explorer.md)。

## <a name="view-and-edit-other-component-managed-properties"></a>查看和编辑其他组件的托管属性
您可以查看和编辑许多其他解决方案组件的托管属性，例如 Web 资源、流程、图表或仪表板。 在解决方案中在组件旁边，选择 **…** 然后选择**托管属性**。 

## <a name="view-and-edit-relationship-managed-properties"></a>查看和编辑关系托管属性
在[解决方案资源管理器](../model-driven-apps/advanced-navigation.md#solution-explorer)中查看实体关系时，从非托管解决方案中选择关系，然后在菜单栏上选择**其他操作** > **托管属性**。
  
对于关系，唯一的托管属性是**可以自定义**。 这一个设置控制可对实体关系做出的所有更改。 

### <a name="see-also"></a>另请参阅

[导出解决方案](export-solutions.md) <br />
[解决方案概述](solutions-overview.md)

