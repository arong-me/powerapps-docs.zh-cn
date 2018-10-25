---
title: 使用 Common Data Service for Apps Web 服务 | Microsoft Docs
description: 了解开发人员可以如何使用 Common Data Service for Apps Web 服务。
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/26/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 7e9e14a9d44a3326fb8ac32b11e46b61cc119c27
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42854429"
---
# <a name="use-common-data-service-for-apps-web-services"></a>使用 Common Data Service for Apps Web 服务

Common Data Service for Apps 提供两种可用于与数据进行交互的 Web 服务。 选择最适合自己需求和技能的服务。 详细信息：[Dynamics 365 客户参与开发人员指南：为 Dynamics 365 客户参与选择开发风格](/dynamics365/customer-engagement/developer/choose-development-style)

## <a name="web-api"></a>Web API
Web API 是 OData v4 RESTful 终结点。 为支持 HTTP 请求和使用 OAuth 2.0 身份验证的任何编程语言使用此终结点。

详细信息：[Dynamics 365 客户参与开发人员指南：使用 Dynamics 365 客户参与 Web API](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api)

## <a name="organization-service"></a>组织服务

组织服务是 Common Data Service for Apps 平台的核心部分。 它是一项 Windows Communication Foundation (WCF) 服务，当前仅公开 SOAP 终结点。 .NET 开发人员可以使用 SDK 程序集执行数据操作。 在插件中，通过 SDK 程序集实现组织服务是唯一的选项。
> [!NOTE]
> 开发人员可以使用组织服务的 SOAP 终结点，而不使用 .NET SDK 程序集，但 Web API 的 RESTful 性质让其成为更优的选择。

详细信息：[Dynamics 365 客户参与开发人员指南：使用 Dynamics 365 组织服务](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-organization-service)

## <a name="about-the-web-services-and-the-platform"></a>关于 Web 服务和平台

组织服务定义了平台，意识到这一点很有必要。 Web API 提供 RESTful 编程体验，但最终所有数据操作都通过基础组织服务完成。 

组织服务将支持的操作定义为消息。 每条消息有一个名称。 在 SDK 程序集中，每条消息都有相应的&lt;消息名称&gt;`Request`和&lt;消息名称&gt;`Response`类。 `Microsoft.Xrm.Sdk.dll` 中的 [IOrganizationService 接口](/dotnet/api/microsoft.xrm.sdk.iorganizationservice)定义多个用于常见 CRUD 操作的帮助程序方法以及可用于调用消息的[执行方法](/dotnet/api/microsoft.xrm.sdk.iorganizationservice.execute)。 所有消息都使用基础的 [OrganizationRequest 类](/dotnet/api/microsoft.xrm.sdk.organizationrequest)。

Web API 可提供组织服务提供的所有操作，但使用 OData v4 协议以 RESTful 样式呈现这些操作。 OData v4 通过函数或操作为命名操作提供所需。 几乎所有在组织服务中可用的消息都公开为相应的命名函数或操作。 那些与 CRUD 操作相对应的消息在 Web API 中不可用，因为作为 RESTful 服务，它们的实现使用 GET、POST、PATCH 和 DELETE HTTP 方法。

组织服务 SOAP 终结点的 .NET SDK 程序集其功能在于基于 [IOrganizationService 接口](/dotnet/api/microsoft.xrm.sdk.iorganizationservice)为基础平台服务建立精确模型。 但二者不是相同的组件，不能混淆。 

组织服务的 SOAP 终结点于 2011 年引入，我们已宣布不久后将弃用该组件。 这意味着在彻底弃用之前，该组件将继续正常工作并受到支持。 我们还宣布了将更新 .NET SDK 程序集，以便在 SOAP 终结点弃用后继续正常工作。 这意味着在移除 SOAP 终结点之前，会提供更新的 SDK 程序集，开发人员需要更新代码以便将来使用新的程序集。

## <a name="discovery-services"></a>发现服务

每个 Common Data Service for Apps 用户可以访问多个 Common Data Service for Apps 实例。 借助发现服务可编写代码，为用户提供可连接的实例的列表（基于其所使用的 Microsoft 帐户）。 每个实例包含稍后可用来连接所选实例的 URL。 

