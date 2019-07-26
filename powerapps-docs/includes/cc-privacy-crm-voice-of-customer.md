---
ms.openlocfilehash: 3fb3961dc88033a44c60c4b6f09124c7c38a11bf
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212788"
---
通过启用 Dynamics 365 的“客户之声”，在从 Dynamics 365 中发布调查时，调查定义将发送到 Azure 并保存在 Azure 存储中。 当答复者提交调查时（通过打开经电子邮件收到的调查邀请链接），调查答复将临时存储在 Azure 服务总线中，然后被检索并存储在 Dynamics 365 中。 答复存储到 Dynamics 365 中之后，将从 Azure 中删除它们。  
  
 请注意，在为答复者显示调查时，可在调查中（在问题和答案等调查元素中）包含 Dynamics 365 数据，例如客户姓名、产品名和案例编号等。 在生成调查邀请链接时，此 Dynamics 365 数据会从 Dynamics 365 发出并存储在 Azure SQL 数据库中，以换取调查邀请链接中使用的标识符。 使用调查邀请链接打开调查后，此标识符用于显示调查中的 Dynamics 365 数据。 通过电子邮件发送给答复者的调查链接中的标识符存储在答复者的电子邮件系统中。  
  
 管理员可启用 Dynamics 365 的“客户之声”功能，方式是在 Dynamics 365 组织中安装该功能作为一种解决方案。 之后，管理员还可从 Dynamics 365 组织卸载此解决方案来禁用此功能。  
  
 以下各部分详细介绍了与 Dynamics 365“客户之声”功能相关的 Azure 组件和服务。  
  
 注意:有关其他 Azure 服务产品的详细信息, 请参阅 Microsoft Azure 信任中心 ([https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/))。  
  
 **云服务** ([- https://azure.microsoft.com/services/cloud-services/](https://azure.microsoft.com/services/cloud-services/))  
  
 **设计器服务（Web 角色）**  
  
 它提供多个 Web 服务，便于 Dynamics 365 组织与 Dynamics 365 Azure 组件的多租户“用户之声”进行通信。  例如，调查将发布并存储到 Azure Blob 存储。  从 Azure 服务总线队列中检索调查答复，并将其返回以保留在 Dynamics 365 组织中。  所有请求都针对 Azure Active Directory 进行身份验证。  
  
 **调查运行时（Web 角色）**  
  
 这是向答复者提供调查的 Web 应用程序。  所提交的调查答复临时存储在 Azure 服务总线队列中，然后由 Dynamics 365 异步服务进行检索。  
  
 **答复处理器（辅助角色）**  
  
 该辅助角色负责将最初已完成的调查处理成可在 Dynamics 365 中创建的有效调查答复。  
  
 **推送处理器 (辅助角色)**  此辅助角色负责处理有效的调查响应并更新为 Dynamics 365 实体记录。 
 
 **Azure Key Vault** ([https://azure.microsoft.com/services/key-vault/](https://azure.microsoft.com/services/key-vault/))  
  
 所有云服务都将配置数据存储在 Azure Key Vault 中。  组织（租户）数据存储在 SQL Azure 中。  
  
 **Azure SQL 数据库** ([https://azure.microsoft.com/services/sql-database/](https://azure.microsoft.com/services/sql-database/))  
  
 Dynamics 365 的“客户之声”功能使用 SQL Azure 存储以下数据：  
  
-   所传送的数据  
  
-   调查元数据  
  
-   组织（租户）数据  
  
 **Azure Blob 存储** ([https://azure.microsoft.com/services/storage/](https://azure.microsoft.com/services/storage/))  
  
 调查定义和部分已完成（已保存）的答复存储在 Azure Blob 存储中。  
  
 **Azure 内容分发网络 (CDN)** ([https://azure.microsoft.com/services/cdn/](https://azure.microsoft.com/services/cdn/))  
  
 Dynamics 365 的“客户之声”解决方案使用 Azure 内容分发网络向调查运行时提供静态内容，例如图像（包括客户徽标等上传的图像）、JavaScript 和 CSS。  
  
 **Azure Active Directory** ([https://azure.microsoft.com/services/active-directory/](https://azure.microsoft.com/services/active-directory/))  
  
 Dynamics 365 的“客户之声”解决方案使用 Azure Active Directory 服务对 Web 服务进行身份验证。  
  
 **Azure 服务总线** ([https://azure.microsoft.com/services/service-bus/](https://azure.microsoft.com/services/service-bus/))  
  
 显示/提交调查时创建的消息临时存储到组织（租户）的 Azure 服务总线队列，直到 Azure 辅助角色将调查答复推送到组织的 Dynamics 365 实例并将其作为 Dynamics 365 实体记录保留。
