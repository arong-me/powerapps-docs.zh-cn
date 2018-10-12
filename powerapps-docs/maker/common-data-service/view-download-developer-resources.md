---
title: 查看或下载开发人员资源 | MicrosoftDocs
description: 查找开发人员资源和服务终结点 URL
keywords: ''
ms.date: 06/06/2018
ms.service: crm-online
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: e200d242-ff3f-48e5-af32-aed050e02441
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.openlocfilehash: ae93b57d9ead3a62fb538ae986eb524367259545
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669158"
---
<!-- TODO: The Developer Resources page have to be updated to match this page -->

# <a name="view-or-download-developer-resources"></a>查看或下载开发人员资源

此页面为开发人员提供资源，并介绍你要使用的特定实例。 

## <a name="view-the-developer-resources-page-for-your-environment"></a>查看适用于你的环境的“开发人员资源”页面

1. 从 PowerApps 门户中选择![“设置”按钮](../../administrator/media/settings-button-nav-bar.png)“设置”按钮，然后选择“高级自定义”。

    ![高级自定义](media/advanced-customizations-menu.png)

1. 在“高级自定义”面板中，选择“开发人员资源”链接：<br />![“开发人员资源”链接](media/developer-resources-link.png)

## <a name="getting-started"></a>入门 

本部分为开发人员提供用于查找资源的链接。 以下资源可用：


|链接 |描述|
|---------|---------|
|[开发人员中心](https://go.microsoft.com/fwlink/?LinkId=551006)|开发人员文档的主要入口点。|
|[开发人员论坛](https://go.microsoft.com/fwlink/?LinkId=550993)|向其他开发人员提问和回答问题。|
|[NuGet 包](https://go.microsoft.com/fwlink/?LinkId=550994)|发现 NuGet 包以将 SDK 程序集添加到项目中。|
|[下载工具](https://go.microsoft.com/fwlink/?LinkID=512122)|可以从 NuGet 下载所需的工具。 使用此页面上的 PowerShell 脚本获取最新版本。|
|[示例代码](https://go.microsoft.com/fwlink/?LinkId=553007)|可用示例列表。|
|[开发人员概述](https://go.microsoft.com/fwlink/?LinkId=550995)|链接到为开发人员提供概述的主题。|

<!-- TODO update 512122 to go to https://docs.microsoft.com/dynamics365/customer-engagement/developer/download-tools-nuget -->


## <a name="connect-your-apps-to-this-instance-of-common-data-service-for-apps"></a>将应用连接到此 Common Data Service for Apps 实例

本部分提供连接到 Common Data Service for Apps 实例所需的信息。

### <a name="instance-web-api"></a>实例 Web API

这是实例的 Web API 的 URL。 Web API 是 OData v4 RESTful API。 还可以下载描述实例中可用元数据和操作的服务文档。 详细信息：[开发人员文档：使用 Dynamics 365 Customer Engagement Web API](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api)

### <a name="organization-service"></a>组织服务

这是实例的组织服务的 SOAP 终结点 URL。
可以在此处下载此服务的 WSDL，但通常将使用 CrmSvcUtil.exe 代码生成工具为 .NET 项目生成实体类。 详细信息： 
- [开发人员文档：使用代码生成工具 (CrmSvcUtil.exe) 创建早期绑定的实体类](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool)
- [开发人员文档：使用组织服务读取和写入数据或元数据](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata)

### <a name="instance-reference-information"></a>实例参考信息

此信息唯一地描述了你的实例。 有一个 GUID **ID** 和一个**唯一名称**。
将 Azure 扩展与实例一起使用时需要此信息。
详细信息：[开发人员文档：用于 Dynamics 365 Customer Engagement 的 Azure 扩展](/dynamics365/customer-engagement/developer/azure-extensions)

## <a name="connect-your-apps-to-the-common-data-service-for-apps-discovery-service"></a>将应用连接到 Common Data Service for Apps 发现服务

由于用户可能有权访问多个 CDS for Apps 环境，因此发现服务允许检索用户可以基于其用户凭据访问的可用环境。

### <a name="discovery-web-api"></a>发现 Web API

这是将用于实例的发现服务的 RESTful OData v4 版本的终结点地址。 还可以在此处下载服务文档。
详细信息：[开发人员文档：使用 Web API 发现组织的 URL](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api)


### <a name="discovery-service"></a>发现服务

这是将用于实例的发现服务的 SOAP 版本的终结点地址。 还可以在此处下载服务文档。
详细信息：[开发人员文档：使用发现服务发现组织的 URL](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  
### <a name="more-information"></a>详细信息

[开发人员文档：“开发人员资源”页面](/dynamics365/customer-engagement/developer/developer-resources-page)<br />
[开发人员文档：使用 Dynamics 365 Customer Engagement Web API](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-web-api)<br />
[开发人员文档：使用组织服务读取和写入数据或元数据](/dynamics365/customer-engagement/developer/org-service/use-organization-service-read-write-data-metadata)<br />
[开发人员文档：用于 Dynamics 365 Customer Engagement 的 Azure 扩展](/dynamics365/customer-engagement/developer/azure-extensions)<br />
[开发人员文档：使用 Web API 发现组织的 URL](/dynamics365/customer-engagement/developer/webapi/discover-url-organization-web-api)<br />
[开发人员文档：使用发现服务发现组织的 URL](/dynamics365/customer-engagement/developer/org-service/discover-url-organization-organization-service)
  

