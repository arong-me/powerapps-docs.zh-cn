---
title: Common Data Service for Apps 开发人员概述 | Microsoft Docs
description: 了解开发人员如何使用 Common Data Service for Apps 来提升价值。
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
ms.date: 03/19/2018
ms.author: jdaly
ms.openlocfilehash: 5ed61c77cc0cea3cf25e48b347f8a524cf62dfd5
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="common-data-service-for-apps-developer-overview"></a>Common Data Service for Apps 开发人员概述
PowerApps 为用户、企业、合作伙伴、独立软件供应商 (ISV) 和系统集成商 (SI) 提供了用于生成业务线应用的功能强大的平台。 此 PowerApps 版本中的新增功能是全新的 Common Data Service for Apps。 Common Data Service for Apps 现在包含 Dynamics 365 客户参与平台这一核心功能。


## <a name="get-started"></a>入门
如果已拥有 Dynamics 365 客户参与应用的相关经验，将发现可运用自身相关经验来自定义和扩展 Common Data Service for Apps。

如果不熟悉 Dynamics 365 客户参与应用程序，可借助以下主题获取重要相关概念的高级概述，并开始使用 Common Data Service for Apps。

> [!NOTE]
> - 模型驱动应用可连接 Common Data Service for Apps。 有关开发人员如何在应用程序级别提升价值的信息，请参阅[模型驱动的应用开发人员概述](../model-driven-apps/overview.md)。 本节中的内容仅涉及开发人员可在服务级别操作的扩展。 
> - 由于 Common Data Service for Apps 和 Dynamics 365 客户参与采用同一平台，因此可在 [Dynamics 365 客户参与开发人员指南](/dynamics365/customer-engagement/developer/developer-guide)中找到有关开发人员的完整详细信息。 这些主题提供相关概述和链接，可通过链接访问开发人员指南和其他指南，获取详细信息。


## <a name="tools-and-resources-for-developers"></a>开发人员的工具和资源

当开发人员在处理和运用涉及 Common Data Service for Apps 的解决方案时，会用到以下工具和资源。

### <a name="tools-available-for-download-from-nuget"></a>可从 NuGet 下载的工具

以下工具分布于 NuGet 包中。 [开发人员指南：从 NuGet 下载工具](/dynamics365/customer-engagement/developer/download-tools-nuget)主题包括一个 PowerShell 脚本，可用于下载和提取这些工具的最新版本。

