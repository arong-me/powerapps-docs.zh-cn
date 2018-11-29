---
title: 在 PowerApps 中使用解决方案 | MicrosoftDocs
description: 了解如何使用解决方案创建或自定义应用
ms.custom: ''
ms.date: 10/29/2018
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
ms.assetid: 72bacfbb-96a3-4daa-88ff-11bdaaac9a3d
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="use-solutions-in-powerapps"></a>在 PowerApps 中使用解决方案

 在 PowerApps 内，您可以通过选择左侧导航中的**解决方案**查看解决方案列表。 然后可以选择解决方案来查看其所有组件。 
 
> [!NOTE]
>  解决方案体验仅在线可用，且仅可用于环境版本 9.1.0.267 及以后版本。 若要检查您的版本，请转到…[PowerApps 管理中心](https://admin.powerapps.com/)>“环境”>“选择您的环境”>“详细信息”选项卡。对于早期版本的实例，选择解决方案将在经典体验中打开它。 

> [!div class="mx-imgBorder"]  
> ![具有所有组件的演示解决方案](media/solution-all-items-list.PNG "具有所有组件的演示解决方案")  
  
 
 您可以通过在项目中滚动来滚动浏览解决方案中的所有组件。 如果列表中有超过 100 个项目，您可以选择**加载另外 100 个项目**来查看更多项目。 
 
> [!div class="mx-imgBorder"]  
> ![加载更多组件](media/load-more.PNG "加载更多组件")  

 ## <a name="search-and-filter-in-a-solution"></a>在解决方案中搜索和筛选
 
 您还可以按名称搜索特定组件。 
 
> [!div class="mx-imgBorder"]  
> ![搜索组件](media/solution-search-box.PNG "搜索组件")  
 
 或者按组件类型在列表中筛选所有项目。
  
> [!div class="mx-imgBorder"]  
> ![按类型筛选组件](media/solution-filter.PNG "按类型筛选组件")  
 
 ## <a name="contextual-commands"></a>上下文命令
 
 在您选择每个组件时，命令栏中的可用操作会发生变化，具体取决于选择的组件的类型，以及解决方案是默认还是托管解决方案。 
 
> [!div class="mx-imgBorder"]  
> ![组件特定命令](media/component-commands.PNG "组件特定命令")  
 
 如果未选择任何组件，命令栏将显示已应用到解决方案本身的操作。 
 
> [!div class="mx-imgBorder"]  
> ![解决方案特定命令](media/solution-commands.PNG "解决方案特定命令")  
 
 ## <a name="create-components-in-a-solution"></a>在解决方案中创建组件
 使用非托管或默认的解决方案，您可以使用**新建**命令来创建不同类型的组件。 这会将您带入不同的创建体验，具体取决于您选择的组件类型。 完成创建组件后，组件将被添加到解决方案中。 
 
> [!div class="mx-imgBorder"]  
> ![在解决方案中创建新组件](media/solution-new-component.PNG "在解决方案中创建新组件")  
 
 ## <a name="add-an-existing-component-to-a-solution"></a>向解决方案添加现有组件
 
 对于属于非托管解决方案但不是默认的解决方案，可以使用**添加现有**命令导入尚不在解决方案中的组件。  
 
> [!div class="mx-imgBorder"]  
> ![向解决方案添加现有组件](media/solution-add-existing-component.PNG "向解决方案添加现有组件")  
  
 对于托管解决方案，将不会有可用的命令，您将看到一条消息，如下所示。 您将需要查找名为**默认解决方案**的解决方案中的组件，并尝试在其中组件，或将其添加到已经创建的其他非托管解决方案。 组件可能不可自定义。 详细信息：[托管属性](solutions-overview.md#managed-properties)

> [!div class="mx-imgBorder"]  
> ![托管解决方案](media/managed-solution.PNG "托管解决方案")  

 您需要执行的许多自定义将涉及到实体。 您可以使用**实体**筛选器以显示可进行某种程度的自定义的当前解决方案中的所有实体的列表。 在钻取实体后，您可以查看组成实体的组件，如以下屏幕截图中的客户实体所示。 
 
> [!NOTE]
>  目前，在向解决方案添加现有实体时，系统会将属于实体一部分的所有组件自动添加到您的解决方案中。 如果这不是您希望的，可使用命令**切换到经典**来导航到经典体验，然后只添加所需的那些组件。 <!-- We will soon improve this experience from PowerApps and allow you to select only the specific component(s) under entity that you want to add into a solution. -->
  
> [!div class="mx-imgBorder"]  
> ![显示已展开的客户实体的演示解决方案](media/solution-entity-account.PNG "显示已展开的客户实体的演示解决方案")  

## <a name="classic-solution-explorer"></a>经典解决方案资源管理器

在 PowerApps 中，您可以通过选择左侧导航窗格中的**解决方案**，然后选择命令栏中的**切换到经典**，来查看经典方案资源管理器。 经典解决方案资源管理器是之前通过 PowerApps 中的**设置 > 高级自定义**区域提供的那个。 如果您是 Dynamics 365 for Customer Engagement 用户，您使用经典解决方案资源管理器来处理解决方案。  

## <a name="known-limitations"></a>了解限制

- 删除或移除托管解决方案不会从 PowerApps 中删除区域应用。
- 解决方案中不提供自定义连接器。
- 区域应用需要在导入解决方案以更新连接后打开。
- 在添加现有 SDK 程序集后，它不会显示在解决方案中。 
- 如果区域应用在托管解决方案中打包，它们仍可以由新管理员在新环境中进行编辑。
- 依赖项对区域应用不可用
- 删除托管解决方案不会回滚到其他区域应用版本 
-   区域应用访问（CRUD 和安全性）在 PowerApps 中完全托管，而不是在 Common Data Service 数据库中
-   调用区域应用的 CDS API 被阻止，不会返回任何信息 
-   在解决方案中创建的区域应用还不能作为共同负责人共享到 AAD 安全组
-   区域应用不显示在经典解决方案资源管理器中 
-   解决方案不能识别现有区域应用 

 有关自定义解决方案中的单个组件的详细信息，请参阅以下主题：  
  
-   有关实体、实体关系、字段和消息自定义，请参阅[元数据](create-edit-metadata.md)。  
  
-   有关实体窗体，请参阅[窗体](../model-driven-apps/create-design-forms.md)。  
  
-   有关进程，请参阅[流程](../model-driven-apps/guide-staff-through-common-tasks-processes.md)。  
  
-   有关业务规则，请参阅[业务规则](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)。  
