---
title: 在模型驱动的应用程序中应用带业务规则和流程的自定义业务逻辑 | MicrosoftDocs
description: 了解可以在应用中使用的不同类型的业务逻辑
ms.custom: ''
ms.date: 08/02/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.assetid: 0b4e6602-5701-4859-81cc-6f6fe50901b2
caps.latest.revision: 44
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="apply-custom-business-logic-with-business-rules-and-flows-in-model-driven-apps"></a>在模型驱动的应用程序中应用带业务规则和流程的自定义业务逻辑

定义和实施一致的业务流程是人们使用模型驱动应用的主要原因之一。 一致的流程可以帮助确保使用模型驱动的应用程序的用户可以关注其工作，而不是记住执行一套手动步骤。 

## <a name="business-rules"></a>业务规则

业务规则可以提供一个简单的界面来实施和维护快速更改和常用的规则。 业务规则的*范围*定义业务规则的运行位置：

|||  
|-|-|  
|**如果选择此项...**|**范围将设置为...**|  
|**实体**|所有窗体和服务器|  
|**所有窗体**|所有窗体|  
|指定窗体（例如，**客户**窗体）|仅该表单| 

有关在模型驱动的应用程序中为窗体定义业务规则的详细信息，请参阅[创建业务规则以在模型驱动的应用程序窗体中应用逻辑](create-business-rules-recommendations-apply-logic-form.md)

> [!NOTE]
> 若要为实体定义业务规则，以使其在服务器级别同时应用于*画布应用程序*和*模型驱动的应用程序*，请参阅[为实体创建业务规则](/powerapps/maker/common-data-service/data-platform-create-business-rule)。

## <a name="flows"></a>流  
  
Microsoft Flow 中包含针对于不同目的而设计的多种类型的流程：  

-   自动化流。 创建在被事件触发后自动执行一个或多个任务的流。 详细信息：[创建流](/flow/get-started-logic-flow)
    
-   按钮流。 只需点按移动设备上的按钮即可执行重复任务。 详细信息：[引入按钮流](/flow/introduction-to-button-flows)
  
-   计划流。 创建按日程安排（如一天一次）、在特定日期或在某个时间后执行一个或多个任务的流。 详细信息：[按日程安排运行流](/flow/run-scheduled-tasks)
  
-   业务流程。  通过创建业务流程，确保用户输入的数据一致并且每次在应用程序中运行时都遵循相同的步骤。 更多信息：[业务流程概述](/flow/business-process-flows-overview)

-   工作流和操作。 Dynamics 365 customer engagement 定制员可以熟悉面向应用程序的 CDS 经典流程，即工作流和操作。 详细信息：[使用工作流过程](/flow/workflow-processes)和[操作概述](/flow/actions)
  
## <a name="next-step"></a>下一步

[创建业务规则以在模型驱动的应用程序窗体中应用逻辑](create-business-rules-recommendations-apply-logic-form.md)

### <a name="see-also"></a>另请参阅

[通过面向应用程序的 Common Data Service 应用业务逻辑](../common-data-service/cds-processes.md)
