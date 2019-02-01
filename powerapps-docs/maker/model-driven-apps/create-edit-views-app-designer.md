---
title: 通过 PowerApps 创建和编辑模型驱动应用程序的公共视图或系统视图 | MicrosoftDocs
description: 立即了解如何使用应用程序设计器创建或编辑视图
keywords: ''
ms.date: 11/27/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 666ab3f3-abda-468c-b248-3a0b410286b0
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 1
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-and-edit-public-or-system-model-driven-app-views"></a>创建和编辑模型驱动应用程序的公共视图或系统视图

在本主题中，您执行使用视图所需的多个任务，如创建公共视图，将现有视图添加到应用程序，以及更改视图的列、筛选器和排序顺序。

在 PowerApps 中，视图定义如何显示特定实体的记录。 视图定义以下事项：
-  要显示的列（属性）
-  列的宽度
-  默认如何为记录排序
-  默认应用哪些筛选器确定哪些记录显示在列表中

视图通常分为三类：
- **个人：** 单个用户可根据自己的个人要求创建个人视图。 只有创建者和创建者选择与其共享的任何人才能查看这些视图。 
- **公共：** 作为应用制造者，您可根据组织需求创建和编辑公共视图。 这些视图在视图选择器中可用，并且您在窗体的子网格中可以使用它们或在仪表板上作为列表。
- **系统：** 作为应用制造者，您还可以修改系统视图以满足组织的需求。 这些视图是应用程序依赖的特殊视图：它们为系统实体而存在或在您创建自定义实体时自动创建。 这些视图可供部分或全部用户使用，具体取决于用户的权限。

详细信息：[了解视图](create-edit-views.md)

## <a name="create-a-public-view-in-powerapps"></a>在 PowerApps 中创建公共视图
作为应用制造者，您可使用 PowerApps 创建和编辑公共视图。
1. 登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  


    > [!IMPORTANT]
    > “如果**模型驱动**的设计模式不可用，您可能需要[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)。   
  
2.  展开**数据**，选择**实体**，选择所需实体，然后选择**视图**选项卡。 

3. 在工具栏上，选择**添加视图**。 

4. 在**创建视图**对话框中，输入名称和描述（可选），然后选择**创建**。 
    
