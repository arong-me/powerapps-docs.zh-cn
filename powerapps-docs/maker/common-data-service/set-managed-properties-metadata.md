---
title: 在 Common Data Service for Apps 元数据中设置托管属性 | MicrosoftDocs
description: 了解如何在解决方案中为元数据项设置托管属性
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
ms.assetid: edaa7d4a-a95f-4d66-a9d9-2ad6051332f7
caps.latest.revision: 41
ms.author: matp
manager: kvivek
ms.openlocfilehash: 46727f5a46e3fd518da52fac7d08a6e43992c00d
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668274"
---
# <a name="set-managed-properties-in-common-data-service-for-apps-metadata"></a>在 Common Data Service for Apps 元数据中设置托管属性 

托管属性仅在将元数据包含在托管解决方案中并将解决方案导入另一个环境时才适用。 这些设置使解决方案制定者可以对他们希望安装其托管解决方案的人员拥有的自定义级别有一定的控制。 

> [!TIP]
> 通常，最好使人员能够扩展处理业务数据的解决方案中的元数据。 这将使他们能够以适用于标准实体的相同方式按照需求来量身定制解决方案。
>
>对于提供支持解决方案的功能但不包含业务数据的元数据，最好限制所允许进行的自定义。

必须使用解决方案资源管理器设置托管属性。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="entity-managed-properties"></a>实体托管​​属性

[查看实体](create-edit-entities-solution-explorer.md#view-entities)时，选择实体并在菜单栏上选择“托管属性”。  这将打开“设置托管属性”对话框。

![设置实体托管属性](media/set-managed-properties.png)
  
实体具有比任何其他类型的解决方案组件更多的托管属性。 如果实体可自定义，则可以设置以下选项：  

|选项|描述|
|--|--|
|**可以自定义** |控制所有其他选项。 如果此选项为 `False`，其他任何设置均不适用。 如果为 `True`，则可以指定其他自定义选项。 如果为 `False`，则相当于将所有其他选项设置为 false。|
|**可以修改显示名称**|是否可以修改实体显示名称。|
|**可以更改其他属性** |适用于其他选项未涵盖的内容。|
|**可以创建新窗体**|是否可以为实体创建新窗体。|
|**可以创建新图表**|是否可以为实体创建新图表。|
|**可以创建新视图** |是否可以为实体创建新视图。|
|**可以更改分层关系**|是否可以更改“分层关系”设置。 详细信息：[定义和查询按层次结构相关的数据](define-query-hierarchical-data.md)|
|**可以启用更改跟踪** |是否可以更改实体“更改跟踪”属性。|
|**可以启用同步到外部搜索索引** |是否可以将实体配置为启用相关性搜索。 详细信息：[配置相关性搜索以改善搜索结果和性能](/dynamics365/customer-engagement/admin/configure-relevance-search-organization) |

## <a name="field-managed-properties"></a>字段托管属性

有关如何编辑字段的信息，请参阅[使用 PowerApps 解决方案资源管理器为 Common Data Service for Apps 创建和编辑字段](create-edit-field-solution-explorer.md)。

[查看字段](create-edit-field-solution-explorer.md#view-fields)时，从非托管解决方案中选择自定义字段，然后在菜单栏上选择“更多操作” >  “托管属性”。

![查看字段托管属性](media/view-field-managed-properties-solution-explorer.png)  
  
这将打开“设置托管属性”对话框。

![设置字段托管属性](media/set-field-managed-property.png)

“可以自定义”选项控制所有其他选项。 如果此选项为 False，其他任何设置均不适用。 如果为 True，则可以指定其他自定义选项。  
  
如果此字段可自定义，则可以将以下选项设置为 True 或 False。  
  
- **可以修改显示名称**
- **可以更改要求级别** 
- **可以更改其他属性**：此属性控制任何其他没有特定托管属性的自定义。

将所有单个选项设置为 False 等同于将“可以自定义”设置为 False。  

应用你的选择，然后单击“设置”以关闭对话框。

> [!NOTE]
> 如果此字段是“日期和时间”字段，将提供附加的“可以更改日期和时间行为”属性。 详细信息：[“日期和时间”字段的行为和格式](behavior-format-date-time-field.md)

## <a name="relationship-managed-properties"></a>关系托管​​属性

查看实体关系时，从非托管解决方案中选择关系，然后在菜单栏上选择“更多操作” > “托管属性”。
  
对于关系，唯一的托管属性是“可以自定义”。 这一项设置控制可以对实体关系做出的所有更改。 


### <a name="see-also"></a>另请参阅

[托管​​属性](solutions-overview.md#managed-properties)<br />
[使用解决方案资源管理器创建和编辑实体](create-edit-entities-solution-explorer.md)<br />
[使用 PowerApps 解决方案资源管理器为 Common Data Service for Apps 创建和编辑字段](create-edit-field-solution-explorer.md)<br />
[使用解决方案资源管理器创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships-solution-explorer.md)<br />
[使用解决方案资源管理器在 Common Data Service for Apps 中创建 N:N（多对多）实体关系](create-edit-nn-relationships-solution-explorer.md)