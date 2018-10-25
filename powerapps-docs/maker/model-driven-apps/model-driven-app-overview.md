---
title: 借助 PowerApps 生成模型驱动应用的概述 | Microsoft Docs
description: 提供分步说明，介绍如何创建并配置实体以将其与 PowerApps 应用结合使用。
documentationcenter: na
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 08/09/2018
ms.author: matp
ms.openlocfilehash: f6434e6a9248586c05fa0b56b8934d910af3087a
ms.sourcegitcommit: 2a61989be5880fede31510c5dab1593a6f42a741
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "39723837"
---
# <a name="what-are-model-driven-apps-in-powerapps"></a>PowerApps 中的模型驱动应用是什么？

模型驱动应用设计是一种侧重于组件的应用开发方法。 模型驱动应用设计不需要代码，无论是简单还是非常复杂的应用，都可以开发。  画布应用开发中的应用布局完全受设计器控制，但是对于模型驱动应用，大多数布局已为你确定，并主要由添加到应用的组件指定。 

![示例模型驱动应用](media/model-driven-app-overview/model-app-sample.png)

模型驱动应用设计具有下列优势：
- 丰富的针对组件的无代码设计环境 
- 创建复杂的响应式应用，具备在多种设备（从台式机到移动设备）上类似的 UI
- 设计功能与 Dynamics 365 客户参与平台上的可用功能类似 
- 可将应用作为解决方案分发
 
## <a name="the-approach-to-model-driven-app-making"></a>创建模型驱动应用的方法
从基本层面看，模型驱动应用的创建由三个关键方面组成。

- 业务数据建模 
- 定义业务流程 
- 编写应用

### <a name="modeling-business-data"></a>业务数据建模
对于业务数据建模，确定应用需要什么数据并确定此数据将如何与其他数据关联。 模型驱动设计使用元数据驱动的体系结构，使设计者无需编写代码即可自定义应用程序。 元数据是“描述数据的数据”，它定义了系统中存储的数据的结构。 [教程：在 PowerApps 中创建含组件的自定义实体](../common-data-service/create-custom-entity.md)

### <a name="defining-business-processes"></a>定义业务流程
定义并强制执行一致的业务流程是模型驱动应用设计的一个重要方面。 一致的流程可以确保应用的用户能专注于他们的工作，而无需花精力记住手动步骤。 流程可以简单也可以复杂，并且不断变化。 若要创建流程，则从 PowerApps.com 的“模型驱动”区选择![设置](media/powerapps-gear.png)  > “高级自定义” > “打开解决方案资源管理器”。 接下来，在解决方案资源管理器的左侧导航窗格中选择“流程”，然后选择“新建”。 详细信息：[业务流程概述](/flow/business-process-flows-overview)及[通过 Common Data Service for Apps 应用业务逻辑](../common-data-service/cds-processes.md)。 

### <a name="composing-the-model-driven-app"></a>编写模型驱动应用
完成数据建模和流程定义后，使用应用设计器选择并配置所需组件以生成应用。

![应用设计器](media/model-driven-app-overview/app-designer.png)

## <a name="next-steps"></a>后续步骤

[生成首个模型驱动应用](build-first-model-driven-app.md)

[了解模型驱动应用的组件](model-driven-app-components.md)

