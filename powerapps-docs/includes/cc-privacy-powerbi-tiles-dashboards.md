---
ms.openlocfilehash: 162e914a6753e9fd95a8ec57857c280469308a68
ms.sourcegitcommit: 9576b34403634a8e960eb5f8e320a14c4a03746c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/17/2019
ms.locfileid: "72517327"
---
通过启用 Power BI 磁贴和仪表板的嵌入功能，当用户嵌入 Power BI 磁贴或仪表板时，该用户的 Common Data Service [!INCLUDE[pn_azure_active_directory](pn-azure-active-directory.md)] 授权令牌将用于通过隐式授权向 Power BI 服务进行身份验证，从而向最终用户提供无缝的“单一登录”体验。  
  
 管理员可随时禁用 Power BI 磁贴和仪表板的嵌入功能，以停止使用 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 授权令牌向 Power BI 服务进行身份验证。 将停止向最终用户显示当前所有的磁贴和仪表板。  
  
 以下部分详细介绍了与 Power BI 磁贴嵌入功能相关的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件或服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)  
  
 此服务提供与 Power BI 服务交换的身份验证令牌用于 API 和 UI 身份验证。
