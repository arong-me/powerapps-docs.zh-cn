---
ms.openlocfilehash: 787ff9592604f9a9bce1929e4d429a39da5ec48a
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456828"
---
若启用 Dynamics 365 Mobile Offline，会基于为脱机可用性启用的实体使用 Azure 云将 Dynamics 365（联机）数据下载至 SQL Azure 数据库。 在用户从具备脱机可用性的移动应用连接至 Azure 云服务时，会将数据从 SQL Azure 数据库下载至移动设备上的本地数据库。 Azure 云上的 SQL Azure 数据库和具备脱机可用性的 Dynamics 365 移动应用之间的数据传输是通过安全的 SSL 连接完成的。 客户数据最终存储在 SQL Azure 数据库中和移动设备上。  
  
 管理员使用安全角色和 Dynamics 365 Mobile 配置文件自定义项确定是否允许组织的用户使用 Microsoft Dynamics 365 Mobile Offline 应用程序脱机执行操作。 Dynamics 365 管理员可以使用“设置 - Mobile Offline”对话框中的“同步筛选器”设置来配置通过“脱机同步”下载的实体。  
  
 请注意，存储在用户设备中的数据由客户（而不是 Microsoft）控制。 管理员对能在用户安全角色级别和实体级别提取的数据具备完全控制权。 提取数据后，数据便在 Dynamics 365 Online 提供的安全边界之外。  
  
 下面提供了与 Mobile Offline 功能相关的 Azure 组件和服务列表。  
  
 **注意：** 有关其他 Azure 服务相关产品/服务的详细信息，请参阅 [Microsoft Azure 信任中心](https://azure.microsoft.com/support/trust-center/)。  
  
 **云服务（Web 角色）**  
  
 Mobile Offline 利用两种云服务，一种用于预配，另一种用于数据同步。  
  
 预配服务通过一个 Web 角色为来自 Dynamics 365 的不同事件（例如预配或取消预配）从服务总线 (SB) 队列读取消息。 然后通过创建/删除组织数据库并将重复工作项（消息）提交至数据同步 SB 队列来处理这些消息。 在此过程中，它从 CSCFG 文件或 Dynamics 365 SW API 读取/写入配置数据。  
  
 数据同步服务有两个 Web 角色。 一个保存与 Dynamics 365 组织的元数据和数据同步的临时数据库的架构和数据，另一个用于运行同步服务器并处理客户端的同步请求。 第一个 Web 角色处理来自不同组织的数据同步 SB 队列的消息，然后联系 Dynamics 365，以便在将元数据和数据更改提交至临时数据库之前获取它们。 它还负责配置组织进入和退出系统及其客户端模型时的同步服务器。 另一个 Web 角色运行同步服务器（非托管代码）以托管管理员终结点和同步终结点。 它使用管理员终结点发送配置数据。 外部客户端（Dynamics 365 Mobile 应用程序）使用同步终结点来进行数据同步。和预配服务一样，这两种角色都从 CSCFG 文件或 Dynamics 365 SW API 读取/写入配置数据。  
  
 **队列**  
  
 Mobile Offline 使用 Azure 队列在 Dynamics 365 和 Azure 之间交换消息。 它用于维护由云服务处理的工作项。 每个消息均存储组织 ID、要向其同步数据的实体名称、组织 OData 终结点的连接字符串等信息。  
  
 **SQL 数据库**  
  
 Mobile Offline 使用 Azure SQL 存储来存储以下内容：  
  
-   来自 Dynamics 365 组织、用于处理客户端同步请求的数据副本。  
  
-   配置数据，例如组织数据库连接字符串。  
  
 **存储**  
  
 Mobile Offline 使用 Azure Blob 存储来存储云服务生成的日志和跟踪信息。  
  
 **Active Directory 服务**  
  
 Mobile Offline 使用 Azure Active Directory 服务来进行其他服务（例如 Dynamics 365、SW API 或 Azure 管理 API）的身份验证。  
  
 **Azure DNS**  
  
 Mobile Offline 使用 Azure DNS 根据组织名称将客户端请求重定向至正确的云服务终结点。  
  
 **Azure 虚拟网络**  
  
 Azure 虚拟网络 (VNet) 是你自己的网络在云中的表示形式。 Dynamics 365 产品团队可以控制你的 Azure 网络设置并定义 DHCP 地址块、DNS 设置、安全策略和路由。  
  
 **Azure 负载均衡器**  
  
 Azure 负载均衡器可为应用程序提供高可用性和优异的网络性能。 这是一种第 4 层（TCP、UCP）型负载均衡器，用于在云服务中的健康服务实例或负载均衡器集中定义的虚拟机之间分配传入流量。 我们将它用于均衡部署中的终结点的负载。