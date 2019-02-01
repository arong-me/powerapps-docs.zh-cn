---
title: 访问模型驱动的应用程序视图定义 | MicrosoftDocs
description: 在本主题中，您将了解如何访问实体视图
ms.custom: ''
ms.date: 11/27/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Mattp123
ms.assetid: 034c8bef-0d1c-4ef9-8da7-f81343c4553a
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="access-a-model-driven-app-view-definition-in-powerapps"></a>在 PowerApps 中访问模型驱动的应用程序视图定义

 在本主题中，您打开视图定义以显示用于配置视图的属性和选项。 在 PowerApps 中，可以通过多种方法访问视图定义。 
  
  
## <a name="open-a-view-for-editing-in-the-latest-view-designer"></a>在最新视图设计器中打开视图进行编辑

> [!IMPORTANT]
> 最新视图设计器版本现在正处于预览阶段。 尚未支持某些功能，如高级筛选、自定义控件和列属性。 若要完成这些任务，请[在经典视图设计器中打开视图](#open-a-view-in-solution-explorer)。

1.  登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  


    > [!IMPORTANT]
    > “如果**模型驱动**的设计模式不可用，您可能需要[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)。 

2.  展开**数据**，选择**实体**，然后选择所需实体，如**客户**实体。   
3. 选择**视图**选项卡。

    > [!div class="mx-imgBorder"] 
    > ![客户视图定义](media/account-view-definitions.png)

4. 选择要打开的视图，如客户实体**所有客户**视图。

    > [!div class="mx-imgBorder"] 
    > ![所有客户视图](media/account-view-designer.png)

5. 从视图编辑器可执行几项任务： 
 
- [为视图中的记录排序](configure-sorting.md)
- [选择和配置视图中的列](choose-and-configure-columns.md)

## <a name="open-a-view-for-editing-from-a-legacy-web-app"></a>从旧版 Web 应用打开视图进行编辑
在旧版 Web 应用中实体的列表视图上，在选择省略号 (...) 按钮后将在命令栏发现以下命令：  

- **查看**：在默认解决方案中打开当前视图的定义。  
  
- **新系统视图**：在默认解决方案中打开新窗口以创建当前实体的新视图。  
  
- **自定义实体**：在默认解决方案中转到当前实体的定义，您便可以选择**视图**。  
  
- **系统视图**：打开与**自定义实体**相同的窗口，只是**视图**已选择。  

   ![从旧版 Web 应用打开视图编辑器](media/open-view-editor-from-view.png)

## <a name="open-a-view-for-editing-in-solution-explorer"></a>在解决方案资源管理器中打开视图进行编辑 
1.  打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。  
  
2.  在**组件**下，展开**实体**，然后展开所需实体。  
  
3.  选择**视图**。  
  
4.  双击要打开的视图。 这将打开经典视图设计器。
    
    > [!div class="mx-imgBorder"] 
    > ![所有客户视图](media/all-accounts-view.png)

 查看此列表可以使用希望更轻松地查找视图四台筛选器：  
  
- **所有活动视图**  

- **活动公共视图**  

- **非活动公共视图**  

- **活动的系统定义的视图**  
  
 如果与视图关联的实体是非托管解决方案的一部分，仍然可以在默认解决方案中为该实体创建或编辑视图。 系统视图与实体相关联并且作为单独的解决方案组件不可用。 不同于字段，视图不在解决方案中应一致的唯一名称中使用自定义前缀，因此，不需要在解决方案上下文中创建视图。 
 
## <a name="next-steps"></a>后续步骤
[了解视图](create-edit-views.md)


