---
title: 响应针对 PowerApps 客户数据的数据主体权限 (DSR) 请求 | Microsoft Docs
description: 演练如何响应针对 PowerApps 客户数据的数据主体权限 (DSR) 请求
author: jamesol-msft
manager: kfile
ms.service: powerapps
ms.component: pa-admin
ms.topic: conceptual
ms.date: 05/23/2018
ms.author: jamesol
ms.openlocfilehash: 14fe0c749a17a1a28ebc7c8680ff55df2392999e
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34552935"
---
# <a name="responding-to-data-subject-rights-dsr-requests-for-powerapps-customer-data"></a>响应针对 PowerApps 客户数据的数据主体权限 (DSR) 请求

## <a name="introduction-to-dsr-requests"></a>DSR 请求简介
欧盟 (EU) 一般数据保护条例 (GDPR) 为用户（在条例中称为“数据主体”）提供了多种权限，使其有权管理由雇主或其他类型的机构或组织（称为“数据控制者”或简称为“控制者”）收集的个人数据。 在 GDPR 下，个人数据被广泛定义为与确定的或可识别的自然人相关的任何数据。 GDPR 为数据主体提供针对其个人数据的以下权限：

* 获取副本
* 请求更正
* 限制处理
* 删除个人数据
* 接收电子格式的个人数据，以便将其发送给另一个控制者

数据主体权限 (DSR) 请求是数据主体向控制者发出的正式请求，请求对其个人数据执行操作。

本文介绍 Microsoft 如何针对 GDPR 进行准备工作，还提供了一些可以采取的步骤示例，在使用 PowerApps、Microsoft Flow 和 Common Data Service (CDS) for Apps 时，提供对 GDPR 符合性的支持。 你可了解如何使用 Microsoft 产品、服务和管理工具，帮助控制者客户发现、访问并处理 Microsoft 云中的个人数据，以响应 DSR 请求。

本文介绍了以下操作：

* 发现 — 使用搜索和发现工具轻松找到可能是 DSR 请求主体的客户数据。 收集了潜在的响应性文档后，就可以执行以下一个或多个 DSR 操作，以响应请求。 或者，可以确定请求不符合组织用于响应 DSR 请求的指导原则。

* 访问 - 检索驻留在 Microsoft 云中的个人数据，如果收到请求，则复制一份可供数据主体使用的数据副本。

* 纠正 — 在适用情况下，对个人数据进行更改或执行其他请求的操作。

* 限制 — 通过移除各种在线服务的许可证，或者在可能的情况下关闭所需的服务，限制对个人数据的处理。 此外还可以从 Microsoft 云中移除数据，并将其保留在本地或另一个位置。

* 删除 - 永久删除驻留在 Microsoft 云中的个人数据。

* 导出 — 向数据主体提供个人数据的电子副本（采用计算机可读格式）。

## <a name="discover"></a>发现
响应 DSR 请求的第一步是查找请求主体的个人数据。 第一步 &mdash; 查找和审查所涉及的个人数据 &mdash; 帮助确定 DSR 请求是否满足组织要求以接受或拒绝 DSR 请求。 例如，在发现和审查所涉及的个人数据后，可能确定请求不符合组织要求，因为这样做可能会对他人的权利和自由产生负面影响。

### <a name="step-1-find-personal-data-for-the-user-in-powerapps"></a>步骤 1：在 PowerApps 中查找用户个人数据
下面是包含特定用户个人数据的 PowerApps 资源类型的摘要。

