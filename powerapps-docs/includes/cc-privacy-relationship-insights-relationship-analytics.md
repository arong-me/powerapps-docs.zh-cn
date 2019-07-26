---
ms.openlocfilehash: 1f6d0eb19a8127e42f1d6a8da8d8c3a452782be0
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456924"
---
通过启用关系分析（嵌入式智能功能），              [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 客户数据（包括用户可识别信息）将发送到并存储在              [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]（Azure 中运行的服务）中，用于计算              [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 用户和客户之间的关系 KPI。 数据也将临时存储在              [!INCLUDE[pn_azure_service_fabric](pn-azure-service-fabric.md)] 中并进行处理以获得额外的输出（例如关系健康状况和趋势），然后将该信息返回              [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)]，随后再返回              [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]。  
  
 管理员可以通过将关系分析功能作为              [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 组织中的解决方案安装来启用此功能。 此外，管理员随后可以通过从              [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 组织卸载此解决方案来禁用此功能。  
  
 通过启用              [!INCLUDE[pn_Exchange](pn-exchange.md)] 数据作为数据源，你将发送              [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 客户数据（包括最终用户可识别信息），从              [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 发送到              [!INCLUDE[pn_Exchange_Online](pn-exchange-online.md)]，以便收集其他数据，这些数据将用于 KPI 计算并创建其他分析。  为了完全启用此功能，你需要让              [!INCLUDE[pn_Office_365](pn-office-365.md)][!INCLUDE[pn_Exchange](pn-exchange.md)] 管理员同意              [!INCLUDE[pn_Exchange](pn-exchange.md)] 应用程序中的单独同意声明。  两位管理员通过适用产品同意后，              [!INCLUDE[pn_Exchange](pn-exchange.md)] 将提供电子邮件和会议元数据，这些元数据将存储在              [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 中，用于改进 KPI 计算以及可能由              [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 管理员决定的其他分析。 在关系分析配置中禁用              [!INCLUDE[pn_Exchange](pn-exchange.md)] 数据作为数据源不会从              [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 中删除              [!INCLUDE[pn_Exchange](pn-exchange.md)] 数据。  删除              [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 中的              [!INCLUDE[pn_Exchange](pn-exchange.md)] 数据只能直接从              [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 完成。  
  
 以下各部分详细介绍了与关系分析相关的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 **[!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]**  
  
 [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)] 是在              [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 中运行的服务，用于存储              [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]数据（包括客户相关的个人身份信息），用于计算关系分析功能的输出。 [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)] 的预览受这些[预览功能的补充使用条款](http://go.microsoft.com/fwlink/p/?LinkId=511446)约束。  
  
 [详细了解 Customer Insights 的预览](https://azure.microsoft.com/services/customer-insights/)。  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 [!INCLUDE[pn_azure_service_fabric](pn-azure-service-fabric.md)] 用于临时存储              [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 数据（包括客户相关的个人身份信息），用于计算关系分析功能的输出。