---
title: 在 PowerApps 中使用应用程序设计器创建或编辑模型驱动应用 | MicrosoftDocs
description: 了解如何使用应用程序设计器创建或编辑应用
keywords: ''
ms.date: 05/23/2018
ms.service: crm-online
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
author: Mattp123
ms.assetid: 2a44229e-44f0-4c4e-ba21-a476210d0a12
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: 19
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="tutorial-create-a-model-driven-app-by-using-the-app-designer"></a>教程：使用应用程序设计器创建模型驱动应用

在本教程中，您将了解如何使用基于磁贴的应用程序设计器创建和编辑模型驱动应用程序的基础知识。

## <a name="prerequisites"></a>必备条件 
在开始创建应用程序之前，请先验证以下必备条件：
- PowerApps 环境。 详细信息：[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)
- 系统管理员或系统定制员安全角色： 详细信息：[关于预定义的安全角色](https://docs.microsoft.com/powerapps/maker/model-driven-apps/share-model-driven-app#about-predefined-security-roles)
 
<a name="createApp"></a>   
## <a name="create-an-app"></a>创建应用  

1.  在 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 站点，选择**模型驱动**（导航窗格的右下方）。  

    ![模型驱动设计模式](media/model-driven-switch.png)

    > [!IMPORTANT]
    > “如果**模型驱动**的设计模式不可用，您可能需要[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)。 

2. 选择**应用程序**，然后选择**创建应用程序**。

3. 在**创建新应用**页中，输入以下详细信息： 

    - **名称**：输入应用程序的名称。  
  
    - **唯一名称**：唯一名称根据您指定的应用名称自动填充。 该名称带有发布商前缀。 可以更改可编辑的唯一名称部分。 该唯一名称只能包含英文字符和数字。  
  
        > [!NOTE]
        >  发布商前缀是为具有发布商的解决方案创建的任何实体或字段添加的文本。   
  
    - **说明**：键入应用或其用途的简短说明。  
  
    - **图标**：默认情况下，**使用默认应用**缩略图复选框已选中。 若要选择其他 Web 资源充当该应用的图标，请清除该复选框，然后从下拉列表选择一个图标。 此图标在应用的预览磁贴中显示。  
  
    - 选择应用程序将用于的客户端类型。  
  
        - **统一接口**：这是在 PC 和移动设备中具有相似界面的更新的响应 Web 浏览器客户端。  

        - **Web**：是的经典 Dynamics 365 customer engagement Web 浏览器客户端。  
    
    - **应用 URL 后缀**：应用 URL 根据您指定的应用名称自动填充。 您将看到完整 URL 的外观预览。 应用 URL 必须是唯一的。  
  
         例如：https://\<org>.crm#.dynamics.com/Apps/\<App URL>

         对于本地部署：http://\<server>/\<org name>/Apps/\<App URL> 
  
      > [!NOTE]
      >  如果清除**应用 URL 后缀**字段然后保存应用，将使用应用 ID 自动生成应用 URL。  
  
    - **使用现有解决方案创建应用**：选择此选项将从所安装解决方案列表创建应用。 如果选择此选项，标题中的**完成**将切换为**下一步**。 如果选择 **下一步**，将打开**从现有解决方案创建应用**页。 从**选择解决方案**列表中，选择您要从中创建应用的解决方案。 如果所选解决方案有任何可用站点地图，将显示**选择站点地图**下拉列表。 选择站点地图，然后选择**完成**。

      > [!NOTE]
      > 通过在添加站点地图时选择**默认解决方案**，将把与该站点地图关联的组件自动添加到应用。  

      ![使用现有解决方案创建应用页](media/use-existing-solution-to-create-the-app.png "使用现有解决方案创建应用") 

    - **选择欢迎页**：此选项用于从组织中的可用 Web 资源进行选择。 创建的欢迎页可以包含对用户有用的信息，如视频的链接、升级说明或入门信息。 欢迎页在打开应用程序时显示。 用户可在欢迎页上选择**下次不显示此欢迎屏幕**以禁用此页面，这样应用程序下次启动时不显示。 有关如何创建 Web 资源（如可用作欢迎页的 HTML 文件）的详细信息：[创建和编辑 Web 资源以扩展 Web 应用程序](create-edit-web-resources.md)  
      
    若要以后编辑应用属性，请转到应用设计器中的**属性**选项卡。 详细信息：[管理应用程序属性](manage-app-properties.md)  
  
     > [!NOTE]
     >  可以在**属性**选项卡中更改唯一名称和应用 URL 后缀。  
  
4. 选择**完成**，或者 &mdash; 如果选择了**使用现有解决方案创建应用程序** &mdash; 则单击**下一步**从组织中已导入的可用解决方案中进行选择。  
  
    将创建新应用，并且该新应用显示“草稿”状态。 您将看到新应用的应用设计器区域。 从此处，可以添加组件（如实体、视图和仪表板）来让您的应用程序更有用。 详细信息：[添加或编辑应用程序组件](add-edit-app-components.md)  
   
<a name="editApp"></a>   
## <a name="edit-an-app"></a>编辑应用  
  
1.  在 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 站点，选择**模型驱动**（导航窗格的右下方）。  

> [!IMPORTANT]
> “如果**模型驱动**的设计模式不可用，您可能需要[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)。 

2. 在左侧导航窗格上选择**应用程序**，选择一个应用程序，然后在工具栏上选择**编辑**。   

3. 在应用程序设计器中根据需要向应用程序添加组件或编辑组件。 详细信息：[添加或编辑应用程序组件](add-edit-app-components.md)  
 
  
### <a name="next-steps"></a>后续步骤  
 [添加或编辑应用组件](add-edit-app-components.md)   


