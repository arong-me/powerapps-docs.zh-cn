---
title: 使用 Common Data Service 定义和查询分层数据 | MicrosoftDocs
description: 了解如何定义和按层次结构查询相关数据
ms.custom: ''
ms.date: 06/02/2018
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
ms.assetid: 0cf62817-5ff5-40bb-ad17-e1f6b0921720
caps.latest.revision: 42
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c829665baf2688c755bdfba7debb19d7b69a1c46
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758664"
---
# <a name="define-and-query-hierarchically-related-data"></a>定义和按层次结构查询相关数据

可以通过按层次结构定义和查询相关数据获得有价值的业务见解。 分层建模和可视化功能提供了许多好处：  
  
- 显示和浏览复杂的分层信息。  
- 在层次结构的上下文视图中查看关键性能指标 (KPI)。  
- 以直观方式在 Web 和平板电脑中分析重要的信息。  
  
有些标准实体已经定义了层次结构。 可为层次结构启用其他实体，包括自定义实体，并且您可以为其创建可视化项。 

## <a name="define-hierarchical-data"></a>定义分层数据

使用 Common Data Service，分层数据结构支持相关记录的*自我参照*的一对多 (1:N) 关系。 

> [!NOTE]
> *自我参照*意味着实体与其自身相关。 例如，客户实体具有将其与其他客户实体记录关联的查找字段。

当自我参照一对多 (1:N) 关系存在时，在关系定义中，**分层**选项可以设置为**是**。

![关系定义中的分层设置](media/self-referential-relationship-car-solution-explorer.png)

若要按层次结构查询数据，您必须将实体的一对多 (1:N) 自我参照关系设置为分层。 这只能使用解决方案资源管理器执行。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

要打开层次结构：  
  
1. 在[查看 1:N 关系](create-edit-1n-relationships-solution-explorer.md#view-entity-relationships)时，选择要编辑的自我参照关系。
2. 在**关系定义**中，将**分层**设置为**是**。  
  
> [!NOTE]
> - 一些现成的 (1:N) 关系是不能自定义的。 这使您无法将这些关系设置为分层形式。  
> - 您可以为系统自引用关系指定一个分层关系。 这包括系统类型的 1:N 自引用关系，例如“contact_master_contact”关系。  

> [!IMPORTANT]
> 您可以有多个自我参照关系，但每个实体只有一个关系可以定义为分层关系。 如果您在应用后尝试更改设置，您将收到警告：
>
> - **禁用时：** 如果您关闭此关系的层次结构设置，则使用此层次结构的所有汇总定义、流程和视图都将无法工作。 是否继续？ 
> - **禁用时：** 如果您启用此关系的层次结构设置，则使用现有层次结构的所有汇总定义都将变为无效。 是否继续？
>
> 除非您确定现有层次结构中没有其他依赖项，否则您应该查看有关部署的任何文档，或与其他定制员协商以了解如何在继续前使用现有的分层关系。

<a name="BKMK_Querydata"></a> 
  
## <a name="query-hierarchical-data"></a>查询分层数据  

如果没有已定义的层次结构，要检索分层数据，需要迭代查询相关记录。 如果有已定义的层次结构，只需一个步骤就可以按层次结构查询相关数据。 您可以使用 **Under** 和 **Not Under** 逻辑查询记录。 **Under**和**Not Under**分层操作符在“高级查找”和工作流编辑中显示。 有关如何使用这些运算符的详细信息，请参阅[配置工作流步骤](/flow/configure-workflow-steps#setting-conditions-for-workflow-actions)。 有关高级查找的更多信息，请查看[创建、编辑或保存高级查找搜索](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search)  

> [!NOTE]
> 开发人员还可以在代码中使用这些运算符。 详细信息[开发人员文档：查询分层数据](/dynamics365/customer-engagement/developer/org-service/query-hierarchical-data)
  
以下示例说明查询层次结构的方案：  
  
### <a name="query-account-hierarchy"></a>查询帐户层次结构  
  
![在客户层次结构中查询客户](media/query-accounts.png)  
  
### <a name="query-account-hierarchy-including-related-activities"></a>查询帐户层次结构，包括相关活动  
  
![查询客户的相关活动](media/query-account-related-activities.png)  
  
###  <a name="query-account-hierarchy-including-related-opportunities"></a>查询帐户层次结构，包括相关商机  
  
![查询客户的相关商机](media/query-account-related-opportunities.png)  
  
## <a name="see-also"></a>另请参阅 
[创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships.md)<br />
[使用解决方案资源管理器创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships-solution-explorer.md)<br />
[使用模型驱动应用程序可视化分层数据](visualize-hierarchical-data.md)<br />
[视频：分层安全建模](https://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)<br />
[视频：层次结构可视化](https://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
