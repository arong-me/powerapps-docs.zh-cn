---
ms.openlocfilehash: ac90bfc27e03047cf422c44c83f550608d67b57e
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212856"
---
通过启用 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 的门户功能，可以通过面向外部的 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 门户公开 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 数据，例如客户名称、产品名称、案例编号或任何自定义实体数据。 通过门户公开的任何数据都将存储在 Microsoft [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Web 应用用于进行缓存的内存中，此外还以文件形式存储在本地硬盘上以支持门户搜索功能。

租户管理员通过使用 [!INCLUDE[pn_dyn_365_admin_center](../includes/pn-dyn-365-admin-center.md)]配置 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 门户来启用此门户，此门户还可在所选 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 实例中安装包（含解决方案和数据）。 然后，设置为门户管理员的租户管理员或 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 用户可以指定将通过该门户公开的数据。 若要在随后禁用门户功能，租户管理员可以取消 [!INCLUDE[pn_Office_365](pn-office-365.md)] 的门户附加产品订阅。

门户功能涉及的重要 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务包括：
- [Azure Web 应用](https://azure.microsoft.com/services/app-service/web/):[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]Web Apps 用于在中[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]承载门户。
- [Azure 流量管理器](https://azure.microsoft.com/services/traffic-manager/):[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]流量管理器用于通过将用户路由到启动和运行的 Web 应用来确保服务的高可用性。 
- [Azure 服务总线](https://azure.microsoft.com/services/service-bus/):[!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)](主题/订阅) 用于缓存无效的门户。 [!INCLUDE[pn_azure_service_bus](pn-azure-service-bus.md)]临时存储消息，当 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 中任何与门户相关的记录发生改变时，将触发这些消息，并将消息传递至 Web 应用以执行缓存失效操作。 
- [Azure Key Vault](https://azure.microsoft.com/services/key-vault/):所有服务都将配置数据存储在 [!INCLUDE[pn_azure_key_vault](pn_azure_key_vault.md)] 中。
- [Azure 存储](https://azure.microsoft.com/services/storage/):与组织、租户和门户相关的数据存储在存储中[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 。
- [Azure Active Directory](https://azure.microsoft.com/services/active-directory/):所有 web 服务都用[!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)]来进行身份验证。
