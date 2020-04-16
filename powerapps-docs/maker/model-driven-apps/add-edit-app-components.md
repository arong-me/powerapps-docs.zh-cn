---
title: 使用 Power Apps 添加或编辑模型驱动应用组件的教程 | MicrosoftDocs
description: 使用 Power Apps 应用程序设计器添加或编辑组件
keywords: ''
ms.date: 03/05/2020
ms.service: powerapps
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5f357bd55060258ca8545fae6ad4bb3c7621ab5c
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136465"
---
# <a name="tutorial-add-or-edit-model-driven-app-components-in-the-power-apps-app-designer"></a>教程：在 Power Apps 应用程序设计器中添加或编辑模型驱动应用组件

在本教程中，您将了解如何在模型驱动的应用程序中添加和移除组件。 

模型驱动的应用程序由大量组件构成。 可以添加到应用的组件有两种：项目和实体资产。 在应用程序设计器上下文中，实体、仪表板和业务流程是应用程序的全部项目。 实体资产包含窗体、视图、图表和仪表板。  
  
应用程序设计器参考默认解决方案的现有元数据。 可将其用于创建组件，如窗体、视图、图表和仪表板。  
  
## <a name="app-designer-layout"></a>应用程序设计器布局  
 应用程序设计器有两个主要区域。 在左侧是添加组件的区域。  
  
 > [!div class="mx-imgBorder"]
 > ![应用设计器区域](../model-driven-apps/media/app-designer-canvas-pane.png "应用设计器区域")

 在右侧是您用于选择组件并设置组件属性的选项卡。  
 
 > [!div class="mx-imgBorder"]
 > ![应用设计器组件](../model-driven-apps/media/app-designer-canvas-components-tab.png "应用设计器组件")  
  
 在区域中，您将看到站点地图、业务流程、仪表板和实体区域。 在选择仪表板或业务流程或配置站点地图时，应用程序设计器将这些组件中使用的实体自动添加到此区域。 实体准备就绪后，您只需选择每个实体，并向其添加所需实体资产，如窗体、视图和图表。
 
 也可以使用**搜索区域**搜索区域中的组件。 如果选择**搜索区域**，将在最右窗格中选项卡右侧打开一个新的搜索选项卡。   
 
 > [!div class="mx-imgBorder"]
 > ![区域搜索选项](media/app-designer-search-tab.png "区域搜索")

