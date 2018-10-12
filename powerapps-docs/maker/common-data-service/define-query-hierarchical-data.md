---
title: 使用 Common Data Service for Apps 定义和查询分层数据 | Microsoft Docs
description: 了解如何定义和查询按层次结构相关的数据
ms.custom: ''
ms.date: 06/02/2018
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
ms.assetid: 0cf62817-5ff5-40bb-ad17-e1f6b0921720
caps.latest.revision: 42
ms.author: matp
manager: kvivek
ms.openlocfilehash: 4dad7da635156350d104d68108ac4acfbb991862
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667791"
---
# <a name="define-and-query-hierarchically-related-data"></a>定义和查询按层次结构相关的数据

通过定义和查询按层次结构相关的数据，可获取有价值的业务见解。 分层建模和可视化功能为你提供了许多权益：  
  
- 查看和浏览复杂的分层信息。  
- 在层次结构的上下文视图中查看关键性能指标 (KPI)。  
- 直观地分析 Web 和平板电脑中的关键信息。  
  
某些标准实体已定义了层次结构。 可为层次结构启用其他实体（包括自定义实体），并且可以为这些实体创建可视化效果。 

## <a name="define-hierarchical-data"></a>定义分层数据

通过 Common Data Service for Apps，相关记录的自引用一对多 (1:N) 关系支持分层数据结构。 

> [!NOTE]
> 自引用意味着实体与其自身相关。 例如，帐户实体具有将其与另一个帐户实体记录相关联的查找字段。

存在自引用一对多 (1:N) 关系时，关系定义中的“分层”选项可设置为“是”。

![关系定义中的分层设置](media/self-referential-relationship-car-solution-explorer.png)

要将数据作为层次结构进行查询，必须将实体的某个一对多 (1:N) 自引用关系设置为分层关系。 只能使用解决方案资源管理器执行此设置。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

启用层次结构：  
  
1. [查看 1:N 关系](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships)时，选择要编辑的自引用关系。
2. 在“关系定义”中，将“分层”设置为“是”。  
  
> [!NOTE]
> - 无法自定义某些现成的 (1:N) 关系。 这将阻止你将这些关系设置为分层关系。  
> - 可为系统自引用关系指定分层关系。 这包括系统类型的 1:N 自引用关系，例如“contact_master_contact”关系。  

> [!IMPORTANT]
> 可拥有多个自引用关系，但每个实体只能将一个关系定义为分层关系。 如果应用后尝试更改设置，则会收到警告：
>
> - **禁用时：** 如果关闭此关系的层次结构设置，则使用此层次结构的所有汇总定义、流程和视图都将不起作用。 是否继续？ 
> - **启用时：** 如果启用此关系的层次结构设置，则使用现有层次结构的所有汇总定义都将无效。 是否继续？
>
> 除非你确定现有层次结构上没有其他依赖项，否则在继续之前，应查看有关部署的任何文档或与其他定制员协商，以了解现有分层关系的用法。

<a name="BKMK_Querydata"></a> 
  
## <a name="query-hierarchical-data"></a>查询分层数据  

如果没有定义的层次结构，要检索分层数据，需要以迭代方式查询相关记录。 而如果有定义的层次结构，一步即可查询一个层次结构的相关数据。 你可以使用 Under 和 Not Under 逻辑查询记录。 “高级查找”和工作流编辑器中公开了 Under 和 Not Under 分层运算符。 有关如何使用这些运算符的详细信息，请参阅[配置工作流步骤](/flow/configure-workflow-steps#setting-conditions-for-workflow-actions)。 有关高级查找的详细信息，请参阅[创建、编辑或保存高级查找搜索](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search)  

> [!NOTE]
> 开发人员还可在代码中使用这些运算符。 详细信息：[开发人员文档：查询分层数据](/dynamics365/customer-engagement/developer/org-service/query-hierarchical-data)
  
以下示例说明了查询层次结构的方案：  
  
### <a name="query-account-hierarchy"></a>查询帐户层次结构  
  
![查询帐户层次结构中的帐户](media/query-accounts.png)  
  
### <a name="query-account-hierarchy-including-related-activities"></a>查询帐户层次结构，包括相关活动  
  
![查询帐户的相关活动](media/query-account-related-activities.png)  
  
###  <a name="query-account-hierarchy-including-related-opportunities"></a>查询帐户层次结构，包括相关机会  
  
![查询帐户的相关商机](media/query-account-related-opportunities.png)  
  
## <a name="see-also"></a>另请参阅 
[创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships.md)<br />
[使用解决方案资源管理器创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships-solution-explorer.md)<br />
[使用模型驱动应用可视化分层数据](visualize-hierarchical-data.md)<br />
[视频：分层安全建模](http://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)<br />
[视频：层次结构可视化效果](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
