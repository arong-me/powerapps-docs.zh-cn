通过启用“相关性搜索”，您的 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 实例中参与实体和属性的数据将开始同步并将存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 搜索索引中。  
  
 默认情况下不启用“相关性搜索”。 系统管理员必须在 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 实例内启用此功能。 启用“相关性搜索”后，系统管理员和定制员将对将同步到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 搜索索引的数据具有完全控制权。  
  
 系统定制员可使用**自定义工具**中的**配置相关性搜索**对话框启用要搜索的特定实体，然后在已启用的实体上配置“快速查找”视图以选择可搜索的属性。 数据更改将通过安全连接在 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 和 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 搜索之间持续同步。  配置会经过加密并且所需的密码都将存储在 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] 中。  
  
 以下章节中详细介绍了“相关性搜索”功能涉及的 Azure 组件和服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure 搜索服务](https://azure.microsoft.com/services/search/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 搜索索引用于提供高质量的搜索结果和快速的响应时间。  [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 搜索将强大和高级的下一代搜索功能添加到 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)]。  这是 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 外部的专用搜索服务，由 [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)] 提供。 所有新 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 搜索索引均为静态加密。  如果您已选择在 2018 年 1 月 24 日之前加入，您需要按相关性搜索的退出、等待时间和重新加入对数据重新编制索引。  
  
 [Azure SQL 数据库](https://azure.microsoft.com/services/sql-database/)  
  
 相关性搜索使用 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] 来存储：  
  
-   与此组织和对应索引相关的配置数据  
  
-   与搜索服务和索引相关的元数据  
  
-   同步更改时指向系统元数据和数据的指针  
  
-   启用增强型行级安全性的授权数据  
  
[Azure 事件中心](https://azure.microsoft.com/services/event-hubs/)  
  
[!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)] 组件用于 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 和 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 之间的消息交换并维护同步过程管理的工作项。 每条消息都存储用于同步数据的组织 ID 和实体名称等信息。  
  
[Azure Service Fabric Cluster](https://azure.microsoft.com/services/service-fabric/)  
  
数据的处理和索引编制在通过 Service Fabric 运行时托管的虚拟机上部署的微服务中进行处理。 搜索 API 和数据同步过程也托管在 Service Fabric 群集上。  
  
Service Fabric 由 Microsoft 基于多年经验开发而成，提供任务关键型云服务，现在已历经超过五年的生产考验。 它是我们运行 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 核心基础结构的基础技术，提供多种服务支持，包括 [!INCLUDE[pn_skype_for_business](pn-skype-for-business.md)]、[!INCLUDE[pn_intune](pn-intune.md)]、[!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)]、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 数据工厂、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] DocumentDB、[!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] 和 [!INCLUDE[pn_cortana](pn-cortana.md)] - 可以扩展到每秒处理超过 5 亿次计算。  
  
[Azure 虚拟机规模集](https://azure.microsoft.com/services/virtual-machine-scale-sets/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 虚拟机规模集具有弹性，旨在支持超级扩展工作负荷。 [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] 群集在虚拟机规模集上运行。 用于处理数据和编制数据索引的微服务将托管在此规模集上并由 Service Fabric 运行时进行管理。  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
[!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] 用于搜索过程中使用的证书、密钥及其他密钥的安全管理。  
  
[Azure 存储（Blob 存储）](https://azure.microsoft.com/services/storage/blobs/?b=16.38)  
  
对客户数据的更改最多在 [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)] 中存储 2 天。  这些 blob 利用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage SDK 中的最新功能进行加密，此 SDK 提供对称加密和非对称加密支持以及与 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] 的集成。 对于 [!INCLUDE[pn_crm_8_2_0_online_subsequent](pn-crm-8-2-0-online-subsequent.md)]，在电子邮件和约会的注释和附件中找到的文档也会同步到 blob 存储。  
  
[Azure Active Directory 服务](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 用于 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 和 [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)] 服务之间进行身份验证。  
  
[Azure 负载均衡器](https://azure.microsoft.com/services/load-balancer/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Load Balancer 用于将传入流量分发给云服务中的各个正常运行的服务实例或在负载平衡器集中定义的各个虚拟机。 相关性搜索使用它对部署中的终结点进行负载平衡。  
  
[Azure 虚拟网络](https://azure.microsoft.com/documentation/articles/virtual-networks-overview/)  
  
在一个或多个子网中运行的 Service Fabric 群集上的虚拟机通过 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 虚拟网络进行连接。 安全策略、DNS 设置、路由表和 IP 地址在此虚拟网络范围内完全受控。 利用网络安全组将安全规则应用于此虚拟网络。 这些规则允许或拒绝到此虚拟网络中 VM 的网络流量。