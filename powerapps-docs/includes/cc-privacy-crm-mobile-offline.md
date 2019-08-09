启用 Dynamics 365 Mobile Offline 时，系统会基于针对脱机可用性而启用的实体，使用 Azure 云将 Dynamics 365 (online) 数据下载到 SQL Azure 数据库。 当用户从具有脱机功能的移动应用连接到 Azure 云服务时，数据将从 SQL Azure 数据库下载到移动设备上的本地数据库。 Azure 云上的 SQL Azure 数据库与具有脱机功能的 Dynamics 365 Mobile 应用之间的数据传输通过安全的 SSL 连接实现。 最后，客户数据将存储在 SQL Azure 数据库中以及移动设备上。  
  
 管理员可以通过使用安全角色和 Dynamics 365 Mobile 配置文件自定义来确定是否允许组织用户通过 Microsoft Dynamics 365 Mobile Offline 应用程序来脱机使用 CRM。 Dynamics 365 管理员可以通过使用“设置 - Mobile Offline”对话框中的“同步筛选器”设置来配置通过脱机同步下载哪些实体。  
  
 请注意，存储在用户设备中的数据由客户而非 Microsoft 控制。 管理员对于可以提取的数据具有完全控制权限（在用户安全角色级别或实体级别）。 但是，数据在提取之后便离开了 Dynamics 365 Online 提供的安全边界。  
  
 下面提供了 Mobile Offline 功能涉及的 Azure 组件和服务的列表。  
  
 **注意：** 有关其他 Azure 服务产品的更多信息，请访问 [Microsoft Azure 信任中心](https://azure.microsoft.com/support/trust-center/)。  
  
 **云服务（Web 角色）**  
  
 Mobile Offline 利用了两个云服务，一个用于设置，另一个用于数据同步。  
  
 设置服务具有单个 Web 角色，该角色从服务总线 (SB) 队列中读取来自 Dynamics 365 的不同事件（如设置或取消设置）的消息。 然后，通过创建/删除组织数据库，并在数据同步 SB 队列中提交重复的工作项（消息），来处理这些消息。 在此过程中，该角色会在 CSCFG 文件或 Dynamics 365 SW API 中读取/写入配置数据。  
  
 数据同步服务具有两个 Web 角色。 一个 Web 角色用于让临时数据库的架构和数据与 Dynamics 365 组织的元数据和数据保持同步，另一个 Web 角色用于运行同步服务器和处理客户端的同步请求。 第一个 Web 角色处理数据同步 SB 队列中的不同组织的消息，然后联系 Dynamics 365 以在将元数据和数据更改提交到临时数据库之前获取这些更改。 该角色还负责为出入系统的组织及其客户端模型配置同步服务器。 另一个 Web 角色运行同步服务器（非托管代码）以托管管理员终结点和同步终结点。 管理员终结点供第二个 Web 角色用来发送配置数据。 外部客户端（Dynamics 365 Mobile 应用程序）使用同步终结点进行数据同步。就像设置服务一样，这两个角色都可以从 CSCFG 文件或 Dynamics 365 SW API 中读取/写入配置数据。  
  
 **队列**  
  
 Mobile Offline 使用 Azure 队列来实现 Dynamics 365 和 Azure 之间的消息交换。 它用于维护云服务处理的工作项。 每条消息都存有信息，如组织 ID、要为其同步数据的实体名称以及组织的 OData 终结点的连接字符串。  
  
 **SQL 数据库**  
  
 Mobile Offline 使用 Azure SQL Storage 来存储：  
  
-   从 Dynamics 365 组织复制并用于处理客户端同步请求的数据。  
  
-   配置数据，例如组织数据库连接字符串。  
  
 **存储**  
  
 Mobile Offline 使用 Azure Blob 存储来存储由云服务生成的日志与跟踪数据。  
  
 **Active Directory 服务**  
  
 Mobile Offline 使用 Azure Active Directory 服务来对其他服务（如 Dynamics 365、SW API 或 Azure Management API）进行身份验证。  
  
 **Azure DNS**  
  
 Mobile Offline 使用 Azure DNS 根据组织名称来将客户端请求重定向到正确的云服务终结点。  
  
 **Azure 虚拟网络**  
  
 Azure 虚拟网络 (VNet) 是您自己的网络在云中的表现形式。 Dynamics 365 产品团队可控制您的 Azure 网络设置并定义 DHCP 地址块、DNS 设置、安全策略和路由。  
  
 **Azure 负载均衡器**  
  
 Azure 负载均衡器可为您的应用程序提供较高的可用性和网络性能。 它是一个第 4 层（TCP、UDP）类型的负载平衡器，用于将传入流量分发给云服务中的各个正常运行的服务实例或在负载平衡器集中定义的各个虚拟机。 我们使用它对部署中的终结点进行负载平衡。