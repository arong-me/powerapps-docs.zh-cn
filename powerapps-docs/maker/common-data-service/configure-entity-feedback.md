---
title: 使用 PowerApps 配置要反馈的实体 | MicrosoftDocs
description: 了解如何启用实体的反馈
ms.custom: ''
ms.date: 05/18/2018
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
ms.assetid: 5b25cf09-d43b-4165-9eaa-7549f4855e7c
caps.latest.revision: 13
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="configure-an-entity-for-feedbackratings"></a>为反馈/评级配置实体

可通过为实体启用反馈，请客户或员工为任何实体记录撰写反馈，或在定义的评级范围内为实体记录评级。  

此功能通常用于通过门户或调查获取数据的系统。 有关服务或产品满意度的数据可以应用于表示该类数据的实体。

反馈还可以被员工用于提供有关协作的反馈。

> [!NOTE]
> 您需要具有系统管理员或系统定制员安全角色或等效权限以执行这些步骤。
  
## <a name="enable-feedback"></a>启用反馈  
  
编辑实体以启用**反馈**。 详细信息：[编辑实体](edit-entities.md)
  
## <a name="add-a-subgrid-for-feedback-on-the-entity-form"></a>在实体窗体为反馈添加子网格  

默认情况下，用户必须转到要向其添加反馈的记录的关联记录列表。 为了方便用户添加反馈，您可能希望向要为其启用反馈的实体的窗体添加反馈子网格。  

<!-- This is the closest I could find to a topic about adding an subgrid to a form. -->详细信息：[子网格属性概述](../model-driven-apps/sub-grid-properties-legacy.md)

## <a name="add-a-rollup-field--to-the-entity-form-to-show-the-ratings"></a>向实体窗体添加一个汇总字段以显示评级  

根据所需的实体评级计算方法，可以创建用于计算评级的汇总字段，然后添加到要为其启用反馈的实体的窗体中。 详细信息：[定义用于聚合值的汇总字段](define-rollup-fields.md)
  
### <a name="see-also"></a>另请参阅  
 [提交 Dynamics 365 记录的反馈或评级](/dynamics365/customer-engagement/basics/submit-feedback-ratings)
