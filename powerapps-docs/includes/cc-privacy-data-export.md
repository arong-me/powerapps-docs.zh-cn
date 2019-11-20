通过使用“数据导出服务”，当您在 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 内激活数据导出配置文件时，添加到此配置文件的实体的数据将发送至 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]。 初始同步包含与添加到此导出配置文件的实体关联的所有数据，但之后同步仅包含新更改，这些更新将持续发送至“数据导出服务”。 发送至“数据导出服务”的数据将暂时存储在 [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] 和 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储中，在 [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] 中进行处理，最后同步（插入、更新或删除）至在您的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 订阅中指定的目标数据库。 同步数据之后，数据将从 [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] 和 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储中删除。 如果数据同步期间出现故障，与实体类型、记录 ID 和同步时间戳对应的最小数据将存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储中，以允许下载尚未更新的记录的列表。  
  
 管理员可以随时停用此数据导出配置文件以停止数据同步。 此外，管理员还可以删除此导出配置文件以删除任何失败的记录日志，并且可以卸载“数据导出服务”解决方案以停止使用“数据导出服务”。  
  
 数据同步将以安全方式不断发生在 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 与“数据导出服务”之间。 当数据在 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 和“数据导出服务”之间不断交换时进行加密。  
  
 以下章节中详细介绍了“数据导出服务”涉及的 Azure 组件和服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 这会提供 API 和计算 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] VM 以处理从 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 接收的记录同步通知，然后进行处理以在目标数据库中插入、更新或删除记录数据。 在由 [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] 运行时托管的虚拟机上部署的微服务可处理与数据同步相关的所有计算服务。  
  
 [Azure 服务总线](https://azure.microsoft.com/services/service-bus/)  
  
 这会提供 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 将同步通知消息插入其中的消息总线，这些消息由 [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] 中的计算节点进行处理。 每条消息都存储要同步其数据的组织 ID 和记录等信息。 Azure 服务总线中的数据不是静态加密的，而且只能由数据导出服务访问。  
  
 [Azure Blob 存储](https://azure.microsoft.com/services/storage/)  
  
 如果记录同步通知的数据太大而无法存储在消息中，或者在处理同步通知时遇到瞬间失败，则数据将暂时存储在 [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)] 中。 这些 blob 利用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Storage SDK 中的最新功能进行加密，此 SDK 提供同步和异步加密支持以及与 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] 的集成。  
  
 [Azure SQL](https://azure.microsoft.com/services/sql-database/)  
  
 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] 存储数据导出配置文件配置和数据同步指标。