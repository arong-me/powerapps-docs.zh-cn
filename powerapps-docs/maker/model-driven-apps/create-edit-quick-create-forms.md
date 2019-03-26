---
title: 在 PowerApps 中创建或编辑模型驱动应用程序的快速创建窗体 | MicrosoftDocs
description: 了解如何创建或编辑快速创建窗体
ms.custom: ''
ms.date: 01/25/2019
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
ms.assetid: 68ca9059-cc5a-45e7-88bd-cc57186bbb48
caps.latest.revision: 18
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="create-or-edit-model-driven-app-quick-create-forms-for-a-streamlined-data-entry-experience"></a>创建或编辑模型驱动应用程序的快速创建窗体以简化数据输入体验

在本主题中，您创建和编辑快速创建窗体。

 使用快速创建窗体，您的应用可以获得精简的数据输入体验，并且完全支持窗体脚本和业务规则定义的逻辑。 在 PowerApps 模型驱动应用程序中，选择导航栏中的**创建**按钮或从查找或子网格创建新记录期间选择 **+ 新建**时，将显示快速创建窗体。
  
 Dynamics 365 Customer Engagement 移动应用使用快速创建窗体创建新记录。 如果已经为实体配置了快速创建窗体，移动应用程序将使用该窗体。 如果没有为实体配置快速创建窗体，PowerApps 将生成快速创建窗体，用于在移动应用程序中基于主窗体定义创建记录。  
  
<a name="BKMK_QuickCreateFormEntities"></a>   
## <a name="entities-with-quick-create-forms"></a>具有快速创建窗体的实体  
 默认情况下，只有以下系统实体有快速创建窗体。  
  
|||||  
|-|-|-|-|  
|客户|市场活动响应|案例|竞争对手|  
|联系人|潜在顾客|商机​​||  
  
虽然您可以为系统活动实体创建快速创建窗体（约会实体除外），但是它们并不支持快速创建窗体。 随着 Dynamics 365 版本 9.0 的发布，约会实体将包括用于统一接口的快速创建窗体。 当前，禁用约会实体的快速创建窗体的选项不受支持。 通过在实体定义中选择**允许快速创建**并为该实体创建快速创建窗体，可以启用任何其他[更新后的实体](create-design-forms.md)以及任何自定义实体以支持这些窗体。 

您可以启用自定义活动实体以支持快速创建窗体，还可以为那些实体创建快速创建窗体。 但是，当用户选择导航栏上的**创建**时，不能使用自定义活动实体的快速创建窗体。 只有当用户为显示指定自定义活动实体的网格添加一个新的记录时，才可以使用这些快速创建窗体。  
  
<a name="BKMK_CreateQuickCreate"></a>   
## <a name="create-a-quick-create-form"></a>创建快速创建窗体  
 虽然您可以定义多个快速创建窗体，但每个人都可以使用的快速创建窗体只有一个。 每个人都将使用的窗体是使用窗体顺序设置的。 不能向快速创建窗体分派安全角色，它们不提供用户切换窗体的功能。  
  
> [!NOTE]
>  - 实体必须为要显示的快速创建窗体启用**允许快速创建**选项。 
>  - 某些字段（如 CREATEDON 字段）不能添加到快速创建窗体。  
  
### <a name="how-to-create-a-quick-create-form"></a>如何创建快速创建窗体  
  
1.  登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。


> [!IMPORTANT]
> “如果**模型驱动**的设计模式不可用，您可能需要[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)。     
  
2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。  

3.  在工具栏上，选择**添加窗体** > **快速创建窗体**。  
  
4.  在窗体设计器中，将任何字段从**字段资源管理器**拖到窗体中的各个分区。  
  
5.  在您完成时，选择**保存**。  
  
6.  选择**发布**查看应用程序中的新窗体。  
  
<a name="BKMK_EditQuickCreate"></a>   
## <a name="edit-a-quick-create-form"></a>编辑快速创建窗体  
 虽然快速创建窗体支持窗体脚本和业务规则，但其目的不同于主窗体，它们并不支持主窗体的所有功能。 快速创建窗体始终有一个三栏分区。 您不能添加额外的分区或栏。  
  
 不能将以下控件添加到快速创建窗体：  
  
-   子网格  
  
-   快速视图窗体  
  
-   Web 资源  
  
-   IFRAMES  
  
-   注释​​  
  
-   必应地图  
  
如果将一个复合字段添加到快速创建窗体，该字段将显示为单独字段。  
  
### <a name="to-edit-a-quick-create-form"></a>编辑快速创建窗体  
  
1.  登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

> [!IMPORTANT]
> “如果**模型驱动**的设计模式不可用，您可能需要[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)。    
  
2. 展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。    

3. 在窗体列表中，选择窗体**类型**为**快速创建**的窗体。  
  
3.  将任何字段从**字段资源管理器**拖到窗体中的各个分区。  
  
     有关编辑窗体脚本的事件处理程序的信息，请参阅[配置事件处理程序](configure-event-handlers-legacy.md)。  
  
4.  在您完成时，选择**保存**。  
  
5.  选择**发布**查看应用程序中修改后的窗体。  
  
### <a name="next-steps"></a>后续步骤  
[窗体编辑器用户界面概述](form-editor-user-interface-legacy.md)
