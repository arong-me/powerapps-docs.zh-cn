---
ms.openlocfilehash: fa4a17c2a3131f49f8a702388bdb405661855c10
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2019
ms.locfileid: "61550010"
---
接受事件管理的条款和条件时，会激活网络研讨会集成功能。 网络研讨会集成功能利用合作伙伴网络研讨会提供商，以网络研讨会形式执行事件或会话。 若要使用任何网络研讨会提供商的服务，必须具有其帐户。 目前提供的唯一现成的合作伙伴网络研讨会提供商服务是 ON24。 使用网络研讨会集成功能时，系统会处理提供和运行网络研讨会所必需的数据并将其存储在 [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)] 上，然后发送到 ON24。 此类数据包含网络研讨会参与者的注册数据，例如其姓名、电子邮件和公司名称。 此外，ON24 会通过 [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)] 向 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] 发送网络研讨会指标（如查看网络研讨会的持续时间）。

无需激活网络研讨会功能，即可使用事件管理解决方案的其余部分。 管理员可通过删除网络研讨会配置中的凭据来关闭网络研讨会集成功能。

网络研讨会集成功能使用的 [!INCLUDE[pn-windows-azure](../includes/pn-windows-azure.md)] 组件和服务包括：

- [!INCLUDE[pn_azure_key_vault](../includes/pn_azure_key_vault.md)]（[!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [什么是 Azure 密钥保管库？](https://docs.microsoft.com/azure/key-vault/key-vault-whatis)）
  - 提供加密密钥，用于加密/解密客户的 ON24 帐户凭据
- [!INCLUDE[pn-azure-service-fabric](../includes/pn-azure-service-fabric.md)]（[!INCLUDE[proc-more-information](../includes/proc-more-information.md)] [Azure Service Fabric 概述](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)）
  - 处理注册数据和网络研讨会帐户凭据并将其发送到 ON24
  - 从 On24 检索网络研讨会指标并将其发送至 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] - 存储客户的 ON24 帐户凭据（自定义加密）