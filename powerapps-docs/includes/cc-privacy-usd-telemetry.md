帮助改进 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)]功能将发送 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] 使用信息，例如操作系统详细信息、浏览器详细信息、[!INCLUDE[pn_unified_service_desk](../includes/pn-unified-service-desk.md)] 应用程序特定的信息以及在其中安装客户端的计算机上的 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] 版本。 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] 通过与组织见解的安全连接将信息发送到 [!INCLUDE[cc_Microsoft](cc-microsoft.md)]，并将信息存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 表存储中。
  
> [!NOTE]
>  [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 组织的系统管理员可以通过组织见解快速了解组织的使用方式概况。 系统管理员可以查看最活跃的用户、发起的 SDK 请求数量以及 SDK 用户查看的次数。
  
 下面提供了“帮助改进 Unified Service Desk”功能涉及的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务的列表。  
  
> [!NOTE]
>  有关其他 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 服务产品的更多信息，请访问 [Microsoft Azure 信任中心](https://azure.microsoft.com/support/trust-center/)。  
  
 [云服务](https://azure.microsoft.com/services/cloud-services/) OrgInsights Data REST API（Web 角色）  
  
 此 Web 角色接受要在组织见解中显示数据的图表请求。 该 API 读取从 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 表汇总的数据并返回这些数据。  
  
 [Azure Blob 存储](https://azure.microsoft.com/services/storage/blobs/)  
  
 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 组织的原始遥测数据通过监视代理（运行在每个 Scale Group 计算机上）收集并以 Bond 格式（二进制格式）上传到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中。  
  
 [Azure 表存储](https://azure.microsoft.com/services/storage/tables/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中的原始遥测数据由云服务读取，并汇总和存储在 Azure 表存储中。  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 组织见解使用 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 服务对 Web 服务进行身份验证。  
  
 [Azure 服务总线](https://azure.microsoft.com/services/service-bus/)  
  
 无论监视代理何时将数据上传到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中，它都会创建消息并将消息加入队列。 这些消息由 CMA 管道选择并与所上传的数据汇总。