## <a name="open-an-app"></a>打开应用
1. 登录到 [Power Apps](https://make.powerapps.com/)。 

2. 选择模型驱动的现有应用程序，或选择**从头开始制作模型驱动应用**。 有关如何创建应用程序的信息，请参阅[使用应用设计器创建或编辑模型驱动的应用程序](create-edit-app.md#create-an-app)。

## <a name="add-an-artifact-entity-dashboard-or-business-process-flow"></a>添加项目（实体、仪表板或业务流程）  
 向应用添加仪表板或业务流程时，将自动向应用添加仪表板或业务流程所用实体。 在添加某个实体时，其资产的磁贴会自动添加。 将项目添加到设计器区域有以下两种方法：使用命令栏中的**添加**按钮 ![在设计器中添加按钮](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "在设计器中添加按钮") ，或使用**组件**选项卡中的磁贴。  
  
 下面是将仪表板添加到应用程序的步骤。 可以使用相同的步骤添加业务流程或实体。  
  
1.  在应用设计器区域中，选择**仪表板**磁贴。  
  
     在应用设计器区域中，最右窗格显示您在默认解决方案中可用的仪表板。  
  
    > [!TIP]
    >  也可以执行以下操作之一：  
    >   
    > - 选择**添加** ![在设计器中添加按钮](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "在设计器中添加按钮")，然后选择**仪表板**。  
    > - 在**组件**选项卡上，在**项目**下，选择**仪表板**。  
  
2.  在**搜索**框中，键入要查找的仪表板名称的几个关键字。  
  
     仪表板列表将经过筛选，显示与关键字匹配的结果。  
  
3.  如果希望您的用户仅使用选择的仪表板，选择要添加的仪表板对应的复选框。 可从以下仪表板类型选择：
    - **经典仪表板**，同时在 Web 应用和统一接口应用中显示。
    - **交互式仪表板**，仅在统一接口应用中显示。 如果为应用选择了客户端类型充当 Web 应用，则不显示**交互式仪表板**。

     这些仪表板将添加到应用设计器区域的**仪表板**磁贴中。 **仪表板**磁贴还显示添加到应用程序的仪表板数的计数。 如果不选择仪表板，将不显示仪表板计数，而是显示**全部**，而用户使用应用时，所有仪表板均可供其使用。  
  
     仪表板使用的所有实体也会添加到**实体视图**区域。 例如，如果添加“Customer Service 经理”仪表板，“案例”、“权限”和“队列项”实体将添加到“实体视图”区域。 对于每个实体，还会添加其资产的磁贴。 您可以使用这些磁贴添加窗体、视图和图表。 详细信息：[在 Power Apps 应用程序设计器中添加或编辑应用组件](add-edit-app-components.md#bkmk_AddEntityAssets)   
  
    > [!div class="mx-imgBorder"]
    > ![将实体添加到应用程序设计器区域](../model-driven-apps/media/add-entity-app-designer-canvas.png "将实体添加到应用程序设计器区域")  
  
4.  如果默认解决方案中没有您所需仪表板，请通过选择区域右侧**组件**选项卡中的**新建**创建仪表板。  
  
     > [!div class="mx-imgBorder"]
     > ![应用程序设计器的“组件”选项卡中的“新建”链接](../model-driven-apps/media/app-designer-components-tab-create-new.png "应用程序设计器的“组件”选项卡中的“新建”链接")  
  
     仪表板设计器随即打开。 详细信息：[创建和编辑仪表板](create-edit-dashboards.md)  
  
    > [!NOTE]
    > - 在添加业务流程或实体时，**新建**选项打开相应的设计器。 若要了解有关创建业务流程或实体的详细信息，请参阅[创建业务流程](/flow/create-business-process-flow)和[创建自定义实体](https://docs.microsoft.com/powerapps/maker/common-data-service/data-platform-create-entity)。  
      
  
5.  添加完项目后，选择命令栏中的**保存**。  
  
<a name="bkmk_AddEntityAssets"></a>   
## <a name="add-entity-assets-forms-views-charts-or-dashboards"></a> 添加实体资产（窗体、视图、图表或仪表板）  
 拥有项目后，您可以开始添加类似窗体、视图、图表和仪表板的实体资产到应用程序。
此外，如果在使用统一接口客户端，还可以向应用添加实体仪表板资产。  
  
 本部分介绍将窗体添加到应用程序的步骤。 使用相同的步骤可以将视图或图表添加到应用程序中。  
  
1.  在应用设计器区域中，选择要为其添加窗体的实体的**窗体**磁贴。  
  
     在应用程序设计器区域中，将选中实体的整行。 在右侧，您将看到所选实体的所有现有窗体。  
  
    > [!NOTE]
    >  也可以执行以下操作之一：  
    >   
    > - 选择**添加** ![在设计器中添加按钮](../model-driven-apps/media/dynamics365-designer-addbutton.PNG "在设计器中添加按钮")，然后选择**窗体**。  
    > - 在**组件**选项卡，在**实体资产**下，选择**窗体**。  
  
    > [!TIP]
    >  对于为应用选择的所有实体，将在**组件**选项卡上**选定实体**列表中显示**更多选项**按钮 (**...**)。若要为选定实体添加所有资产，请选择**更多选项** (**...**)，然后选择**添加所有资产**。  
  
2.  如果希望您的应用程序用户仅使用选择的窗体，选择要添加的窗体对应的复选框。 窗体定义用户查看应用中数据并与之交互的方式。 
 
     所选实体的窗体磁贴将显示添加的窗体数。  
  
     ![案例实体的窗体磁贴](../model-driven-apps/media/add-forms-entity.png "案例实体的窗体磁贴")  
  
     例如，如果不为实体选择任何窗体，则最终用户使用应用时，将向其显示该实体的所有窗体。 如果不选择视图或图表，则视图和图表的此行为类似。 这有助于在需要处理所有可用组件时快速创建应用程序；无需在应用程序设计期间选择每个组件。  

     如果不选择仪表板或业务流程，则用户在使用应用时可使用所有仪表板和业务流程。
  
    > [!NOTE]
    > 对于要运行的应用程序，您添加的每个实体都必须至少有一个活动窗体。 如果选择了多个窗体，默认解决方案中显示的第一个活动窗体在用户运行应用程序时使用。  
  
3.  如果要添加列表中不存在的新窗体，选择**新建**。  
  
     在下拉列表中，选择您要创建的窗体类型。  
  
    > [!NOTE]
    >  只有当您添加窗体时下拉列表才可用。 它对于视图和图表不可用。  
  
     窗体设计器将打开。 详细信息：[创建和设计窗体](create-design-forms.md)  
  
     在添加视图或图表时，**新建**选项打开相应的设计器。 详细信息：[了解视图](create-edit-views.md)和[创建或编辑系统图表](create-edit-system-chart.md)  
  
    > [!NOTE]
    >  在添加视图时，可以只参考解决方案资源管理器中**视图**节点下列出的公共视图。  
  
4. 选择下拉箭头 ![下拉箭头图标](../model-driven-apps/media/drop-down-icon.png "向下箭头") 展开磁贴并查看已添加的窗体的列表。  
  
     ![应用程序设计器中已展开的窗体磁贴](../model-driven-apps/media/app-designer-expanded-form-tile.png "应用程序设计器中已展开的窗体磁贴")  
  
5.  重复上述步骤以将实体视图和图表添加到应用程序。  
  
6.  选择**保存**。  
  
## <a name="edit-or-remove-artifacts"></a>编辑或移除项目  
  
- 若要编辑仪表板或业务流程，请选择下拉箭头 ![下拉箭头图标](../model-driven-apps/media/drop-down-icon.png "向下箭头") 展开磁贴，然后选择与要编辑的仪表板或业务流程对应的站点地图设计器按钮 ![打开站点地图设计器按钮](../model-driven-apps/media/dynamics365-open-designer.PNG "“打开站点地图设计器”按钮")。  
  
     选定项的设计器打开。  
  
- 若要移除仪表板或业务流程，请选择下拉箭头 ![下拉箭头图标](../model-driven-apps/media/drop-down-icon.png "向下箭头") 展开磁贴，然后选择要移除的仪表板或业务流程。 在命令栏上，选择**移除**。  

    还可以通过清除**组件**选项卡上的相应复选框移除仪表板或业务流程。
  
- 要编辑或移除实体，选择实体磁贴，然后在命令栏，选择**编辑**或**移除**。 在编辑实体时，解决方案资源管理器打开，您可以在其中对实体进行更改。  
  
     还可以通过选择仪表板、业务流程或实体磁贴来移除组件。 在**组件**选项卡上，清除要从设计器移除的项目的复选框。  
  
    > [!NOTE]
    >  对实体执行任何更改 &mdash; 如更改实体的显示名称或说明 &mdash; 除非在解决方案资源管理器中发布这些更改，否则应用设计器中不显示这些更改。  
  
## <a name="edit-or-remove-entity-assets"></a>编辑或移除实体资产  

### <a name="edit-entity-assets"></a>编辑实体资产
  
1. 选择下拉箭头 ![下拉箭头图标](../model-driven-apps/media/drop-down-icon.png "向下箭头") 展开窗体、视图、图表或仪表板的磁贴。  
  
2. 选择要编辑的窗体、视图、图表或仪表板。  
  
3. 在命令栏上，选择**编辑**。

   or

   选择与窗体、视图、图表或仪表板对应的站点地图编辑器按钮 ![“打开站点地图设计器”按钮](../model-driven-apps/media/dynamics365-open-designer.PNG "“打开站点地图设计器”按钮")。  

### <a name="remove-entity-assets"></a>移除实体资产  

1. 选择下拉箭头 ![下拉箭头图标](../model-driven-apps/media/drop-down-icon.png "向下箭头") 展开窗体、视图、图表或仪表板的磁贴。  
  
2. 选择要编辑的窗体、视图、图表或仪表板。

3. 在命令栏上，选择**移除**。 

也可以选择窗体、视图、图表或仪表板磁贴，然后在**组件**选项卡上，清除要从设计器移除的资产的复选框。  
  
## <a name="next-steps"></a>后续步骤  
 [为应用程序创建站点地图](create-site-map-app.md) </br>  
 [验证并发布应用程序](validate-app.md)
