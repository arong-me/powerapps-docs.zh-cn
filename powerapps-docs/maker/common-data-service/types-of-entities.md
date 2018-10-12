---
title: 实体类型 | MicrosoftDocs
ms.custom: ''
ms.date: 05/30/2018
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
ms.assetid: 2f3f6053-0b9e-41e7-bd94-2239351e9f4b
caps.latest.revision: 41
ms.author: matp
manager: kvivek
ms.openlocfilehash: 60e16ff8cb5c40a37cf0a5243b420f77c4a695bb
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669602"
---
# <a name="types-of-entities"></a>实体类型

创建或编辑 Common Data Service for Apps 中的实体之前，应了解实体有不同的类型。 创建自定义实体后，无法更改这些类型。 两个主要分类基于实体所有权以及实体是否为活动实体。  
  
<a name="BKMK_EntityOwnership"></a>

## <a name="entity-ownership"></a>实体所有权  

有四种不同类型的实体所有权。 创建自定义实体时，唯一的选项是“用户或团队所有”或“组织所有”，但应该意识到，其他实体具有不同的所有权类型。  
  
|所有权|描述|  
|---------------|-----------------|  
|**企业所有**|这些实体中的数据属于业务部门。 可在业务部门级别控制对数据的访问。|  
|**无**|不属于其他实体的数据。|  
|**组织所有**|数据属于组织。 在组织级别控制对数据的访问。|  
|**用户或团队所有**|数据属于用户或团队。 可在用户级别控制对这些记录执行的操作。|  
  
  
> [!IMPORTANT]
>  创建实体后，无法更改所有权。 在创建实体之前，请确保选择正确的所有权类型。 如果之后才确定自定义实体必须是其他类型，则必须将其删除并创建一个新实体。
  
<a name="BKMK_ActivityEntities"></a>

## <a name="activity-entities"></a>Activity 实体

可将活动视为可以在日历上进行输入的任何操作。 活动具有时间维度（开始时间、停止时间、截止日期和持续时间），有助于确定操作发生或即将发生的时间。 活动还包含有助于确定活动所代表的操作的数据，例如主题和描述。 可以打开、取消或完成活动。 活动的完成状态将具有与其关联的若干子状态值，用于阐明活动的完成方式。  
  
活动实体只能为用户或团队所有，不能为组织所有。  
  
下表列出了默认 CDS for Apps 环境中可用的活动实体。
  
|名称|描述|在活动菜单中显示|参考|
|----------|-----------------|----------------|---------------|  
|**Appointment**|代表时间间隔的承诺，包括开始/结束时间和持续时间。|是|[Appointment](/powerapps/developer/common-data-service/reference/entities/appointment)|
|**Email**|使用电子邮件协议传送的活动。|是|[Email](/powerapps/developer/common-data-service/reference/entities/email)|
|**Fax**|跟踪传真呼叫结果和页数并可选择存储文档电子副本的活动。|是|[Fax](/powerapps/developer/common-data-service/reference/entities/fax)|
|**Letter**|跟踪信件发送的活动。 该活动可包含该信件的电子副本。|是|[Letter](/powerapps/developer/common-data-service/reference/entities/letter)|
|**Phone Call**|跟踪电话呼叫的活动。|是|[PhoneCall ](/powerapps/developer/common-data-service/reference/entities/phonecall)|
|**Recurring Appointment**|定期约会系列的主约会。|是|[RecurringAppointmentMaster](/powerapps/developer/common-data-service/reference/entities/recurringappointmentmaster)|
|**Task**|通用活动，代表必须完成的工作。|是|[Task](/powerapps/developer/common-data-service/reference/entities/task)|
  
可创建新的自定义活动实体。 例如，可创建自定义活动实体来记录即时消息通信。 创建活动实体与创建非活动实体不同，因为未指定主要字段。 所有活动实体都具有设置为“主题”的“主字段”以及活动实体定义的其他常用字段。 这允许在仅显示公共字段的视图中显示所有类型的活动。  

> [!NOTE]
> 无法使用 PowerApps 门户创建自定义活动。 必须使用“高级”按钮打开解决方案资源管理器。
  
若要创建自定义活动实体，请选择“定义为活动实体”。 选择此选项后，将看到“在活动菜单中显示”处于选中状态。 这项设置允许人员在活动菜单中创建此类活动。 对于通常与特定事件关联并在使用代码或工作流后创建的活动，则不会选择此选项。 保存实体后，无法更改这些设置。  

### <a name="see-also"></a>另请参阅
[创建或编辑实体](create-edit-entities.md)
