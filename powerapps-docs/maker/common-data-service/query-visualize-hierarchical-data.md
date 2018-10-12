---
title: 使用 PowerApps 查询和可视化分层数据 | Microsoft Docs
description: 了解如何查询和可视化分层的相关数据
ms.custom: ''
ms.date: 06/20/2018
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
ms.openlocfilehash: ec45f43266c1920d05301c92bdd67838b40b7734
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667904"
---
# <a name="query-and-visualize-hierarchically-related-data"></a>查询和可视化分层相关数据

通过可视化分层相关数据，可获取有价值的业务见解。 分层建模和可视化功能为你提供了许多权益：  
  
-   查看和浏览复杂的分层信息。  
  
-   在层次结构的上下文视图中查看关键性能指标 (KPI)。  
  
-   直观地分析 Web 和平板电脑中的关键信息。  
  
对于某些实体（例如帐户和用户），可视化效果现成可用。 可为层次结构启用其他实体（包括自定义实体），并且可以为这些实体创建可视化效果。 可以根据需要选择使用显示整个层次结构的树状视图，或使用描绘层次结构较小部分的磁贴视图。 这两种视图并排显示。 可通过展开和收缩层次结构树来浏览层次结构。 可视化效果的相同分层设置只设置一次，但同时适用于 Web 客户端和移动客户端。 在平板电脑中，视觉对象以适合较小外形规格的修改过的格式呈现。 分层可视化效果所需的可自定义组件可识别解决方案，因此，它们可以像任何其他自定义项一样在组织之间传输。 可以使用窗体编辑器自定义快速窗体，以便配置可视化效果中所示的属性。 无需编写代码。  
  
<a name="BKMK_Querydata"></a>   
## <a name="query-hierarchical-data"></a>查询分层数据  
 通过 Common Data Service for Apps，相关记录的自引用一对多 (1:N) 关系支持分层数据结构。 过去，若要查看分层数据，必须以迭代方式查询相关记录。 目前，可一步查询作为层次结构的相关数据。 可使用 Under 和 Not Under 逻辑查询记录。 “高级查找”和工作流编辑器中公开了 Under 和 Not Under 分层运算符。 有关如何使用这些运算符的详细信息，请参阅[配置工作流步骤](/flow/configure-workflow-steps)。 有关高级查找的详细信息，请参阅[创建、编辑或保存高级查找搜索](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search)  
  
 以下示例介绍了查询层次结构的各种方案：  
  
 查询帐户层次结构  
  
 ![查询帐户层次结构中的帐户](media/query-accounts.png "Query accounts in the account hierarchy")  
  
 查询帐户层次结构，包括相关活动  
  
 ![查询帐户的相关活动](media/query-account-related-activities.png "Query account's related activities")  
  
 查询帐户层次结构，包括相关机会  
  
 ![查询帐户的相关机会](media/query-account-related-opportunities.png "Query account's related opportunities")  
  
 要将数据作为层次结构进行查询，必须将实体的某个一对多 (1:N) 自引用关系设置为分层关系。 启用层次结构：  
  
1.  打开[解决方案资源管理器](../model-driven-apps/advanced-navigation.md#solution-explorer)。 
  
2.  选择所需实体，选择“1:N 关系”，然后选择 (1:N) 关系。 

3.  在“关系定义”中，将“分层”设置为“是”。  
  
> [!NOTE]
> - 无法自定义某些现成的 (1:N) 关系。 这将阻止你将这些关系设置为分层关系。  
> - 可为系统自引用关系指定分层关系。 这包括系统类型的 1:N 自引用关系，例如“contact_master_contact”关系。  
  
<a name="BKMK_Visualizedata"></a>   
## <a name="visualize-hierarchical-data"></a>可视化分层数据  
 具有现成可用可视化效果的系统实体包括 `Account`、`Position`、`Product` 和 `User`。 在这些实体的网格视图中，可在记录名称左侧看到描绘层次结构图表的图标。 默认情况下，并非所有记录都显示层次结构图标。 具有父记录、子记录或父记录和子记录的记录会显示图标。  
  
 ![活动帐户](media/cust-hs-active-account.png "Active accounts")  
  
 如果选择层次结构图标，则可以查看层次结构，左侧是树状视图，右侧是磁贴视图，如下所示：  
  
 ![帐户树视图和磁贴视图](media/hierachy-security-accounts-tile-view.png "Account tree and tile view")  
  
 可为层次结构启用一些其他现成的系统实体。 这些实体包括 `Case`、`Contact`、`Opportunity`、`Order`、`Quote`、`Campaign` 和 `Team`。 可为层次结构启用所有自定义实体。  
  
> [!TIP]
>  如果可为层次结构启用实体：  
>  在解决方案资源管理器中，展开所需实体。 将看到名为“层次结构设置”的实体组件。 除 Dynamics 365 客户参与“销售区域”实体外，无法为层次结构启用的实体不具有此组件。 虽然“销售区域”实体显示“层次结构设置”，但无法为层次结构启用此实体。  
  
 创建可视化效果时要记住的重要事项：  
  
-   每个实体只能将一个 (1: N) 自引用关系设置为分层。 在此关系中，主实体和相关实体必须属于同一类型，例 account_parent_account 或 new_new_widget_new_widget。  
  
-   目前，层次结构或可视化效果仅基于一个实体。 可以描绘在多个级别显示帐户的帐户层次结构，但不能在同一层次结构可视化效果中显示帐户和联系人。  
  
-   可在磁贴中显示的最大字段数为 4。 如果向用于磁贴视图的“快速窗体”添加更多字段，则仅显示前四个字段。  
  
### <a name="visualization-example"></a>可视化效果示例  
 我们来看一个为自定义实体创建可视化效果的示例。 我们创建了一个名为 new_Widget 的自定义实体，创建了一个 (1:N) 自引用关系 new_new_widget_new_widget，并将其标记为分层，如下所示。  
  
 ![小组件关系定义](media/widget-relationship-definition.png "Widget relationship definition")  
  
 接下来，在“层次结构设置”网格视图中，我们选择了 new_new_widget_new_widget 分层关系。 在窗体中，我们填写了必填字段。 如果尚未将 (1:N) 关系标记为分层，则通过窗体上的链接可返回到关系定义窗体，可在该窗体中将关系标记为分层。  
  
 对于“快速视图窗体”，我们创建了一个名为“小组件层次结构磁贴窗体”的快速窗体。 在此窗体中，我们在每个磁贴中添加了四个要显示的字段。  
  
 ![创建小组件的快速窗体](media/create-quickf-orm.png "Create quick form for widget")  
  
 完成设置后，我们创建了两条记录：标准小组件和高级小组件。 使用查找字段使高级小组件成为标准小组件的父级后，new_Widget 网格视图描绘了层次结构图标，如下所示：  
  
 ![小组件的层次结构网格](media/widget-hierarchy-grid.png "Widget's hierarchy grid")  
  
> [!TIP]
>  在父-子关系中对记录进行配对之前，层次结构图标不会显示在记录网格视图中。  
  
 选择层次结构图标将显示 new_Widget 层次结构，左侧为树视图，右侧为磁贴视图，并且显示两条记录。 每个磁贴均包含我们在“小组件层次结构磁贴窗体”中提供的四个字段。  
  
 ![小组件的树视图和磁贴视图](media/widget-tree-tiles.png "Widget's tree and tiles views")  
  
## <a name="see-also"></a>另请参阅  
 [视频：分层安全建模](http://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)   
 [视频：层次结构可视化效果](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
