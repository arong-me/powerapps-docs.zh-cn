---
title: 使用解决方案资源管理器创建和编辑实体 | MicrosoftDocs
description: 了解如何使用解决方案资源管理器创建实体
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
author: Mattp123
ms.author: matp
manager: kvivek
ms.openlocfilehash: 48025088da85bf0685ba1a46efa4f3a989a20a58
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667683"
---
# <a name="create-and-edit-entities-using-solution-explorer"></a>使用解决方案资源管理器创建和编辑实体

可以使用 PowerApps 门户针对最常见的情况轻松创建实体，但并非所有功能都可在该处实现。 当需要满足[在 Common Data Service for Apps 中创建和编辑实体](create-edit-entities.md)中所述的要求时，可以使用解决方案资源管理器，通过创建或编辑实体来实现它们。

## <a name="open-solution-explorer"></a>打开解决方案资源管理器

所创建的任何实体的部分名称是自定义前缀。 这是根据所用解决方案的解决方案发布者设置的。 如果很在意自定义前缀，请确保使用的是非托管解决方案，其中自定义前缀是你希望此实体使用的前缀。 详细信息：[更改解决方案发布者前缀](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-entities"></a>查看实体

在解决方案资源管理器“组件”节点中，选择“实体”节点。

![在解决方案资源管理器中查看实体](media/view-entities-solution-explorer.png)

## <a name="create-an-entity"></a>创建实体

在[查看实体](#view-entities)时，选择“新建”以打开新建实体窗体。

![解决方案资源管理器中的新建实体窗体](media/new-entity-form-solution-explorer.png)

新建实体窗体包含两个选项卡。 “常规”选项卡用于实体选项。 “主字段”选项卡中的选项与每个实体都具有的特殊单行文本字段有关，该字段定义在查找字段中存在用于打开实体的链接时显示的文本。

有关每个部分的信息，请参阅以下内容：
- [配置主字段](#configure-the-primary-field)
- [配置必填字段](#configure-required-fields)

> [!NOTE]
> 还可以使实体成为自定义活动。 这种选择会更改某些默认选项值。 详细信息：[创建自定义活动实体](#create-custom-activity-entity)

为实体设置了所需选项之后，单击 ![保存命令](media/save-entity-icon-solution-explorer.png) 可创建自定义实体。

### <a name="configure-the-primary-field"></a>配置主字段

在“主字段”通常可以接受主字段的默认值，不过可以使用以下选项：

|字段   |描述  |
|---------|---------|
|**显示名称**|输入在窗体和列表中为此字段显示的可本地化标签。 默认值是“名称”。|
|**名称**|设置在系统中用于此字段的名称。 默认值是 `<customization prefix>_name`|
|**最大长度**|输入字段值的最大长度。 默认值是 100。|

> [!NOTE]
> 如果实体是活动实体，则这些选项不适用。 详细信息：[创建自定义活动实体](#create-custom-activity-entity)

### <a name="configure-required-fields"></a>配置必填字段

在“常规”选项卡中，需要先填写某些选项，然后才能保存实体。

|字段   |描述  |
|---------|---------|
|**显示名称**|这是在应用中显示的实体单数名称。<br />这可以在以后进行更改。|
|**复数名称**|这是在应用中显示的实体复数名称。<br />这可以在以后进行更改。|
|**名称**|此字段基于输入的显示名称进行预填充。 它包括解决方案发布者自定义前缀。|
|**所有权**|可以选择用户或团队拥有或是组织拥有。 详细信息：[实体所有权](types-of-entities.md#entity-ownership)|

## <a name="edit-an-entity"></a>编辑实体

在[查看实体](#view-entities)时，选择要编辑的实体或继续编辑刚保存的新实体。

> [!NOTE]
> 属于托管解决方案一部分的标准实体或自定义实体可能对可以应用的更改有所限制。 如果选项不可用或已禁用，则不允许进行更改。

#### <a name="set-once-options"></a>一次性设置选项

以下选项可以设置一次，在设置之后无法更改。 请谨慎操作，仅当需要时才设置这些选项。

<!-- 
Same data is presented in edit-entities.md
Both should point to this include
 -->
[!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

#### <a name="options-that-you-can-change"></a>可以更改的选项

以下属性可以随时更改。

<!-- 
Same data is presented in edit-entities.md
Both should point to this include
 -->
[!INCLUDE [cc_entity-changeable-options-table](../../includes/cc_entity-changeable-options-table.md)]

还可以进行以下更改：
- [为 Common Data Service for Apps 创建和编辑字段](create-edit-fields.md)
- [创建和编辑实体之间的关系](create-edit-entity-relationships.md)
- [创建并设计窗体](../model-driven-apps/create-design-forms.md)
- [创建业务流程以使流程标准化](/flow/create-business-process-flow)

## <a name="delete-an-entity"></a>删除实体

作为具有系统管理员安全角色的人员，可以删除不属于托管解决方案一部分的自定义实体。  
  
> [!IMPORTANT]
>  当删除自定义实体时，存储该实体数据的数据库表会删除，它们包含的所有数据都会丢失。 与自定义实体具有父关系的任何关联记录也会删除。 有关父关系的详细信息，请参阅[创建和编辑实体之间的关系](create-edit-entity-relationships.md)。  
  
> [!NOTE]
> 从已删除的实体恢复数据的唯一方法从删除实体之前的时间点还原数据库。 详细信息：[备份和还原实例](/dynamics365/customer-engagement/admin/backup-restore-instances)

在[查看实体](#view-entities)时，单击工具栏中的 ![“删除”命令](media/delete.gif) 命令。

在查看实体时使用菜单栏中的删除命令。

![“删除”命令](media/delete-custom-entity-solution-explorer.png)

> [!WARNING]
> 删除包含数据的实体会删除所有数据。 此数据只能通过数据库的备份进行检索。

> [!NOTE]
> 如果存在任何实体依赖项，则你会收到“无法删除组件”错误，其中包含“详细信息”链接，可以用于发现有关为何无法删除实体的信息。 在大多数情况下，这是因为必须删除依赖项。 
>
> 可能有多个依赖项阻止删除实体。 此错误消息可能仅显示第一个。 有关发现依赖项的替代方法，请参阅[标识实体依赖项](#identify-entity-dependencies)



### <a name="identify-entity-dependencies"></a>标识实体依赖项

在尝试删除实体之前可以标识会阻止删除它的依赖项。 

1. 在选择了实体的解决方案资源管理器中，单击命令栏中的“显示依赖项”。

![“显示依赖项”命令](media/entity-show-dependencies.png)

2. 在打开的对话框窗口中，向右滚动列表以查看“依赖项类型”列。

![已发布依赖项类型](media/published-entity-dependency.png)

“已发布”依赖项会阻止删除实体。 “内部”依赖项应由系统解析。  

3. 删除这些已发布依赖项，你应能够删除实体。

 > [!NOTE]
 > 一种非常常见的依赖项是另一个实体窗体具有针对要删除的实体的查找字段。 从窗体删除查找字段会解析依赖项。

## <a name="create-custom-activity-entity"></a>创建自定义活动实体

若要将实体创建为活动实体，请使用本主题中所述的相同步骤，除了选择“定义为活动实体”。

![定义为活动实体](media/create-activity-entity-solution-explorer.png)

活动实体是可跟踪操作的一种特殊类型实体，可以在日历上为其生成条目。 详细信息：[活动实体](types-of-entities.md#activity-entities)。

当设置此选项时，某些实体属性不兼容。 活动实体必须符合所有活动实体都使用的标准行为。

主字段“名称”和“显示名称”会设置为“使用者”并且无法更改。

以下选项会在默认情况下进行设置，并且无法更改：

 - **反馈**
 - **说明（包括附件）**
 - **连接**
 - **队列**
 - **Dynamics 365 for Outlook 的脱机功能**

以下选项无法设置：

- **显示此实体的区域**
- **活动**
- **发送电子邮件**
- **邮件合并**
- **单记录审核**
- **多记录审核**

## <a name="create-a-virtual-entity"></a>创建虚拟实体

某些选项仅当创建虚拟实体时才进行使用。

|选项   |描述  |
|---------|---------|
|**虚拟实体**|实体是否为虚拟实体。|
|**数据源**|实体的数据源。|

详细信息：[创建和编辑包含外部数据源数据的虚拟实体](create-edit-virtual-entities.md)

### <a name="see-also"></a>另请参阅
[在 Common Data Service for Apps 中创建和编辑实体](create-edit-entities.md)<br />
[教程：在 PowerApps 中创建含组件的自定义实体](/powerapps/maker/common-data-service/create-custom-entity)<br />
[创建解决方案](create-solution.md)