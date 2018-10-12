---
title: 了解 PowerApps 中的模型驱动应用组件 | Microsoft Docs
description: 了解模型驱动应用的各种组件，如数据、UI、逻辑和可视化效果。
Keywords: fields, attributes, model-driven app
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: crm-online
ms.topic: article
ms.openlocfilehash: 249f0d35ce9eb466303ef16658aa01198632875e
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667842"
---
# <a name="understand-model-driven-app-components"></a>了解模型驱动应用的组件
设计良好的模型驱动应用包含你使用设计器选择的多个组件，用于生成最终应用的外观和功能。 这些构成应用的组件和组件属性成为了元数据。 

要了解每个组件与应用设计之间的关系，此处将它们分为以下几类：“数据”、“UI”、“逻辑”和“可视化”。 

## <a name="data"></a>数据
这些组件决定了应用基于哪些数据。


|组件  |描述  |设计器  |
|---------|---------|---------|
|实体     |包含你跟踪的属性的项，例如“联系人”或“帐户”。 提供很多标准实体。 可以自定义非系统标准实体（生产实体）或从头创建自定义实体。     | [!INCLUDE [powerapps](../../includes/powerapps.md)] entity designer        |
|字段     | 一个与实体关联的属性。 字段由数据类型定义，数据类型决定了可以输入或可以选中的数据类型。 例如文本、数字、日期和时间、货币或查找（创建与其他实体之间的关系）。 字段通常与窗体、视图以及搜索结合使用。        | [!INCLUDE [powerapps](../../includes/powerapps.md)] entity designer   |
|关系     | 实体关系定义了实体与实体之间的关联方式。 有三种类型的关系：1:N（一对多）、N:1（多对一）以及 N:N（多对多）。 例如，将查找字段添加到实体会在两个实体间创建一个新的 1:N 关系，并且你可以将查找字段放置在窗体上。   | [!INCLUDE [powerapps](../../includes/powerapps.md)] entity designer        |
|选项集字段     | 这是字段的一种特殊类型，为用户提供一组预定的选项。 每个选项都有一个数值和标签。 将字段添加到窗体时，字段会显示一个控件，以便用户选择一个选项。  有两种类型的选项集：选项集，用户只能选择一个选项；多选选项集，用户可以进行多选。  | [!INCLUDE [powerapps](../../includes/powerapps.md)] 选项集设计器     |

详细信息：[定义模型驱动应用的数据](define-data-model-driven-app.md) 

## <a name="ui"></a>UI
这些组件决定了用户与应用的交互方式。 

|组件  |描述  |设计器  |
|---------|---------|---------|
|应用     | 决定应用程序的基础元素，例如应用的组件、属性、客户端类型和 URL。      | 应用设计器   |
|站点地图     | 指定应用的导航设置        | 站点地图设计器        |
|窗体     | 给定实体的一组数据输入字段，这组字段与组织为实体跟踪的项相匹配。 例如一组数据输入字段，该字段让用户输入相关信息以跟踪客户以前的订单和客户特别要求的再订购日期。        | 窗体设计器        |
|查看     | 视图定义了特定实体的记录列表在应用程序中的显示方式。 视图定义了要显示的列、每列的宽度、排序方式和默认筛选器。   |  视图设计器       |

![应用程序设计器和窗体设计器](media/model-driven-app-overview/app-and-form-designers.png)

## <a name="logic"></a>逻辑
确定应用的业务流程、规则和自动化。 [!INCLUDE [powerapps](../../includes/powerapps.md)] 创建者使用特定于流程类型或规则的设计器。 


|逻辑类型  |描述  |设计器  |
|---------|---------|---------|
|业务流程     | 这是一种联机流程，引导用户完成标准的业务流程。 例如，如果希望每个人都以同样的方式处理客户服务请求，或者要求员工在提交订单之前获得使用发票的批准，请使用业务流程。        | 业务流程设计器        |
|工作流     |  工作流自动执行业务流程，无需用户界面。 设计器使用工作流启动自动化操作，无需用户交互。       | 工作流设计器        |
|操作    |  操作是一种流程，让你直接从工作流中手动调用操作，包括自定义操作。       |  流程设计器       |
|业务规则     | 用于向窗体应用规则或建议逻辑，例如设置字段要求、隐藏字段或验证数据。 应用程序设计器使用简单的界面以实现并维护快速变化且通用的规则。         |  业务规则设计器       |
|流     | 流是基于云的服务，让你在应用和服务之间创建自动化工作流，以获取通知、同步文件、收集数据等。        | Microsoft Flow        |

![工作流、操作和业务流程设计器](media/model-driven-app-overview/designer-mash.png)

详细信息：[在模型驱动应用中应用业务逻辑](guide-staff-through-common-tasks-processes.md)

## <a name="visualizations"></a>可视化
决定将在应用中提供的数据可视化和报告类型。


|组件  |描述  |设计器  |
|---------|---------|---------|
|图表     | 可以在视图、窗体中显示或可以添加到仪表板的单个图形可视化。        | 图表设计器        |
|仪表板     | 用于处理一个或多个图形可视化，提供可操作的业务数据的概览。        | 仪表板设计器        |
|嵌入式 Power BI     | 将嵌入式 Power BI 磁贴和仪表板添加到应用。 Power BI 是基于云的服务，提供商业智能见解。        |  图表设计器、仪表板设计器和 Power BI 的组合       |

![示例仪表板](media/model-driven-app-overview/dashboard-designer.png)

## <a name="advanced-model-driven-app-making"></a>创建高级模型驱动应用
解决方案资源管理器是一种综合工具，用于生成高级模型驱动应用。 在解决方案资源管理器中，可以使用工具左侧的导航窗格，在包含所有应用组件的层次结构中导航。

![解决方案资源管理器](media/model-driven-app-overview/solutionexplorer-entitiescollapsed.png)

若要打开解决方案资源管理器，在 [!INCLUDE [powerapps](../../includes/powerapps.md)] 的左侧窗格上选择“模型驱动”。

  ![选择模型驱动](media/model-driven-app-overview/app-type-picker-mod.png)

然后选择“高级”选项卡。

详细信息：[高级应用的创建和自定义](advanced-navigation.md)

## <a name="related-topics"></a>相关主题

[验证并发布模型驱动应用](validate-app.md)

[共享模型驱动应用](share-model-driven-app.md)