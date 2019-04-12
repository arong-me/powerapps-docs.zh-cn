---
title: 在 PowerApps 中为相关实体添加模型驱动的应用程序窗体导航 | MicrosoftDocs
description: 了解如何为相关实体添加窗体导航
ms.custom: ''
ms.date: 06/18/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Mattp123
ms.assetid: b4098c96-bce1-4f57-804f-8694e6254e81
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="add-model-driven-app-form-navigation-for-related-entities"></a>为相关实体添加模型驱动的应用程序窗体导航

在本主题中，您使用用于添加相关实体的链接的窗体导航窗格。 当应用程序用户单击记录中这些链接之一时，会显示实体的关联视图。   
  
1.  登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

  
    > [!IMPORTANT]
    > “如果**模型驱动**的设计模式不可用，您可能需要[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)。 

2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。 
  
3.  在列表中，打开**主**类型的窗体进行编辑。  
  
4.  若要向相关实体添加链接，请在**主页**选项卡上的**选择**组中选择**导航**。  
  
     将在表单编辑器的右侧打开**关系资源管理器**。  
  
5.  在**关系资源管理器**窗格中，在**筛选器**列表中，选择以下选项之一：  
  
    - **可用关系**。 列出了可与实体（表单与之关联）相关联的所有实体。  
  
    - **1:N 关系**。 列出了在 1:N 关系中可与实体（表单与之关联）相关联的实体。  
  
    - **N:N 关系**。 列出了在 N:N 关系中可与实体（表单与之关联）相关联的所有实体。  
  
    > [!NOTE]
    >  如果相关实体在**关系资源管理器**窗格中未显示，则无法在此表单上创建到相关实体的链接。  
  
6.  选择您想链接的相关实体，将其拖动到导航窗格中，然后将其放到您希望其显示的位置。  
  
    > [!TIP]
    >  还可选择**关系资源管理器**窗格中的**新建 1:N** 或**新建 N:N** 来创建新关系。   
  
7. 若要编辑导航窗格中此实体或任何其他相关实体链接的属性，请选择该链接，然后在**主页**选项卡上选择**更改属性**。  
  
8. 在**关系属性**对话框中的**显示**选项卡上，键入新显示标签。  
  
9. 在**名称**选项卡上，选择**编辑**以查看或编辑与关系记录相关联的详细信息。  
  
10. 选择**确定**。  
  
11. 预览主窗体的显示方式以及事件的运行方式：  
  
    1.  在**主页**选项卡上，选择**预览**，然后选择**创建窗体**、**更新窗体**或**只读窗体**。  
  
    2.  若要关闭**预览**窗体,请在**文件**菜单上，选择**关闭**。  
  
12. 编辑完窗体后，选择**保存并关闭**即可关闭该窗体。  
  
13. 完成自定义后，发布自定义项：  
  
    -   发布您当前编辑组件的自定义项，在导航栏或导航窗格中，选择使用的实体，然后选择**发布**。  
  
    -   若要同时发布所有未发布组件的自定义项，在导航窗格中，请选择**实体**，然后在命令栏上选择**发布所有自定义**。  
  
> [!NOTE]
> 安装解决方案或发布自定义项会干扰常规的系统操作。 我们建议您以对用户造成的干扰最少为宗旨，合理安排解决方案导入时间。
  
## <a name="next-steps"></a>后续步骤  
 [创建和编辑 Common Data Service 的实体关系](../common-data-service/create-edit-entity-relationships.md)
