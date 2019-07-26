---
ms.openlocfilehash: dff813dcdf6d025ba47e29699e2047f79cf85600
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2019
ms.locfileid: "67225486"
---
通过启用相关性搜索，实例 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 中参与的实体和属性中的数据将开始同步并存储到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 搜索索引中。  
  
 默认情况下不启用相关性搜索。 系统管理员必须在 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 实例中启用该功能。 启用相关性搜索后，对于要同步到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 搜索索引的数据，系统管理员和定制员具有完全控制权。  
  
 系统定制员可以使用“自定义工具”中的“配置相关性搜索”对话框来启用特定的搜索实体，然后在启用的实体上配置“快速查找”视图以选择可搜索的属性。 通过安全连接，实现 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 和 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 搜索之间的持续数据更改同步。  配置数据已加密，所需机密存储在 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] 中。  
  
 以下各节详细介绍了与相关性搜索功能相关的 Azure 组件和服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure 搜索服务](https://azure.microsoft.com/services/search/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 搜索索引用于提供高质量搜索结果，且响应迅速。  [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 搜索为 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 添加了强大且成熟的下一代搜索功能。  这是 [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)] 提供的 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 外部专用搜索服务。 所有新的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 搜索索引都是静态加密的。  如果是在 2018 年 1 月 24 日之前选择加入的，需要重新编制数据索引，方法是选择退出相关性搜索，等待一小时后，再重新选择加入。  
  
 [Azure SQL 数据库](https://azure.microsoft.com/services/sql-database/)  
  
 相关性搜索使用 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] 来存储以下内容：  
  
-   与组织和相应索引相关的配置数据  
  
-   与搜索服务和索引相关的元数据  
  
-   同步更改时指向系统元数据和数据的指针  
  
-   授权数据可提升行级安全性  
  
[Azure 事件中心](https://azure.microsoft.com/services/event-hubs/)  
  
[!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)] 组件用于实现 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 和 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 之间的消息交换，以及维护由同步过程管理的工作项。 每条消息都会存储组织 ID 和实体名称等信息，用于同步数据。  
  
[Azure Service Fabric 群集](https://azure.microsoft.com/services/service-fabric/)  
  
数据处理和索引通过虚拟机上部署的微服务来实现，这些虚拟机通过 Service Fabric 运行时进行管理。 搜索 API 和数据同步进程也托管在 Service Fabric 群集上。  
  
Service Fabric 源自 Microsoft 提供任务关键型云服务的多年经验, 现已在5年内进行生产验证。 这是一项基础性技术，基于此技术，我们可以运行 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 核心基础结构，并为后列服务提供支持：[!INCLUDE[pn_skype_for_business](pn-skype-for-business.md)]、[!INCLUDE[pn_intune](pn-intune.md)]、[!INCLUDE[pn_azure_event_hubs](pn-azure-event-hubs.md)]、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 数据工厂、[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]、[!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] 和 [!INCLUDE[pn_cortana](pn-cortana.md)] - 可扩展到每秒处理超过 5 亿次计算的速度。  
  
[Azure 虚拟机规模集](https://azure.microsoft.com/services/virtual-machine-scale-sets/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 虚拟机规模集具有弹性，支持超大规模横向扩展的工作负载。 [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] 群集在虚拟机规模集上运行。 用于处理和索引数据的微服务托管在规模集上，并由 Service Fabric 运行时管理。  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
[!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] 用于安全管理搜索过程中使用的证书、密钥和其他机密。  
  
[Azure 存储（Blob 存储）](https://azure.microsoft.com/services/storage/blobs/?b=16.38)  
  
对客户数据所做的更改在 [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)] 中最多可存储 2 天。  这些 blob 利用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储 SDK 中的最新功能进行加密，该 SDK 提供对称和非对称的加密支持以及与 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] 的集成。 [!INCLUDE[pn_crm_8_2_0_online_subsequent](pn-crm-8-2-0-online-subsequent.md)] 也会将电子邮件和约会的备注和附件中的文档同步到 blob 存储。  
  
[Azure Active Directory 服务](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 用于在 [!INCLUDE[pn_dynamics_crm_online](pn-dynamics-crm-online.md)] 和 [!INCLUDE[pn_Windows_Azure](pn-windows-azure.md)] 服务之间进行身份验证。  
  
[Azure 负载均衡器](https://azure.microsoft.com/services/load-balancer/)  
  
[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 负载均衡器用于在云服务中的健康服务实例之间或负载均衡器集中定义的虚拟机之间分配传入的流量。 相关性搜索使用它来实现部署中的终结点的负载均衡。  
  
[Azure 虚拟网络](https://azure.microsoft.com/documentation/articles/virtual-networks-overview/)  
  
在一个或多个子网中运行的 Service Fabric 群集上的虚拟机通过 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 虚拟网络进行连接。 此虚拟网络中的安全策略、DNS 设置、路由表和 IP 地址受完全控制。 利用网络安全组在此虚拟网络上应用安全规则。 这些规则会允许或拒绝流向该虚拟网络中 VM 的网络流量。