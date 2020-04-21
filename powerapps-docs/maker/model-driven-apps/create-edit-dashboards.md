---
title: 创建或编辑模型驱动应用程序仪表板 | MicrosoftDocs
ms.custom: ''
ms.date: 04/08/2020
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
ms.openlocfilehash: bcd178eef75c5ee63389048aff2f1cf0baf01fae
ms.sourcegitcommit: cbaf5ba8b6435796a538ece2da5cc172c0781fad
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2020
ms.locfileid: "3254348"
---
# <a name="create-or-edit-model-driven-app-dashboards"></a>创建或编辑模型驱动应用程序仪表板

有两类仪表板,用户仪表板和系统仪表板。 应用程序用户可以在其有权访问的应用程序区域创建仅向他们显示的仪表板。 管理员或定制员可以创建或自定义系统仪表板，当仪表板发布时，所有应用程序用户都可以看到。 用户可以选择将其用户仪表板设置为默认仪表板并替代系统仪表板。   

仪表板可以是标准仪表板或交互式仪表板。 标准仪表板支持添加一个或多个不相关的组件，如图表或列表。 交互式仪表板使用户能够直接从仪表板对特定记录执行操作。 本主题重点介绍标准的系统仪表板。 有关交互式仪表板的信息，请参阅[配置模型驱动应用交互式体验仪表板](configure-interactive-experience-dashboards.md)。
  
<a name="BKMK_createdashboard"></a>   
## <a name="create-a-new-standard-dashboard"></a>创建新的标准仪表板  
  
1.  登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
  
2. 选择**解决方案**，然后打开您需要的解决方案。

3. 在工具栏上选择**新建**，选择**仪表板**，然后选择 2、3 或 4 列布局。  
  
4.  在**仪表板：新建**页面中输入仪表板名称。  
  
5.  选择某个组件区域然后为图表或列表选择图标。  
  
     仪表板中最多有六个组件。  
  
6.  例如，若要添加图表，请在要显示图表的仪表板区域的磁贴上选择图表图标。 然后，在**添加组件**对话框中，为**记录类型**、**视图**和**图表**选择值，然后选择**添加**以添加图表到仪表板。 有关如何创建图表的信息，请参阅[创建模型驱动应用系统图表](create-edit-system-chart.md)。
  
7.  当在仪表板中添加完组件后，请选择**保存**，然后选择**关闭**。  

8. 在解决方案工具栏中，选择**发布**。 
  
<a name="BKMK_editdashboard"></a>   
## <a name="edit-an-existing-dashboard"></a>编辑现有的仪表板  
  
1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

2. 选择**解决方案**，然后打开您需要的解决方案。  

3. 在解决方案组件列表中，打开仪表板，选择一个组件区域，然后在工具栏上选择**编辑组件**。  
  
4.  在**设置属性**对话框中，您可以对图表或列表进行更改，如更改实体、默认视图，添加图表选择器，或在移动应用程序中提供仪表板。 完成后，请选择**确定**。  
  
     有关设置仪表板组件属性的详细信息，请参阅[设置仪表板包括的图表或列表的属性](set-properties-chart-list-included-dashboard.md)。  
  
5.  当您在工具栏上完成更改后，请选择**保存**，然后选择**关闭**。 

6. 在解决方案工具栏中，选择**发布**。  
  
其他可以执行的系统仪表板任务包括：  
  
-   从仪表板中移除列表或图表  

-   向仪表板添加列表或图表  

-   设置默认仪表盘  

-   使用安全角色使仪表板只向某些角色显示    

## <a name="next-steps"></a>后续步骤  
[设置中仪表板包括的图表或列表的属性](set-properties-chart-list-included-dashboard.md)