5. 在视图设计器中，选择加号按钮添加您要在视图中显示的其他列。 详细信息：[向视图中添加列](#add-a-column-to-your-view)

   ![添加列](../common-data-service/media/add-column-to-view.png)

6. 在视图设计器中，可以执行以下任务： 
   - 若要更改列筛选，请选择要筛选的列的标题，然后在下拉列表中选择**筛选条件**。
   - 若要更改列排序，请选择要筛选的列的标题，然后选择**从 A 到 Z 排序**或**从 Z 到 A 排序**。
   - 通过单击列并拖到所需位置配置列宽。
   - 通过将列拖到要将其移到的位置来为列重新排序。 

    > [!NOTE]
    > 也可以通过单击列标题，然后选择**右移**或**左移**来更改列顺序。

10. 选择**发布**保存视图并提供给组织中的其他用户。 
   

## <a name="work-with-views-in-app-designer"></a>在应用程序设计器中处理视图
以下部分说明如何在应用程序设计器中创建和编辑视图。

### <a name="open-and-add-a-view-in-the-app-designer"></a>在应用程序设计器中打开和添加视图

以下步骤介绍如何在应用程序设计器中打开和添加视图。
1. 在 PowerApps 中，从左侧导航窗格选择**应用**，选择所需应用旁边的 **...**，然后选择**编辑**。 

2. 在应用程序设计器的**实体视图**部分中，选择**视图**。

    在本例中，我们已从**客户**实体选择 **视图**。

    ![应用程序设计器视图](media/ViewAppDesigner_AccountAppDesignerView.png "客户实体的应用程序设计器视图")

3. 要添加视图，请通过使用“公共”、“高级查找”、“关联”和“查找”进行选择。 将把视图自动添加到**视图**列表。

    > [!NOTE]
    > 视图根据您已选择的实体显示。 例如，如果选择**客户**，将显示与客户实体关联的视图。

有关应用程序设计器的详细信息：[通过使用应用程序设计器设计自定义业务应用程序](design-custom-business-apps-using-app-designer.md)


### <a name="add-a-column-to-your-view-in-app-designer"></a>在应用程序设计器中向视图添加列
视图通过包含行和列的表显示记录。 每行就是一条记录，而从记录中显示的字段由添加到视图的列确定。

1. 在应用程序设计器中，选择所需实体视图，然后在右侧窗格上所需视图旁边选择编辑（铅笔按钮）。  
2. 在**组件**选项卡中，选择**主实体**或**相关实体**的**列属性**列表。

    ![添加列](media/ViewAppDesigner_AddColumn.png "向视图中添加列") 

3. 从列表选择所需属性，然后将其拖到列标题。 还可以通过双击属性来添加属性。
4. 重复步骤 3，直到添加了要在视图中显示的所有属性。

添加属性时，可将其随现有列标题一起拖到任意位置。 将列添加到视图后，还可以移动列。


### <a name="define-filter-criteria-in-app-designer"></a>在应用程序设计器中定义筛选条件
您可以设置筛选条件，以便在视图中仅显示一小组记录。 用户打开视图时，将仅显示满足定义的筛选条件的记录。 可以同时从主实体和相关实体选择要充当筛选条件的字段。
1. 在应用程序设计器中，展开**筛选条件**部分。
   
    ![设置筛选条件](media/ViewAppDesigner_FilterCriteria.png "设置筛选条件") 

2. 选择**添加筛选器**。
3. 从第一列中的下拉列表选择属性。 
4. 从第二列中的下拉列表选择运算符。

    ![设置筛选条件运算符](media/ViewAppDesigner_FilterCriteriaOption.png "设置筛选条件运算符")

5. 在第三列中输入要充当筛选依据的值。

除了主实体，还可以基于相关实体的属性筛选数据。 

1. 在**组件**选项卡中，选择**相关实体**的**列属性**列表，选择最上方字段中的**选择实体**向下箭头，然后选择所需实体。

    这将添加一个单独的部分。

2. 重复上一过程中的步骤 2 到 5。

详细信息：[创建和编辑实体之间的关系](../common-data-service/create-edit-entity-relationships.md)

#### <a name="group-multiple-filters-in-app-designer"></a>在应用程序设计器中为多个筛选器分组
如果要通过使用多个字段筛选记录，可向视图添加多个筛选器。 

1. 选择要分组的筛选器。
    ![设置组筛选器](media/ViewAppDesigner_GroupFilter.png "设置组筛选器")
2. 选择“组 And”或“组 Or”为筛选器分组。
    ![组筛选器选择](media/ViewAppDesigner_GroupFilterSelection.png "选择组筛选器") 如果选择**组 And**，则视图中仅显示同时满足两个条件的记录。 如果选择**组 Or**，则显示满足任何筛选条件的记录。 例如，要仅显示优先级为“高”或“普通”且状态为“活动”的记录，请选择**组 And**。

要从组中移除筛选器，请选择组，然后选择**取消组合**。 

### <a name="set-primary-and-secondary-sort-order-for-columns-in-app-designer"></a>在应用程序设计器中为列设置主要排序顺序和次要排序顺序
视图打开时，将按照创建该视图时设置的顺序为其显示的记录排序。   默认情况下，如果未选择排序顺序，将根据视图中的第一列为记录排序。 可选择根据一列排序，也可以选择根据两列排序，即一个主要列，一个次要列。 视图打开时，将首先根据要用于主要排序顺序的列为记录排序，然后根据要用于次要排序顺序的列为记录排序。 

> [!NOTE]
> 只能为从主实体添加的列属性设置主要排序顺序和次要排序顺序。

1. 选择要用于排序的列。
2. 选择向下箭头，然后选择**主要排序**或**次要排序**。
 
    ![为记录排序](media/ViewAppDesigner_SortRecords.png "基于主要排序顺序和次要排序顺序为记录排序") 

如果移除为主要排序顺序选择的列，为次要排序顺序选择的列将变为主要排序顺序。

### <a name="define-a-web-resource-in-app-designer"></a>在应用程序设计器中定义 Web 资源
指定要与视图中的列关联的脚本类型的 Web 资源。 这些脚本有助于显示列的图标。

1. 选择要向其添加 Web 资源的列。
2. 在**属性**选项卡上，选择**高级**。
3. 在 **Web 资源**选项列表中，选择要使用的 Web 资源。
4. 在**功能名称**框中，输入功能名称。

### <a name="edit-a-public-or-system-view-in-app-designer"></a>在应用程序设计器中编辑公共视图或系统视图
可通过添加、配置或移除列，更改公共视图或系统视图的显示方式。
1. 在实体的**视图**列表中，选择**显示参考列表**下拉箭头 ![下拉箭头](media/DownArrow.png "下拉箭头")。
    ![编辑视图](media/ViewAppDesigner_EditView.png "编辑公共视图或系统视图")
2. 在要编辑的视图旁边，选择**打开视图设计器** ![打开视图设计器](media/dynamics365-open-designer.png "打开视图设计器")。 

    将在视图设计器中打开视图。 

编辑公共视图或系统视图时，更改必须先保存并发布，才会在应用程序中显示。


## <a name="community-tools"></a>社区工具
**View Layout Replicator** 和**视图设计器**是 XrmToolbox 社区为 Dynamics 365 Customer Engagement 开发的工具。

详细信息：[开发人员工具](https://docs.microsoft.com/dynamics365/customer-engagement/developer/developer-tools)。

> [!NOTE]
> 这些工具由 XrmToolBox 提供，不受 Microsoft 支持。 如果有与该工具相关的疑问，请联系发布者。 详细信息：[XrmToolBox](https://www.xrmtoolbox.com/)。 

### <a name="next-steps"></a>后续步骤
[创建 1:N（一对多）或 N:1（多对一）关系](../common-data-service/create-edit-1n-relationships.md)
