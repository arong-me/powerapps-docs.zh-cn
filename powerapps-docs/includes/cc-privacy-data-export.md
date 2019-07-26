---
ms.openlocfilehash: e9b0446c2fb09cad33f5a3ae4bb69103f7d07d70
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212651"
---
通过使用数据导出服务，当从 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 内激活数据导出配置文件时，添加到此配置文件的实体数据将发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]。 初始同步包括所有与添加到导出配置文件的实体关联的数据，但此后同步仅包括会不断发送到数据导出服务的新更改。 发送到数据导出服务的数据将临时存储在 [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] 和 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储中，并在 [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] 中被处理，最后会同步（插入、更新或删除）到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 订阅中指定的目标数据库。 数据同步后，将从 [!INCLUDE[pn_azure_service_bus](pn_azure_service_bus.md)] 和 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储中删除此数据。 如果在数据同步期间出现故障，与实体类型、记录 ID 和同步时间戳相对应程度最低的数据将存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储中，以允许下载未更新的记录列表。  
  
 管理员可以随时停用数据导出配置文件来停止数据同步。 此外，管理员可以删除导出配置文件来删除任何失败的记录日志，并可以卸载数据导出服务解决方案来停止使用数据导出服务。  
  
 数据同步以安全的方式在 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 和数据导出服务之间连续发生。 数据在 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 和数据导出服务之间不断被交换时将处于加密状态。  
  
 以下各节详细介绍了与数据导出服务相关的 Azure 组件和服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc_privacy_note_azure_trust_center.md)]  
  
 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)  
  
 这提供了 API 和计算 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] VM 来处理从 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 接收的记录同步通知，然后对这些通知进行处理以在目标数据库中插入、更新或删除记录数据。 部署在由 [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] 运行时托管的虚拟机上的微服务处理所有与数据同步相关的计算服务。  
  
 [Azure 服务总线](https://azure.microsoft.com/services/service-bus/)  
  
 这将消息总线提供到 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 在其中插入由 [!INCLUDE[pn_azure_service_fabric](pn_azure_service_fabric.md)] 中的计算节点处理的同步通知消息中。 每条消息会存储要为其同步数据的信息，例如组织 ID 和记录。 尽管 Azure 服务总线中的数据在静止时未加密，但数据仅供数据导出服务访问。  
  
 [Azure Blob 存储](https://azure.microsoft.com/services/storage/)  
  
 如果记录同步通知的数据太大而无法存储在消息中，或者在处理同步通知时遇到瞬间失败，则数据会临时存储在 [!INCLUDE[pn_azure_blob_storage](pn_azure_blob_storage.md)] 中。 这些 blob 利用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储 SDK 中的最新功能进行加密，该 SDK 提供对称和非对称的加密支持以及与 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] 的集成。  
  
 [Azure SQL](https://azure.microsoft.com/services/sql-database/)  
  
 [!INCLUDE[pn_Azure_SQL_Database_long](pn-azure-sql-database-long.md)] 存储数据导出配置文件配置和数据同步指标。