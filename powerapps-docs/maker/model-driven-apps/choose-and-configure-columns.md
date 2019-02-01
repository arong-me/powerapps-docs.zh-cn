---
title: 在 PowerApps 选择和配置模型驱动应用程序视图中的列 | MicrosoftDocs
description: 了解如何选择和配置您的应用的视图
keywords: ''
ms.date: 11/27/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: 31bfcf18-58c3-491c-91b5-f9b0f5424852
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 25
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="choose-and-configure-columns-in-model-driven-app-views"></a>选择和配置模型驱动应用程序视图中的列

<a name="BKMK_ChooseAndConfigureColumns"></a>   

 与筛选条件一样，在 PowerApps 视图中可见的列对于视图提供的值非常重要。 在本主题中，您通过执行以下任务创建或编辑视图：  

-   [打开视图编辑器](choose-and-configure-columns.md#open-the-view-editor)  
   
-   [添加列](choose-and-configure-columns.md#BKMK_AddColumns)  
  
-   [删除列](choose-and-configure-columns.md#BKMK_RemoveColumns)  
  
-   [更改列宽度](choose-and-configure-columns.md#BKMK_ChangeColumnWidth)  
  
-   [移动列](choose-and-configure-columns.md#BKMK_MoveAColumns)  
    
  > [!IMPORTANT]
  > 最新视图设计器版本现在正处于预览阶段。 尚不支持某些功能，如启用或禁用列显示和添加查找列。 若要完成这些任务，请[在经典视图设计器中打开视图](/dynamics365/customer-engagement/customize/create-and-edit-views#open-the-classic-view-designer)。
  >  -   [对列启用或禁用状态显示](/dynamics365/customer-engagement/customize/choose-and-configure-columns#BKMK_EnableOrDisablePresence)  
  >
  >  -   [添加查找列](choose-and-configure-columns.md#BKMK_AddFindColumns)  



### <a name="open-the-view-editor"></a>打开视图编辑器

1.  登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

2.  展开**数据**，选择**实体**，选择所需实体，然后选择**视图**选项卡。 

    > [!div class="mx-imgBorder"] 
    > ![视图](media/available-views.png)

3. 选择现有视图将其打开或在工具栏上选择**添加视图**。 

<a name="BKMK_AddColumns"></a>   
### <a name="add-columns"></a>添加列  
 您可以从当前实体或与当前实体具有 1:N 实体关系的任意相关实体中包含列。  
  
 例如，您可能希望在列中显示用户负责实体的负责人。 您可以选择当前实体的 **负责人** 字段以显示负责人的名称。 这将显示为链接来为身为负责人的人员打开 **用户** 记录。  
  
 如果要查看记录的负责人电话号码，那么您必须选择从 **记录类型** 下拉菜单中选择 **负责用户（用户）**，然后选择 **主要电话** 字段。  
  
#### <a name="add-columns-to-views"></a>将列添加到视图  
  
1.  编辑和创建视图时，请确保**字段**面板已打开。 如果未打开，请选择工具栏上的**添加字段**。 

    > [!div class="mx-imgBorder"] 
    > ![视图编辑器添加列](media/fields-drawer-view-designer.png)

2.  选择要添加到视图设计器的字段。 这将把字段作为列添加到视图右侧。

3.  选择**相关**选项卡可查看相关实体及其相应字段。
  
 因为您添加列，所以将增加视图的宽度。 如果视图宽度超过页面中显示它时可用的空间，水平滚动条将允许用户滚动和查看隐藏列。  
  
> [!TIP]
>  如果您的数据筛选视图针对特定字段，以便只显示具有某些值的记录，那么请勿在视图中包含该列。 例如，如果仅显示可用记录，那么请勿在视图中包含状态列。 相反，命名视图以指示视图显示的所有记录处于可用状态。  
  
> [!NOTE]
>  在添加列到针对更新实体的查找视图时，将仅显示前三列。  
  
<a name="BKMK_RemoveColumns"></a>   
### <a name="remove-columns"></a>删除列  
  
1.  选择要移除的列的标题。  
  
2.  在下拉列表中，选择**移除**。  
  
<a name="BKMK_ChangeColumnWidth"></a>   
### <a name="change-column-width"></a>更改列宽度  
  
1.  将鼠标光标悬停在视图中列之间的区域上方。  
  
2.  将显示一条线，而鼠标光标则变为双向箭头。  
  
3.  将列拖到适当宽度。  
  
<a name="BKMK_MoveAColumns"></a>   
### <a name="move-a-column"></a>移动列  
  
单击列标题并拖到正确位置。
  
> [!TIP]
>   也可以选择要移动的列的标题，然后从下拉列表选择**右移**或**左移**。  
  
## <a name="next-steps"></a>后续步骤
[创建或编辑视图](create-edit-views.md)
