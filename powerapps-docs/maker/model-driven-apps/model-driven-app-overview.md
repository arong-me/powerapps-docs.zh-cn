---
title: 借助 PowerApps 生成模型驱动应用的概述 | Microsoft Docs
description: 提供分步说明，介绍如何创建并配置实体以将其与 PowerApps 应用结合使用。
documentationcenter: na
author: Mattp123
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/21/2018
ms.author: matp
ms.openlocfilehash: eceaf1886bf77b85d6d6b3faae3f32428223cb7e
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2018
ms.locfileid: "37899493"
---
# <a name="overview-of-building-a-model-driven-app"></a>生成模型驱动应用的概述

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
定义并强制执行一致的业务流程是模型驱动应用设计的一个重要方面。 一致的流程可以确保应用的用户能专注于他们的工作，而无需花精力记住手动步骤。 流程可以简单也可以复杂，并且不断变化。 若要创建流程，选择“高级”，打开[解决方案资源管理器](#advanced-model-driven-app-making)。 接下来，在解决方案资源管理器的左侧导航窗格中选择“流程”，然后选择“新建”。 更多信息：[处理业务逻辑](#working-with-business-logic)  

### <a name="composing-the-model-driven-app"></a>编写模型驱动应用
完成数据建模和流程定义后，使用应用设计器选择并配置所需组件以生成应用。

![应用设计器](media/model-driven-app-overview/app-designer.png)

## <a name="model-driven-app-components-and-designers"></a>模型驱动应用组件和设计器
设计良好的模型驱动应用包含设计器选择的组件，以生成最终应用的外观和功能。 这些构成应用的组件和组件属性成为了元数据。 要了解每个组件与应用设计之间的关系，此处将它们分为以下几类：“数据”、“UI”、“逻辑”和“可视化”。 

### <a name="data"></a>数据
这些组件决定了应用基于哪些数据。



|组件  |描述  |设计器  |
|---------|---------|---------|
|实体     |包含你跟踪的属性的项，例如“联系人”或“帐户”。 提供很多标准实体。 可以自定义非系统标准实体（生产实体）或从头创建自定义实体。     | [!INCLUDE [powerapps](../../includes/powerapps.md)] entity designer        |
|字段     | 一个与实体关联的属性。 字段由数据类型定义，数据类型决定了可以输入或可以选中的数据类型。 例如文本、数字、日期和时间、货币或查找（创建与其他实体之间的关系）。 字段通常与窗体、视图以及搜索结合使用。        | [!INCLUDE [powerapps](../../includes/powerapps.md)] entity designer   |
|关系     | 实体关系定义了实体与实体之间的关联方式。 有三种类型的关系：1:N（一对多）、N:1（多对一）以及 N:N（多对多）。 例如，将查找字段添加到实体会在两个实体间创建一个新的 1:N 关系，并且你可以将查找字段放置在窗体上。   | [!INCLUDE [powerapps](../../includes/powerapps.md)] entity designer        |
|选项集字段     | 这是字段的一种特殊类型，为用户提供一组预定的选项。 每个选项都有一个数值和标签。 将字段添加到窗体时，字段会显示一个控件，以便用户选择一个选项。  有两种类型的选项集：选项集，用户只能选择一个选项；多选选项集，用户可以进行多选。  | [!INCLUDE [powerapps](../../includes/powerapps.md)] 选项集设计器     |

### <a name="ui"></a>UI
这些组件决定了用户与应用的交互方式。 

|组件  |描述  |设计器  |
|---------|---------|---------|
|应用     | 决定应用程序的基础元素，例如应用的组件、属性、客户端类型和 URL。      | 应用设计器   |
|站点地图     | 指定应用的导航设置        | 站点地图设计器        |
|窗体     | 给定实体的一组数据输入字段，这组字段与组织为实体跟踪的项相匹配。 例如一组数据输入字段，该字段让用户输入相关信息以跟踪客户以前的订单和客户特别要求的再订购日期。        | 窗体设计器        |
|查看     | 视图定义了特定实体的记录列表在应用程序中的显示方式。 视图定义了要显示的列、每列的宽度、排序方式和默认筛选器。   |  视图设计器       |

![应用程序设计器和窗体设计器](media/model-driven-app-overview/app-and-form-designers.png)

### <a name="logic"></a>逻辑
确定应用的业务流程、规则和自动化。 [!INCLUDE [powerapps](../../includes/powerapps.md)] 创建者使用特定于流程类型或规则的设计器。 


|逻辑类型  |描述  |设计器  |
|---------|---------|---------|
|业务流程     | 这是一种联机流程，引导用户完成标准的业务流程。 例如，如果希望每个人都以同样的方式处理客户服务请求，或者要求员工在提交订单之前获得使用发票的批准，请使用业务流程。        | 业务流程设计器        |
|工作流     |  工作流自动执行业务流程，无需用户界面。 设计器使用工作流启动自动化操作，无需用户交互。       | 工作流设计器        |
|操作    |  操作是一种流程，让你直接从工作流中手动调用操作，包括自定义操作。       |  流程设计器       |
|业务规则     | 用于向窗体应用规则或建议逻辑，例如设置字段要求、隐藏字段或验证数据。 应用程序设计器使用简单的界面以实现并维护快速变化且通用的规则。         |  业务规则设计器       |
|流     | 流是基于云的服务，让你在应用和服务之间创建自动化工作流，以获取通知、同步文件、收集数据等。        | Microsoft Flow        |

![工作流、操作和业务流程设计器](media/model-driven-app-overview/designer-mash.png)

### <a name="visualizations"></a>可视化
决定将在应用中提供的数据可视化和报告类型。


|组件  |描述  |设计器  |
|---------|---------|---------|
|图表     | 可以在视图、窗体中显示或可以添加到仪表板的单个图形可视化。        | 图表设计器        |
|仪表板     | 用于处理一个或多个图形可视化，提供可操作的业务数据的概览。        | 仪表板设计器        |
|嵌入式 Power BI     | 将嵌入式 Power BI 磁贴和仪表板添加到应用。 Power BI 是基于云的服务，提供商业智能见解。        |  图表设计器、仪表板设计器和 Power BI 的组合       |

![示例仪表板](media/model-driven-app-overview/dashboard-designer.png)

### <a name="advanced-model-driven-app-making"></a>创建高级模型驱动应用
解决方案资源管理器是一种综合工具，用于生成高级模型驱动应用。 在解决方案资源管理器中，可以使用工具左侧的导航窗格，在包含所有应用组件的层次结构中导航。

![解决方案资源管理器](media/model-driven-app-overview/solutionexplorer-entitiescollapsed.png)

若要打开解决方案资源管理器，在 [!INCLUDE [powerapps](../../includes/powerapps.md)] 的左侧窗格上选择“模型驱动”。

  ![选择模型驱动](media/model-driven-app-overview/app-type-picker-mod.png)

然后选择“高级”选项卡。 

## <a name="model-driven-app-development-resources"></a>模型驱动应用开发资源
若要详细了解模型驱动应用开发，请查看下列主题。
### <a name="modeling-your-data"></a>数据建模
- [使用应用程序设计器设计自定义商业应用](https://docs.microsoft.com/dynamics365/customer-engagement/customize/design-custom-business-apps-using-app-designer)
- [创建并设计窗体](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-design-forms)
- [创建或编辑视图](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-views)  

### <a name="modeling-and-composing-your-app"></a>建模并编写应用
- [创建或编辑实体](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-entities)
- [创建并编辑关系](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-entity-relationships) 
- [创建并编辑字段](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-fields)
- [创建并编辑全局选项集](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-global-option-sets)

### <a name="working-with-business-logic"></a>处理业务逻辑
- [业务流程概述](https://docs.microsoft.com/dynamics365/customer-engagement/customize/business-process-flows-overview)
- [使用工作流程自动执行流程](https://docs.microsoft.com/dynamics365/customer-engagement/customize/workflow-processes)
- [操作概述](https://docs.microsoft.com/dynamics365/customer-engagement/customize/actions)
- [创建业务规则和建议以应用逻辑](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-business-rules-recommendations-apply-logic-form)

### <a name="using-visualizations-in-your-app"></a>在应用中使用可视化效果
- [创建或编辑系统图表](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-system-chart)
- [创建或编辑仪表板](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-dashboards)


### <a name="distributing-your-app"></a>分发应用
[创建解决方案](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-solution)

## <a name="next-steps"></a>后续步骤
[快速入门：创建自定义实体](../common-data-service/data-platform-create-entity.md)

[教程：在 PowerApps 中创建含组件的自定义实体](../common-data-service/create-custom-entity.md)

