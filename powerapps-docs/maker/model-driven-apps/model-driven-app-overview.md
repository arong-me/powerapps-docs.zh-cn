---
title: 使用 PowerApps 构建模型驱动应用程序概述 | Microsoft Docs
description: 包含创建和配置实体以使用 PowerApps 应用程序的分步说明。
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
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 38ea420dc973e5e6c0a4df2ff361344c4704137a
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711727"
---
# <a name="what-are-model-driven-apps-in-powerapps"></a>PowerApps 中的模型驱动应用程序是什么？

模型驱动应用程序的设计是以组件为中心的应用程序开发方法。 模型驱动应用程序的设计不需要代码，您制造的应用程序可以很简单，也可以非常复杂。  与画布应用程序的开发不同，其设计器对应用程序布局进行完全控制，而使用模型驱动应用程序，很多布局由您确定，大部分由您添加到应用程序的组件指定。 

![示例模型驱动应用程序](media/model-driven-app-overview/model-app-sample.png)

模型驱动应用程序提供以下好处：
- 丰富的以组件为中心的无代码设计环境 
- 使用从台式到移动跨各类设备的相似 UI 创建复杂的响应式应用程序。
- 丰富的设计功能 
- 您的应用程序可以作为解决方案分发
 
## <a name="the-approach-to-model-driven-app-making"></a>模型驱动应用程序的制造方法
在基本层面，模型驱动应用程序制造包括三个关键的关注方面。

- 对业务数据建模 
- 定义业务流程 
- 编写应用程序

### <a name="modeling-business-data"></a>对业务数据建模
若要对您的业务数据建模，您确定应用程序需要的数据，以及该数据如何与其他数据相关。 模型驱动设计使用元数据驱动的体系结构，以便设计人员可以在不编写代码的情况下自定义应用程序。 元数据是指“关于数据的数据”，它定义数据系统中存储的数据的结构。 [教程：在 PowerApps 中创建包含组件的自定义实体](../common-data-service/create-custom-entity.md)

### <a name="defining-business-processes"></a>定义业务流程
定义和强制实施一致的业务流程是模型驱动应用程序设计的一个重要方面。 一致的流程可以帮助确保应用程序用户可以关注其工作，而不是记住执行一套手动步骤。 流程可以简单也可以复杂，经常随时间变化。 若要创建一个流程，从 PowerApps.com 模型驱动区域，选择 ![设置](media/powerapps-gear.png) > **高级自定义** > **打开解决方案资源管理器**。 接下来，在解决方案资源管理器中的左侧导航窗格上，选择**流程**，然后选择**新建**。 详细信息：[业务流程概述](/flow/business-process-flows-overview)和[使用 Common Data Service 应用业务逻辑](../common-data-service/cds-processes.md)。 

### <a name="composing-the-model-driven-app"></a>编写模型驱动应用程序
在对数据建模并定义流程后，通过使用应用程序设计器选择并配置所需组件来构建应用程序。

![应用程序设计器](media/model-driven-app-overview/app-designer.png)

## <a name="next-steps"></a>后续步骤

[构建您的第一个模型驱动应用程序](build-first-model-driven-app.md)

[了解模型驱动应用程序组件](model-driven-app-components.md)

