---
title: 在 PowerApps 中创建或编辑模型驱动应用程序视图 | MicrosoftDocs
description: 了解如何创建或编辑视图
ms.custom: ''
ms.date: 06/11/2018
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
ms.assetid: bd1d393d-16ea-40ac-8136-26643c37dd2a
caps.latest.revision: 25
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-a-model-driven-app-view"></a>创建或编辑模型驱动应用程序视图

<a name="BKMK_CreatingAndEditingViews"></a>   

 在本主题中，您创建新的自定义公共视图。 您还编辑现有视图。  
  
### <a name="create-a-new-view"></a>创建新视图  
  
1.  在 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 站点，选择**模型驱动**（导航窗格的右下方）。  

    ![模型驱动设计模式](media/model-driven-switch.png)

    > [!IMPORTANT]
    > “如果**模型驱动**的设计模式不可用，您可能需要[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)。 

2.  展开**数据**，选择**实体**，选择**客户**实体，然后选择**视图**选项卡。 

3.  在工具栏上，选择**添加视图**。  

4.  在**查看属性**对话框中，提供**名称**，如**有 25 名或以上员工的客户**，也可以为视图添加**描述**，然后选择**确定**。

    > [!div class="mx-imgBorder"] 
    > ![查看属性](media/view-properties.png)
  
5.  在“常规任务”右侧窗格中，选择**添加列**，在**添加列**对话框中选择**员工人数**，然后选择**确定**。  

    > [!div class="mx-imgBorder"] 
    > ![员工人数列](media/column-no-employees.png)
  
6. 在“常规任务”右侧窗格中，选择**编辑筛选条件**，在“编辑筛选条件”对话框中，选择**员工人数**，选择**大于或等于**，然后输入 **25**。  

    > [!div class="mx-imgBorder"] 
    > ![编辑筛选条件](media/edit-filter-criteria.png)

7.  选择**确定**关闭**编辑筛选条件**对话框，然后在视图编辑器中选择**保存并关闭**。  
  
8.  请注意，您的视图现在已在 PowerApps 站点的**视图**选项卡上提供，这让它可以添加到应用程序。
  
### <a name="edit-a-view"></a>编辑视图  
  
1.  从 PowerApps 站点的**视图**选项卡，选择**员工人数**视图。
  
2.  将视图的**名称**更改为**在亚利桑那有 25 名或更多员工人数**，然后选择**确定**。  

3.  在“常规任务”右侧窗格中，选择**添加列**，在**添加列**对话框中选择**地址 1：市/县**，然后选择**确定**。  

4. 在“常规任务”右侧窗格中，选择**编辑筛选条件**，在“编辑筛选器条件”对话框中，再添加一个筛选子句。 选择**地址 2: 省/市/自治区**，选择**等于**，然后输入**亚利桑那**。 

    > [!div class="mx-imgBorder"] 
    > ![地址 2: 省/市/自治区](media/column-address-2-state.png)

5. 选择**确定**关闭**编辑筛选条件**对话框，然后在视图编辑器中选择**保存并关闭**。  
  

## <a name="create-a-new-view-from-an-existing-view"></a>根据现有视图创建新视图  
 按照此过程编辑某个视图，除不选择**保存并关闭**之外，选择**另存为**并为视图输入新的**名称**和**说明**。  
 
### <a name="next-steps"></a>后续步骤
[选择和配置活动](choose-and-configure-columns.md)  
  
[编辑筛选条件](edit-filter-criteria.md)  
  
[配置排序方式](configure-sorting.md)  
