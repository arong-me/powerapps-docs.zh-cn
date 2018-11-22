启用 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]，即表示您同意从 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 到特定 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] 服务的数据流，从而执行某些市场营销流程。 这些服务统称为“[!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务”。

若要执行客户旅程，[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 需要向 [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)] 上运行的这些 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务发送客户旅程、电子邮件、提交表单以及市场营销页面定义。 下一步将市场营销页面发送至客户自己的用于 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] 的门户功能实例。

若要对已发送电子邮件进行个性化设置，[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 需要启用 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 的数据流。 请参阅下文，了解有关 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 服务的更多信息。 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 的数据流包含将联系人和客户同步到 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]。 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务使用此数据个性化电子邮件内容。 所包含的数据仅取决于电子邮件定义。

若要重新计算潜在顾客计分模型和市场营销细分，[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 需要将潜在顾客计分模型定义和细分定义发送至 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]，并需要在这些计算中利用 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 中的个人资料和交互。

若要提供对 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务捕获的电子邮件和 Internet 交互的见解，需要将所收集的数据从 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务流向 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 和 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]。

此外，如果 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 活动管理集成已启用，[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 会将活动同步到 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]（直接通过 [!INCLUDE[pn-crm-online-shortest](../includes/pn-crm-online-shortest.md)] 的连接器），并同步活动注册和登记（通过 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务，作为交互）。

涉及 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 的数据流如下：
- 从 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 传输到 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 的实体数据，使用 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 的常规入站连接器，目的是为电子邮件个性化、潜在顾客计分和细分（主要是联系人和客户，最终也是潜在顾客和活动）提供内容
- 通过 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务从 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 传输到 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 的实体数据，目的是为交互和见解（客户旅程、市场营销电子邮件、市场营销页面）提供标识符
- 从 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务传输到 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 的交互（电子邮件跟踪、网站跟踪、客户旅程进度）
- 通过 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务从 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 传输到 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 的交互（活动注册和登记），
- 通过 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务从 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 传输到 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 的 [!INCLUDE[pn-insights](../includes/pn-insights.md)]（交互和 KPI）（主要是客户旅程和电子邮件发送进度，以及潜在顾客计分结果）
- 以 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 形式从 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 直接传入专用沙盒 UI 元素的 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 应用程序（细分和小组件）

### <a name="marketing-services"></a>市场营销服务

[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 使用以下 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 服务：

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] DocumentDB
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 存储

> [!NOTE]
> 有关其他 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 服务产品的更多信息，请参阅 [!INCLUDE[cc_privacy_note_azure_trust_center](../includes/cc_privacy_note_azure_trust_center.md)] (<https://azure.microsoft.com/support/trust-center/>)。

### [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]

通过使用 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)]，可激活将客户数据传入 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 以进行进一步处理。 使用 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] 的 [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] 可能需要遵守特定隐私法律。 如有任何问题，请联系您组织内的相应代表。

[!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] 目前为公开预览版，不提供与 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 或 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] Customer Engagement 相同级别的隐私和安全承诺。 [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] 在 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 服务上本机构建，并需要遵守每种适用的 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 服务各自的合规性和安全标准。 有关更多信息，请转到 [!INCLUDE[cc-microsoft](../includes/cc-microsoft.md)] 信任中心：[https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)

[!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] 使用以下 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 服务：

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] HDInsight（Spark、Phoenix、HBase）
- [!INCLUDE[pn-ms-azure-sql-database](../includes/pn-ms-azure-sql-database.md)]
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 机密存储
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 事件中心
- [!INCLUDE[pn-azure-stream-analytics](../includes/pn-azure-stream-analytics.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Redis 缓存
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 监视
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 度量
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 网站
- [!INCLUDE[pn_azure_service_bus](../includes/pn_azure_service_bus.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 存储
