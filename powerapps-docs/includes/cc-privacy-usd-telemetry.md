---
ms.openlocfilehash: 7b58f302f694246564d7073a954ecd53b1b25361
ms.sourcegitcommit: 982cab99d84663656a8f73d48c6fae03e7517321
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2019
ms.locfileid: "67456893"
---
“帮助改进 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)]”功能从安装客户端的计算机上发送 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] 使用情况信息，如操作系统详细信息、浏览器详细信息、特定于 [!INCLUDE[pn_unified_service_desk](../includes/pn-unified-service-desk.md)] 应用程序的信息和 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] 版本。 [!INCLUDE[pn_unified_service_desk](pn-unified-service-desk.md)] 通过与“组织见解”的安全连接将信息发送到 [!INCLUDE[cc_Microsoft](cc-microsoft.md)]，并存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 表存储中。
  
> [!NOTE]
>  组织见解为 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 组织的系统管理员提供了组织使用方式的快速概述。 系统管理员可以查看大多数活跃用户、启动的 SDK 请求数和 SDK 用户正在查看的数量。
  
 下面提供了与“帮助改进 Unified Service Desk”功能相关的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务列表。  
  
> [!NOTE]
>  有关其他 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 服务/产品的详细信息，请参阅 [Microsoft Azure 信任中心](https://azure.microsoft.com/support/trust-center/)。  
  
 [云服务](https://azure.microsoft.com/services/cloud-services/) OrgInsights 数据 REST API（Web 角色）  
  
 此 web 角色可接受来自显示组织见解中数据的图表的请求。 API 从 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 表中读取聚合数据并将其返回。  
  
 [Azure Blob 存储](https://azure.microsoft.com/services/storage/blobs/)  
  
 监视代理（在每个规模组计算机上运行）会收集 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 组织的原始遥测数据，并以 Bond 格式（二进制格式）上传到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中。  
  
 [Azure 表存储](https://azure.microsoft.com/services/storage/tables/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中的原始遥测数据聚合并存储在 Azure 表存储中，由云服务读取。  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 组织见解使用 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 服务对 Web 服务进行身份验证。  
  
 [Azure 服务总线](https://azure.microsoft.com/services/service-bus/)  
  
 每当监视代理将数据上传到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储时，监视代理均会创建消息并对其进行排队。 CMA 管道会获取这些消息来聚合上传的数据。