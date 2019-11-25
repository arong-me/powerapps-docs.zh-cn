---
title: 在 PowerApps 中创建或编辑模型驱动应用程序的快速创建窗体 | MicrosoftDocs
description: 了解如何创建或编辑快速创建窗体
ms.custom: ''
ms.date: 05/14/2019
ms.reviewer: ''
ms.service: powerapps
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
ms.openlocfilehash: b1496fcb600524e7934fe55ca17a7a7bafb54c75
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759148"
---
# <a name="create-or-edit-model-driven-app-quick-create-forms-for-a-streamlined-data-entry-experience"></a>创建或编辑模型驱动应用程序的快速创建窗体以简化数据输入体验

在本主题中，您创建和编辑快速创建窗体。

 使用快速创建窗体，您的应用可以获得精简的数据输入体验，并且完全支持窗体脚本和业务规则定义的逻辑。 在 PowerApps 模型驱动应用程序中，选择导航栏中的**创建**按钮或从查找或子网格创建新记录期间选择 **+ 新建**时，将显示快速创建窗体。
  
 Dynamics 365 移动应用程序使用快速创建窗体创建新记录。 如果已经为实体配置了快速创建窗体，移动应用程序将使用该窗体。 如果没有为实体配置快速创建窗体，PowerApps 将生成快速创建窗体，用于在移动应用程序中基于主窗体定义创建记录。  
  
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
>  - 您还必须将实体和快速创建窗体添加到您的应用中。
>  - 某些字段（如 CREATEDON 字段）不能添加到快速创建窗体。  
  
### <a name="how-to-create-a-quick-create-form"></a>如何创建快速创建窗体  
  
1.  登录到 [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。


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
  
1.  登录到 [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

> [!IMPORTANT]
> 如果**模型驱动**的设计模式不可用，您可能需要[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)。    
  
2. 展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。    

3. 在窗体列表中，选择窗体**类型**为**快速创建**的窗体。  
  
3.  将任何字段从**字段资源管理器**拖到窗体中的各个分区。  
  
     有关编辑窗体脚本的事件处理程序的信息，请参阅[配置事件处理程序](configure-event-handlers-legacy.md)。  
  
4.  在您完成时，选择**保存**。  
  
5.  选择**发布**查看应用程序中修改后的窗体。  

## <a name="allow-quick-create-property-form-behavior-for-activities"></a>活动的“允许快速创建”属性窗体行为
在 9.1.0.2007 更新中引入，**允许快速创建**属性可以为所有标准活动启用或禁用，除定期约会外。 此属性让您可以更改为大部分活动默认显示的窗体。 默认情况下，**允许快速创建**属性启用，快速创建窗体是显示在应用程序区域以及支持它的活动实体中的窗体。 

> [!div class="mx-imgBorder"] 
> ![](media/allow-quick-create.png "Allow Quick Create property on appointment entity")


### <a name="unified-interface-client-form-display-behavior"></a>统一接口客户端窗体显示行为
下表指未当**允许快速创建**属性在统一接口客户端中*启用*时默认显示哪些窗体。
 
|访问窗体的位置  |显示的窗体  |
|---------|---------|
|特定活动关联网格  | 快速创建      |
|特定活动子网格   |  快速创建     |
|活动 (activitypointer) 网格     | 快速创建     |
|活动 (activitypointer) 关联网格   | 快速创建    |
|活动 (activitypointer) 子网格  | 快速创建    |
|全局命令栏 + 按钮<sup>1</sup>    | 快速创建    |
|日程表留言板   | 快速创建    |
|活动 (activitypointer) 网格   | 主要   |
|特定活动网格    | 主要   |

<sup>1</sup>当**允许快速创建**属性启用时，活动出现在全局的**创建**或 **+ 新建**按钮中。 在这种情况下，如果存在快速创建窗体则使用它，如果不存在则使用主窗体。 如果禁用**允许快速创建**，实体条目将不会显示。

### <a name="classic-web-client-form-display-behavior"></a>经典 Web 客户端窗体显示行为

下表指未当**允许快速创建**属性在经典 Web 客户端中*启用*时默认显示哪些窗体。

|访问窗体的位置  |显示的窗体  |
|---------|---------|
|特定活动关联网格  | 快速创建      |
|特定活动子网格   |  快速创建     |
|活动 (activitypointer) 网格     | 主要     |
|活动 (activitypointer) 关联网格   | 主要    |
|活动 (activitypointer) 子网格  | 主要    |
|全局命令栏 + 按钮    | 主要    |
|特定活动网格   | 主要    |

 #### <a name="classic-web-client-social-pane-behavior"></a>经典 Web 客户端社交窗格行为
 
社交窗格是一种特殊情况，因为它不使用**允许快速创建**属性，而使用其他活动实体的其他窗体，如此处所示。


|活动  |显示的窗体  |
|---------|---------|
|任务     | 快速创建    |
|电话联络   | 快速创建     |
|电子邮件   | 主要     |
|约会  | 主要     |
|自定义活动     | 主要      |

### <a name="solution-import-allow-quick-create-value-behavior"></a>解决方案导入“允许快速创建”值行为

在从版本 8.2 导入解决方案，而不管解决方案中的**允许快速创建**属性的值时，以下实体将重置为默认窗体显示值，主窗体将显示：任务、电话联络、电子邮件和约会。 如此一来，您需要在导入后将这些活动实体的**允许快速创建**选项重置回*启用*。
 
如果在版本 9.0 解决方案中对启用了**允许快速创建**的实体进行了自定义，导入后值不会更改。  但是，如果您将**允许快速创建**选项设置为对任务、电话联络、电子邮件和约会实体*禁用*，此值将会被覆盖为启用值。 如此一来，您需要在导入后将这些活动实体的**允许快速创建**选项重置回“禁用”。 
  
### <a name="see-also"></a>另请参阅  
[窗体编辑器用户界面概述](form-editor-user-interface-legacy.md)
