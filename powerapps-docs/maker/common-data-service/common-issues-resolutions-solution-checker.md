---
title: 解决方案检查器的常见问题和解决 | Microsoft Docs
description: ' 解决方案检查器内的常见问题和解决的列表'
keywords: ''
ms.date: 02/11/2019
ms.service:
  - powerapps
ms.custom:
  - ''
ms.topic: article
ms.assetid: caa4e3f2-9700-49b8-87ed-8a68e8878b02
author: jowells1
ms.author: jowells
manager: austinj
ms.reviewer: null
robots: 'noindex,nofollow'
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="common-issues-and-resolutions-for-solution-checker"></a>解决方案检查器的常见问题和解决

本文列出您在使用解决方案检查器时可能会遇到的一些常见问题。 如果有，将提供解决方法。

## <a name="solution-checker-runs-fail-due-to-powerapps-checker-version-installed"></a>解决方案检查器由于安装了 PowerApps 检查器版本而失败
解决方案检查器是 PowerApps 检查器解决方案附带的功能。  如果您有早于 1.0.0.47 的 PowerApps 检查器版本，解决方案检查器将无法成功完成。 您应从 [!INCLUDE [pn-dyn-365-admin-center](../../includes/pn-dyn-365-admin-center.md)] 升级您的 PowerApps 检查器版本。 

但是，如果您安装了 1.0.0.45 以前的 PowerApps 检查器版本，我们建议您删除解决方案并重新进行安装。 由于最近的架构更改，从早于 1.0.0.45 的版本升级 PowerApps 检查器可能失败。

如果要保留解决方案检查器过去的结果，请使用[将数据导出至 Excel](../../user/export-data-excel.md) 从以下实体导出数据来导出之前运行的结果或导出所有解决方案检查器数据

- 分析组件
- 分析作业
- 分析结果
- 分析结果详细信息

### <a name="delete-powerapps-checker"></a>删除 PowerApps 检查器

删除 PowerApps 检查器解决方案：

1. 作为系统管理员或系统定制员，转到 https://web.powerapps.com/environments 打开 PowerApps 门户。
2. 选择**解决方案**。
3. 选择 **PowerApps 检查器**，然后在解决方案工具栏上，选择**删除**。

### <a name="add-powerapps-checker"></a>添加 PowerApps 检查器

将 PowerApps 检查器重新添加到 Common Data Service 环境：

1. 作为系统管理员或系统定制员，转到 https://web.powerapps.com/environments 打开 PowerApps 门户。
2. 选择**解决方案**。
3. 在解决方案工具栏上选择**解决方案检查器**，然后选择**安装**。

## <a name="runs-on-large-solutions-fail"></a>在较大解决方案上运行失败

如果解决方案太大，可能出现几个不同的场景。 这些场景在下面进一步说明。 每个场景的解决方法是创建更小的解决方案，使其要分析的组件更少。 如果解决方案的文件很大是由于插件程序集组件，请参阅[优化自定义程序集开发](../../developer/common-data-service/best-practices/business-logic/optimize-assembly-development.md)中的指导。

解决方案检查器可能无法根据这些场景检查解决方案：
- 30MB 解决方案文件大小限制的硬性限制。  
- 从 Common Data Service 环境导出解决方案有 10 分钟的超时。 大解决方案，如默认解决方案，可能无法在此时间内导出，检查将无法成功完成。 解决方案检查器将重试三次，然后确定无法处理作业，因此您可能需要 30 分钟时间收到失败通知。

若要解决这些问题，请检查或创建要分析的更小解决方案。 为了尽可能减少误报，请确保您添加相关的自定义项。 当您创建解决方案和添加这些组件时，请包括以下内容：

- 当您添加插件时，包括插件的 SDK 消息处理步骤。
- 在添加实体窗体时，包括附加到窗体事件的 JavaScript Web 资源。  
- 在添加 JavaScript Web 资源时，包括所有相关的 JavaScript Web 资源。
- 当您添加 HTML Web 资源时，包括在 HTML Web 资源中定义的任何相关的脚本。
- 在添加自定义工作流时，包含工作流中使用的程序集。

## <a name="solution-checker-run-or-download-results-dont-complete"></a>解决方案检查器运行或下载结果未完成 
在运行解决方案检查器不久后，操作未完成并显示以下消息：<br />
“我们无法在 *SOLUTIONNAME* 解决方案上运行检查。 请尝试再次运行。” <br />
![无法运行](media/solution-checker-werent-able-to-run.png)

出现此问题的原因是组织处理**管理模式**状态，解决方案检查器无法验证执行此请求的用户权限。 若要解决此问题，请禁用管理模式。 

### <a name="disable-administration-mode-for-an-instance"></a>禁用实例的管理模式
1. 访问 Dynamics 365 for Customer Engagement 实例选取器：https://port.crm.dynamics.com/G/Instances/InstancePicker.aspx。
2. 选择运行解决方案检查器有问题的实例。
3. 选择 **ADMIN**。<br />
![实例管理](media/solution-checker-instance-admin.png)

4. 清除**启用管理模式**。 <br />
![禁用管理模式](media/solution-checker-instance-disable-admin-mode.png)

5. 再次运行解决方案检查器。

## <a name="solution-checker-will-not-process-patched-solutions"></a>解决方案检查器不会处理已修补的解决方案

如果解决方案已应用了[修补程序](https://docs.microsoft.com/powerapps/developer/common-data-service/create-patches-simplify-solution-updates)，解决方案检查器将无法导出解决方案以进行分析。 在解决方案应用了修补程序后，原始解决方案将被锁定，只要将解决方案确定为父解决方案的组织中有相关修补程序，其将无法更改或导出，

若要解决该问题，可以克隆解决方案，以便与解决方案相关的所有修补程都汇总到新建的解决方案中。 这将解锁解决方案并允许将解决方案从系统中导出。 详细信息：[克隆解决方案](use-segmented-solutions-patches-simplify-updates.md#clone-a-solution)

## <a name="line-number-references-for-issues-in-html-resources-with-embedded-javascript-are-not-correct"></a>具有嵌入的 JavaScript 的 HTML 资源中问题的行号引用不正确 

当在解决方案检查器内处理了 HTML Web 资源时，HTML Web 资源将在 HTML Web 资源内与 JavaScript 分开单独处理。 因此，在 HTML Web 资源的 `<script>` 内找到的冲突的行号将不正确。

## <a name="web-unsupported-syntax-issue-for-web-resources"></a>Web 资源的 Web-unsupported-syntax 问题

解决方案检查器当前不支持 ECMAScript 6 (2015) 或更高版本。 当解决方案检查器使用 ECMAScript 6 或更高版本分析 JavaScript 时，将报告 Web 资源的 web-supported-syntax 问题。  

## <a name="see-also"></a>另请参阅
[Common Data Service 的最佳实践和指南](../../developer/common-data-service/best-practices/index.md)<br />
[模型驱动应用的最佳实践和指南](../../developer/model-driven-apps/best-practices/index.md)<br />
