---
ms.openlocfilehash: 80997689e9d4ebca8eb4809cc3e94dab549482b5
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2019
ms.locfileid: "67224733"
---
通过启用文本分析功能，可在 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 中启用依存功能，这些功能利用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 认知服务文本分析 API 来提供高级见解。 这些依存功能分别是：  
  
-   知识建议  
  
-   案例主题分析  
  
-   类似案例建议  
  
 管理员可通过 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 组织中的“设置” > “管理” > “系统设置” > “预览”选项卡启用文本分析功能。  
  
 通过启用文本分析功能，在 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 中设置基于文本分析的知识建议时，会将案例及其相关实体的数据发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API，用于提取关键字/短语。 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 不存储任何数据。 知识文章配置中只有已配置的字段会被发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 用于提取术语。 管理员或定制员可以选择停用知识文章配置，从而停止对 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 进行 API 调用。 此外，定制员可通过在“案例实体窗体”配置中切换回“基于字段的建议”，停止使用基于文本分析的建议。  
  
 通过启用文本分析功能，在 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 中设置案例主题分析时，会将案例及其相关实体的数据发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API，用于确定主题。 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 不存储任何数据。 主题模型配置中只有已配置的字段会被发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 用于提取主题。 管理员或定制员可选择停用知识文章配置，从而停止进行 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 调用。  
  
 通过启用文本分析功能，在 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 中设置类似案例建议时，如果相似性规则中已启用高级文本分析选项，则会将案例及其相关实体的数据发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API，用于提取关键字和短语。 相似性规则中只有已配置的文本字段会被发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API。 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 不存储任何数据。 管理员或定制员可以选择停用相似性规则配置，从而停止对 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 进行 API 调用。  
  
 以下各节详细介绍了与基于文本分析的功能相关的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure API App](https://azure.microsoft.com/services/app-service/api/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API 应用会触发从 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 组织读取数据的 Web 作业，并将数据发送到文本分析 API 以进行主题分析。 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API 应用使用 Web 作业在后台进行实际数据处理，并将数据输出写入 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储。 数据暂时存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中。 最后，确定完主题后，数据会从 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储中删除。  
  
 [Azure 计划程序](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 计划程序用于按计划触发 Web 作业以执行主题分析。 将仅向计划程序共享主题模型生成计划。  
  
 [Azure 表](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 表用于在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API 应用和 Web 作业之间传送模型版本和组织上下文信息。  
  
 [Azure Blob 存储](https://azure.microsoft.com/services/storage/)  
  
 Web 作业暂时将数据存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中，在逻辑应用管道执行完毕后便将其删除。  
  
 [Azure 文本分析 API](https://www.microsoft.com/cognitive-services/en-us/text-analytics-api)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 基于在活动知识搜索字段、主题模型配置或相似性规则配置中配置的字段发送数据。 例如，案例实体字段（如标题和说明，以及相关备注和活动中的说明字段）在知识搜索字段配置中进行配置。  
  
 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 相关性搜索  
  
 如果管理员已启用相关性搜索，则可以使用它来查找类似的案例记录。 相似性规则中使用的文本匹配字段和完全匹配字段用于调用相关性搜索 API。 请参阅 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 相关性搜索的技术内容，了解数据处理相关详细信息。