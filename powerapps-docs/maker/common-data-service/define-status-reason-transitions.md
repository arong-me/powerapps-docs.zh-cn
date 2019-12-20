---
title: 使用 Power Apps 定义状态描述转换 | MicrosoftDocs
description: 了解如何定义状态描述转换
ms.custom: ''
ms.date: 05/25/2018
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
ms.assetid: dbc4f436-0b23-42f9-8079-b0de482aaebe
caps.latest.revision: 11
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5dd257a07a21b2d0b0d2a449feb9df855d51d604
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861103"
---
# <a name="define-status-reason-transitions-for-the-case-or-custom-entities"></a>为案例或自定义实体定义状态原因转换

您可以为事件（**案例**）实体或自定义实体指定状态描述转换。

> [!NOTE]
> 虽然事件（案例）实体不包含在默认的 Common Data Service 环境中，它由 [Dynamics 365 for Customer Service](https://dynamics.microsoft.com/customer-service/) 使用，并在[通用数据模型](https://github.com/Microsoft/CDM/blob/master/schemaDocuments/core/applicationCommon/foundationCommon/crmCommon/service/Incident.cdm.json)内定义
  
状态描述转换是一个可选的附加筛选级别，定义了每个状态描述可以更改的状态描述值。 当有大量有效的状态描述值组合时，定义一个有效的选项受限列表可以方便用户为记录选择正确的下一个状态描述。  
  
<a name="BKMK_StatusAndStatusReasons"></a>

## <a name="what-is-the-connection-between-status-and-status-reason-fields"></a>状态和状态描述字段之间的联系是什么？  

可以有不同状态值的实体具有可以捕获此数据的两个字段：  
  
|显示名称|说明|  
|------------------|-----------------|  
|**状态**|表示记录的状态。 通常**可用**或**停用**。 您不可以添加新的状态选项。|  
|**状态描述**|表示链接到特定状态的描述。 每个状态至少有一个可能的状态描述。 您可以添加其他状态描述选项。|  
  
字段的元数据定义对给定状态有效的状态值。 例如，对于事件（**案例**）实体，默认状态和状态描述选项为：  
  
|状态|状态描述|  
|------------|-------------------|  
|**可用**|<li>**正在进行**</li><li>**暂候**</li><li>**等待详情**</li><li>**正在研究**</li>| 
|**已解析**|<li>**问题已解决**</li><li>**提供的信息**</li>|
|**已取消**|<li>**已取消**</li><li>**合并**</li>|
  
  
<a name="BKMK_EditStatusReasonTransitions"></a>   

## <a name="edit-status-reason-transitions"></a>编辑状态描述转换
 
您可以修改案例实体和自定义实体的状态描述字段选项，从而定义用户可以选择的其他状态描述。 唯一的限制是有效状态的每个状态描述选项必须允许至少一个路径到无效状态。 否则，可能会产生无法解析或删除的案例。  

> [!NOTE]
> 编辑状态描述转换需要使用解决方案资源管理器。 有关如何编辑字段的信息，请参阅[使用 Power Apps 解决方案资源管理器创建和编辑 Common Data Service 的字段](create-edit-field-solution-explorer.md)。
  
 在您编辑状态描述字段时，菜单中显示**编辑状态描述转换**按钮。 

![编辑状态描述转换命令](media/status-reason-transitions-command.png)

当您单击此按钮时，**状态描述转换**对话提供一个选项**启用状态描述转换**。 选择此选项后，您需定义每个状态描述允许的*其他*状态描述值。 若要删除应用的筛选，请删除**启用状态描述转换**选择。 您定义的转换会被保留，但不会被应用。  
  
下面的屏幕截图提供满足下列要求的一个示例： 
 
- 可随时合并的案例。 如果状态描述转换不允许，您将无法合并案例。  
- 可随时取消可用案例。  
- 无法重新激活已解析或取消的案例。  
- 所有案例必须通过以下阶段：**正在进行** > **暂候** > **等待详情** > **正在研究**。 该配置使案例无法设置为较早的状态。  
  > [!NOTE]
  >  对实际工作而言这不是一个好示例，但它演示了如何通过状态描述转换强制执行状态阶段。  
  
 ![案例的状态描述转换的示例](media/status-reason-transitions-example.PNG)  
  
### <a name="see-also"></a>另请参阅  

[使用 Power Apps 解决方案资源管理器创建和编辑 Common Data Service 的字段](create-edit-field-solution-explorer.md)<br />
[实体元数据 > 实体状态](/powerapps/developer/common-data-service/entity-metadata#entity-states)<br />
[定义自定义状态模型转换](/dynamics365/customer-engagement/developer/define-custom-state-model-transitions)