|工具  |说明  |
|---------|---------|
|代码生成工具 `CrmSvcUtil.exe`|一个命令行代码生成工具，用于生成早期绑定的 .NET Framework 类，这些类表示供组织服务使用的实体数据模型。 <br />详细信息： <br />[组织服务](use-web-services.md#organization-service)<br />[Dynamics 365 客户参与开发人员指南：使用代码生成工具创建早期绑定的实体类](/dynamics365/customer-engagement/developer/org-service/create-early-bound-entity-classes-code-generation-tool)|
|配置迁移工具 `DataMigrationUtility.exe`|用于在环境间移动配置数据。 配置数据用于定义自定义功能，通常存储在自定义实体中。 此工具不用于移动业务数据。 <br /> 详细信息：[Dynamics 365 客户参与管理员指南：使用配置迁移工具在实例和组织间移动配置数据](/dynamics365/customer-engagement/admin/manage-configuration-data)|
|Package Deployer `PackageDeployer.exe`|用于在 Common Data Service for Apps 实例上部署包。 包是包含解决方案的可安装单元。 <br /> 详细信息： <br />[部署解决方案包](introduction-solutions.md#deploy-solution-packages)<br />[Dynamics 365 客户参与开发人员指南：为 Dynamics 365 Package Deployer 创建包](/dynamics365/customer-engagement/developer/create-packages-package-deployer)|
|插件注册工具 `PluginRegistration.exe`|用于将 .NET 程序集插件类订阅到服务器事件的工具。 <br />详细信息： <br />[创建插件](apply-business-logic-with-code.md#create-a-plug-in)<br />[Dynamics 365 客户参与开发人员指南：演练：使用插件注册工具注册插件](/dynamics365/customer-engagement/developer/walkthrough-register-plugin-using-plugin-registration-tool)|
|SolutionPackager 工具 `SolutionPackager.exe`|一种工具，可将 Common Data Service for Apps 压缩解决方案文件逆向分解为多个 XML 文件和其他文件，以便源代码管理系统可以轻松管理这些文件。<br /> 详细信息： <br />[解决方案的团队开发](introduction-solutions.md#team-development-of-solutions)<br />[Dynamics 365 客户参与开发人员指南：使用 SolutionPackager 工具压缩和提取解决方案文件](/dynamics365/customer-engagement/developer/compress-extract-solution-file-solutionpackager)|

### <a name="net-sdk-assemblies"></a>.NET SDK 程序集 

以下是 .NET 开发人员可使用的程序集。 可在相应的 NuGet 包中下载最新版本。

#### <a name="work-with-data"></a>处理数据

使用这些程序集与组织服务和发现服务进行交互。

详细信息：[Dynamics 365 客户参与开发人员指南：使用 Dynamics 365 组织服务](/dynamics365/customer-engagement/developer/use-microsoft-dynamics-365-organization-service)

**NuGet 包**：[Microsoft.CrmSdk.CoreAssemblies](https://www.nuget.org/packages/Microsoft.CrmSdk.CoreAssemblies/)

|程序集  |命名空间  |
|---------|---------|
|Microsoft.Crm.Sdk.Proxy.dll|[Microsoft.Crm.Sdk](/dotnet/api/microsoft.crm.sdk)<br />[Microsoft.Crm.Sdk.Messages](/dotnet/api/microsoft.crm.sdk.messages)|
|Microsoft.Xrm.Sdk.dll|[Microsoft.Xrm.Sdk](/dotnet/api/microsoft.xrm.sdk)<br />[Microsoft.Xrm.Sdk.Client](/dotnet/api/microsoft.xrm.sdk.client)<br />[Microsoft.Xrm.Sdk.Discovery](/dotnet/api/microsoft.xrm.sdk.discovery)<br />[Microsoft.Xrm.Sdk.Messages](/dotnet/api/microsoft.xrm.sdk.messages)<br />[Microsoft.Xrm.Sdk.Metadata](/dotnet/api/microsoft.xrm.sdk.metadata)<br />[Microsoft.Xrm.Sdk.Metadata.Query](/dotnet/api/microsoft.xrm.sdk.metadata.query)<br />[Microsoft.Xrm.Sdk.Organization](/dotnet/api/microsoft.xrm.sdk.organization)<br />[Microsoft.Xrm.Sdk.Query](/dotnet/api/microsoft.xrm.sdk.query)<br />[Microsoft.Xrm.Sdk.WebServiceClient](/dotnet/api/microsoft.xrm.sdk.webserviceclient)|

#### <a name="create-process-designer-workflow-extensions"></a>创建进程设计器（工作流）扩展

使用此程序集将自定义活动添加到进程设计器。 

详细信息 [Dynamics 365 客户参与开发人员指南：自定义工作流活动（工作流程序集）](/dynamics365/customer-engagement/developer/custom-workflow-activities-workflow-assemblies)

**NuGet 包**：[Microsoft.CrmSdk.Workflow](https://www.nuget.org/packages/Microsoft.CrmSdk.Workflow/) 

|程序集|命名空间|
|---------|---------|
|Microsoft.Xrm.Sdk.Workflow.dll|[Microsoft.Xrm.Sdk.Workflow](/dotnet/api/microsoft.xrm.sdk.workflow)<br />[Microsoft.Xrm.Sdk.Workflow.Activities](/dotnet/api/microsoft.xrm.sdk.workflow.activities)<br />[Microsoft.Xrm.Sdk.Workflow.Designers](/dotnet/api/microsoft.xrm.sdk.workflow.designers)|

#### <a name="build-windows-client-applications"></a>生成 Windows 客户端应用程序

使用这些程序集，以便连接到组织服务并生成 Windows 客户端应用程序。 

详细信息 [Dynamics 365 客户参与开发人员指南：使用 XRM 工具生成 Windows 客户端应用程序](/dynamics365/customer-engagement/developer/build-windows-client-applications-xrm-tools)

**NuGet 包**：
- [Microsoft.CrmSdk.XrmTooling.CoreAssembly](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.CoreAssembly/) (Microsoft.Xrm.Tooling.Connector.dll)
- [Microsoft.CrmSdk.XrmTooling.WpfControls](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.WpfControls/) 

|程序集|命名空间  |
|---------|---------|
|Microsoft.Xrm.Tooling.Connector.dll|[Microsoft.Xrm.Tooling.Connector](/dotnet/api/microsoft.xrm.tooling.connector)<br />[Microsoft.Xrm.Tooling.Connector.Model](/dotnet/api/microsoft.xrm.tooling.connector.model)|
|Microsoft.Xrm.Tooling.CrmConnectControl.dll|[Microsoft.Xrm.Tooling.CrmConnectControl](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Model](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.model)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Properties](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.properties)<br />[Microsoft.Xrm.Tooling.CrmConnectControl.Utility](/dotnet/api/microsoft.xrm.tooling.crmconnectcontrol.utility)|
|Microsoft.Xrm.Tooling.WebResourceUtility.dll|[Microsoft.Xrm.Tooling.WebResourceUtility](/dotnet/api/microsoft.xrm.tooling.webresourceutility)|

#### <a name="create-packages"></a>创建包

使用这些程序集为 Package Deployer 创建包。

详细信息：[Dynamics 365 客户参与开发人员指南：为 Dynamics 365 Package Deployer 创建包](/dynamics365/customer-engagement/developer/create-packages-package-deployer)

**NuGet 包**：[Microsoft.CrmSdk.XrmTooling.PackageDeployment](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PackageDeployment/)

|程序集|命名空间  |
|---------|---------|
|Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase.dll|[Microsoft.Xrm.Tooling.PackageDeployment.CrmPackageExtentionBase](/dotnet/api/microsoft.xrm.tooling.packagedeployment.crmpackageextentionbase)|

#### <a name="create-custom-virtual-entity-data-providers"></a>创建自定义虚拟实体数据提供程序

使用此程序集创建自定义虚拟实体数据提供程序。 

详细信息：[Dynamics 365 客户参与开发人员指南：虚拟实体入门](/dynamics365/customer-engagement/developer/virtual-entities/get-started-ve)

**NuGet 包**：[Microsoft.CrmSdk.Data](https://www.nuget.org/packages/Microsoft.CrmSdk.Data/)

|程序集  |命名空间  |
|---------|---------|
|Microsoft.Xrm.Sdk.Data.dll|[Microsoft.Xrm.Sdk.Data](/dotnet/api/microsoft.xrm.sdk.data)<br />[Microsoft.Xrm.Sdk.Data.CodeGen](/api/microsoft.xrm.sdk.data.codegen)<br />[Microsoft.Xrm.Sdk.Data.Converters](/dotnet/api/microsoft.xrm.sdk.data.converters)<br />[Microsoft.Xrm.Sdk.Data.Exceptions](/dotnet/api/microsoft.xrm.sdk.data.exceptions)<br />[Microsoft.Xrm.Sdk.Data.Expressions](/dotnet/api/microsoft.xrm.sdk.data.expressions)<br />[Microsoft.Xrm.Sdk.Data.Infra](/dotnet/api/microsoft.xrm.sdk.data.infra)<br />[Microsoft.Xrm.Sdk.Data.Mappings](/dotnet/api/microsoft.xrm.sdk.data.mappings)|

#### <a name="extend-outlook-client"></a>扩展 Outlook 客户端

使用此程序集可与 Microsoft Dynamics 365 for Outlook 和 Microsoft Dynamics 365 for Microsoft Office Outlook with Offline Access 进行交互。 

详细信息：[Dynamics 365 客户参与开发人员指南：扩展适用于 Outlook 的 Dynamics 365 客户参与](/dynamics365/customer-engagement/developer/extend-customer-engagement-outlook)

**NuGet 包**：[Microsoft.CrmSdk.Outlook](https://www.nuget.org/packages/Microsoft.CrmSdk.Outlook/)

|程序集|命名空间|
|---------|---------|
|Microsoft.Crm.Outlook.Sdk.dll|[Microsoft.Crm.Outlook.Sdk](/dotnet/api/microsoft.crm.outlook.sdk)|



### <a name="community-tools-for-common-data-service-for-apps"></a>Common Data Service for Apps 的社区工具

Dynamics 365 社区创建工具！ 许多最常见的工具分布于 [XrmToolBox](https://www.xrmtoolbox.com/) 中。 XrmToolBox 是连接到 Common Data Service for Apps 的 Windows 应用程序，提供用于简化自定义、配置和操作任务的工具。 它附带 30 多个插件，使管理、自定义或配置任务变得更容易、更省时。

以下是通过 XrmToolBox 分发的社区工具选定列表，可将其与 Common Data Service for Apps 一起使用。

|工具  |说明  |
|---------|---------|
|[属性管理器](https://www.xrmtoolbox.com/plugins/DLaB.Xrm.AttributeManager/)|用于重命名/删除属性或更改其类型。|
|[早期绑定的生成器](https://www.xrmtoolbox.com/plugins/DLaB.Xrm.EarlyBoundGenerator/)|生成早期绑定的实体/选项集/操作。 使用 SDK 中的 CrmSvcUtil，并显示用于创建类的命令行。|
|[导出到 Excel](https://www.xrmtoolbox.com/plugins/Ryr.XrmToolBox.ExportToExcel/)|轻松将记录从所选视图/fetchxml 导出到 Excel 中。|
|[FetchXML 生成器](https://www.xrmtoolbox.com/plugins/Cinteros.Xrm.FetchXmlBuilder/)|创建和测试 FetchXml 查询|
|[元数据浏览器](https://www.xrmtoolbox.com/plugins/MsCrmTools.MetadataBrowser/)|浏览 Dynamics CRM 组织中的元数据|
|[插件跟踪查看器](https://www.xrmtoolbox.com/plugins/Cinteros.XrmToolBox.PluginTraceViewer/)|通过轻松筛选来调查插件跟踪日志并显示可能性|
|[用户设置实用程序](https://www.xrmtoolbox.com/plugins/MsCrmTools.UserSettingsUtility/)|批量管理用户个人设置|

> [!NOTE]
> Microsoft 不支持社区创建的工具。 如果对社区工具有任何疑问，请联系该工具的发布者。
