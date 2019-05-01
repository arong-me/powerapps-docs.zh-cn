---
ms.openlocfilehash: 747ea34b784b852261debe91f587d64ee3277804
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61567275"
---
通过安装并启用 [!INCLUDE[pn_gamification](pn-gamification.md)] 解决方案，启用用户的帐户标识符（例如姓、名和电子邮件地址）将存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 中以便进行 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 服务授权（该服务托管于 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 中）。 这适用于由管理员在 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 服务中启用的所有用户。 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 解决方案会将由管理员配置的关键绩效指标 (KPI) 数据发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 服务，这些数据存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 结构化存储以及 blob 存储中。  每个用户的头像、自定义奖励和公司徽标都存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 中，但这些信息不会返回到 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]。  
  
请注意，管理员和授权用户可利用 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 数据（如电话联络、商机和登记的收入）来配置要用于游戏的 KPI。 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 服务并不会调用 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)]，而是仅响应流回 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 的数据，如正在使用 KPI 的游戏。  
  
管理员还可将 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 电视流设为允许公开访问。 设置 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 电视流并启用公共流的游戏经理将允许电视流由 Internet 上具有流链接的任何人查看。  
  
管理员随后可以通过从 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 组织中卸载此解决方案来删除 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 功能。  
  
以下各部分详细介绍了 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 涉及的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务。  
  
[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
[云服务](https://azure.microsoft.com/services/cloud-services/)  
  
 **设计器服务（Web 角色）**  
  
这提供了多种用于 [!INCLUDE[pn_crm_shortest](pn-crm-shortest.md)] 组织与多租户 [!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件之间通信的 Web 服务。 例如，存储到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] SQL Storage 的 Gamification 详细信息。  游戏计算使用 [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)]队列，并返回到该服务中计分和显示。  客户和用户上传的图像存储在 [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)]中。 所有请求都将针对 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 进行身份验证。  
  
[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)  
  
所有服务都将配置数据存储在 [!INCLUDE[pn_azure_key_vault](pn-azure-key-vault.md)] 中。  
  
[Azure SQL 数据库](https://azure.microsoft.com/services/sql-database/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 使用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 来存储：  
  
- KPI 数据  
  
- 游戏计算  
  
- 组织（租户）数据  
  
[Azure Blob 存储](https://azure.microsoft.com/services/storage/)  
  
头像、公司徽标和其他客户上传的图像存储在 [!INCLUDE[pn_azure_blob_storage](pn-azure-blob-storage.md)]中。  
  
[Azure 内容交付网络 (CDN)](https://azure.microsoft.com/services/cdn/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 使用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 内容交付网络向运行时提供静态内容，如图像（包括客户徽标等上传的图像）、[!INCLUDE[pn_JavaScript](pn-javascript.md)] 和 CSS。  
  
[Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
[!INCLUDE[pn_gamification_shortest](pn-gamification-shortest.md)] 使用 [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 对用户进行身份验证并确定其是否有资格使用平台。