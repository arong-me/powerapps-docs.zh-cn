通过启用“产品建议”功能，当您在 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 内构建建议模型时，基于配置的购物篮数据实体及其筛选器的历史交易记录数据将会发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)]，在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 中进行处理，然后暂时存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储中，并最后发送到 Azure 建议 API 以构建机器学习模型。 在使用 Azure 建议 API 构建此模型后，数据将会从 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储中删除。 请注意，仅 ID（帐户 ID、产品 ID、交易记录 ID）将会发送到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 以构建建议模型。

管理员可在 [!INCLUDE[pn_microsoftcrm](pn-microsoftcrm.md)] 组织中的**设置** &gt; **管理** &gt; **系统设置** &gt; **预览**选项卡下启用“产品建议”功能。 仅当构建建议模型时才会将数据发送到 Azure 建议 API。 系统管理员可以选择删除现有模型以删除与 Azure 建议 API 共享的数据。 此外，系统管理员还可以删除与 Azure 建议 API 的连接以停止在以后构建任何建议模型。

以下章节中详细介绍了“产品建议”涉及的 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 组件和服务。

[!INCLUDE[cc_privacy_note_azure_trust_center](cc-privacy-note-azure-trust-center.md)]

[Azure 逻辑应用](https://azure.microsoft.com/services/app-service/logic/)

这会提供协调的数据管道以将产品目录和交易数据与建议 API 同步，从而构建建议模型版本。 此管道利用多个 API 应用以多租户服务的形式执行，从而在 Dynamics 365 组织与建议 API 之间进行通信。 逻辑应用通过最小上下文（如模型版本 ID 和 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 组织 URL）从 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 中触发。 

[Azure API 应用](https://azure.microsoft.com/services/app-service/api/)

这些是触发 Web 作业的 Web 应用程序，可读取来自 [!INCLUDE[pn_dynamics_crm](pn-dynamics-crm.md)] 组织的数据并将数据发送到建议 API 以构建建议模型。 有 3 种 API 应用和对应的 Web 作业 - 一种用于读取产品数据，一种用于读取交易数据，还有一种则用于构建建议模型。 API 应用使用 Web 作业来在后台中执行实际数据处理并将数据输出写入到 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储。 此数据暂时存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中。 最后，在构建模型后，数据将从 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 存储中立即删除。

[Azure 表](https://azure.microsoft.com/services/storage/tables/)

[!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] 表用于在 API 应用和 Web 作业之间的模型版本和组织上下文的通信。

[Azure Blob 存储](https://azure.microsoft.com/services/storage/) 

数据将由 Web 作业暂时存储在 [!INCLUDE[pn_azure_shortest](pn-azure-shortest.md)] Blob 存储中并在逻辑应用管道完成执行后立即删除。

[Azure 建议 API](https://www.microsoft.com/cognitive-services/recommendations-api) 将最小数据（产品 ID、交易记录 ID 和帐户 ID）发送到 Azure 建议 API 以构建建议模型。 使用建议 API 服务存储数据，直到对应的模型版本存在。
