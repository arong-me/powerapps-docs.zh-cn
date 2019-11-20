通过安装 [!INCLUDE[pn_connected_field_service_msdyn365](pn-connected-field-service-msdyn365.md)]，当您提供 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 订阅信息时，将部署所需的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 资源（在下面列出）并且您的 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 实例会将数据（例如命令和注册）发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]，以实现支持 IoT 的方案，该方案将注册设备，然后向已注册设备发送命令以及从这些设备接收命令。 管理员可以卸载 Connected Field Service 以删除功能，然后导航回 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 门户来管理任何不再需要的相关 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 服务。  
  
 以下章节中详细介绍了 Connected Field Service 功能涉及的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [服务总线队列](https://azure.microsoft.com/documentation/articles/service-bus-dotnet-get-started-with-queues/)  
  
 这为 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 和 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 之间的入站和出站消息（命令）流提供了队列。 在将 IoT 警报发送到 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 时，或者将命令从 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 发送到 IoT 中心时，将在此处排队。  
  
 [逻辑应用程序](https://azure.microsoft.com/services/logic-apps/)  
  
 这提供了使用 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 连接器和队列连接器的业务流程服务。 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 连接器用于构建特定于 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 的实体，而队列连接器用于轮询队列。  
  
 [流分析](https://azure.microsoft.com/services/stream-analytics/)  
  
 这提供完全托管的实时事件处理引擎，该引擎有助于从数据中发掘深层次的见解。 使用流分析可以轻松地对来自设备、传感器、网站、社交媒体、应用程序、基础结构系统等的数据流设置实时分析计算。 它起到漏斗的作用，将经过挑选的 IoT 警报发送到 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)]。  
  
 [IoT 中心](https://azure.microsoft.com/services/iot-hub/)  
  
 Connected Field Services 使用 IoT 中心来管理已注册设备和资产的状态。 此外，IoT 中心将命令和通知发送到连接的设备，并通过确认收据来跟踪消息传送。 设备消息以持久方式发送，以适应间歇性连接的设备。  
  
 **模拟器**  
  
 这是用于模拟向 IoT 中心发送命令或从 IoT 中心接收命令的设备的 Web 应用程序。  
  
 [Azure SQL 数据库](https://azure.microsoft.com/services/sql-database/)  
  
 Connected Field Service 使用 SQL [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 来存储设备心跳消息，供 PowerBI 以后用于在 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 中显示设备状态。  
  
 [Azure Blob 存储](https://azure.microsoft.com/services/storage/)  
  
 流分析所使用的查询将存储到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中。