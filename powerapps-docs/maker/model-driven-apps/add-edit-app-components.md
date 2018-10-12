---
title: 教程：使用 PowerApps 添加或编辑模型驱动应用组件 | MicrosoftDocs
description: 使用 PowerApps 应用程序设计器添加或编辑组件
keywords: ''
ms.date: 03/30/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: be93b9d7-f1c2-4ee7-8d7c-0f5c34dfa5f7
ms.author: matp
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 17
topic-status: Drafting
ms.openlocfilehash: 87fec3bff3ad21a5c0474b67f001cca5c902d609
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669141"
---
# <a name="tutorial-add-or-edit-model-driven-app-components-in-the-powerapps-app-designer"></a>教程：在 PowerApps 应用程序设计器中添加或编辑模型驱动应用组件

本教程介绍如何向模型驱动应用添加组件以及如何从中删除组件。 

模型驱动应用包含多种组件。 可向应用添加两种类型的组件：项目和实体资产。 在应用程序设计器的上下文中，实体、仪表板和业务流程都是应用的项目。 实体资产包括窗体、视图、图表和仪表板。  
  
应用程序设计器引用默认解决方案中的现有元数据。 可用于创建窗体、视图、图表和仪表板等组件。  
  
## <a name="app-designer-layout"></a>应用程序设计器布局  
 应用程序设计器包含两个主要区域。 左侧是用于添加应用组件的区域。  
  
![应用程序设计器区域](../model-driven-apps/media/app-designer-canvas-pane.png)

 右侧是用于选择组件和设置组件属性的选项卡。  
  
 ![应用程序设计器组件](../model-driven-apps/media/app-designer-canvas-components-tab.png "应用程序设计器组件")  
  
 该区域将显示站点地图、业务流程、仪表板和实体的分区。 选择仪表板或业务流程，或者配置站点地图时，应用程序设计器会自动将这些组件中使用的实体添加至该区域。 添加好实体后，只需选择各个实体并向其添加所需的实体资产（如窗体、视图和图表）即可。
 
 还可以使用“搜索区域”来搜索该区域上的组件。 选择“搜索区域”后，将在最右窗格中的选项卡右侧打开新的搜索选项卡。   
  
 ![区域搜索选项](media/app-designer-search-tab.png "区域搜索")

