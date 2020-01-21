---
title: 在 Common Data Service 中应用业务逻辑 | MicrosoftDocs
description: 了解可以在应用中使用的不同类型的业务逻辑
ms.custom: ''
ms.date: 12/20/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 0b4e6602-5701-4859-81cc-6f6fe50901b2
caps.latest.revision: 44
author: Mattp123
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9267f8385e19d3c0b87a36b495a4ff2b88b4d420
ms.sourcegitcommit: f70be39855e4931312fe0035525586a15ed4487b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2019
ms.locfileid: "2922357"
---
# <a name="apply-business-logic-in-common-data-service"></a>在 Common Data Service 中应用业务逻辑
Common Data Service 中有一些用于分析业务逻辑的选项。 

## <a name="business-rules"></a>业务规则
无需编写代码或创建插件，即可创建业务规则和建议以应用逻辑和验证。业务规则可以提供一个简单的界面来实施和维护快速更改和常用的规则。

为实体定义应用于所有实体窗体的和服务器级别的*业务规则*。 如果在应用程序中使用实体，则为该实体定义的业务规则同时应用于*画布应用程序*和*模型驱动的应用程序*。 详细信息，[为实体创建业务规则](data-platform-create-business-rule.md)。

> [!NOTE]
> 若要定义应用于模型驱动的应用程序中的窗体的业务规则，请参阅[为模型驱动的应用程序窗体创建业务规则](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)

## <a name="power-automate"></a>Power Automate
除了可用于同步文件，获取通知，收集数据等的流之外，Power Automate 还有可用于在 Common Data Service 内或 Common Data Service 和另一个应用之间创建自动化工作流的流。 


|流类型  |说明  |更多信息  |
|---------|---------|---------|
|业务流程     | 定义中 Power Apps 模型驱动应用中运行的一组步骤，供用户执行来获得所需结果。        | [了解更多](/power-automate/create-business-process-flow)     |
|自动化流     |  创建在被事件触发后自动执行一个或多个任务的流。    | [了解更多](/power-automate/get-started-logic-flow)        |
|按钮流   | 随时随地通过移动设备上的流应用运行重复性任务。        | [了解更多](/power-automate/introduction-to-button-flows)        |
|计划流   | 创建按计划执行一个或多个任务的流。    | [了解更多](/power-automate/run-scheduled-tasks)        |
|UI 流   | 在旧软件中录制和自动运行手动步骤。    | [了解更多](/power-automate/ui-flows/overview)     |


## <a name="classic-common-data-service-processes"></a>经典 Common Data Service 进程
也可以使用经典 Common Data Service 流程，其形式为工作流和操作。 详细信息：[Power Automate：使用工作流过程](/flow/workflow-processes)和[Power Automate：操作概述](/flow/actions)。

### <a name="see-also"></a>另请参阅

[在模型驱动的应用程序中应用业务逻辑](../model-driven-apps/guide-staff-through-common-tasks-processes.md)
