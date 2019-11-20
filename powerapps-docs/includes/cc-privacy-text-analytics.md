通过启用“文本分析”功能，您可在利用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 认知服务文本分析 API 的 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 内启用相关功能以提供高级见解。 这些相关功能包括：  
  
-   知识建议  
  
-   案例主题分析  
  
-   类似案例建议  
  
 管理员可在 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 组织中的**设置** > **管理** > **系统设置** > **预览**选项卡下启用“文本分析”功能。  
  
 通过启用“文本分析”功能，当您在 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 内设置基于文本分析的知识建议时，案例及其相关实体的数据将发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 以提出关键字/关键短语。 未使用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 存储任何数据。 仅在知识文章配置中配置的字段将发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 以提取术语。 管理员或定制员可以选择停用知识文章配置以停止对 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 执行 API 调用。 此外，定制员还可以通过切换到“案例实体窗体”配置中基于字段的建议，以停止使用基于文本分析的建议。  
  
 通过启用“文本分析”功能，当您在 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 内设置案例主题分析时，案例及其相关实体数据将发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 以进行主题确定。 未使用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 存储任何数据。 仅在主题模型配置中配置的字段将发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 以提取主题。 管理员或定制员可以选择停用“主题模型”以停止执行 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 调用。  
  
 通过启用“文本分析”功能，当您在 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 内设置类似案例建议时，如果在相似性规则中启用“高级文本分析”选项，则案例及其相关实体数据将发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 以提取关键字和关键短语。 仅在相似性规则中配置的文本字段将发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API。 未使用 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 存储任何数据。 管理员或定制员可以选择停用“相似性规则”以停止执行 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API 调用。  
  
 以下章节中详细介绍了基于文本分析的功能涉及的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务。  
  
 [!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]  
  
 [Azure API 应用](https://azure.microsoft.com/services/app-service/api/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API 应用触发 Web 作业，这些作业可读取来自 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 组织的数据并将数据发送到文本分析 API 以执行主题分析。 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API 应用 Web 作业来在后台中执行实际数据处理并将数据输出写入到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储。 此数据暂时存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中。 最后，在完成主题确定后，数据将从 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储中立即删除。  
  
 [Azure 计划程序](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 计划程序用于按计划触发 Web 作业以执行主题分析。 仅与此计划程序共享主题模型生成计划。  
  
 [Azure 表](https://azure.microsoft.com/services/storage/)  
  
 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 表用于在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] API 应用和 Web 作业之间的模型版本和组织上下文的通信。  
  
 [Azure Blob 存储](https://azure.microsoft.com/services/storage/)  
  
 Web 作业将数据暂时存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中并在逻辑应用管道完成执行后立即删除数据。  
  
 [Azure 文本分析 API](https://www.microsoft.com/cognitive-services/text-analytics-api)  
  
 数据基于可用的知识搜索字段或主题模型配置或相似性规则配置中配置的字段发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 文本分析 API。 例如，案例实体字段（如标题和描述）以及相关注释和活动中的描述字段将在知识搜索字段配置中进行配置。  
  
 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 相关性搜索  
  
 如果管理员已启用“相关性搜索”功能，则您可以使用此功能查找案例的类似记录。 相似性规则中使用的文本匹配字段和精确匹配字段用于调用相关性搜索 API。 有关数据处理详细信息，请参阅有关 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 相关性搜索的技术内容。