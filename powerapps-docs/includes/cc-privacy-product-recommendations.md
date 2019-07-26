---
ms.openlocfilehash: 1cdcb40245aae9a23ecb6d3392e412f8a60b95ba
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2019
ms.locfileid: "67212314"
---
通过启用“产品建议”功能，在从 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 内生成建议模型时，基于已配置的购物篮数据实体及其筛选的历史交易数据将发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 并在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 中进行处理，然后临时保存到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储中，最终发送到 Azure 建议 API 以生成机器学习模型。 使用 Azure 建议 API 生成模型后，将从 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储中删除数据。 请注意，仅向 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 发送 ID（帐户 ID、产品 ID 和交易ID）以生成建议模型。

管理员可在 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 组织中的“设置”&gt;“管理”&gt;“系统设置”&gt;“预览”选项卡下启用产品建议功能。 只有在生成建议模型时，才会将数据发送到 Azure 建议 API。 系统管理员可选择删除现有模型，进而删除与 Azure 建议 API 共享的数据。 此外，系统管理员可删除到 Azure 建议 API 的连接，以停止在将来生成任何建议模型。

以下各部分详细介绍了与产品建议相关的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务。

[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]

[Azure 逻辑应用](https://azure.microsoft.com/services/app-service/logic/)

这提供了所安排的数据管道，以使产品目录和交易数据与建议 API 同步，进而生成建议模型版本。 此管道作为具有多个 API 应用的多租户服务执行，用于在 Dynamics 365 组织与建议 API之间的进行通信。 使用最小上下文（例如模型版本 ID 和 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 组织 URL）从 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 触发逻辑应用。 

[Azure API 应用](https://azure.microsoft.com/services/app-service/api/)

它们是触发 Web 作业的 Web 应用程序，这些作业从 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 组织读取数据并将数据发送到建议 API 以生成建议模型。 存在 3 个 API 应用和相应的 Web 作业：一个用于读取产品数据，一个用于读取交易数据，还有一个用于生成建议模型。 API 应用使用 Web 作业在后台执行实际数据处理操作，并将数据输出写入 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob存储。 数据暂时存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中。 最后，在模型生成后，数据将从 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储中删除。

[Azure 表](https://azure.microsoft.com/services/storage/tables/)

[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 表用于在 API 应用和 Web 作业之间就模型版本和组织上下文进行通信。

[Azure Blob 存储](https://azure.microsoft.com/services/storage/) 

Web 作业将数据临时保存在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob存储中，并在逻辑应用管道执行完毕后删除此数据。

[Azure 建议 API](https://www.microsoft.com/cognitive-services/en-us/recommendations-api)使用最少数据产品 ID、交易 ID 和帐户 ID 发送 Azure 建议 API 以生成建议模型。 数据与建议 API 服务一并存储，直到存在相应的模型版本。
