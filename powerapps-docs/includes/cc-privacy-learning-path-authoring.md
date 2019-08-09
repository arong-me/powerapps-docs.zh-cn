通过为 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 组织启用学习路径创作，用户（具有合适的安全权限）创建的学习路径内容（已发布或草稿）将存储在 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] 中。 此外，启用该功能将允许 [!INCLUDE[pn_azure_cloud_services](pn-azure-cloud-services.md)] 捕获与 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 组织关联的下列数据：  
  
-   租户中的组织列表  
  
-   最终用户的 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 客户端和适用浏览器/操作系统配置  
  
-   最终用户的使用情况数据，例如在学习路径上所用的时间或记录的单击操作  
  
-   聚合的最终用户数据 - 位置、安全角色、用户语言  
  
-   聚合的最终用户数据 - 位置、安全角色、用户语言  
  
-   最终用户的逐字反馈  
  
 管理员可以通过**系统设置**对话框的**常规**选项卡上的设置来启用（并可在以后禁用）学习路径创作。  
  
 以下章节中详细介绍了学习路径创作功能涉及的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [云服务](https://azure.microsoft.com/services/cloud-services/)  
  
 **Web 服务**  
  
 Web 服务用作由学习路径运行时呈现在客户端上的控件。 Web 服务还支持设计器 API，这可由学习路径创作使用。 控件由服务存储在 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] 上。  
  
 **编译器（工作人员角色）**  
  
 编译器角色管理将控件发布到发布组。 编译器使用队列来存储有关发布作业的消息。 结果存储在 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] 中。  
  
 [Azure SQL 数据库](https://azure.microsoft.com/services/sql-database/)  
  
 学习路径使用 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] 来存储：  
  
-   使用学习路径创建的控件。  
  
-   与配置相关的学习路径创作。  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 学习路径使用 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 验证 Web 服务。  
  
 [Azure 流量管理器](https://azure.microsoft.com/services/traffic-manager/)  
  
 学习路径使用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 流量管理器对 Web 服务进行负载平衡，从而确保可用性和性能。  
  
 [Azure 存储队列](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储队列用于协调 Web 服务和编译器角色之间的通信。  
  
 [Azure Blob 存储](https://azure.microsoft.com/services/storage/)  
  
 学习路径使用 [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)] 存储静态内容（客户端 [!INCLUDE[pn_JavaScript](pn-javascript.md)]、图像、CSS 内容）。  
  
 [Azure 内容分发网络 (CDN)](https://azure.microsoft.com/services/cdn/)  
  
 CDN 用于缓存客户端静态内容（[!INCLUDE[pn_JavaScript](pn-javascript.md)]、图像和 CSS 文件），以便从全局 CDN 网络提供这些内容。