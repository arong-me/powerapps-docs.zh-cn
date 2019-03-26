---
title: 开发人员：在 Common Data Service 中进行插件和工作流开发的最佳做法和指南 | Microsoft Docs
description: 面向 PowerApps 中 Common Data Service 开发人员的插件和工作流开发最佳做法和指南。
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 1/15/2019
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---
# <a name="best-practices-and-guidance-regarding-plug-in-and-workflow-development-for-the-common-data-service"></a>在 Common Data Service 中进行插件和工作流开发的最佳做法和指南

下表包含所有关于在 Common Data Service 中进行插件和工作流开发的指南和最佳做法。

|最佳做法  |描述  |
|---------|---------|
|[避免在插件和工作流活动中使用批处理请求类型](avoid-batch-requests-plugin.md)     |不得在插件或工作流活动的上下文中使用 ExecuteMultipleRequest 或 ExecuteTransactionRequest 消息请求类。         |
|[将 IPlugin 实现开发为“无状态”](develop-iplugin-implementations-stateless.md)     |实现 IPlugin 的类成员可能遇到线程安全性问题，这会导致数据不一致或性能问题。         |
|[不要复制插件单步注册](do-not-duplicate-plugin-step-registration.md)     |重复的插件单步注册将导致插件对同一消息/事件多次触发。         |
|[在插件注册中包括筛选特性](include-filtering-attributes-plugin-registration.md)     |如果未为插件注册步骤设置筛选特性，则在该事件每次出现更新消息时，都会执行插件。         |
|[对 Retrieve 和 RetrieveMultiple 消息限制插件注册](limit-registration-plugins-retrieve-retrievemultiple.md)     |如果将同步插件逻辑添加到 Retrieve 和 RetrieveMultiple 消息事件，则可能导致速度缓慢。         |
|[优化自定义程序集开发](optimize-assembly-development.md)     |请考虑将单独的插件/自定义工作流活动合并到单个自定义程序集中，从而提升性能和可维护性，同时在程序集大小接近沙盒程序集大小约束时，将插件/自定义工作流活动移动到多个自定义程序集。         |
|[在插件中与外部主机交互时，将 KeepAlive 设置为 false](set-keepalive-false-interacting-external-hosts-plugin.md)     |如果 KeepAlive 特性在 HTTP 请求头中设置为 true 或未显式定义为 false，则会导致插件执行时间增加。         |
|[在插件和工作流活动中使用 InvalidPluginExecutionException](use-invalidpluginexecutionexception-plugin-workflow-activities.md)     |当插件或工作流活动的上下文中引发错误时，使用 InvalidPluginExecutionException。         |

# <a name="see-also"></a>另请参阅
[使用代码应用业务逻辑](../../apply-business-logic-with-code.md)<br />
[使用插件扩展业务进程](../../plug-ins.md)<br />
[工作流扩展](../../workflow/workflow-extensions.md)<br />