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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="types-of-entities"></a>实体类型

在面向应用程序的 Common Data Service 中创建或编辑实体之前，应了解存在不同的实体类型。 创建了自定义实体后，就不能更改这些类型。 两种主要的划分基于实体所有权以及实体是否为活动实体。  
  
<a name="BKMK_EntityOwnership"></a>

## <a name="entity-ownership"></a>实体所有权  

有四种不同的实体所有权类型。 在创建自定义实体时，只有**由用户或团队负责**和**由组织负责** 选项，但是，您应该知道，其他实体具有不同的所有权类型。  
  
|所有权|说明|  
|---------------|-----------------|  
|**由业务部门负责**|这些实体中的数据属于业务部门。 对数据的访问可以在业务部门级别控制。|  
|**无**|数据不由其他实体负责。|  
|**由组织负责**|数据属于组织。 对数据的访问在组织级别控制。|  
|**用户或团队负责**|数据属于用户或团队。 可以对这些记录执行的操作可以在用户级别控制。|  
  
  
> [!IMPORTANT]
>  在创建实体后，将无法更改所有权。 在创建实体之前，请务必选择正确的所有权类型。 如果以后确定您的自定义实体必须属于其他类型，必须将其删除并创建一个新的自定义实体。
  
<a name="BKMK_ActivityEntities"></a>

## <a name="activity-entities"></a>活动实体

可以将活动视为可在日历上进行输入的任何操作。 活动具有时间维度（开始时间、停止时间、截止日期和持续时间），可帮助确定操作发生或将要发生的时间。 活动也包含一些数据，可帮助确定活动所代表的操作（例如，主题和说明）。 活动可以处于已打开、已取消或已完成状态。 活动的已完成状态具有几个与之关联的子状态值，用于阐明活动的完成方式。  
  
活动实体可以由用户或团队负责，但不能由组织负责。  
  
下表列出了可在默认的面向应用程序的 CDS 环境中使用的活动实体。
  
|姓名|说明|在活动菜单中显示|参考|
|----------|-----------------|----------------|---------------|  
|**约会**|表示具有开始/结束时间和持续时间的时间间隔的承诺。|是|[约会](/powerapps/developer/common-data-service/reference/entities/appointment)|
|**Email**|使用电子邮件协议传递的活动。|是|[电子邮件](/powerapps/developer/common-data-service/reference/entities/email)|
|**传真**|跟踪传真的呼叫结果和页数并可以选择存储文档的电子副本的活动。|是|[传真](/powerapps/developer/common-data-service/reference/entities/fax)|
|**信件**|跟踪信件传递的活动。 此活动可包含信件的电子副本。|是|[信件](/powerapps/developer/common-data-service/reference/entities/letter)|
|**电话联络**|用于跟踪电话联络的活动。|是|[PhoneCall ](/powerapps/developer/common-data-service/reference/entities/phonecall)|
|**定期约会**|定期约会系列的主约会。|是|[定期约会主体](/powerapps/developer/common-data-service/reference/entities/recurringappointmentmaster)|
|**任务**|表示需要完成的工作的通用活动。|是|[任务](/powerapps/developer/common-data-service/reference/entities/task)|
  
您可以创建新的自定义活动实体。 例如，您可以创建自定义活动实体来记录即时消息通信。 创建活动实体不同于创建非活动实体，因为不指定主要字段。 所有活动实体都有一个设置为**主题**的**主要字段** ，以及活动实体定义的其他公用字段。 这使得所有类型的活动都可以在仅显示公用字段的视图中显示。  

> [!NOTE]
> 您不能使用 PowerApps 门户创建自定义活动。 您必须使用**高级**按钮打开解决方案资源管理器。
  
若要创建自定义活动实体，请选择**定义为活动实体** 。 在选择此选项后，您将看到选择了**在活动菜单中显示** 。 通过此设置，用户可以在活动菜单中创建此类型的活动。 这不是为通常与特定事件关联并使用代码或工作流创建的活动选择的。 保存实体后，将不能更改这些设置。  

### <a name="see-also"></a>另请参阅
[创建或编辑实体](create-edit-entities.md)
