---
title: '在 PowerApps 中创建 1:N（一对多）或 N:1（多对一）实体关系概述 | MicrosoftDocs'
description: 了解如何创建一对多或多对一实体关系
ms.custom: ''
ms.date: 05/27/2018
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
ms.assetid: 52c00707-b2bc-4950-abec-89baefd94f6e
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-one-to-many-or-many-to-one-entity-relationships-overview"></a>创建一对多或多对一实体关系概述

在 Common Data Service 中，1:N（一对多）或 N:1（多对一）关系定义两个实体如何相互关联。 
  
在创建自定义实体关系之前，应评估使用现有实体关系是否满足您的要求。 <br />详细信息：[新建元数据或使用现有元数据？](create-edit-metadata.md#create-new-metadata-or-use-existing-metadata)

有两个设计器您可以用来创建和编辑 1:N（一对多）或 N:1（多对一）关系：

|设计器| 说明|
|--|--|
|[PowerApps 门户](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|提供简单的简化体验，但是有些特殊设置不可用。<br />详细信息：[在 PowerApps 门户中创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships-portal.md)|
|解决方案资源管理器|不那么简单，但提供更多灵活性可减少常见要求。 <br />详细信息：[使用解决方案资源管理器创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships-solution-explorer.md) |

> [!NOTE]
> 您还可以使用以下方法在您的环境中创建新实体关系：
> - 在模型驱动应用程序中，从窗体编辑器选择**新建字段**，然后创建*查找*字段。 <br />详细信息：[将字段添加到窗体](../model-driven-apps/add-field-form.md)
> - 为相关实体创建新查找字段。 <br />详细信息：[创建和编辑字段](create-edit-fields.md)
> - 导入包含实体关系定义的解决方案。 <br />详细信息：[导入、更新和导出解决方案](import-update-export-solutions.md)
> - 使用 Power Query 创建新实体并使用数据填充它们。 <br />详细信息：[使用 Power Query 将数据添加到 Common Data Service 中的实体](data-platform-cds-newentity-pq.md)。
> - 开发人员可以使用[元数据服务](../../developer/common-data-service/metadata-services.md)编写程序来创建和更新实体关系。 <br />详细信息：[自定义实体关系元数据](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)。

本主题中的信息将帮助您选择可以使用的设计器。 

您应该使用 PowerApps 门户创建和编辑 1:N（一对多）或 N:1（多对一）实体关系，除非您需要满足任何下列要求：

- 配置字段映射
- 配置模型驱动应用程序的导航窗格选项
- 配置关系行为
- 定义关系是否在高级查找中隐藏。
- 建立分层关系


## <a name="community-tools"></a>社区工具

**[实体关系示意图创建器](https://www.xrmtoolbox.com/plugins/JourneyIntoCRM.XrmToolbox.ERDPlugin/)** 是 XrmToolbox 社区为 Common Data Service 开发的工具。 请参阅 [Common Data Service 的开发工具](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools)主题了解更多社区开发的工具。

> [!NOTE]
> 这些社区工具不是 Microsoft 的产品，因此不能将支持延伸到这些社区工具。 如果有与该工具相关的疑问，请联系发布者。 详细信息：[XrmToolBox](https://www.xrmtoolbox.com)。

### <a name="see-also"></a>另请参阅

[创建和编辑实体之间的关系](create-edit-entity-relationships.md)<br />
[在 PowerApps 门户中创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships-portal.md)<br />
[使用解决方案资源管理器创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships-solution-explorer.md)<br />
[开发人员文档：自定义实体关系元数据](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)<br />
[开发人员文档：实体关系资格](/dynamics365/customer-engagement/developer/entity-relationship-eligibility)


