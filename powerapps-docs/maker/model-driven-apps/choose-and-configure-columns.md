---
title: 在 PowerApps 选择和配置模型驱动应用程序视图中的列 | MicrosoftDocs
description: 了解如何选择和配置您的应用的视图
keywords: ''
ms.date: 06/11/2018
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

# <a name="tutorial-choose-and-configure-columns-in-model-driven-app-views"></a>教程：选择和配置模型驱动应用程序视图中的列

<a name="BKMK_ChooseAndConfigureColumns"></a>   

 与筛选条件一样，在 PowerApps 视图中可见的列对于视图提供的值非常重要。 在本教程中，您通过执行以下任务创建或编辑视图：  

-   [打开视图编辑器](choose-and-configure-columns.md#open-the-view-editor)  
   
-   [添加列](choose-and-configure-columns.md#BKMK_AddColumns)  
  
-   [删除列](choose-and-configure-columns.md#BKMK_RemoveColumns)  
  
-   [更改列宽度](choose-and-configure-columns.md#BKMK_ChangeColumnWidth)  
  
-   [移动列](choose-and-configure-columns.md#BKMK_MoveAColumns)  
  
-   [对列启用或禁用状态显示](choose-and-configure-columns.md#BKMK_EnableOrDisablePresence)  
  
-   [添加查找列](choose-and-configure-columns.md#BKMK_AddFindColumns)  

### <a name="open-the-view-editor"></a>打开视图编辑器

1.  在 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 站点，选择**模型驱动**（导航窗格的右下方）。  

    ![模型驱动设计模式](../model-driven-apps/media/model-driven-switch.png)

2.  展开**数据**，选择**实体**，选择所需实体，然后选择**视图**选项卡。 

    > [!div class="mx-imgBorder"] 
    > ![视图](media/available-views.png)

3. 选择现有视图将其打开或在工具栏上选择**添加视图**。 

<a name="BKMK_AddColumns"></a>   
### <a name="add-columns"></a>添加列  
 您可以从当前实体或与当前实体具有 1:N 实体关系的任意相关实体中包含列。  
  
 例如，您可能希望在列中显示用户负责实体的负责人。 您可以选择当前实体的 **负责人** 字段以显示负责人的名称。 这将显示为链接来为身为负责人的人员打开 **用户** 记录。 在这种情况下，也可以选择[启用或禁用列的状态](choose-and-configure-columns.md#BKMK_EnableOrDisablePresence)。  
  
 如果要查看记录的负责人电话号码，那么您必须选择从 **记录类型** 下拉菜单中选择 **负责用户（用户）**，然后选择 **主要电话** 字段。  
  
#### <a name="add-columns-to-views"></a>将列添加到视图  
  
1.  当创建和编辑视图时，选择**添加列**。 

    > [!div class="mx-imgBorder"] 
    > ![视图编辑器添加列](media/view-editor.png)

    此时会显示**添加列**对话框。

    > [!div class="mx-imgBorder"] 
    > ![添加列](media/add-columns.png)
  
2.  如果要包含来自相关实体的字段，请选择**记录类型**。  
  
3.  您可以选择多个字段，即使是从相关实体中选择。  
  
4.  在选择所需的字段时，请选择**确定**以关闭**添加列**对话框。  
  
 因为您添加列，所以将增加视图的宽度。 如果视图宽度超过页面中显示它时可用的空间，水平滚动条将允许用户滚动和查看隐藏列。  
  
> [!TIP]
>  如果您的数据筛选视图针对特定字段，以便只显示具有某些值的记录，那么请勿在视图中包含该列。 例如，如果仅显示可用记录，那么请勿在视图中包含状态列。 相反，命名视图以指示视图显示的所有记录处于可用状态。  
  
> [!NOTE]
>  在添加列到针对更新实体的查找视图时，将仅显示前三列。  
  
<a name="BKMK_RemoveColumns"></a>   
### <a name="remove-columns"></a>删除列  
  
1.  创建和编辑视图时，选择要移除的列。  
  
2.  在**常规任务**区域中，选择**移除**。  
  
3.  在确认消息中，选择**确定**。  
  
<a name="BKMK_ChangeColumnWidth"></a>   
### <a name="change-column-width"></a>更改列宽度  
  
1.  创建和编辑视图时，选择要更改的列。  
  
2.  在**常规任务**区域中，选择**更改属性**。  
  
3.  在**更改列属性**对话框中，选择一个选项以设置列宽，然后选择**确定**。  
  
<a name="BKMK_MoveAColumns"></a>   
### <a name="move-a-column"></a>移动列  
  
1.  创建和编辑视图时，选择要移动的列。  
  
2.  在**常规任务**区域中，使用箭头向左或向右移动该列。  
  
<a name="BKMK_EnableOrDisablePresence"></a>   
### <a name="enable-or-disable-presence-for-a-column"></a>对列启用或禁用状态显示  
 满足以下条件时，用户可以在列表中看到 Skype for Business 联机状态控件，该控件显示用户是否有空，并允许用户通过即时消息与其交互：  
  
-   用户使用 Edge 或 Internet Explorer。  
  
-   用户已安装 Skype for Business。  
  
-   用户在 Internet Explorer 中启用 Microsoft ActiveX。  
  
-   您的组织在系统设置中已启用系统的状态。  
  
 状态控制和启用设置仅可用于针对启用电子邮件的实体（用户、联系人、商机、潜在顾客或自定义实体）显示主字段的列。  
  
#### <a name="enable-or-disable-skype-for-business-presence-for-a-column"></a>对列启用或禁用 Skype for Business 状态  
  
1.  创建和编辑视图时，选择要更改的列。  
  
2.  在**常规任务**区域中，选择**更改属性**。  
  
3.  在**更改列属性**对话框中，选择或删除**启用此列的状态显示**，然后选择**确定**。  
  
<a name="BKMK_AddFindColumns"></a>   
### <a name="add-find-columns"></a>添加查找列  
 查找列是应用程序用户在搜索的列，当用户使用列表中显示的**搜索记录** 文本框或者在应用程序中任何时间能够对实体的记录进行搜索，例如，用户搜索查找字段的某个记录。  
  
1.  打开**快速查找**视图。 有关快速查找视图的信息，请参阅[视图类型](create-edit-views.md#types-of-views)。  
  
2.  选择**添加查找列**以打开对话框。  
  
3.  选择包含要搜索的字段。  
  
4.  选择**确定**以关闭**添加查找列**对话框。  

## <a name="community-tools"></a>社区工具

**View Layout Replicator** 和**视图设计器**是 XrmToolbox 社区提供并为 Dynamics 365 customer engagement 开发的工具。 请参阅[开发人员工具](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools)主题以获取社区开发的工具。

> [!NOTE]
> 这些社区工具不是 Microsoft Dynamics 的产品，因此不能将支持延伸到这些社区工具。 如果有与该工具相关的疑问，请联系发布者。 详细信息：[XrmToolBox](https://www.xrmtoolbox.com)。 

## <a name="next-steps"></a>后续步骤
[创建或编辑视图](create-edit-views.md)