## <a name="open-an-app"></a>打开应用
1. 登录 [PowerApps](https://web.powerapps.com/)。 

2. 选择“模型驱动” > “应用”，然后选择现有应用或“创建应用”。 若要详细了解如何创建应用，请参阅[使用应用程序设计器创建或编辑模型驱动应用](create-edit-app.md#create-an-app)。

## <a name="add-an-artifact-entity-dashboard-or-business-process-flow"></a>添加项目（实体、仪表板或业务流程）  
 在将仪表板或业务流程添加至应用时，它们所用的实体会自动添加到应用。 添加实体时，其资产的磁贴会自动添加。 可通过两种方法将项目添加到设计器区域：使用命令栏上的“添加”按钮 ![设计器上的“添加”按钮](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "设计器上的“添加”按钮") 或使用“组件”选项卡上的磁贴。  
  
 下面是将仪表板添加到应用的步骤。 添加业务流程或实体的步骤与此相同。  
  
1.  在应用程序设计器区域上选择“仪表板”磁贴。  
  
     应用程序设计器区域最右侧的窗格会显示默认解决方案中可用的仪表板。  
  
    > [!TIP]
    >  或者，也可以执行以下任一操作：  
    >   
    > - 选择“添加”![设计器上的“添加”按钮](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "设计器上的“添加”按钮")，然后选择“仪表板”。  
    > - 在“组件”选项卡上，选择“项目”下的“仪表板”。  
  
2.  在搜索框中键入所需仪表板名称的几个关键字。  
  
     这样即可筛选仪表板列表，显示与关键字匹配的结果。  
  
3.  如果希望自己的用户仅使用选定的仪表板，请勾选想添加的仪表板的复选框。 可选择以下类型的仪表板：
    - **经典仪表板**：可在 Web 应用和统一接口应用上显示。
    - **交互式仪表板**：仅可在统一接口应用上显示。 如果应用的客户端类型已选为 Web 应用，则不会显示“交互式仪表板”选项。

     这些仪表板将添加到应用程序设计器区域上的“仪表板”磁贴。 “仪表板”磁贴还会显示已添加到应用的仪表板数量。 如果没有选择仪表板，则会显示“全部”而不是仪表板数量，用户在使用该应用时可使用所有仪表板。  
  
     仪表板使用的所有实体也会添加到“实体视图”分区。 例如，如果添加客户服务管理器仪表板，则会将案例、授权和队列项实体添加至“实体视图”分区。 还会添加每个实体的资产磁贴。 可使用这些磁贴来添加窗体、视图和图表。 详细信息：[在 PowerApps 应用程序设计器中添加或编辑应用组件](add-edit-app-components.md#bkmk_AddEntityAssets)   
  
    ![将实体添加到应用程序设计器区域](../model-driven-apps/media/add-entity-app-designer-canvas.png "将实体添加到应用程序设计器区域")  
  
4.  如果默认解决方案中没有需要的仪表板，可通过选择区域右侧“组件”选项卡上的“新建”来创建仪表板。  
  
     ![应用程序设计器“组件”选项卡上的“新建”链接](../model-driven-apps/media/app-designer-components-tab-create-new.png "应用程序设计器“组件”选项卡上的“新建”链接")  
  
     仪表板设计器随即打开。 详细信息：[创建和编辑仪表板](create-edit-dashboards.md)  
  
    > [!NOTE]
    > - 添加业务流程或实体时，“新建”选项将打开对应的设计器。 若要详细了解如何创建业务流程或实体，请参阅[创建业务流程](/flow/create-business-process-flow)和[创建自定义实体](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-create-entity)。  
      
  
5.  添加完项目后，请在命令栏上选择“保存”。  
  
<a name="bkmk_AddEntityAssets"></a>   
## <a name="add-entity-assets-forms-views-charts-or-dashboards"></a>添加实体资产（窗体、视图、图表或仪表板）  
 项目准备就绪后，可以开始向应用添加窗体、视图、图表和仪表板等实体资产。
此外，若使用的是统一接口客户端，则还能向应用添加实体仪表板资产。  
  
 本部分介绍向应用添加窗体的步骤。 使用相同的步骤向应用添加视图或图表。  
  
1.  在应用程序设计器区域上，选择想向其添加窗体的实体的“窗体”磁贴。  
  
     在应用程序设计器区域上，将选中该实体的整行。 右侧将显示所选实体的所有现有窗体。  
  
    > [!NOTE]
    >  或者，也可以执行以下任一操作：  
    >   
    > - 选择“添加”![设计器上的“添加”按钮](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "设计器上的“添加”按钮")，然后选择“窗体”。  
    > - 在“组件”选项卡上，选择“实体资产”下的“窗体”。  
  
    > [!TIP]
    >  对于为该应用选择的所有实体，“组件”选项卡上的“选择实体”列表中将显示一个“更多选项”按钮 (...)。若要添加所选实体的所有资产，请选择“更多选项”(...) ，然后选择“添加全部资产”。  
  
2.  如果希望应用的用户仅使用选定的窗体，请勾选想添加的窗体的复选框。 窗体定义了用户在应用中查看数据以及和数据交互的方式。 
 
     所选实体的窗体磁贴会显示已添加的窗体数量。  
  
     ![示例实体的窗体磁贴](../model-driven-apps/media/add-forms-entity.png "实体的窗体磁贴")  
  
     例如，如果没有为实体选择任何窗体，那么最终用户在使用应用时将看到该实体的所有窗体。 对于视图和图表，如果没有选择视图或图表，这种行为也是类似的。 这有助于在需要使用所有可用组件时快速创建应用；不需要在应用设计时选择每个组件。  

     如果没有选择仪表板或业务流程，则用户在使用应用时可使用所有仪表板和业务流程。
  
    > [!NOTE]
    > 为了确保应用运行，所添加的每个实体都必须具有至少一个有效窗体。 如果选择了多个窗体，则用户在运行应用时会使用默认解决方案中显示的第一个有效窗体。  
  
3.  如果想添加列表中没有的新窗体，请选择“新建”。  
  
     在下拉列表中选择要创建的窗体类型。  
  
    > [!NOTE]
    >  该下拉列表仅用于添加窗体。 不适用于视图和图表。  
  
     窗体设计器随即打开。 详细信息：[创建和设计窗体](create-design-forms.md)  
  
     添加视图或图表时，“新建”选项将打开对应的设计器。 详细信息：[了解视图](create-edit-views.md)和[创建或编辑系统图表](create-edit-system-chart.md)  
  
    > [!NOTE]
    >  添加视图时，只能引用解决方案资源管理器中“视图”节点下列出的公共视图。  
  
4. 选择下拉箭头![下拉箭头图标](../model-driven-apps/media/drop-down-icon.png "下拉箭头")可展开磁贴并查看已添加的窗体列表。  
  
     ![应用程序设计器中展开的窗体磁贴](../model-driven-apps/media/app-designer-expanded-form-tile.png "应用程序设计器中展开的窗体磁贴")  
  
5.  重复上述步骤，向应用添加实体视图和图表。  
  
6.  选择“保存”。  
  
## <a name="edit-or-remove-artifacts"></a>编辑或删除项目  
  
- 若要编辑仪表板或业务流程，请选择下拉箭头 ![下拉箭头图标](../model-driven-apps/media/drop-down-icon.png "下拉箭头") 展开磁贴，然后选择与想编辑的仪表板或业务流程对应的站点地图设计器按钮 ![“打开站点地图设计器”按钮](../model-driven-apps/media/dynamics365-open-designer.PNG "“打开站点地图设计器”按钮")。  
  
     所选项目的设计器随即打开。  
  
- 若要删除仪表板或业务流程，请选择下拉箭头 ![下拉箭头图标](../model-driven-apps/media/drop-down-icon.png "箭头") 展开磁贴，然后选择要删除的仪表板或业务流程。 在命令栏上选择“删除”。  

    另一种删除仪表板或业务流程的方法是在“组件”选项卡上取消勾选其对应的复选框。
  
- 若要编辑或删除实体，请选择实体磁贴，然后在命令栏上选择“编辑”或“删除”。 编辑实体时会打开解决方案资源管理器，可在其中对实体进行更改。  
  
     另一种删除组件的方法是选择仪表板、业务流程或实体磁贴。 在“组件”选项卡上，取消勾选要从设计器中删除的项目对应的复选框。  
  
    > [!NOTE]
    >  在对实体进行任何更改时（例如更改实体显示名称或描述），这些更改在发布至解决方案资源管理器后才会显示在应用程序设计器中。  
  
## <a name="edit-or-remove-entity-assets"></a>编辑或删除实体资产  

### <a name="edit-entity-assets"></a>编辑实体资产
  
1. 选择下拉箭头 ![下拉箭头图标](../model-driven-apps/media/drop-down-icon.png "箭头")展开窗体、视图、图表或仪表板的磁贴。  
  
2. 选择想要编辑的窗体、视图、图表或仪表板。  
  
3. 在命令栏上选择“编辑”。

   或

   选择与该窗体、视图、图表或仪表板对应的站点地图设计器按钮 ![“打开站点地图设计器”按钮](../model-driven-apps/media/dynamics365-open-designer.PNG "“打开站点地图设计器”按钮")。  

### <a name="remove-entity-assets"></a>删除实体资产  

1. 选择下拉箭头 ![下拉箭头图标](../model-driven-apps/media/drop-down-icon.png "箭头")展开窗体、视图、图表或仪表板的磁贴。  
  
2. 选择想要编辑的窗体、视图、图表或仪表板。

3. 在命令栏上选择“删除”。 

或者，可以选择窗体、视图、图表或仪表板磁贴，然后在“组件”选项卡上取消勾选想从设计器中删除的资产的复选框。  
  
## <a name="next-steps"></a>后续步骤  
 [为应用创建站点地图](create-site-map-app.md) </br>  
 [验证并发布应用](validate-app.md)
