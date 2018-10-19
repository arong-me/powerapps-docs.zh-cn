---
title: 在 PowerApps 中设置模型驱动应用程序注释控件以访问有关公告的信息 | MicrosoftDocs
ms.custom: ''
ms.date: 05/06/2018
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
ms.assetid: f10cdf1c-3540-439c-a171-27a10e72da45
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="set-up-the-model-driven-app-notes-control-to-access-information-about-posts"></a>设置模型驱动应用程序注释控件以访问有关公告的信息

 在使用[更新后的窗体](main-form-presentations.md#updated-forms)的某些系统实体的 PowerApps 窗体中，“注释”控件可用于访问有关**公告**、**活动**和**注释**的信息。 对于启用了注释和活动的自定义实体，您将仅看到**注释**和**活动**。 若要包括**公告**，必须为自定义实体启用公告。  
  
## <a name="enable-posts-for-a-custom-entity"></a>为自定义实体启用公告  
  
1.  转到**[设置](advanced-navigation.md#settings)** > **活动源配置**。 
  
2.  打开您的自定义实体的记录。  
  
3.  确保选择了**为此类型的记录窗体启用留言板**，并保存记录。  
  
4.  在命令栏上，选择**激活**。  
  
5.  如果需要启用留言板，需要发布实体。  
  
 默认情况下，对于系统实体，注释控件位于窗体顶部的三栏选项卡中心的社交窗格分区中。 它只能在窗体中出现一次。 您可以移动或删除注释控件。 若要重新添加注释控件，可使用**插入**选项卡上**控件**组中的**注释**按钮。  
  
 下表介绍了注释控件的属性。  
  
|选项卡|属性|说明|  
|---------|--------------|-----------------|  
|**显示器**|**标签**|**必需**：虽然默认情况下不显示标签，但标签是必需的。|  
||**在窗体上显示标签**|您可以选择显示标签。|  
||**在表单上锁定字段**|这将防止从窗体中意外删除注释。|  
||**默认选项卡**|选择默认情况下应显示的选项卡。 选项包括：<br /><br /> - **活动**<br />- **公告**<br />- **注释**|  
|**格式设置**|**选择控件所占据的栏数**|当包含注释控件的分区有多栏时，可以将字段设置为最多占据分区具有的栏数。|  
||**行数**|通过选择控件占据的行数，控制注释控件的高度。|  
||**自动扩展以利用可用空间**|除了按行数设置高度以外，还可以允许注释控件高度扩展到可用空间。|  
  
## <a name="next-steps"></a>后续步骤
[打开窗体编辑器](open-form-editor.md)
