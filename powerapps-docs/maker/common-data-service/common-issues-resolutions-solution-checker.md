---
title: 解决方案检查器的常见问题和解决 | Microsoft Docs
description: " 解决方案检查器内的常见问题和解决的列表"
keywords: ''
ms.date: 02/11/2019
ms.service: powerapps
ms.custom:
- ''
ms.topic: article
ms.assetid: caa4e3f2-9700-49b8-87ed-8a68e8878b02
author: jowells1
ms.author: jowells
manager: austinj
ms.reviewer: ''
robots: noindex,nofollow
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6f9168f51f8bfffc2ef9519e183e951706b7a024
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2758312"
---
# <a name="common-issues-and-resolutions-for-solution-checker"></a>解决方案检查器的常见问题和解决

本文列出您在使用解决方案检查器时可能会遇到的一些常见问题。 如果有，将提供解决方法。

## <a name="youre-unable-to-use-solution-checker-to-run-analysis-or-download-results"></a>无法使用解决方案检查器运行分析或下载结果

提交解决方案检查器请求以运行分析或下载结果后不久，操作未完成，并显示错误消息，如：

> *“我们无法在 **[解决方案名称]** 解决方案上运行检查。请重试运行。”*

解决方案检查器会尽可能尝试返回具体错误消息，其中包含可能原因和解决步骤详细信息的链接。 选择**了解更多**了解详细信息。

![错误消息栏](media/solution-checker-missing-roles-error.png)

在后台处理分析期间发生的失败将以**无法完成**状态失败，并在 PowerApps 门户返回错误消息，同时向请求者发送电子邮件通知。 

![错误状态](media/solution-checker-exception-status.png)

选择门户通知将链接到这个常见问题页面以提供进一步的疑难解答。 如果提供的常见问题之一未解决问题，还将返回一个参考编号。 请向 Microsoft 支持提供此参考编号以进行进一步调查。

![失败通知](media/solution-checker-failure-notification.png)

## <a name="solution-checker-fails-due-to-unsupported-version-of-powerapps-checker"></a>解决方案检查器由于不支持的 PowerApps 检查器版本而失败

解决方案检查器是 PowerApps 检查器应用支持的功能。  如果您已安装了早于版本 **1.0.0.47** 的 PowerApps 检查器应用版本，解决方案检查器可能无法成功完成。 您应从 [!INCLUDE [pn-dyn-365-admin-center](../../includes/pn-dyn-365-admin-center.md)] 升级您的 PowerApps 检查器版本。 

但是，如果您安装了版本 **1.0.0.45** 以前的 PowerApps 检查器版本，我们建议您删除解决方案并重新进行安装。 由于最近的架构更改，从早于版本 **1.0.0.45** 的版本升级 PowerApps 检查器可能失败。

如果要保留解决方案检查器过去的结果，请使用[将数据导出至 Excel](../../user/export-data-excel.md) 从以下实体导出数据来导出之前运行的结果或导出所有解决方案检查器数据

- 分析组件
- 分析作业
- 分析结果
- 分析结果详细信息

### <a name="how-to-uninstall-powerapps-checker"></a>如何卸载 PowerApps 检查器

卸载 PowerApps 检查器解决方案：

1. 作为系统管理员或系统定制员，转到 https://make.powerapps.com/environments 打开 PowerApps 门户。
2. 选择**解决方案**。
3. 选择 **PowerApps 检查器**，然后在解决方案工具栏上，选择**删除**。

### <a name="how-to-install-powerapps-checker"></a>如何安装 PowerApps 检查器

在您的 Common Data Service 环境中重新安装 PowerApps 检查器：

1. 作为系统管理员或系统定制员，转到 https://make.powerapps.com/environments 打开 PowerApps 门户。
2. 选择**解决方案**。
3. 在解决方案工具栏上选择**解决方案检查器**，然后选择**安装**。

## <a name="solution-checker-cant-access-organizations-in-administration-mode"></a>解决方案检查器不能访问处于“管理模式”的组织

