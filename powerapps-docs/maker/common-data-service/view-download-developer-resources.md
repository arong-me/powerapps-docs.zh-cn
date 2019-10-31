---
title: 查看或下载适用于 PowerApps 和 Common Data Service 的开发人员资源 | MicrosoftDocs
description: 查找适用于 PowerApps 和 Common Data Service 的开发人员资源和服务终结点 URL
keywords: ''
ms.date: 09/25/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
ms.assetid: e200d242-ff3f-48e5-af32-aed050e02441
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="view-or-download-developer-resources"></a>查看或下载开发人员资源

本页提供面向开发人员的资源以及有关您使用的特定实例的信息。 

## <a name="view-the-developer-resources-page-for-your-environment"></a>查看您的环境的“开发人员资源”页

1. 从 PowerApps 门户，选择 ![设置按钮](../../administrator/media/settings-button-nav-bar.png)“设置”按钮并选择**高级自定义**。

    ![高级自定义](media/advanced-customizations-menu.png)

1. 在**高级自定义**面板内，选择**开发人员资源**链接：<br />![开发人员资源链接](media/developer-resources-link.png)

## <a name="getting-started"></a>入门 

本部分提供供开发人员查找资源的链接。 提供以下资源：


|链接 |说明|
|---------|---------|
|[开发人员中心](https://go.microsoft.com/fwlink/?LinkId=551006)。|在此处开始获取有关 PowerApps和 Common Data Service 的开发人员文档。|
|[PowerApps 社区/论坛](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)|在 PowerApps 社区中提问和回答问题。|
|[NuGet包](https://www.nuget.org/profiles/crmsdk)|了解 NuGet 包，向您的项目添加 SDK 程序集。|
|[下载工具](/powerapps/developer/common-data-service/download-tools-nuget)|您需要的工具可以从 NuGet 下载。 使用此页面的 PowerShell 脚本获取最新版本。|
|[示例代码](https://go.microsoft.com/fwlink/?LinkId=553007)|适用于 PowerApps 的 GitHub 存储库示例。|
|[开发人员概述](https://go.microsoft.com/fwlink/?LinkId=550995)|为开发人员提供概述的主题的链接。|

## <a name="connect-your-apps-to-this-instance-of-common-data-service"></a>将您的应用程序连接到 Common Data Service 的此实例

本部分提供连接到 Common Data Service 实例所需的信息。

### <a name="instance-web-api"></a>实例 Web API

这您的实例的 Web API 的 URL。 Web API 是一个 OData v4 RESTful API。 您还可以下载介绍您的实例中提供的元数据和操作的服务文档。 详细信息：[开发人员文档：使用 Common Data Service Web API](/powerapps/developer/common-data-service/webapi/overview)

### <a name="organization-service"></a>组织服务

这是您的实例的组织服务的 SOAP 终结点的 URL。
您可以在此处下载此服务的 WSDL，不过通常您将使用 CrmSvcUtil.exe 代码生成工具为 .NET 项目构建实体类。 详细信息： 
- [开发人员文档：使用代码生成工具 (CrmSvcUtil.exe) 生成早期绑定实体类](/powerapps/developer/common-data-service/org-service/generate-early-bound-classes)
- [开发人员文档：使用“组织服务”读取和写入数据或元数据](/powerapps/developer/common-data-service/org-service/overview)

### <a name="instance-reference-information"></a>实例参考信息

此信息只描述您的实例。 存在 GUID **ID** 和**唯一名称**。
当您对实例使用 Azure 扩展时需要此信息。
详细信息：[开发人员文档：Dynamics 365 的 Azure 扩展](/dynamics365/customer-engagement/developer/azure-extensions)

## <a name="connect-your-apps-to-the-common-data-service-discovery-service"></a>将您的应用程序连接到 Common Data Service 发现服务

由于用户可能有多个 Common Data Service 环境的访问权限，发现服务允许检索用户可以根据其用户凭据访问的可用环境。

### <a name="discovery-web-api"></a>发现 Web API

这是用于您的实例的发现服务的 RESTful OData v4 版本的终结点地址。 您还可以在此处下载服务文档。
详细信息：[开发人员文档：使用 Web API 发现您的组织的 URL](/powerapps/developer/common-data-service/webapi/discover-url-organization-web-api)


### <a name="discovery-service"></a>发现服务

这是用于您的实例的发现服务的 SOAP 版本的终结点地址。 您还可以在此处下载服务文档。
详细信息：[开发人员文档：使用“发现服务”发现您的组织的 URL](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  
