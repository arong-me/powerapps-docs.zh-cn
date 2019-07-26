---
ms.openlocfilehash: 252f09737dbf55309a64ef5d02d479fde0e61c0e
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224863"
---
“电子邮件参与度”是一项嵌入式智能功能。启用该项功能后，如果从 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 发送了标有“跟踪”设置的电子邮件，则系统将收集收件人与该电子邮件交互的相关信息，并将该信息存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 中，用于计算收件人活动 KPI 以及与“所跟踪”的电子邮件的交互情况。  
  
 系统管理员可通过嵌入式智能服务中的“电子邮件参与度”选项卡预配该功能，以启用“电子邮件参与度”。 之后，管理员可通过“设置”下的“智能配置”节点禁用“电子邮件参与度”。  
  
 如果此功能被禁用，则无论是从用户界面还是以编程方式，都无法跟踪发送自 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 的电子邮件。 此外，也不再就已发送的标有“跟踪”设置的电子邮件收集收件人交互数据。 此前收集的所有数据均保留在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 中，并在组织重新启用该功能后恢复可用状态。 此数据自客户终止其 Microsoft 订阅起保留 90 天。 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 用户还可根据每位联系人或每位潜在客户禁用嵌入式智能功能（即“电子邮件参与度”），方式是更改“联系人首选项”下的“跟踪电子邮件”设置。  
  
 下面详细介绍与电子邮件参与度功能相关的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 **[!INCLUDE[pn_azure_storage_account](pn-azure-storage-account.md)]**  
  
 电子邮件参与度功能使用 [!INCLUDE[pn_azure_storage_account](pn-azure-storage-account.md)] 来暂时存储电子邮件交互 Blob。