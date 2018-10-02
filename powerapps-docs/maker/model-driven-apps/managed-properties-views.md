---
title: PowerApps 的视图的模型驱动应用程序的托管属性 | MicrosoftDocs
description: 了解如何设置视图的托管属性
ms.custom: ''
ms.date: 06/12/2018
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
ms.assetid: a9014576-8fb2-4f28-b8bb-5d2d49d76e12
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="model-driven-app-managed-properties-for-views"></a>视图的模型驱动应用程序的托管属性

<a name="BKMK_ManagedProperties"></a>   
 
 如果您已经在 PowerApps 中创建自己在托管解决方案中包含要分发的自定义公共视图，您可以选择限制从自定义视图安装解决方案的用户能力。  
  
 默认情况下，大多数视图具有其设置 **可自定义** 的托管属性设置为 true，以便用户可以进行自定义。 除非您具有一个非常充足的原因更改此属性，我们建议您允许用户在您的应用中自定义视图。  
  
## <a name="set-managed-properties-for-a-view"></a>设置视图的托管属性  
  
1.  打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)，展开**实体**，选择所需实体，然后选择**视图**。  
  
2.  选择自定义公共视图。  
  
3.  在菜单栏上，选择**其他操作** > **托管属性**。  

    > [!div class="mx-imgBorder"] 
    > ![托管属性菜单](media/managed-properties.png)
  
4.  将**可自定义**或**可以删除**选项设置为 **True** 或 **False**。  

    > [!div class="mx-imgBorder"] 
    > ![设置托管属性](media/set-managed-properties.png)
  
> [!NOTE]
> 此设置将不生效，直到您导出包含视图作为托管解决方案的解决方案并将它安装在不同环境中。  

## <a name="next-steps"></a>后续步骤
[了解视图](create-edit-views.md)
