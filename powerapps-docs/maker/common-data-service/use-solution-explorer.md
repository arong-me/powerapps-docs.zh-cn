---
title: 在 PowerApps 中使用解决方案资源管理器 | MicrosoftDocs
description: 了解如何使用解决方案资源管理器创建或自定义应用
ms.custom: ''
ms.date: 06/18/2018
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
# <a name="use-the-solution-explorer"></a>使用解决方案资源管理器

 在解决方案资源管理器中，可以使用左侧的导航窗格在节点的层次结构中浏览，如以下屏幕截图所示：  
  
 ![具有折叠的实体的默认解决方案](media/crm-itpro-cust-defaultsolutionentitiescollapsed.PNG "具有折叠的实体的默认解决方案")  
  
> [!NOTE]
>  在解决方案管理器中使用自定义工具时，请使用鼠标和键盘。 应用程序的此部分并不是为了优化触屏效果。  
  
 在选择每个节点时，可以看到一个解决方案组件的列表。 命令栏中的可用操作会发生变化，具体取决于选择的节点的上下文，以及解决方案是默认解决方案还是托管解决方案。 对于不是默认解决方案的非托管解决方案，可以使用**添加现有** 命令导入尚不在解决方案中的解决方案组件。  
  
对于托管解决方案，将不会有可用的命令，您将看到一条消息：  

> [!NOTE]
> 无法直接编辑托管解决方案中的组件。 如果解决方案组件的托管属性设置为允许自定义，则可以使用 PowerApps 设计工具或从其他非托管解决方案编辑它们。    
  
 您将需要查找默认解决方案中的解决方案组件，并尝试在其中组件，或将其添加到已经创建的其他非托管解决方案。 解决方案组件可能不可自定义。 详细信息：[托管属性](solutions-overview.md#managed-properties)
  
 您需要执行的许多自定义将涉及到实体。 您可以展开**实体**节点以显示可进行某种程度的自定义的系统中的所有实体的列表。 您可以进一步展开每个实体以查看组成实体的解决方案组件，如以下屏幕截图中的帐户实体所示：  
  
 ![显示已展开的客户实体的默认解决方案](media/crm-itpro-cust-defaultsolution.PNG "显示已展开的客户实体的默认解决方案")  
  
 有关自定义解决方案资源管理器中找到的单个解决方案组件的详细信息，请参阅以下主题：  
  
-   有关实体、实体关系、字段和消息自定义，请参阅[元数据](create-edit-metadata.md)。  
  
-   有关实体窗体，请参阅[窗体](../model-driven-apps/create-design-forms.md)。  
  
-   有关进程，请参阅[流程](../model-driven-apps/guide-staff-through-common-tasks-processes.md)。  
  
-   有关业务规则，请参阅[业务规则](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)。  
