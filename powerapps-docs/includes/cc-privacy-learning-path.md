通过启用“学习路径”功能（静态 html），可以将图像和脚本存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 内容分发网络 (CDN) 中。 此外，显示的所有动态内容将存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis 缓存中，后者用于预缓存来自 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL 数据库的数据。  
  
 管理员可以通过在 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 组织中使用“启用引导式帮助”设置来在 [!INCLUDE[pn_crm_online_shortest](pn-crm-online-shortest.md)] 实例中启用和禁用“学习路径”功能。  
  
 以下章节中详细介绍了“学习路径”功能涉及的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务。  
  
> [!NOTE]
>  有关其他 Azure 服务产品的更多信息，请访问 [Microsoft Azure 信任中心](https://azure.microsoft.com/support/trust-center/)。  
  
 [云服务](https://azure.microsoft.com/services/cloud-services/)  
  
 **学习路径运行时（Web 角色）**  
  
 这是为用户提供内容的 Web 应用程序。  
  
 **学习路径服务（工作人员角色）**  
  
 工作人员角色负责处理来自 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL 数据库的数据并将这些数据缓存到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis 缓存中。  
  
 [Azure SQL 数据库](https://azure.microsoft.com/services/sql-database/)  
  
 学习路径使用 SQL 数据库来存储：  
  
-   内容  
  
-   内容元数据  
  
-   系统元数据  
  
 [Azure Blob 存储](https://azure.microsoft.com/services/storage/)  
  
 HTML、图像、[!INCLUDE[pn_JavaScript](pn-javascript.md)] 和 CSS 都存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中。  
  
 [Azure 内容分发网络 (CDN)](https://azure.microsoft.com/services/cdn/)  
  
 学习路径使用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 内容分发网络向调查运行时提供静态内容，例如 HTML、图像、[!INCLUDE[pn_JavaScript](pn-javascript.md)] 和 CSS。  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 学习路径使用 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 服务专门针对设计器对 Web 服务进行身份验证。 当前设计器未对客户和合作伙伴公开。 只有在 [!INCLUDE[cc_Microsoft](cc-microsoft.md)] 域内才能执行身份验证。  
  
 [Azure Redis 缓存](https://azure.microsoft.com/services/cache/)  
  
 学习路径使用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Redis 缓存来缓存我们向用户提供的动态内容。  
  
 [Azure 流量管理器](https://azure.microsoft.com/services/traffic-manager/)  
  
 学习路径使用流量管理器改进重要应用程序的可用性，方法是监视您的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 或外部站点和服务，并且在任何时候出现故障都自动将用户定向到一个新位置。  
  
 [Azure 资源管理器](https://azure.microsoft.com/features/resource-manager/)  
  
 学习路径使用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 资源管理器将 CDN、Redis 缓存、SQL 数据库和云服务部署为资源组，以便这些项目状态一致并且可以重复部署。