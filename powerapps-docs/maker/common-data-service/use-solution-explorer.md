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
ms.openlocfilehash: 6abbe701a6207e68ac367fbe80495a7d04a6e682
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668023"
---
# <a name="use-the-solution-explorer"></a>使用解决方案资源管理器

 在解决方案资源管理器中，可以使用左侧的导航窗格浏览节点层次结构，如以下屏幕截图所示：  
  
 ![实体的默认解决方案（折叠）](media/crm-itpro-cust-defaultsolutionentitiescollapsed.PNG "实体的默认解决方案（折叠）")  
  
> [!NOTE]
>  在解决方案资源管理器中使用自定义工具时，请使用鼠标和键盘。 应用程序的此部分未针对触控进行优化。  
  
 选择每个节点时，可以看到解决方案组件列表。 基于所选节点的上下文以及解决方案是默认解决方案还是托管解决方案，命令栏中的可用操作将发生更改。 对于不是默认解决方案的非托管解决方案，可使用“添加现有”命令引入解决方案中尚不存在的解决方案组件。  
  
使用托管解决方案时将没有可用命令，并且将看到以下消息：  

> [!NOTE]
> 不能直接编辑托管解决方案中的组件。 如果解决方案组件的托管属性设置为允许自定义，则可以使用 PowerApps 设计工具或从其他非托管解决方案中编辑这些组件。    
  
 需要在默认解决方案中找到解决方案组件，并尝试在该处对其进行编辑或将其添加到已创建的另一个非托管解决方案中。 解决方案组件可能无法自定义。 详细信息：[托管属性](solutions-overview.md#managed-properties)
  
 要执行的许多自定义操作都将涉及实体。 可以展开“实体”节点，以显示系统中可通过某种方式进行自定义的所有实体的列表。 可以进一步展开每个实体，查看该实体具有的解决方案组件，如以下屏幕截图中的帐户实体所示：  
  
 ![显示展开的帐户实体的默认解决方案](media/crm-itpro-cust-defaultsolution.PNG "显示展开的帐户实体的默认解决方案")  
  
 有关自定义在解决方案资源管理器中找到的各个解决方案组件的详细信息，请参阅以下主题：  
  
-   有关实体、实体关系、字段和消息自定义的信息，请参阅[元数据](create-edit-metadata.md)。  
  
-   对于实体窗体，请参阅[窗体](../model-driven-apps/create-design-forms.md)。  
  
-   对于流程，请参阅[流程](../model-driven-apps/guide-staff-through-common-tasks-processes.md)。  
  
-   对于业务规则，请参阅[业务规则](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)。  
