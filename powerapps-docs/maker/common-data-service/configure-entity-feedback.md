---
title: 通过 PowerApps 配置实体进行反馈 | Microsoft Docs
description: 了解如何为实体启用反馈
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
ms.openlocfilehash: efb1cf167353d5928564b42aeb7a49f43cf272d6
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668331"
---
# <a name="configure-an-entity-for-feedbackratings"></a>配置实体进行反馈/评级

让客户或员工为任意实体记录撰写反馈，或通过启用反馈的实体在所定义的评级范围内对实体记录进行评级。  

此功能通常与经门户或调查从客户处捕获数据的系统结合使用。 有关服务或产品满意度的数据可应用于表示该类数据的实体中。

员工也可通过反馈就协作工作进行反馈。

> [!NOTE]
> 要执行这些步骤，需具有系统管理员或系统定制员安全角色或等效权限。
  
## <a name="enable-feedback"></a>启用反馈  
  
编辑实体以启用“反馈”。 详细信息：[编辑实体](edit-entities.md)
  
## <a name="add-a-subgrid-for-feedback-on-the-entity-form"></a>添加子网格以获取有关实体表单的反馈  

默认情况下，用户必须转到要添加反馈的记录的关联记录列表。 为了便于用户添加反馈，可能要将反馈子网格添加到要为其启用反馈的实体表单中。  

<!-- This is the closest I could find to a topic about adding an subgrid to a form. --> 详细信息：[子网格属性概述](../model-driven-apps/sub-grid-properties-legacy.md)

## <a name="add-a-rollup-field--to-the-entity-form-to-show-the-ratings"></a>将汇总字段添加到实体表单以显示评级  

根据要计算实体评级的方式，可创建用于计算评级的汇总字段，然后将其添加到要启用反馈的实体表单中。 详细信息：[定义聚合值的汇总字段](define-rollup-fields.md)
  
### <a name="see-also"></a>另请参阅  
 [提交 Dynamics 365 的反馈或评级](/dynamics365/customer-engagement/basics/submit-feedback-ratings)
