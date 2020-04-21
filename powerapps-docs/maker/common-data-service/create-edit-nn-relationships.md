---
title: 在 Common Data Service 中创建多对多实体关系概述 | MicrosoftDocs
description: 了解如何创建多或多实体关系
ms.custom: ''
ms.date: 04/07/2020
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
ms.assetid: 248cecfd-c9e8-430b-b4b0-860669866084
caps.latest.revision: 33
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5f5c0f78f94ae2ec452bcbf6f5d677723d5ede52
ms.sourcegitcommit: 6acc6ac7cc1749e9681d5e55c96613033835d294
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2020
ms.locfileid: "3238270"
---
# <a name="create-many-to-many-entity-relationships-overview"></a>创建多对多实体关系概述

一对多 (1:N) 实体关系确立记录之间的层次结构。 对于多对多 (N:N) 关系，没有明确的层次结构。 没有要配置的查找字段或行为。 可以将使用多对多关系创建的记录视为对等的，并且关系是相互的。  

多对多关系的示例在 Dynamics 365 Sales 应用附带的两个标准实体之间定义。 “商机”实体与“竞争对手”实体有 N:N 关系。 这允许将多个竞争对手添加到商机中，并将多个商机与同一竞争对手相关联。 
  
使用多对多关系，关系（或相交）实体存储关联实体的数据。 此实体与两个相关实体都有一对多实体关系，并且仅存储定义关系的必要值。 您无法将自定义字段添加到关系实体，并永远不会显示在用户界面中。 
  
创建多对多关系需要选择两个您希望参与关系的实体。 对于模型驱动应用程序，您可以决定您希望各个列表分别在每个实体的导航内如何提供。 这些选项与用于 1:N 实体关系中的主要实体的选项相同。 详细信息：[主要实体的导航窗格项](create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)
  
并非所有实体可用于多对多关系。 如果实体在设计器中不可以选择，则无法在此实体中创建新的多对多关系。 详细信息：[开发人员文档：实体关系资格](https://docs.microsoft.com/dynamics365/customer-engagement/developer/entity-relationship-eligibility)

有两个设计器您可以用来创建和编辑 1:N（一对多）或 N:1（多对一）关系：

|设计器| 说明|
|--|--|
|[Power Apps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|提供简单的简化体验，但是有些特殊设置不可用。<br />详细信息：[使用 Power Apps 门户在 Common Data Service 中创建多对多实体关系](create-edit-nn-relationships-portal.md)|
|解决方案资源管理器|不那么简单，但提供更多灵活性可减少常见要求。<br />详细信息：[使用解决方案资源管理器在 Common Data Service 中创建 N:N（多对多）实体关系](create-edit-nn-relationships-solution-explorer.md) |

> [!NOTE]
> 您还可以使用以下方法在您的环境中创建新的多对多 (N:N) 实体关系：
> - 导入包含关系定义的解决方案。 详细信息：[导入、更新和导出解决方案](import-update-export-solutions.md)
> - 开发人员可以使用[元数据服务](../../developer/common-data-service/metadata-services.md)编写程序来创建和更新实体关系。 详细信息：[开发人员文档：自定义实体关系元数据](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)

本主题中的信息将帮助您选择可以使用的设计器。 

您应该使用 Power Apps 门户创建和编辑多对多 (N:N) 实体关系，除非您需要满足任何下列要求：

- 配置模型驱动应用程序的导航窗格选项。
- 从模型驱动应用程序中的“高级查找”中隐藏关系。

## <a name="see-also"></a>另请参阅

[创建和编辑实体之间的关系](create-edit-entity-relationships.md)<br />
[使用 Power Apps 门户在 Common Data Service 中创建多对多实体关系](create-edit-nn-relationships-portal.md)<br />
[使用解决方案资源管理器在 Common Data Service 中创建 N:N（多对多）实体关系](create-edit-nn-relationships-solution-explorer.md)<br />
[开发人员文档：自定义实体关系元数据](https://docs.microsoft.com/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)<br />
[开发人员文档：实体关系资格](https://docs.microsoft.com/dynamics365/customer-engagement/developer/entity-relationship-eligibility)
