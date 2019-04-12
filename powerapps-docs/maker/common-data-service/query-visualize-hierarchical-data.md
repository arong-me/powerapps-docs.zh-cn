---
title: 使用 PowerApps 查询和可视化分层数据 | MicrosoftDocs
description: 了解如何查询和可视化相关的分层数据
ms.custom: ''
ms.date: 06/20/2018
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
---
# <a name="query-and-visualize-hierarchically-related-data"></a>查询和按层次结构可视化相关数据

可以通过按层次结构可视化相关数据获得有价值的业务见解。 分层建模和可视化功能提供了许多好处：  
  
-   显示和浏览复杂的分层信息。  
  
-   在层次结构的上下文视图中查看关键性能指标 (KPI)。  
  
-   以直观方式在 Web 和平板电脑中分析重要的信息。  
  
对于某些实体，例如帐户和用户，提供现成的可视化项。 可为层次结构启用其他实体，包括自定义实体，并且您可以为其创建可视化项。 基于需要，用户可以在树状视图（显示整个层次结构）或磁贴视图（层次结构的较小部分的详细视图）之间选择。 两种视图并排显示。 可以通过展开和收缩层次结构树来浏览层次结构。 同样的可视化项分层设置只需设置一次，但可同时应用于 Web 和移动客户端。 在平板电脑中，可视化对象采用适合更小外形规格的修改格式来显示。 层次结构可视化所需的可自定义组件是可以识别解决方案的，因此像其他自定义一样，可以在组织之间进行传输。 您可以通过使用表单编辑器自定义快速窗体，来配置可视化项中所显示的属性。 不需要编写代码。  
  
<a name="BKMK_Querydata"></a>   
## <a name="query-hierarchical-data"></a>查询分层数据  
 使用 Common Data Service，分层数据结构支持相关记录的自我参照的一对多 (1:N) 关系。 以前，要想查看分层数据，必须对相关记录进行迭代查询。 现在，只需一个步骤就可以按层次结构查询相关数据。 您将可以使用**Under**和**Not Under**逻辑查询记录。 **Under**和**Not Under**分层操作符在“高级查找”和工作流编辑中显示。 有关如何使用这些运算符的详细信息，请参阅[配置工作流步骤](/flow/configure-workflow-steps)。 有关高级查找的更多信息，请查看[创建、编辑或保存高级查找搜索](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search)  
  
 以下示例说明查询层次结构的不同方案：  
  
 查询帐户层次结构  
  
 ![查询客户层次结构中的客户](media/query-accounts.png "查询客户层次结构中的客户")  
  
 查询帐户层次结构，包括相关活动  
  
 ![查询客户的相关活动](media/query-account-related-activities.png "查询客户的相关活动")  
  
 查询帐户层次结构，包括相关商机  
  
 ![查询客户的相关商机](media/query-account-related-opportunities.png "查询客户的相关商机")  
  
 若要按层次结构查询数据，您必须将实体的一对多 (1:N) 自我参照关系设置为分层。 要打开层次结构：  
  
