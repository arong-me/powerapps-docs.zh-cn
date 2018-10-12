---
title: 使用 PowerApps 定义状态描述转换 | MicrosoftDocs
description: 了解如何定义状态描述转换
ms.custom: ''
ms.date: 05/25/2018
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
ms.assetid: dbc4f436-0b23-42f9-8079-b0de482aaebe
caps.latest.revision: 11
ms.author: matp
manager: kvivek
ms.openlocfilehash: e21069a86d2ef21e8209fea6ea4a4b05e604cda4
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668793"
---
# <a name="define-status-reason-transitions-for-the-case-or-custom-entities"></a>为案例或自定义实体定义状态描述转换

可以为事件（**案例**）实体或自定义实体指定状态描述转换。

> [!NOTE]
> 虽然事件（案例）实体未包括在默认 Common Data Service for Apps 环境中，不过它由 [Dynamics 365 for Customer Service](https://dynamics.microsoft.com/customer-service/) 使用并在 [Common Data Service](https://github.com/Microsoft/CDM/blob/master/schemaDocuments/core/applicationCommon/foundationCommon/crmCommon/service/Incident.cdm.json) 中进行定义
  
状态描述转换是可选的附加级别筛选，用于定义对于每个状态描述，状态描述值可以更改为的内容。 当你对于有效状态描述值具有大量组合时，定义有效选项的有限列表可以使用户更容易选择记录的下一个正确状态描述。  
  
<a name="BKMK_StatusAndStatusReasons"></a>

## <a name="what-is-the-connection-between-status-and-status-reason-fields"></a>状态与状态描述字段之间有何连接？  

可以具有不同状态值的实体具有两个可捕获此数据的字段：  
  
|显示名称|描述|  
|------------------|-----------------|  
|**Status**|表示记录的状态。 通常是“活动”或“非活动”。 无法添加新状态选项。|  
|**状态描述**|表示链接到特定状态的描述。 每个状态必须至少具有一个可能的状态描述。 可以添加其他状态描述选项。|  
  
该字段的元数据定义对给定状态有效的状态值。 例如，对于事件（**案例**）实体，默认状态和状态描述选项是：  
  
|状态|状态描述|  
|------------|-------------------|  
|**活动**|<li>**正在进行**</li><li>**暂停**</li><li>**正在等待详细信息**</li><li>**正在研究**</li>| 
|**已解决**|<li>**问题已解决**</li><li>**提供的信息**</li>|
|**已取消**|<li>**已取消**</li><li>**已合并**</li>|
  
  
<a name="BKMK_EditStatusReasonTransitions"></a>   

## <a name="edit-status-reason-transitions"></a>编辑状态描述转换
 
可以修改案例实体和自定义实体的状态描述字段选项，以定义用户可以选择的其他状态描述选项。 唯一限制是活动状态的每个状态描述选项都必须允许存在至少一个非活动状态路径。 否则可以创建无法解决或取消案例的条件。  

> [!NOTE]
> 编辑状态描述转换需要使用解决方案资源管理器。 有关如何编辑字段的信息，请参阅[使用 PowerApps 解决方案资源管理器为 Common Data Service for Apps 创建和编辑字段](create-edit-field-solution-explorer.md)。
  
 当编辑状态描述字段时，“编辑状态描述转换”按钮会处于菜单中。 

![“编辑状态描述转换”命令](media/status-reason-transitions-command.png)

单击此按钮时，“状态描述转换”对话框会提供用于选择“启用状态描述转换”的选项。 选择此选项时，必须定义允许用于每个状态描述的其他状态描述值。 若要删除应用的筛选，请取消选择“启用状态描述转换”。 定义的转换会保留，但不会进行应用。  
  
下面的屏幕截图提供一个满足以下要求的示例： 
 
- 可以随时合并案例。 如果状态描述转换不允许用于案例，则无法合并案例。  
- 可以随时取消活动案例。  
- 无法重新激活已解决或已取消案例。  
- 所有案例都必须经过以下阶段：**正在进行** > **暂候** > **正在等待详细信息** >  **正在研究**，然后才能进行解决。 使用此配置时，案例无法设置为较早的状态。  
  > [!NOTE]
  >  这不是良好的实际工作示例，但它演示了如何通过状态描述转换强制执行状态的各个阶段。  
  
 ![案例的状态描述转换示例](media/status-reason-transitions-example.PNG)  
  
### <a name="see-also"></a>另请参阅  

[使用 PowerApps 解决方案资源管理器为 Common Data Service for Apps 创建和编辑字段](create-edit-field-solution-explorer.md)<br />
[实体元数据 > 实体状态](/powerapps/developer/common-data-service/entity-metadata#entity-states)<br />
[定义自定义状态模型转换](/dynamics365/customer-engagement/developer/define-custom-state-model-transitions)

