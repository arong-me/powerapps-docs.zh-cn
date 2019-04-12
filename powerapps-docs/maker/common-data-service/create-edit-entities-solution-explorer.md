---
title: 使用解决方案资源管理器创建和编辑实体 | MicrosoftDocs
description: 了解如何使用解决方案资源管理器创建实体
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
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-and-edit-entities-using-solution-explorer"></a>使用解决方案资源管理器创建和编辑实体

您可以使用 PowerApps 门户在大多数常见情况下轻松创建实体，不过不是所有功能都在这里实现。 在需要满足[在 Common Data Service 中创建和编辑实体](create-edit-entities.md)中所述的要求时，可以通过使用解决方案资源管理器创建或编辑实体来实现。

## <a name="open-solution-explorer"></a>打开解决方案资源管理器

您创建的任何实体的名称中都包含自定义前缀。 这是根据您在其中工作的解决方案的解决方案发布商设置的。 如果您关心自定义前缀，请确保在非托管解决方案中工作，其中的自定义前缀是您需要的此实体的前缀。 详细信息：[更改解决方案发布商前缀](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-entities"></a>视图实体

在解决方案资源管理器的**组件**节点中，选择**实体**节点。

![在解决方案资源管理器中查看实体](media/view-entities-solution-explorer.png)

## <a name="create-an-entity"></a>创建实体

在[查看实体](#view-entities)时，选择**新**打开新实体窗体。

![解决方案资源管理器中的新实体窗体](media/new-entity-form-solution-explorer.png)

新实体窗体有两个选项卡。 **常规**选项卡用于实体选项。 **主字段**选项卡用于有关每个实体都有的特殊单行文本字段的选项，该字段定义在查找字段中有打开实体的链接时显示的文本。

有关每个部分的信息，请参阅以下内容：
- [配置主字段](#configure-the-primary-field)
- [配置必填字段](#configure-required-fields)

> [!NOTE]
> 您还可以让实体成为自定义活动。 此选择更改某些默认选项值。 详细信息：[创建自定义活动实体](#create-custom-activity-entity)

在设置实体的必需选项后，单击 ![“保存”命令](media/save-entity-icon-solution-explorer.png) 创建自定义实体。

### <a name="configure-the-primary-field"></a>配置主字段

在**主字段**选项卡上，您通常可以接受主字段的默认值，但是，您有以下选项：

|字段   |说明  |
|---------|---------|
|**显示名称**|在窗体和列表中输入将为该字段显示的可本地化标签。 默认值为**名称**。|
|**名称**|设置此字段的系统中使用的名称。 默认值为 `<customization prefix>_name`|
|**最大长度**|输入字段值的最大长度。 默认值为 100。|

> [!NOTE]
> 如果实体是活动实体，这些选项不适用。 详细信息：[创建自定义活动实体](#create-custom-activity-entity)

### <a name="configure-required-fields"></a>配置必填字段

在**常规**选项卡上，需要一些选项才可以保存实体。

|字段   |说明  |
|---------|---------|
|**显示名称**|这是将在应用中显示的实体的单数名称。<br />以后可以更改此信息。|
|**复数名称**|这是将在应用中显示的实体的复数名称。<br />以后可以更改此信息。|
|**名称**|此字段是根据您输入的显示名称预填充的。 其中包括解决方案发布商自定义前缀。|
|**所有权**|您可以选择“由用户或团队负责”或者“由组织负责”。 详细信息：[实体所有权](types-of-entities.md#entity-ownership)|

## <a name="edit-an-entity"></a>编辑实体

在[查看实体](#view-entities)时，选择要编辑的实体，或继续编辑刚才保存的新实体。

> [!NOTE]
> 属于托管解决方案一部分的标准实体或自定义实体可能对您可以应用的更改有限制。 如果此选项不可用或被禁用，将不允许您进行更改。

#### <a name="set-once-options"></a>设置一次性选项

下列选项可以设置一次，并且设置后不能更改。 请仅在需要时谨慎设置这些选项。

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

您还可以进行以下更改：
- [创建和编辑 Common Data Service 的字段](create-edit-fields.md)
- [创建和编辑实体之间的关系](create-edit-entity-relationships.md)
- [创建和设计窗体](../model-driven-apps/create-design-forms.md)
- [创建业务流程以标准化流程](/flow/create-business-process-flow)

## <a name="delete-an-entity"></a>删除实体

具有系统管理员安全角色的用户可以删除不属于托管解决方案的自定义实体。  
  
> [!IMPORTANT]
>  在删除自定义实体时，会删除存储该实体的数据的数据库表，其中包含的所有数据将丢失。 同时也将删除与自定义实体存在父关系的所有关联记录。 有关父关系的详细信息，请参阅[创建和编辑实体之间的关系](create-edit-entity-relationships.md)。  
  
> [!NOTE]
> 从删除的实体中恢复数据的唯一方法是从删除实体前的某个点恢复数据库。 详细信息：[备份和还原实例](/dynamics365/customer-engagement/admin/backup-restore-instances)

在[查看实体](#view-entities)时，单击工具栏中的![删除命令](media/delete.gif)命令。

在查看实体时，使用菜单栏中的“删除命令”。

![删除命令](media/delete-custom-entity-solution-explorer.png)

> [!WARNING]
> 删除包含数据的实体会删除所有数据。 此数据只能通过数据库的备份检索。

> [!NOTE]
> 如果存在任何实体依赖项，您将收到**无法删除组件**错误，其中包含可用于发现实体为何无法删除的信息的**详细信息**链接。 在大多数情况下，这都是因为有必须删除的依赖项。 
>
> 可能有多个阻止删除实体的依赖项。 此错误消息可能只显示第一个依赖项。 有关发现依赖项的备用方法，请参阅[确定实体依赖项](#identify-entity-dependencies)



### <a name="identify-entity-dependencies"></a>确定实体依赖项

您可以在尝试删除实体前确定阻止实体被删除的依赖项。 

1. 在选择了实体的解决方案资源管理器中，在命令栏中单击**显示依赖项**。

![显示依赖项命令](media/entity-show-dependencies.png)

2. 在打开的对话框窗口中，向右滚动列表查看**依赖项类型**列。

![已发布的依赖项类型](media/published-entity-dependency.png)

**已发布**依赖项将会阻止删除实体。 **内部**依赖项应由系统解决。  

3. 删除这些已发布的依赖项，然后您应该可以删除实体了。

 > [!NOTE]
 > 一个非常常见的依赖项是另一个实体窗体有要删除的实体的查找字段。 从窗体中删除查找字段将解决此依赖项。

## <a name="create-custom-activity-entity"></a>创建自定义活动实体

若要将实体创建为活动实体，请使用本主题中介绍的相同步骤，选择**定义为活动实体**除外。

![定义为活动实体](media/create-activity-entity-solution-explorer.png)

活动实体是一种特殊类型的实体，跟踪可在日历上为其进行输入的操作。 详细信息：[活动实体](types-of-entities.md#activity-entities)。

当您设置此选项后，有些实体属性不兼容。 活动实体必须符合所有活动实体使用的标准行为。

主字段**名称**和**显示名称**将设置为**主题**，并且您无法更改。

以下选项为默认设置，无法更改：

 - **反馈**
 - **注释(包括附件)**
 - **连接**
 - **队列**
 - **Dynamics 365 for Outlook 的脱机功能**

以下选项无法设置：

- **显示此实体的区域**
- **活动**
- **正在发送电子邮件**
- **邮件合并**
- **单记录审核**
- **多记录审核**

## <a name="create-a-virtual-entity"></a>创建虚拟实体

有些选项仅在创建虚拟实体时使用。

|选项   |说明  |
|---------|---------|
|**虚拟实体**|实体是否是虚拟实体。|
|**数据源**|实体的数据源。|

详细信息：[创建和编辑包含来自外部数据源的数据的虚拟实体](create-edit-virtual-entities.md)

### <a name="see-also"></a>另请参阅
[在 Common Data Service 中创建和编辑实体](create-edit-entities.md)<br />
[教程：在 PowerApps 中创建包含组件的自定义实体](/powerapps/maker/common-data-service/create-custom-entity)<br />
[创建解决方案](create-solution.md)
