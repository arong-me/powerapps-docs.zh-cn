---
title: 通过代码应用业务逻辑 | Microsoft Docs
description: 了解开发人员如何使用代码在 Common Data Service for Apps 中应用业务逻辑。
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
ms.openlocfilehash: 9abcbf25d2376e28f83988ceb3797d3891ca53bc
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42843328"
---
# <a name="apply-business-logic-with-code"></a>使用代码应用业务逻辑

只要有可能，当要求涉及定义业务逻辑时，就应该先应用其中一个声明性流程选项。 请参阅 [Dynamics 365 客户参与自定义指南：创建进程的自定义业务逻辑](/dynamics365/customer-engagement/customize/guide-staff-through-common-tasks-processes)

声明性流程不满足要求时，开发人员有多种选择。 本主题将介绍编写代码的常用选项。

## <a name="create-a-workflow-extension"></a>创建工作流扩展

可以编写 .NET 程序集提供进程设计器中的新选项。 此方法为使用工作流设计器应用条件或执行新操作的人提供新的选择。 然后，非开发人员可以重新使用工作流扩展在代码中应用逻辑。

详细信息：[Dynamics 365 客户参与开发人员指南：自定义工作流活动（工作流程序集）](/dynamics365/customer-engagement/developer/custom-workflow-activities-workflow-assemblies)

## <a name="create-a-plug-in"></a>创建插件

可将插件的 .NET 程序集写到数据事务流以在服务器上应用业务逻辑。 通过 Common Data Service for Apps，有一个可以将特定事件注册为执行程序集类中定义的代码的框架。 该类继承一个公开[执行方法](/dotnet/api/microsoft.xrm.sdk.iplugin.execute)的特定接口。 注册的事件发生时，类上的 `Execute` 方法会被调用并且传递有关事件的上下文数据。

将使用“插件注册工具”注册程序集。

在 `Execute` 方法中，可以使用 SDK 程序集内定义的对象模型评估上下文事件数据，并执行相应操作来完成以下操作：
- 确定是否通过引发错误取消操作
- 对传递给执行方法的上下文数据进行更改
- 执行其他操作自动化使用组织服务的进程。

### <a name="synchronous-and-asynchronous-plug-ins"></a>同步和异步插件
可以将插件注册为在事务中同步执行，或者延迟并发送到队列以在对服务器影响更小的某一时间应用逻辑。 因此，首选异步插件。

将插件注册为事件同步运行时，选择代码应运行的时间。 有三个阶段：

|事件  |描述  |
|---------|---------|
|预验证|发生在数据库事务开始前。 此处是应用业务逻辑确定是否应在事务开始前取消操作的好位置，避免回滚事务的性能损失。|
|预操作|发生在数据库事务开始后。 在此阶段取消操作必须回滚事务|
|后操作|在主数据操作完成后在数据库事务中发生。 包括任意可能在早期事件中应用但是取消操作时引起更大损失的更改。|

> [!NOTE]
> 同步插件限制可用的系统资源数。 如果插件超出阈值或者无响应，那么将引发取消操作的异常。

详细信息：[Dynamics 365 客户参与开发人员指南：写插件扩展业务流程](/dynamics365/customer-engagement/developer/write-plugin-extend-business-processes)

### <a name="see-also"></a>另请参阅

[Common Data Service for Apps 开发人员概述](overview.md)