包含个人数据的资源 |    用途
--- | ---
环境 |   环境是用来存储、管理和共享组织的业务数据、应用和流的空间。 [了解详细信息](https://go.microsoft.com/fwlink/?linkid=872239)
环境权限 | 向用户分配环境角色，在环境中授予其创建者和管理权限。 [了解详细信息](https://go.microsoft.com/fwlink/?linkid=872240)
画布应用  | 跨平台商业应用，可以从大量空白画布进行构建，并连接到超过 200 个数据源。 [了解详细信息](https://go.microsoft.com/fwlink/?linkid=872241)
画布应用权限  | 画布应用可以与组织中的用户共享。 [了解详细信息](https://go.microsoft.com/fwlink/?linkid=872242)
连接  | 由连接器使用，并允许连接到 API、系统、数据库等。 [了解详细信息](https://go.microsoft.com/fwlink/?linkid=872243)
连接权限  | 某些类型的连接可以与组织中的用户共享。 [了解详细信息](https://go.microsoft.com/fwlink/?linkid=872244)
自定义连接器    | 自定义连接器由用户创建，提供对不通过 PowerApps 标准连接器提供的数据源的访问。 [了解详细信息](https://go.microsoft.com/fwlink/?linkid=872245)
自定义连接器权限    | 自定义连接器可以与组织中的用户共享。 [了解详细信息](https://go.microsoft.com/fwlink/?linkid=872246)
PowerApps 用户和用户应用设置    | PowerApps 存储多个用户首选项和设置，用于提供 PowerApps 运行时和门户体验。
PowerApps 通知 | PowerApps 向用户发送几种类型的通知，包括与用户共享应用以及 CDS for Apps 导出操作完成时。
网关 | 网关是可以由用户安装的本地数据网关，可以在 PowerApps 与非云数据源之间快速安全地传输数据。 [了解详细信息](https://go.microsoft.com/fwlink/?linkid=872247)
网关权限 | 网关可以与组织中的用户共享。 [了解详细信息](https://go.microsoft.com/fwlink/?linkid=872249)
模型驱动应用和模型驱动应用权限  | 模型驱动应用设计是一种侧重于组件的应用开发方法。 模型驱动应用及其用户访问权限作为数据存储在 CDS for Apps 数据库内。  [了解详细信息](https://go.microsoft.com/fwlink/?linkid=872248)

PowerApps 提供以下体验，以查找特定用户的个人数据：

- 网站访问：[PowerApps 站点](https://web.powerapps.com)、[PowerApps 管理中心](https://admin.powerapps.com/)和 [Office 365 服务信任门户](https://servicetrust.microsoft.com/)
- PowerShell 访问：PowerApps cmdlet（用于[应用创建者](https://go.microsoft.com/fwlink/?linkid=871448)和[管理员](https://go.microsoft.com/fwlink/?linkid=871804)），以及[本地网关 cmdlet](https://go.microsoft.com/fwlink/?linkid=872238)

有关如何使用这些体验查找各类型资源特定用户的个人数据的详细步骤，请参阅[响应对导出 PowerApps 客户数据的数据主体权限 (DSR) 请求](powerapps-gdpr-export-dsr.md)。

找到数据后，可以执行特定操作来满足数据主体的请求。

### <a name="step-2-find-personal-data-for-the-user-in-microsoft-flow"></a>步骤 2：在 Microsoft Flow 中查找用户个人数据
PowerApps 许可证始终包含 Microsoft Flow 功能。 除了包含在 PowerApps 许可证中以外，Microsoft Flow 还作为独立服务提供。

有关如何发现由 Microsoft Flow 服务存储的个人数据的指导，请参阅[响应针对 Microsoft Flow 的 GDPR 数据主体请求](https://go.microsoft.com/fwlink/?linkid=872250)。

> [!IMPORTANT]
> 建议管理员为 PowerApps 用户完成此步骤

### <a name="step-3-find-personal-data-for-the-user-in-instances-of-cds-for-apps"></a>步骤 3：在 CDS for Apps 实例中查找用户的个人数据
某些 PowerApps 许可证（包括 PowerApps 社区计划）让组织中的用户可以创建 CDS for Apps 实例，并在 CDS for Apps 上创建和生成应用。 PowerApps 社区计划为免费许可证，用户可在单独环境中试用 CDS for Apps。 有关每个 PowerApps 许可证随附的功能，请参阅 [PowerApps 定价](https://powerapps.microsoft.com/pricing/)页。

有关如何发现由 CDS for Apps 存储的个人数据的指导，请参阅[响应针对 Common Data Service for Apps 客户数据的数据主体权限 (DSR) 请求](common-data-service-gdpr-dsr-guide.md)。

> [!IMPORTANT]
> 建议管理员为 PowerApps 用户完成此步骤。

## <a name="rectify"></a>纠正
如果数据主体要求纠正驻留在组织数据中的个人数据，你和你的组织需要确定是否可以接受此请求。 纠正数据包括编辑、编校或从文档或其他类型的项目中删除个人数据。

可以使用 Azure Active Directory 来管理 PowerApps 中的用户身份（个人数据）。 企业客户可以在给定的 Microsoft 服务内使用有限的编辑功能来管理 DSR 纠正请求。 作为数据处理方，Microsoft 不提供纠正系统生成的日志的功能，因为它们反映真实性活动，并构成 Microsoft 服务内部事件的历史记录。 有关详细信息，请参阅 [GDPR：数据主体请求 (DSR)](https://servicetrust.microsoft.com/ViewPage/GDPRDSR)。

## <a name="restrict"></a>限制
数据主体可能会请求你限制其个人数据处理。  我们提供预先存在的应用程序编程接口 (API) 和用户界面 (UI)。  这些体验为企业客户的租户管理员提供了通过数据导出和数据删除组合来管理此类 DSR 的能力。 客户可能会请求：

* 导出用户个人数据的电子副本，包括：

    - 帐户
    - 系统生成的日志
    - 关联日志

* 删除驻留在 Microsoft 系统中的帐户及关联数据。

## <a name="export"></a>导出
“数据可移植性权限”允许数据主体以电子格式（这是一种“结构化的、常用的、计算机可读和可互操作的格式”）请求其个人数据副本，这些数据可能会传输给另一个数据控制者。

有关详细信息，请参阅[响应对导出 PowerApps 客户数据的数据主体权限 (DSR) 请求](powerapps-gdpr-export-dsr.md)。

## <a name="delete"></a>删除
从组织的客户数据中移除个人数据的“删除权限”是 GDPR 中的关键保护措施。 移除个人数据包括系统生成的日志，但不包括审核日志信息。

PowerApps 允许用户生成业务线应用程序，这些应用程序是组织日常运营的关键部分。 当某位用户离开组织时，你将需要手动检查并确定是否删除用户创建的某些数据和资源。 从 Azure Active Directory 删除用户帐户时，将自动删除其他客户数据。

有关详细信息，请参阅[响应对删除 PowerApps 客户数据的数据主体权限 (DSR) 请求](powerapps-gdpr-delete-dsr.md)。