放入[管理模式](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-sandbox-instances#administration-mode)的组织会有意将访问权限仅限制到具有系统管理员和系统定制员角色的用户。 由于 PowerApps 检查器应用程序标识默认不具有这些分派的角色，因此，它无法访问在此模式下运行的组织。

若要在此组织中使用解决方案检查器，必须禁用“管理模式”。

### <a name="how-to-disable-administration-mode"></a>如何禁用管理模式

禁用组织实例的管理模式：

1. 打开 Dynamics 365 实例选取器：https://port.crm.dynamics.com/G/Instances/InstancePicker.aspx。
2. 选择运行解决方案检查器有问题的组织实例。
3. 选择 **ADMIN**。<br/>
![实例管理](media/solution-checker-instance-admin.png)

4. 清除**启用管理模式**，然后选择**保存**。<br/>
![禁用管理模式](media/solution-checker-instance-disable-admin-mode.png)

5. 再次运行解决方案检查器。

## <a name="solution-checker-fails-due-to-missing-security-roles"></a>解决方案检查器由于缺少安全角色失败

解决方案检查器的应用程序用户需要两个分派的安全角色来提供与 Common Data Service 组织进行通信所需的必要权限。 如果这些角色的哪一个未分派给用户**PowerApps 检查器**，尝试运行分析、下载结果和运行取消将失败。 这最经常在客户已部署了可移除意外用户的安全角色的自动化时发生。 以下安全角色包含最低必需权限：

- 导出自定义项
- 解决方案检查器

### <a name="how-to-assign-missing-security-roles"></a>如何分派缺少的安全角色

向 PowerApps 检查器用户分派缺少的安全角色：

1. 打开您的 Common Data Service 组织并导航到**设置** > **安全性** > **用户**。
2. 从用户列表中选择**PowerApps 检查器**用户。
3. 在命令栏中选择**管理角色**。
4. 选中**导出自定义项**和**解决方案检查器**角色复选框，然后选择**确定**。<br/>
![所需安全角色](media/solution-checker-required-roles.png)

5. 再次运行解决方案检查器。

## <a name="solution-checker-fails-due-to-restricted-access-mode"></a>解决方案检查器由于受限访问模式失败

解决方案检查器的应用程序用户需要**非交互**或**读写**访问模式来与 Common Data Service 组织通信。 如果访问模式已更改为其他值，如**管理**，则尝试运行分析、下载结果和运行取消将失败。

若要解决此问题，必须更新具有“非交互”访问模式的**PowerApps 检查器**应用程序用户。

### <a name="how-to-update-user-access-mode"></a>如何更新用户访问模式

更新 PowerApps 检查器用户的访问模式：

1. 打开您的 Common Data Service 组织并导航到**设置** > **安全性** > **用户**。
2. 从用户列表中选择**PowerApps 检查器**用户，然后双击打开用户窗体。
3. 滚动到窗体的**管理** > **客户端访问许可证 (CAL) 信息**部分。
4. 在**访问模式**下拉列表控件中选择**非交互**。<br/>
![访问模式](media/solution-checker-access-mode.png)

5. 保存并关闭用户窗体。
6. 再次运行解决方案检查器。

## <a name="solution-checker-fails-due-to-disabled-first-party-application-in-aad"></a>解决方案检查器由于在 AAD 中禁用了第一方应用程序失败

解决方案检查器使用的第一方企业应用程序标识 (PowerApps-Advisor) 不应在 Azure Active Directory (AAD) 中禁用。 如果禁用，在代表请求用户为 Common Data Service 和其他所需资源提供商请求持有者令牌时此标识将无法进行身份验证。 

请按照下面的步骤验证应用程序标识是否未在 AAD 中被禁用，同时，如果有必要，启用应用程序。

### <a name="how-to-verify-andor-modify-application-enabled-status"></a>如何验证和/或修改应用程序启用状态

验证和/或修改 PowerApps-Advisor 企业应用程序标识的启用状态

1. 在 [Azure Active Directory (AAD) 门户](https://aad.portal.azure.com/)中访问您的租户。
2. 导航至**企业应用程序**。
3. 选择**所有应用程序**，然后搜索**PowerApps-Advisor**。<br/>
![搜索 PowerApps-Advisor 应用](media/solution-checker-search-advisor-app.png)

4. 选择**PowerApps-Advisor**查看应用详细信息。
5. 选择**属性**。
6. 检查**已为用户登录启用**的状态。 如果为**否**，则应用程序被禁用。<br/>
![禁用的企业应用](media/solution-checker-disabled-app.png)

7. 选择单选按钮控件将值切换到**是**。 这将启用应用程序。<br/>
![启用 PowerApps-Advisor 应用](media/solution-checker-enable-app.png)

8. 选择**保存**。 应用程序现在已启用。 您可能需要等待几分钟让更改传播。
9. 再次运行解决方案检查器。

> [!IMPORTANT]
> 您必须在 Azure Active Directory (AAD) 中具有管理员权限才能编辑企业应用程序。

## <a name="solution-checker-fails-to-export-solutions-with-draft-business-process-flow-components"></a>解决方案检查器无法导出具有草稿业务流程组件的解决方案

如果解决方案包含之前从未激活的草稿状态的业务流程组件，则解决方案检查器将无法为分析导出解决方案。 此错误对于解决方案检查器不是唯一的，其由在后备（自定义）实体组件（在业务流程第一次激活前未创建）上有依赖项的业务流程引发。 如果业务流程在解决方案资源管理器内激活动，也可能发生此问题。

请参考[知识库文章 #4337537：导出无效 - 业务流程实体缺失](https://support.microsoft.com/en-hk/help/4337537/invalid-export-business-process-entity-missing)，了解此问题和解决步骤的详细信息。

## <a name="solution-checker-fails-to-export-patched-solutions"></a>解决方案检查器无法导出已修补的解决方案

如果解决方案已应用了[修补程序](https://docs.microsoft.com/powerapps/developer/common-data-service/create-patches-simplify-solution-updates)，解决方案检查器将无法导出解决方案以进行分析。 在解决方案应用了修补程序后，原始解决方案将被锁定，只要将解决方案确定为父解决方案的组织中有相关修补程序，其将无法更改或导出，

若要解决该问题，可以克隆解决方案，以便与解决方案相关的所有修补程都汇总到新建的解决方案中。 这将解锁解决方案并允许将解决方案从系统中导出。  有关详细信息，请参阅[克隆解决方案](use-segmented-solutions-patches-simplify-updates.md#clone-a-solution)。

## <a name="solution-checker-will-not-analyze-empty-solutions"></a>解决方案检查器不分析空解决方案

如果解决方案检查器导出未包含要分析的组件的解决方案，它将终止进一步处理并考虑运行失败。 请确保为解决方案检查器进行分析提交的选定解决方案至少包含一个组件。

## <a name="solution-checker-fails-to-export-large-solutions"></a>解决方案检查器无法导出较大解决方案

从 Common Data Service 环境导出较大解决方案失败的主要场景包括导出请求中的超时异常。 如果请求超过 20 分钟，则会出现此情况。 大解决方案，如默认解决方案，可能无法在此时间期限内导出，检查将无法成功完成。 如果解决方案检查器在导出时遇到超时，它将重试三次，然后确定无法处理作业，因此您可能需要一小时时间收到失败通知。

解决方法是创建更小的解决方案，使其要分析的组件更少。 如果解决方案的文件很大是由于很多插件程序集组件，请参阅[优化自定义程序集开发](../../developer/common-data-service/best-practices/business-logic/optimize-assembly-development.md)中的指导。 

> [!IMPORTANT]
> 为了尽可能减少误报，请确保您添加相关的自定义项。 当您创建解决方案和添加这些组件时，请包括以下内容：
> - 当您添加插件时，包括插件的 SDK 消息处理步骤。
> - 在添加实体窗体时，包括附加到窗体事件的 JavaScript Web 资源。  
> - 在添加 JavaScript Web 资源时，包括所有相关的 JavaScript Web 资源。
> - 当您添加 HTML Web 资源时，包括在 HTML Web 资源中定义的任何相关的脚本。
> - 在添加自定义工作流时，包含工作流中使用的程序集。

## <a name="line-number-references-for-issues-in-html-resources-with-embedded-javascript-are-not-correct"></a>具有嵌入的 JavaScript 的 HTML 资源中问题的行号引用不正确 

当在解决方案检查器内处理了 HTML Web 资源时，HTML Web 资源将在 HTML Web 资源内与 JavaScript 分开单独处理。 因此，在 HTML Web 资源的 `<script>` 内找到的冲突的行号将不正确。

## <a name="web-unsupported-syntax-issue-for-web-resources"></a>Web 资源的 Web-unsupported-syntax 问题

解决方案检查器当前不支持 ECMAScript 6 (2015) 或更高版本。 当解决方案检查器使用 ECMAScript 6 或更高版本分析 JavaScript 时，将报告 Web 资源的 web-supported-syntax 问题。  

## <a name="multiple-violations-reported-for-plug-ins-and-workflow-activities-based-on-call-scope"></a>基于调用范围报告的插件和工作流活动的多个冲突

对于问题仅与调用上下文相关的插件和工作流活动规则，解决方案检查器工具将在 IPlugin 接口实现时开始分析，并遍历调用图表来检测该实现范围内的问题。  有时，许多调用路径可能到达检测到问题的相同位置。  由于此问题与调用范围相关，工具可能基于该范围报告来提供更好的影响图片，而不是基于不同位置。 因此，多个问题可能引用应该修复的一个位置。

## <a name="see-also"></a>另请参阅
[Common Data Service 的最佳实践和指南](../../developer/common-data-service/best-practices/index.md)<br/>
[模型驱动应用的最佳实践和指南](../../developer/model-driven-apps/best-practices/index.md)<br/>
