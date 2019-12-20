---
title: Power Apps 门户中的版本更新 | MicrosoftDocs
description: 了解 Power Apps 门户的版本更新。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: bbdc9a775c4bfaacc6f99217f6f24ce32db06bca
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "2884461"
---
# <a name="release-updates"></a>版本更新

此主题提供的资源介绍最近发布的新功能和接下来几个月将发布的新功能。

## <a name="power-apps-portals-updates"></a>Power Apps 门户更新

有关可以用于计划的未来几个月内发布的新功能的信息，请参阅：

- [2019 年发行版本第 2 波计划](https://docs.microsoft.com/power-platform-release-plan/2019wave2/microsoft-powerapps/planned-features#portal-capabilities-for-power-apps)

## <a name="previous-portal-updates"></a>以前的门户更新

下面是为 Dynamics 365 门户添加的功能的列表。 有关最新的 Dynamics 365 门户更新的详细信息，请参阅 [Microsoft Dynamics 365 发行版的门户功能](https://support.microsoft.com/help/3181191)。

> [!NOTE]
> Power Apps 门户以前称为 Dynamics 365 门户。

### <a name="dynamics-365-portals-version-914-for-the-model-driven-apps-in-dynamics-365"></a>适用于 Dynamics 365 模型驱动应用的 Dynamics 365 门户版本 9.1.4

适用于 Dynamics 365 模型驱动应用的 Dynamics 365 门户版本 9.1.4 带来了以下新的更新和功能：

- **门户的维护模式**：作为门户管理员，您现在可以配置门户以在每次进行维护活动时都向客户显示适当的消息—例如，解决方案包正在升级。 详细信息：[门户的维护模式](admin/enable-maintenance-mode.md)

- **启用 Power BI Embedded 服务**：作为门户定制员，您现在可以通过启用 Power BI Embedded 服务嵌入在 Power BI 的新工作区创建的仪表板和报表。 使用 powerbi Liquid 标记在门户中的网页上嵌入仪表板和报表。 详细信息：[设置 Power BI 集成](admin/set-up-power-bi-integration.md#enable-power-bi-embedded-service)

- **启用创意内容审核**：作为门户管理员，您现在可以创建内容审核策略来审核在您的门户上提交的创意。

- **OAuth 2.0 隐式授权流**：作为门户开发人员，您现在可以使用 OAuth 2.0 隐式授权流对外部 API 发起客户端 API 调用，并让它们得到保护。 详细信息：[ OAuth 2.0 隐式授权流](oauth-implicit-grant-flow.md)

- **Common Data Service 起点门户（预览）**：作为门户管理员，您现在可以将您的门户配置为连接到 Common Data Service 环境并允许您的用户与其交互。 此功能带来将门户连接到 Common Data Service 环境的能力，此环境内未预安装 Dynamics 365 中的任何模型驱动应用（Dynamics 365 Sales、Dynamics 365 Service 或 Dynamics 365 Marketing）。

### <a name="dynamics-365-portals-version-911-for-the-model-driven-apps-in-dynamics-365"></a>适用于 Dynamics 365 模型驱动应用的 Dynamics 365 门户版本 9.1.1

适用于 Dynamics 365 模型驱动应用的 Dynamics 365 门户版本 9.1.1 带来了以下新的更新和功能：

- **门户检查器**：现在可使用门户检查器通过查看各种配置参数确定门户的问题，并提供有关解决方法的建议。 详细信息：[门户检查器](admin/portal-checker.md)

### <a name="dynamics-365-portals-version-9010-for-the-model-driven-apps-in-dynamics-365"></a>适用于 Dynamics 365 模型驱动应用的 Dynamics 365 门户版本 9.0.10

适用于 Dynamics 365 模型驱动应用的 Dynamics 365 门户版本 9.0.10 带来了以下新的更新和功能：

- **迁移 Dynamics 365 门户配置**：您现在可以将 Dynamics 365 门户配置从开发环境迁移到测试或生产环境。 迁移涉及从源 Dynamics 365 实例中导出现有的配置，然后再将其导入目标 Dynamics 365 实例。 若要迁移配置数据，您需要使用配置迁移工具和门户特定的配置架构文件。 详细信息：[迁移 Dynamics 365 门户配置](admin/migrate-portal-configuration.md)

- **添加 Power BI 可视化效果**：作为门户定制员，您现在可以使用 powerbi Liquid 标记在门户中的网页上嵌入 Power BI 可视化项（仪表板、报表和磁贴）。 详细信息：[设置 Power BI 集成](admin/set-up-power-bi-integration.md)

- **使用 IP 地址限制门户访问**：作为门户管理员，您现在可以定义允许访问您的门户的 IP 地址列表。 在任何用户生成门户请求时，将根据允许列表对其 IP 地址进行评估。 如果 IP 地址不在列表中，门户将显示网页，并附带 HTTP 403 状态代码。 详细信息：[使用 IP 地址限制门户访问](admin/ip-address-restrict.md)

- **管理 SharePoint 文档**：Dynamics 365 门户现在支持直接在门户中的实体窗体和 Web 窗体上从 SharePoint 或向其中上载和显示文档。 这使门户用户可以从门户查看、下载、添加和删除文档。 门户用户还可以创建文件夹来管理文档。 详细信息：[管理 SharePoint 文档](manage-sharepoint-documents.md)

- **新门户内容编辑器（预览）**：在此预览版本中，新的和简化的门户编辑器现在可供 Dynamics 365 门户定制员用来减少 Dynamics 365 门户自定义的学习曲线，并提高定制员的工作效率。

- **为状态描述启用投票**：默认情况下，创意仅在“状态描述”设置为“新”时启用投票。 现在您可以为不同状态描述启用观点投票。 若要为不同状态描述启用投票，则您必须创建 Ideas/EnableVotingForStatusReasons 站点设置，并将其值设置为所需的状态描述值。 

### <a name="dynamics-365-portals-version-906-for-the-model-driven-apps-in-dynamics-365"></a>适用于 Dynamics 365 模型驱动应用的 Dynamics 365 门户版本 9.0.6

适用于 Dynamics 365 模型驱动应用的 Dynamics 365 门户版本 9.0.6 已带来了以下最新的更新和功能：

- **Dynamics 365 门户应用**：Dynamics 365 门户应用提供配置和管理在线平台以与客户沟通和合作的新体验。 在安装 Dynamics 365 门户版本 9.0 和更高版本时，基于统一接口框架构建的 Dynamics 365 门户应用将自动创建。

- **重置门户**：如果您计划移动到其他地理位置或其他租户，且不想再使用该门户，您现在可以重置门户。 在重置门户时，门户的托管资源将被删除，门户 URL 将无法访问。 详细信息：[重置门户](admin/reset-portal.md)

- **更改门户的基础 URL**：在设置门户后，现在可以更改门户的基础 URL。 例如，如果您在设置门户时选择 contosocommunity.microsoftcrmportals.com 作为基础 URL，您以后可以根据要求将其更改为 contosocommunityportal.microsoftcrmportals.com。 详细信息：[更改基础 URL](admin/change-base-url.md)


### <a name="dynamics-365-portals-version-841-for-the-model-driven-apps-in-dynamics-365"></a>适用于 Dynamics 365 模型驱动应用的 Dynamics 365 门户版本 8.4.1

适用于 Dynamics 365 模型驱动应用的 Dynamics 365 门户版本 8.4.1 中增加了大量缺陷修补程序，以及性能改进和以下功能：

- **在知识文章和 Web 文件的附件内容中搜索**：知识文章和 Web 文件的附件内容目前可以搜索以提高相关搜索结果的可能性。 更多信息：[在文件附件内容中搜索](configure/search-file-attachment.md)
- **辅助功能**：现成可用的门户（社区门户、合作伙伴门户、客户门户、员工自助服务门户）现在可以访问。 但是，定制员应该确保在任何自定义或更改后门户仍可访问。


### <a name="dynamics-365-portals-version-84-for-the-model-driven-apps-in-dynamics-365"></a>适用于 Dynamics 365 模型驱动应用的 Dynamics 365 门户版本 8.4

适用于 Dynamics 365 模型驱动应用的 Dynamics 365 门户版本 8.4 中增加了大量缺陷修补程序，以及性能改进和以下功能：

- **访问门户错误日志**：门户开发人员现在可访问详细的错误日志以了解门户中的任何问题。 这有助于在开发门户时调试问题。 门户投入使用后，可以配置门户以将任何应用程序错误发送到您负责的 Azure Blob 存储帐户中。 这样有助于调试客户报告的问题。 详细信息：[访问门户错误日志](admin/view-portal-error-log.md)
- **续订门户身份验证密钥**：门户使用 Azure Active Directory 应用程序连接到 Common Data Service 环境。 为此，需要连接到 Azure Active Directory 应用程序的身份验证密钥。 该密钥是在您配置门户时添加的，必须每隔两年续订。 此版本的门户引入了通知管理员密钥到期并从 Power Apps 门户管理中心续订该密钥的功能。 详细信息：[续订门户身份验证密钥](admin/manage-auth-key.md)
- **在门户中实施全面数据保护法规**：门户管理员现在可以配置门户以满足 GDPR 标准。 也可以提供门户用户使用门户必须同意的特定条款和条件。 也可以设置检查，例如，如果低龄用户访问门户，该用户必须得到父母的同意才能访问门户。 通过实施 GDPR，可以获得门户用户的以下同意：使用其个人数据、识别低龄用户和获得低龄用户的父母同意。 详细信息：[在门户中实施 GDPR](configure/implement-gdpr.md)

### <a name="dynamics-365-portals-version-83-for-the-model-driven-apps-in-dynamics-365"></a>适用于 Dynamics 365 模型驱动应用的 Dynamics 365 门户版本 8.3

适用于 Dynamics 365 模型驱动应用的 Dynamics 365 门户版本 8.3 具有许多新的更新和功能：

- **可在知识文章中添加附件**：可在显示知识文章时一并显示注释附件。 若要启用此功能，请创建站点设置 KnowledgeManagement/DisplayNotes 并将值设置为 **true**。 门户用户也可以搜索这些附件。 详细信息：显示知识文章的文件附件

  > [!Note]
  > 只能对注释描述和文件附件名称执行附件搜索。 无法搜索附件文件的内容。
  
- **用于将实体添加到门户的管理向导**：此功能引进了用于轻松公开门户上的数据的新的管理向导。 通过向导创建的实体从您的组织搜集数据并基于您选择的安全性和权限模型将数据子集提供给您的门户客户。

- **导入元数据翻译**：此功能用于导入安装门户后新激活的语言的元数据翻译。 详细信息：[导入元数据翻译](admin/import-metadata-translation.md)

- **门户的源代码可用性**：Dynamics 365 门户代码的一次性发布版本在 MIT 许可证下发布到 Microsoft 下载中心以供开发人员下载。 此功能允许将门户部署到 Dynamics 365 On-premises 或联机环境，并允许开发人员自定义代码以适合他们的特定业务需要。

  > [!NOTE]
  > 源代码作为工作示例根据需要提供。 对代码的任何修改不提供直接支持。

- **Azure Active Directory B2C (Azure AD B2C) 单一登录 (SSO) 配置改善和支持**：对于需要基于消费者的登录的门户，该功能现在支持以下功能：
  - 将门户身份验证配置为使用 SSO。 
  - 支持 Azure AD B2C 进行客户身份验证。
  - 在 Azure 中管理门户安全性。

  详细信息：[门户的 Azure AD B2C 提供程序设置](configure/azure-ad-b2c.md)

- **支持门户表单中与时区&ndash;无关的日期格式**：此功能将日期/时间字段的**仅限日期**和**时区无关**行为的支持添加到门户。 详细信息：[日期及时间字段的行为和格式](configure/behavior-format-date-time-field.md)

- **允许非全局管理员设置门户**：如果您被分派到为门户选择的 CRM 组织的系统管理员角色，您现在可以设置门户。 如果您具有以下任何一个角色，您现在还可以管理现有门户：
  - Dynamics 365 服务管理员
  - 为门户选择的 CRM 组织的系统管理员

- **存储门户的自定义域名**：该功能在网站记录上存储门户的主域名。 如果将来更改域名，则将存储最新的主域名。

- **跟踪门户的 Cookie**：当用户在任何时候访问门户时，设置永久 Cookie Dynamics365PortalAnalytics。 该 Cookie 在 90 天后到期。 该 Cookie 不存储用户的任何个人数据，且 Microsoft 用它来收集有关门户服务的分析。 请在[此处](https://go.microsoft.com/fwlink/p/?linkid=856855)阅读有关 Microsoft Online Services 隐私声明的详细信息。

- **门户上的页眉和页脚的性能改进**：已添加两个新的站点设置：Header/OutputCache/Enabled 和 Footer/OutputCache/Enabled，当这些设置设置为 true 时启用页眉/页脚输出缓存。 对于新用户，这些设置在默认情况下设置为 True，从而启用页眉和页脚输出缓存。 对于升级到更高版本 Dynamics 365 门户的现有用户，默认情况下禁用输出缓存。 这意味着在每一次页面加载时分析和呈现页眉和页脚 Web 模板。 若要启用输出缓存，必须更新相应的 Web 模板并创建所需的站点设置。 详细信息：[启用页眉和页脚输出缓存](configure/enable-header-footer-output-caching.md)

### <a name="december-2016-updates"></a>2016 年 12 月更新

2016 年 12 月更新为 Dynamics 365 门户功能带来了大量新功能。 这些更新可以改善公司、合作伙伴和客户之间的交互，并加快和简化门户的导航体验。 下面是部分重大更新：

- **多语言支持：** 通过一个门户为多个地区的客户提供支持。 详细信息：[启用多语言支持](configure/enable-multiple-language-support.md)
- **东亚语言支持：** 现在支持多字节语言，如日语、中文和韩文。
- **分面搜索：** 新筛选器加快客户找到查找的内容的速度，同时提高对内容可视性的控制程度。 详细信息：[分面搜索](configure/improve-portal-search-faceted-search.md)
- **产品筛选：** 门户用户可以访问与其产品所有权有关的知识文章，以免信息过多。
- **内容访问级别：** 与门户联系人、客户或 Web 角色关联的新的所有权级别可用来控制对知识文章的访问权限，以帮助面向正确的访问群体定位合适的文章，避免呈现不相关的文章。 更多信息：[内容访问级别](https://docs.microsoft.com/dynamics365/portals/manage-knowledge-articles-content-levels)
- **知识文章报告增强：** 门户跟踪知识文章在门户中的使用位置。
- **Project Service Automation 集成**：在项目生命周期的所有阶段向合作伙伴和客户提供活动和已关闭项目的访问权限和可视性。 团队成员、审核者和客户可通过此解决方案在门户中查看项目状态、报价单、订单论坛和可预订资源。 详细信息：[集成 Project Service Automation](https://docs.microsoft.com/dynamics365/portals/integrate-project-service-automation)
- **Field Service 集成：** 向合作伙伴和客户提供有关有效协议、资产、工作订单、发票和支持案例的信息。 详细信息：[集成 Field Service](https://docs.microsoft.com/dynamics365/portals/integrate-field-service)
- **合作伙伴培训：** 招揽新合作伙伴以改善客户销售和服务体验。 潜在合作伙伴可通过门户申请合作伙伴状态。

### <a name="privacy-notice"></a>隐私声明

[!INCLUDE[cc-privacy-crm-portals-data-exposed](../../includes/cc-privacy-crm-portals-data-exposed.md)]

有关 [!INCLUDE[pn-azure-shortest](../../includes/pn-azure-shortest.md)] 服务产品的详细信息，请参阅[[!INCLUDE[cc_privacy_note_azure_trust_center](../../includes/cc_privacy_note_azure_trust_center.md)]](https://azure.microsoft.com/support/trust-center/)。  
