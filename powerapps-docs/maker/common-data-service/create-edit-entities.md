---
title: 在 Common Data Service 中创建和编辑实体 | MicrosoftDocs
description: 了解如何创建和编辑实体
ms.custom: ''
ms.date: 04/16/2019
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
ms.openlocfilehash: d700c76009f45c4e28f78732e7ae52ab57693ccb
ms.sourcegitcommit: 2b34de88c977c149e4c632b23d8e816901c15949
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2020
ms.locfileid: "3040473"
---
# <a name="create-and-edit-entities-in-common-data-service"></a>在 Common Data Service 中创建和编辑实体

在创建自定义实体之前，应评估使用现有实体是否满足您的要求。 详细信息：[新建元数据或使用现有元数据？](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

有两个设计器可以用来创建实体：

|设计器| 说明|
|--|--|
|[Power Apps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|提供简单的简化体验，但是有些特殊设置不可用。<br />详细信息： <br />[教程：在 Power Apps 中创建包含组件的自定义实体](/powerapps/maker/common-data-service/create-custom-entity)<br />[使用 Power Apps 门户创建和编辑实体](create-edit-entities-portal.md)|
|解决方案资源管理器|不那么简单，但提供更多灵活性可减少常见要求。 <br />详细信息[使用解决方案资源管理器创建和编辑实体](create-edit-entities-solution-explorer.md)|

> [!NOTE]
> 您还可以使用以下方法在您的环境中创建实体：
> - 导入包含实体定义的解决方案。
> - 使用 Power Query 创建新实体并使用数据填充它们。 详细信息：[使用 Power Query 将数据添加到 Common Data Service 中的实体](/powerapps/maker/common-data-service/data-platform-cds-newentity-pq)。
> - 开发人员可以使用[元数据服务](/powerapps/developer/common-data-service/use-web-services#metadata-services)编写程序。

## <a name="entity-options-not-available-in-the-power-apps-portal"></a>Power Apps 门户中不可用的实体选项

本主题中的信息将帮助您选择可以使用的设计器。 除非您需要满足下列要求中的任何一个，否则您可以使用 Power Apps 门户创建实体。

- 控制自定义项前缀

  您创建的任何自定义实体的名称中都包含自定义前缀。 这是根据您在其中工作的解决方案的解决方案发布商设置的。 如果您关心自定义前缀，请确保在非托管解决方案中工作，其中的自定义前缀是您需要的此实体的前缀。 详细信息[更改解决方案发布商前缀](change-solution-publisher-prefix.md)。

- 更改自定义实体的图标

  默认情况下，模型驱动应用程序中的所有自定义实体具有相同的图标。 您可以为自定义实体所需要的图标创建图像 Web 资源。 详细信息：[更改自定义实体的图标](../model-driven-apps/change-custom-entity-icons.md)。 

- 更改唯一可以启用的以下任何一种属性：

  [!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)]

- 更改以下任何一种属性：

  |选项   |说明  |
  |---------|---------|
  |**显示此实体的区域**|在 Web 应用程序中选择其中一个可用站点地图区域以显示此实体。 这不适用于模型驱动应用程序。|
  |**审核**|在为组织启用了审核后，将允许更改随时间获取的实体记录。 为实体启用审核后，也会对其所有字段启用审核。 可以选择或清除要对其启用审核的字段。|
  |**颜色**|在模型驱动应用程序中设置用于实体的颜色。|
  |**文档管理**|在执行了其他任务以启用组织文档管理后，启用此功能可以让此实体加入与 SharePoint 的集成。 |
  |**为移动设备启用**|使此实体对 Dynamics 365 for phones 和 Dynamics 365 for tablets 应用程序可用。 您还可以选择将此实体设为**在移动设备中为只读**。<br /><br /> 如果实体的窗体需要不被 Dynamics 365 for phones 和 Dynamics 365 for tablets 应用程序支持的扩展，请使用此设置确保移动应用程序用户不能编辑这些实体的数据。|
  |**针对 Phone Express 启用**|使此实体对 Dynamics 365 for phones 应用程序可用。|
  |**Dynamics 365 for Outlook 中的阅读窗格**|实体是否在 Dynamics 365 for Outlook 应用程序的阅读窗格中可见。|
  |**使用自定义帮助**|启用后，设置“帮助 URL”来控制用户单击应用程序中的帮助按钮后会看到的页面。 使用此设置来提供特定于您公司的实体流程的指导。|


### <a name="see-also"></a>另请参阅

[使用解决方案资源管理器创建和编辑实体](create-edit-entities-solution-explorer.md)<br />
[教程：在 Power Apps 中创建包含组件的自定义实体](/powerapps/maker/common-data-service/create-custom-entity)<br />
[编辑实体](edit-entities.md)<br />
[开发人员文档：创建自定义实体](/dynamics365/customer-engagement/developer/org-service/create-custom-entity)
