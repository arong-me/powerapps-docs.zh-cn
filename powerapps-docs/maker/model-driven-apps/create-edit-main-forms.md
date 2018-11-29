---
title: 在 PowerApps 中创建或编辑模型驱动应用程序主窗体 | MicrosoftDocs
description: 了解如何创建或编辑主窗体
ms.custom: ''
ms.date: 05/23/2018
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
ms.assetid: <needs new guid>
caps.latest.revision: 18
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-a-model-driven-app-main-form-for-an-entity"></a>创建或编辑实体的模型驱动应用程序主窗体 

在本主题中，您可以了解如何创建或编辑实体的主窗体。

为实体创建新窗体时，其窗体类型为主要。 打开新窗体时，它等同于名为“信息”的窗体。 可以添加或编辑字段、节、选项卡、导航，以及与窗体关联的属性，然后保存该窗体。

每个主窗体由一个或多个选项卡组成。 每个选项卡可包含一个或多个节。 每个节可包含一个或多个字段或 IFRAMES。 如果要基于现有窗体创建新窗体，则可以克隆一个窗体。 

请确保您具有系统管理员或系统定制员安全角色或等效权限以执行此任务。

## <a name="how-to-create-or-edit-a-main-form"></a>如何创建或编辑主窗体
  
1.   登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。


> [!IMPORTANT]
> “如果**模型驱动**的设计模式不可用，您可能需要[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)。   
  
2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。 

3. 若要创建新的主窗体，在工具栏上选择**添加窗体** > **主窗体**。  
    \-或者- 若要编辑现有的主窗体，请选择**类型**为**主**的任何窗体。
  
3.  根据需要按照以下方式更改窗体设计：
    -   向窗体中添加选项卡
    -   向窗体中添加节
    -   向窗体中添加字段
    -   添加或编辑表单 IFRAME
    -   在窗体上添加或编辑子网格
    -   添加或编辑表单 Web 资源
    -   添加或编辑相关实体的窗体导航
    -   编辑表单页眉和页脚
    -   移除选项卡、节、字段或 IFRAME
    -   启用或禁用表单助理
    
4.  根据需要编辑窗体某些部分的属性：
    -   编辑窗体属性
    -   编辑窗体字段属性
    -   编辑选项卡属性
    -   编辑节属性

5.  根据需要添加事件脚本。 

6.  确定哪些安全角色将能够查看窗体。 详细信息：[为窗体分派安全角色](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)

7.  预览主窗体的显示方式和事件的运行方式：
    - 在**主页**选项卡上，选择**预览**，然后选择**创建表单**、**更新表单**或**只读表单**。
    - 若要关闭“预览”表单，请在**文件**菜单上，选择**关闭**。

8.  编辑完窗体后，选择**另存为**，输入窗体名称，然后选择**确定**。

9.  完成自定义后，发布自定义项：
    -   若要发布您当前编辑组件的自定义项，请在**组件**下，单击使用的实体，然后单击**发布**。
    -   若要同时发布所有未发布组件的自定义项，**组件**选项卡下， 请单击**实体**，然后在命令栏上单击**发布所有自定义项**。
    
 
### <a name="next-steps"></a>后续步骤  
[窗体编辑器用户界面概述](form-editor-user-interface-legacy.md)
 
