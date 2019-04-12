---
title: 在 Common Data Service 元数据中设置托管属性 | MicrosoftDocs
description: 了解如何在解决方案中为元数据项目设置托管属性。
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
ms.assetid: edaa7d4a-a95f-4d66-a9d9-2ad6051332f7
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="set-managed-properties-in-common-data-service-metadata"></a>在 Common Data Service 元数据中设置托管属性 

托管属性仅适用于以下情况：元数据包括在某个托管解决方案中，并将该解决方案导入到另一个环境。 利用这些设置，解决方案制造者可以对其允许安装托管解决方案的用户拥有的自定义级别有一定的控制。 

> [!TIP]
> 允许用户在处理业务数据的解决方案中扩展元数据通常是一个好主意。 这会允许他们以对标准实体采用的相同方法根据其需要定制您的解决方案。
>
>对于提供支持解决方案的功能但不包含业务数据的元数据，最好限制允许进行哪些自定义。

必须使用解决方案资源管理器设置托管属性。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="entity-managed-properties"></a>实体的托管属性

在[查看实体](create-edit-entities-solution-explorer.md#view-entities)时，选择实体，然后在菜单栏中选择**托管属性**。  这将打开**设置托管属性**对话框。

![设置实体托管属性](media/set-managed-properties.png)
  
实体具有的托管属性比其他任何类型的解决方案组件都多。 如果实体可以自定义，则可设置以下选项。  

|选项|说明|
|--|--|
|**可以自定义** |控制所有其他选项。 如果此选项为 `False`，则其他设置都不适用。 如果这是 `True`，则可指定其他自定义选项。 当为 `False` 时，等同于将所有其他选项设置为 false。|
|**可以修改显示名称**|是否能修改实体显示名称。|
|**可以更改其他属性** |适用于其他选项包含的任何项目。|
|**可以创建新表单**|能否为此实体创建新窗体。|
|**可以创建新图表**|能否为此实体创建新图表。|
|**可以创建新视图** |能否为此实体创建新视图。|
|**可以更改分层关系**|“分层关系”设置是否可更改。 详细信息：[定义和查询层次上相关的数据](define-query-hierarchical-data.md)|
|**是否可以启用更改跟踪** |实体**更改跟踪**属性是否可更改。|
|**可启用到外部搜索索引的同步** |实体是否可以配置为启用相关性搜索"。 详细信息：[配置相关性搜索以改进搜索结果和性能](/dynamics365/customer-engagement/admin/configure-relevance-search-organization) |

## <a name="field-managed-properties"></a>字段托管属性

有关如何编辑字段的信息，请参阅[使用 PowerApps 解决方案资源管理器创建和编辑 Common Data Service 的字段](create-edit-field-solution-explorer.md)。

在[查看字段](create-edit-field-solution-explorer.md#view-fields)时，从非托管解决方案中选择自定义字段，然后在菜单栏上选择**其他操作** >  **托管属性**。

![查看字段托管属性](media/view-field-managed-properties-solution-explorer.png)  
  
这将打开**设置托管属性**对话框。

![设置字段托管属性](media/set-field-managed-property.png)

**可以自定义** 选项控制其他所有选项。 如果此选项为 **False**，则其他设置都不适用。 如果这是 **True**，则可指定其他自定义选项。  
  
如果字段可以自定义，柯将以下选项设置为 **True** 或 **False**。  
  
- **可以修改显示名称**
- **可以更改需求级别** 
- **可以更改其他属性**：此属性控制没有特定托管属性的任何其他自定义项。

将所有单个选项设置为 **False**，等同于将**可以自定义**设置为 **False**。  

应用您的选择并单击**设置**关闭对话框。

> [!NOTE]
> 如果此字段是**日期和时间**字段，另外的**可更改日期和时间行为**属性可用。 详细信息：[日期及时间字段的行为和格式](behavior-format-date-time-field.md)

## <a name="relationship-managed-properties"></a>关系托管属性

在查看实体关系时，从非托管解决方案中选择关系，然后在菜单栏上选择**其他操作** > **托管属性**。
  
对于关系，唯一的托管属性是**可以自定义**。 这一个设置控制可对实体关系做出的所有更改。 


### <a name="see-also"></a>另请参阅

[托管属性](solutions-overview.md#managed-properties)<br />
[使用解决方案资源管理器创建和编辑实体](create-edit-entities-solution-explorer.md)<br />
[使用 PowerApps 解决方案资源管理器创建和编辑 Common Data Service 的字段](create-edit-field-solution-explorer.md)<br />
[使用解决方案资源管理器创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships-solution-explorer.md)<br />
[使用解决方案资源管理器在 Common Data Service 中创建 N:N（多对多）实体关系](create-edit-nn-relationships-solution-explorer.md)
