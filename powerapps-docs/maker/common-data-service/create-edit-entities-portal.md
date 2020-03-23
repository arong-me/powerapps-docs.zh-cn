---
title: 使用 Power Apps 门户创建和编辑实体 | MicrosoftDocs
description: 了解如何使用 Power Apps 门户创建和编辑实体
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
author: Mattp123
ms.assetid: fa04f99d-a5f9-48cb-8bfb-f0f50718ccee
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 199399fe75103df2d8fde902d54a803ec56fc395
ms.sourcegitcommit: 2b34de88c977c149e4c632b23d8e816901c15949
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2020
ms.locfileid: "3040555"
---
# <a name="create-and-edit-entities-using-power-apps-portal"></a>使用 Power Apps 门户创建和编辑实体

[Power Apps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)提供为 Common Data Service 创建和编辑实体的简单方法。

此门户支持配置最常见的选项，但是某些选项只能使用解决方案资源管理器设置。 详细信息： 
- [在 Common Data Service 中创建和编辑实体](create-edit-entities.md)
- [使用解决方案资源管理器创建和编辑实体](create-edit-entities-solution-explorer.md)

## <a name="view-entities"></a>视图实体

1. 从 [Power Apps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，选择**数据** > **实体**。

![视图实体](media/view-entities-portal.png)

您可以使用列表中的以下视图筛选您看到的实体： 

![实体视图](media/entity-views-portal.png)

 |视图|说明|
 |--|--|
 |**所有**| 显示所有实体|
 |**托管**| 仅显示托管和标准实体|
 |**自定义**|仅显示自定义实体|
 |**默认**|仅显示标准实体 |

您还可以选择**组**来按对其应用的**标记**分组实体。

## <a name="create-an-entity"></a>创建实体

在[查看实体](#view-entities)时，在菜单栏中选择**新实体**。 这将打开“新实体”面板。

![“新实体”面板](media/new-entity-panel.png)

输入以下字段的数据

|字段|说明|
|--|--|
|**显示名称**|这是将在应用中显示的实体的单数名称。 以后可以更改此信息。|
|**复数显示名称**|这是将在应用中显示的实体的复数名称。 以后可以更改此信息。|
|**名称**|此字段是根据您输入的**显示名称**预填充的。 其中包括 Common Data Service 解决方案发布商的自定义前缀。 保存实体后，就不能进行更改。|
|**主要名称**|这是此时唯一可见的字段。| 如果要更改字段的**显示名称**或**名称**，可以编辑该字段。
|**显示名称**|这是您的记录的主要用户友好文本标识符（通常为名称或数字）。 当用户需要从记录列表中进行选择时，会向用户显示此字段的值。
|**名称**|此字段是根据您输入的**显示名称**预填充的。 其中包括 Common Data Service 解决方案发布商的自定义前缀。 保存实体后，就不能进行更改。|

选择**启用附件**可将注释和文件追加到此实体的记录中。

选择**更多设置**。 对于实体，这些设置是可选的。

|字段|说明|
|--|--|
|**说明**|提供实体用途的有意义的描述。|
|**实体类型和所有权**|将实体类型切换到“活动实体”可以创建可管理任务的实体。 **所有权**的类型定义谁可以对记录执行操作。|
|**协作**|启用功能可以帮助用户更加轻松地在此实体上协同工作。|
|**创建和更新设置**|您可以启用快速创建窗体，为您的应用提供简化的数据输入体验。 重复检测让您可以设置重复检测策略并创建重复检测规则。 更改跟踪提供以永久方法保持数据同步的方式。|
|**Dynamics 365 for Outlook**|配置此实体在 Outlook 中的显示方式。|

选择**创建**以继续，这将关闭**新实体**面板并显示字段列表。

实体的**主要名称**字段将显示在字段列表中。 如果要更改字段的**显示名称**或**名称**，请选择**主要名称**字段进行编辑。 默认值如下所示：

![“主要名称”面板](media/primary-name-panel.png)

## <a name="edit-an-entity"></a>编辑实体

在[查看实体](#view-entities)时，选择要编辑的实体。

如果要编辑实体的**显示名称**、**复数显示名称**或**描述**，从菜单选择**设置**。

![实体设置](media/entity-settings-portal.png)

对于其他项目，请从选项卡选择。

### <a name="fields"></a>字段

请参阅[创建和编辑字段](create-edit-fields.md)

### <a name="relationships"></a>关系

请参阅[创建和编辑实体之间的关系](create-edit-entity-relationships.md)

### <a name="business-rules"></a>业务规则

请参阅[创建业务规则和建议以在窗体中应用逻辑](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)

### <a name="views"></a>视图

请参阅[创建或编辑视图](../model-driven-apps/create-edit-views.md)

### <a name="forms"></a>窗体

请参阅[创建和设计窗体](../model-driven-apps/create-design-forms.md)

### <a name="dashboards"></a>仪表板

请参阅[创建或编辑仪表板](../model-driven-apps/create-edit-dashboards.md)

### <a name="charts"></a>图表

请参阅[创建系统图表](../model-driven-apps/create-edit-system-chart.md)

### <a name="keys"></a>键

请参阅[定义引用记录的备用键](define-alternate-keys-reference-records.md)

### <a name="data"></a>数据

查看实体中的数据。
使用**选择视图**菜单从实体的可用视图中选择或显示所有字段。

![选择视图](media/entity-data-select-view.png)

使用窗体底部的**下一页**和**上一页**命令查看更多数据。

## <a name="delete-an-entity"></a>删除实体

具有系统管理员安全角色的用户可以删除不属于托管解决方案的自定义实体。  
  
> [!IMPORTANT]
>  在删除自定义实体时，会删除存储该实体的数据的数据库表，其中包含的所有数据将丢失。 同时也将删除与自定义实体存在父关系的所有关联记录。 有关父关系的详细信息，请参阅[创建和编辑实体之间的关系](create-edit-entity-relationships.md)。  
  
> [!NOTE]
> 从删除的实体中恢复数据的唯一方法是从删除实体前的某个点恢复数据库。 详细信息：[备份和还原实例](/dynamics365/customer-engagement/admin/backup-restore-instances)

在[查看实体](#view-entities)时，选择实体，然后从菜单中选择**删除实体**。

![使用 Power Apps 门户删除实体](media/delete-entity-powerapps-portal.png)

如果实体有依赖项，阻止您删除，您将看到错误消息。 若要确定并删除所有依赖项，您需要使用解决方案资源管理器。 详细信息[确定实体依赖项](create-edit-entities-solution-explorer.md#identify-entity-dependencies)

### <a name="see-also"></a>另请参阅

[在 Common Data Service 中创建和编辑实体](create-edit-entities.md)<br />
[使用解决方案资源管理器创建和编辑实体](create-edit-entities-solution-explorer.md)