1.  打开[解决方案资源管理器](../model-driven-apps/advanced-navigation.md#solution-explorer)。 
  
2.  选择所需实体，选择 **1:N 关系**，然后选择 (1:N) 关系。 

3.  在**关系定义**中，将**分层**设置为**是**。  
  
> [!NOTE]
> - 一些现成的 (1:N) 关系是不能自定义的。 这使您无法将这些关系设置为分层形式。  
> - 您可以为系统自引用关系指定一个分层关系。 这包括系统类型的 1:N 自引用关系，例如“contact_master_contact”关系。  
  
<a name="BKMK_Visualizedata"></a>   
## <a name="visualize-hierarchical-data"></a>可视化分层数据  
 可视化系统实体包括`Account`、`Position`、`Product`和`User`。 在这些实体的网格视图中，您可以看到描述层次结构图的图标，左边是记录名称。 在默认情况下，不是所有的记录都显示层次结构图标。 图标显示的是有一个父记录、一个子记录或两个都有的记录。  
 
 > [!div class="mx-imgBorder"] 
 > ![可用客户](media/cust-hs-active-account.png "可用客户")  
  
 若您选择了层次结构图标，您可以查看层次结构，左边是树状视图，右边是磁贴视图，如下所示：  
  
> [!div class="mx-imgBorder"] 
> ![帐户树和磁贴视图](media/hierachy-security-accounts-tile-view.png "帐户树和磁贴视图")  
  
 可为层次结构启用其他一些现有的系统实体。 这些实体包括`Case`、`Contact`、`Opportunity`、`Order`、`Quote`、`Campaign`和`Team`。 可以为层次结构启用所有自定义实体。  
  
> [!TIP]
>  如果可以为层次结构启用实体：  
>  在解决方案资源管理器中，展开您所需的实体。 您会看到称为**层次结构设置**的实体组件。 无法为层次结构启用的实体不具有此组件，Dynamics 365 customer engagement 销售区域实体除外。 尽管**层次结构设置**为销售区域实体显示，但不能为层次结构启用实体。  
  
 创建可视化项时切记：  
  
-   每个实体中，只能将一个 (1:N) 自引用关系设置为层次结构形式。 在此关系中，主要实体和相关实体必须类型相同，比如 account_parent_account 或 new_new_widget_new_widget。  
  
-   当前，层次结构或可视化项只基于一个实体。 您可以描述客户层次结构以多层次显示客户，但是您不能在相同层次结构可视化中显示客户和联系人。  
  
-   磁贴中可显示至多 4 个字段数量。 如果您向用于磁贴视图的快速窗体添加更多字段，则只能显示前四个字段。  
  
### <a name="visualization-example"></a>可视化示例  
 请看为自定义实体创建可视化的示例。 我们创建了名为 new_Widget 的自定义实体，创建了一个 (1:N) 自引用关系 **new_new_widget_new_widget** 并将其标记为层次结构，如此处所示。  
  
 ![小组件关系定义](media/widget-relationship-definition.png "小组件关系定义")  
  
 下一步，在**层次结构设置**网格视图中，我们选择了**new_new_widget_new_widget**层次关系。 在表单中，我们填充了所需字段。 如果您尚未将 (1:N) 关系标记为分层，表单的链接可返回到关系定义表单，您就可以将该关系标记为分层的了。  
  
 对于**快速窗体视图**，我们创建名为**Widget 层次结构磁贴窗体**的快速窗体。 在此窗体中，我们在每个磁贴中添加了四个显示字段。  
  
> [!div class="mx-imgBorder"] 
> ![为小组件创建快速窗体](media/create-quickf-orm.png "为小组件创建快速窗体")  
  
 我们完成设置后，创建了两个记录：Standard Widget 和 Premium Widget。 通过查找字段使优质部件成为标准部件的父项后，new_Widget 网格视图描述了层次结构图标，如下所示：  
  
> [!div class="mx-imgBorder"] 
> ![小组件的层次结构网格](media/widget-hierarchy-grid.png "小组件的层次结构网格")  
  
> [!TIP]
>  在记录被配对为父 – 子关系之前，分层结构图标是不会在记录网格视图中显示的。  
  
 选择分层结构图标会显示 new_Widget 分层结构，左边为树状视图，右边为磁贴视图，显示两个记录。 每个磁贴包含我们在**部件层次结构磁贴窗体**中提供的四个字段。  
 
 > [!div class="mx-imgBorder"] 
 > ![小组件的树和磁贴视图](media/widget-tree-tiles.png "小组件的树和磁贴视图")  
  
## <a name="see-also"></a>另请参阅  
 [视频： 中的层次结构安全建模](http://www.youtube.com/watch?v=kx5So32DrCo&index=10&list=PLC3591A8FE4ADBE07)   
 [视频：层次结构可视化](http://www.youtube.com/watch?v=_dGBE6icLNw&index=9&list=PLC3591A8FE4ADBE07)
