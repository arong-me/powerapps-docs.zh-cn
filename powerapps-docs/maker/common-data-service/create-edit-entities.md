---
title: 在面向应用程序的 Common Data Service 中创建和编辑实体 | MicrosoftDocs
description: 了解如何创建和编辑实体
ms.custom: ''
ms.date: 05/11/2018
ms.reviewer: ''
ms.service: crm-online
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
---
# <a name="create-and-edit-entities-in-common-data-service-for-apps"></a>在面向应用程序的 Common Data Service 中创建和编辑实体

在创建自定义实体之前，应评估使用现有实体是否满足您的要求。 详细信息：[新建元数据或使用现有元数据？](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

有两个设计器可以用来创建实体：

|设计器| 说明|
|--|--|
|[PowerApps 门户](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|提供简单的简化体验，但是有些特殊设置不可用。<br />详细信息： <br />[教程：在 PowerApps 中创建包含组件的自定义实体](/powerapps/maker/common-data-service/create-custom-entity)<br />[使用 PowerApps 门户创建和编辑实体](create-edit-entities-portal.md)|
|解决方案资源管理器|不那么简单，但提供更多灵活性可减少常见要求。 <br />详细信息[使用解决方案资源管理器创建和编辑实体](create-edit-entities-solution-explorer.md)|

> [!NOTE]
> 您还可以使用以下方法在您的环境中创建实体：
> - 导入包含实体定义的解决方案。
> - 使用 Power Query 创建新实体并使用数据填充它们。 详细信息：[使用 Power Query 将数据添加到 Common Data Service 中的实体](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq)。
> - 开发人员可以使用[元数据服务](/powerapps/developer/common-data-service/use-web-services#metadata-services)编写程序。


## <a name="entity-options-not-available-in-the-powerapps-portal"></a>PowerApps 门户中不可用的实体选项

本主题中的信息将帮助您选择可以使用的设计器。 除非您需要满足下列要求中的任何一个，否则您可以使用 PowerApps 门户创建实体。

- 控制自定义项前缀

  您创建的任何自定义实体的名称中都包含自定义前缀。 这是根据您在其中工作的解决方案的解决方案发布商设置的。 如果您关心自定义前缀，请确保在非托管解决方案中工作，其中的自定义前缀是您需要的此实体的前缀。 详细信息[更改解决方案发布商前缀](change-solution-publisher-prefix.md)。

- 创建由组织负责的实体

  默认情况下，PowerApps 门户将创建**用户或团队**负责的实体。 使用解决方案资源管理器将所有权设置为**组织**。 详细信息：[实体所有权](types-of-entities.md#entity-ownership)

- 创建活动实体

  活动实体是一种特殊类型的实体，跟踪可在日历上为其进行输入的操作。 详细信息：[活动实体](types-of-entities.md#activity-entities)。

- 更改自定义实体的图标

  默认情况下，模型驱动应用程序中的所有自定义实体具有相同的图标。 您可以为自定义实体所需要的图标创建图像 Web 资源。 详细信息：[更改自定义实体的图标](../model-driven-apps/change-custom-entity-icons.md)。 

- 更改唯一可以启用的以下任何一种属性：

  [!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

- 更改以下任何一种属性：

  <!-- Based on ../../includes/cc_entity-changeable-options-table.md 
Removed these:

  /|**Description**/|Provide a meaningful description of the purpose of the entity./|

  /|**Primary Image**/|System entities that support images will already have an **Image** field. You can choose whether to display data in this field as the image for the record by setting this field to **[None]** or **Default Image**.<br /><br /> For custom entities you must first create an image field. Each entity can have only one image field. After you create one, you can change this setting to set the primary image. More information: [Image fields](../maker/common-data-service/types-of-fields.md#image-fields) /|-->

  |选项   |说明  |
  |---------|---------|
  |**访问团队**|为此实体创建团队模板。 |
  |**允许快速创建**|在为此实体创建并发布了**快速创建窗体**之后，用户可以选择使用导航窗格中的**创建**按钮来创建新的记录。 更多信息：[创建和设计窗体](../model-driven-apps/create-design-forms.md)<br /><br /> 如果为某个自定义活动实体启用了此选项，则当用户使用导航窗格中的**创建**按钮时，自定义活动将出现在活动实体的组中。 但是，由于活动不支持快速创建窗体，因此，当单击自定义实体图标时，将使用主窗体。|
  |**显示此实体的区域**|在 Web 应用程序中选择其中一个可用站点地图区域以显示此实体。 这不适用于模型驱动应用程序。|
  |**审核**|在为组织启用了审核后，将允许更改随时间获取的实体记录。 为实体启用审核后，也会对其所有字段启用审核。 可以选择或清除要对其启用审核的字段。|
  |**更改跟踪**|从最初解压缩或最后同步数据开始就检测被更改的数据，从而以永久方法支持数据同步。  |
  |**颜色**|在模型驱动应用程序中设置用于实体的颜色。|
  |**文档管理**|在执行了其他任务来启用组织的文档管理后，启用此功能可以让此实体加入与 SharePoint 的集成。 |
  |**重复检测**|如果为组织启用了重复检测，启用此选项将允许为此实体创建重复检测规则。|
  |**为移动设备启用**|使此实体对 Dynamics 365 for phones 和 Dynamics 365 for tablets 应用程序可用。 您还可以选择将此实体设为**在移动设备中为只读**。<br /><br /> 如果实体的窗体需要不被 Dynamics 365 for phones 和 Dynamics 365 for tablets 应用程序支持的扩展，请使用此设置确保移动应用程序用户不能编辑这些实体的数据。|
  |**针对 Phone Express 启用**|使此实体对 Dynamics 365 for phones 应用程序可用。|
  |**邮件合并**|用户可以将此实体用于邮件合并。|
  |**Dynamics 365 for Outlook 的脱机功能**|当 Dynamics 365 for Outlook 应用程序未连接到网络时，此实体中的数据是否可用。|
  |**Dynamics 365 for Outlook 中的阅读窗格**|实体是否在 Dynamics 365 for Outlook 应用程序的阅读窗格中可见。|
  |**使用自定义帮助**|启用后，设置帮助 URL 来控制用户在单击应用程序中的帮助按钮时他们将看到的页面。 使用此设置来提供特定于您公司的实体流程的指导。|


### <a name="see-also"></a>另请参阅

[使用解决方案资源管理器创建和编辑实体](create-edit-entities-solution-explorer.md)<br />
[教程：在 PowerApps 中创建包含组件的自定义实体](/powerapps/maker/common-data-service/create-custom-entity)<br />
[编辑实体](edit-entities.md)<br />
[开发人员文档：创建自定义实体](/dynamics365/customer-engagement/developer/org-service/create-custom-entity)