可通过 Web API 或组织服务访问发现服务。

- 有关 Web API，请参阅：[Dynamics 365 客户参与开发人员指南：使用 Web API 发现组织的 URL](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api)
- 有关组织服务，请参阅：[Dynamics 365 客户参与开发人员指南：使用组织服务发现组织的 URL](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)

## <a name="use-custom-actions"></a>使用自定义操作

进程可用的声明性选项之一是创建“自定义操作”。 自定义操作实质上是在组织服务中创建一条新消息。 自定义操作可用于将一组操作合并为一个命名的可重用操作。 例如，可以创建名为 new_Escalate 的新消息，该消息合并一组标准操作，当重要客户遇到严重问题时会通知合适的人员，这些操作就是通知时所涉及的操作。

定义自定义操作时，可通过定义要在返回的任何结果中包含的输入参数和属性，来选择操作的签名。 然后可以使用设计器或者通过代码从声明性进程中调用自定义操作。 

自定义操作特有的作用是，非开发人员可使用设计器修改其中包含的特定操作，而不影响其他进程或调用它的代码。  只要操作签名不更改，这就是有效的。 如果需要不同的输入参数或输出属性，应创建一个新的、不同的自定义操作，以避免中断或破坏任何使用现有自定义操作的进程或代码。

在环境中定义自定义操作时，可使用 Web API 实现新的 OData v4 操作，并且在组织服务中，可直接使用 [OrganizationRequest 类](/dotnet/api/microsoft.xrm.sdk.organizationrequest)或使用通过代码生成工具 (CrmSvcUtil.exe) 生成的强类型类来调用自定义操作。

详细信息： 
- [Dynamics 365 客户参与自定义指南：操作概述](/dynamics365/customer-engagement/customize/actions)
- [Dynamics 365 客户参与开发人员指南：创建自己的操作](/dynamics365/customer-engagement/developer/create-own-actions)
- [Dynamics 365 客户参与开发人员指南：使用 Web API 操作 > 使用自定义操作](/dynamics365/customer-engagement/developer/webapi/use-web-api-actions#use-a-custom-action)

## <a name="metadata-services"></a>元数据服务

Web API 和组织服务均包含在实体架构上执行 CRUD 操作的功能。 尽管可以使用代码执行这些操作，但通常使用设计器添加、更新或删除自定义架构元素。 用户必须拥有管理员特权才能应用架构更改，但所有用户都可以读取元数据。

元数据服务更常见的用途是检索有关运行扩展的环境的元数据。 由于环境可能各不相同且架构元数据包含许多有关环境如何配置的信息，所以可能需要检索此信息，来帮助扩展适应在环境中发生作用的其他自定义效果。

下面是一些示例：
- 选项集属性中的可用选项数可能发生变化。 请考虑是否设置其他选项，而不是硬编码环境中的值。 可以查询系统以确定当前环境是否提供其他选项。
- 可以更改实体的显示名称。 帐户实体的默认显示名称为“帐户”。 此名称可更改为“公司”。 如果要向用户显示一条消息并指示一个实体名称，那么不应进行硬编码，而是使用与用户习惯看到的内容相匹配的值并使用从实体元数据检索的显示名称。

更好地了解系统元数据可帮助理解 Common Data Service for Apps 平台的工作方式。 可用于编辑元数据的设计器无法显示在元数据中找到的所有详细信息。 可以安装名为“元数据浏览器”的模型驱动应用，这样就可以查看系统中找到的所有隐藏实体和元数据属性。 

详细信息：[Dynamics 365 客户参与开发人员指南：浏览组织的元数据](/dynamics365/customer-engagement/developer/browse-your-metadata)

有关以编程方式使用元数据的详细信息，请参阅：
- [Dynamics 365 客户参与开发人员指南：结合使用 Web API 和元数据](/dynamics365/customer-engagement/developer/webapi/use-web-api-metadata)
- [Dynamics 365 客户参与开发人员指南：结合使用组织服务和 Dynamics 365 元数据](/dynamics365/customer-engagement/developer/org-service/use-organization-service-metadata)
 
### <a name="see-also"></a>另请参阅

[Common Data Service for Apps 开发人员概述](overview.md)

