---
ms.openlocfilehash: f331670a2fd6b051c91a7fe2bfa607c54c9ab41a
ms.sourcegitcommit: ad203331ee9737e82ef70206ac04eeb72a5f9c7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/18/2019
ms.locfileid: "67225246"
---
启用 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 即表示你同意允许数据从 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] 流向某些 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 服务以便执行某些营销流程。 这些服务统称为“[!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务”。

若要执行客户旅程，[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 需要将客户旅程、电子邮件、提交表单和营销页面定义发送到 [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)] 上运行的这些 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务。 营销页面会进一步发送到客户自己的 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] 门户功能的实例。

若要个性化设置发送的电子邮件，[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 需要启用与 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 之间的数据流。 有关 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 服务的详细信息，请参阅下文。 流向 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 的数据包括同步到 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 的联系人和帐户。 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务使用此数据来个性化设置电子邮件内容。 包含的数据完全取决于电子邮件定义。

若要重新计算潜在客户评分模型和市场营销细分，[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 需要将潜在客户评分模型定义和细分定义发送到 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]，并在这些计算中利用 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 中的配置文件和交互。

为了提供对 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务捕获的电子邮件和 Internet 交互的见解，收集的数据将从 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务流向 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 和 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]。

另外，如果启用了 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 事件管理集成，[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 会将事件同步到 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]（直接通过 [!INCLUDE[pn-crm-online-shortest](../includes/pn-crm-online-shortest.md)] 的连接器），以及事件注册和签入（通过 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务，作为交互）。

涉及 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 的数据流包括：
- 使用 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 的常规入站连接器使实体数据从 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 流向到 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]，以便为电子邮件个性化设置、潜在客户评分和细分提供内容（主要是联系人和帐户，最终还有潜在客户和事件）
- 通过 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务使实体数据从 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 流向 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]，以便为交互和见解提供标识符（客户旅程、市场营销电子邮件、市场营销页面）
- 从 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务到 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 的交互（电子邮件跟踪、网站跟踪、客户旅程进度）
- 通过 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务从 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 到 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 的交互（事件注册和签入）
- 通过 [!INCLUDE[pn-marketing-app-module](../includes/pn-marketing-app-module.md)] 服务从 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 到 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 的 [!INCLUDE[pn-insights](../includes/pn-insights.md)]（交互和 KPI）（主要是客户旅程、电子邮件发送进度和潜在客户评分结果）
- 从 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 直接到 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 形式的专用和沙盒 UI 元素的 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 应用（分段和小组件）

### <a name="marketing-services"></a>市场营销服务

[!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 使用这些 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 服务：

- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Store
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] Data Lake Analytics
- [!INCLUDE[pn-azure-key-vault](../includes/pn-azure-key-vault.md)]
- [!INCLUDE[pn_azure_service_fabric](../includes/pn_azure_service_fabric.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] DocumentDB
- [!INCLUDE[pn-microsoft-azure-active-directory](../includes/pn-microsoft-azure-active-directory.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 存储

> [!NOTE]
> 有关其他 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 服务产品的详细信息，请参阅 [!INCLUDE[cc_privacy_note_azure_trust_center](../includes/cc_privacy_note_azure_trust_center.md)] (<https://azure.microsoft.com/support/trust-center/>)。

### [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)]

使用 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 即会激活将客户数据传输到 [!INCLUDE[pn-customer-insights-full](../includes/pn-customer-insights-full.md)] 以进行进一步处理。 使用 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] 的 [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] 可能需要遵守特定的隐私法。 如有任何问题，请直接咨询贵组织的相应代表。

目前，[!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] 为公开预览版，并且未提供与 [!INCLUDE[pn-marketing-business-app-module-name](../includes/pn-marketing-business-app-module-name.md)] 或 [!INCLUDE[pn-microsoftcrm](../includes/pn-microsoftcrm.md)] Customer Engagement 相同级别的隐私和安全承诺。 [!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] 本机构建在 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 服务上，并且适用于每种适用的 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 服务的相应符合性和安全性标准均适用。 有关详细信息，请转到 [!INCLUDE[cc-microsoft](../includes/cc-microsoft.md)] 信任中心：[https://azure.microsoft.com/support/trust-center/](https://azure.microsoft.com/support/trust-center/)

[!INCLUDE[pn-customer-insights-short](../includes/pn-customer-insights-short.md)] 使用这些 [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 服务：

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
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 指标
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 网站
- [!INCLUDE[pn_azure_service_bus](../includes/pn_azure_service_bus.md)]
- [!INCLUDE[pn-azure-shortest](../includes/pn-azure-shortest.md)] 存储
