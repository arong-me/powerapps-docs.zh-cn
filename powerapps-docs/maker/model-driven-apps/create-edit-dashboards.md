---
title: 创建或编辑模型驱动应用程序仪表板 | MicrosoftDocs
ms.custom: ''
ms.date: 05/23/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
ms.assetid: 641885d2-4a08-41b8-b914-d9a244e4d5b1
caps.latest.revision: 10
ms.author: matp
manager: kvivek
author: Mattp123
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-model-driven-app-dashboards"></a>创建或编辑模型驱动应用程序仪表板

有两类仪表板,用户仪表板和系统仪表板。 应用程序用户可以在其有权访问的应用程序区域创建仅向他们显示的仪表板。 管理员或定制员可以创建或自定义系统仪表板，当仪表板发布时，所有应用程序用户都可以看到。 用户可以选择将其用户仪表板设置为默认仪表板并替代系统仪表板。 本主题重点介绍系统仪表板。  
  
<a name="BKMK_createdashboard"></a>   
## <a name="create-a-new-dashboard"></a>创建新仪表板  
  
1.  登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

    > [!IMPORTANT]
    > “如果**模型驱动**的设计模式不可用，您可能需要[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)。   
  
2. 展开**数据**，选择**实体**，选择您希望仪表板基于的实体，如**客户**实体，然后选择**仪表板**选项卡。 

3. 在工具栏上选择**添加仪表板**，然后选择 2、3 或 4 列布局。  
  
4.  在**仪表板：新建**对话框中输入仪表板名称。  
  
5.  选择某个组件区域然后为图表或列表选择图标。  
  
     仪表板中最多有六个组件。  
  
6.  例如，若要添加图表，请在**添加组件**对话框中，为**记录类型**、**视图**和**图表**选择值，然后选择**添加**以添加图表到仪表板。  
  
7.  当在仪表板中添加完组件后，请选择**保存**和**发布**。  
  
<a name="BKMK_editdashboard"></a>   
## <a name="edit-an-existing-dashboard"></a>编辑现有的仪表板  
  
1. 登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

    > [!IMPORTANT]
    > “如果**模型驱动**的设计模式不可用，您可能需要[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)。    
  
2. 展开**数据**，选择**实体**，选择您希望仪表板基于的实体，如**客户**实体，然后选择**仪表板**选项卡。  

3. 打开仪表板，选择一个组件区域，然后在工具栏上选择**编辑组件**。  
  
4.  在**设置属性**对话框中，您可以对图表或列表进行更改，如更改实体、默认视图，添加图表选择器，或在移动应用程序中提供仪表板。 完成后，请选择**设置**。  
  
     有关设置仪表板组件属性的详细信息，请参阅[设置仪表板包括的图表或列表的属性](set-properties-chart-list-included-dashboard.md)。  
  
4.  当完成所做更改时，请务必保存然后发布它们。  
  
 其他可以执行的系统仪表板任务包括：  
  
    -   从仪表板中移除列表或图表  
  
    -   向仪表板添加列表或图表  
  
    -   设置默认仪表盘  
  
    -   使用安全角色使仪表板只向某些角色显示    
  
## <a name="next-steps"></a>后续步骤  
[设置中仪表板包括的图表或列表的属性](set-properties-chart-list-included-dashboard.md)
