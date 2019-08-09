通过启用“关系分析”这一嵌入式智能功能，[!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 客户数据（包括用户身份信息）将发送并存储到 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]（在 Azure 中运行的一项服务），以便计算 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 用户与客户之间的关系 KPI。 这类数据还将暂时存储在 [!INCLUDE[pn_azure_service_fabric](pn-azure-service-fabric.md)] 中并进行处理以用于其他输出（如关系运行状况和趋势），然后该信息将返回到 [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)]，之后再返回到 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]。  
  
 管理员可通过在 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 组织中以解决方案的形式安装“关系分析”功能来启用此功能。 此外，管理员随后可通过从 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 组织中卸载该解决方案来禁用此功能。  
  
 启用 [!INCLUDE[pn_Exchange](pn-exchange.md)] 数据作为数据源后，您可将 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 客户数据（包括最终用户身份信息）从 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 发送到 [!INCLUDE[pn_Exchange_Online](pn-exchange-online.md)]，以便收集将用于计算 KPI 和创建其他分析的其他数据。  为了完全启用此功能，您需要让 [!INCLUDE[pn_Office_365](pn-office-365.md)][!INCLUDE[pn_Exchange](pn-exchange.md)] 管理员也同意 [!INCLUDE[pn_Exchange](pn-exchange.md)] 应用程序中单独的许可声明。  当两个管理员均通过适用的产品提供了许可，[!INCLUDE[pn_Exchange](pn-exchange.md)] 将提供电子邮件和会议元数据，这些内容将存储在 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 中，用于改进 KPI 计算，并可能用于由 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 管理员决定的其他分析。 在“关系分析”配置中禁用 [!INCLUDE[pn_Exchange](pn-exchange.md)] 数据作为数据源不会从 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 中删除 [!INCLUDE[pn_Exchange](pn-exchange.md)] 数据。  删除 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 中的 [!INCLUDE[pn_Exchange](pn-exchange.md)] 数据只能直接从 [!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)] 中完成。  
  
 以下章节中详细介绍了“关系分析”涉及的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 **[!INCLUDE[pn_customerinsight_full](pn-customer-insights-full.md)]**  
  
 [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)]（在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 中运行的一项服务）存储 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 数据，包括有关客户的个人身份信息，以便针对“关系分析”功能计算输出。 [!INCLUDE[pn_customerinsight_short](pn-customer-insights-short.md)] 的预览版受这些[预览功能补充使用条款](http://go.microsoft.com/fwlink/p/?LinkId=511446)的约束。  
  
 [详细了解 Customer Insights 的预览版](https://azure.microsoft.com/services/customer-insights/)。  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 [!INCLUDE[pn_azure_service_fabric](pn-azure-service-fabric.md)] 用于暂时存储 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 数据，包括有关客户的个人身份信息，以便针对“关系分析”功能计算输出。