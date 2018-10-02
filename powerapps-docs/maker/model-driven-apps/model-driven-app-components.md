---
title: 了解 PowerApps 中的模型驱动应用程序组件 | MicrosoftDocs
description: 了解模型驱动应用程序的不同组件，如数据、UI、逻辑和可视化。
Keywords: 'fields, attributes, model-driven app'
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="understand-model-driven-app-components"></a>了解模型驱动的应用程序组件
设计良好的模型驱动应用程序包括若干您选择的组件，使用设计器创建已完成应用程序的外观和功能。 设计器用来制造应用程序的组件和组件属性成为元数据。 

为了解每个组件如何与应用程序设计相关，它们在此处被分到*数据*、*UI*、*逻辑*和*可视化*类别中。 

## <a name="data"></a>数据
这些组件确定应用程序要基于的数据。


|组件  |说明  |设计器  |
|---------|---------|---------|
|实体     |包含所跟踪属性（例如联系人或客户）的项。 有很多标准实体都可用。 您可以自定义非系统标准实体（生产实体）或从头创建自定义实体。     | [!INCLUDE [powerapps](../../includes/powerapps.md)] 实体设计器        |
|字段     | 与实体关联的属性。 字段由数据类型定义，这确定可输入或选择的数据的类型。 示例包括文本、数字、日期和时间、货币或查找（创建与另一个实体的关系）。 字段通常用于窗体、视图和搜索。        | [!INCLUDE [powerapps](../../includes/powerapps.md)] 实体设计器   |
|关系     | 实体关系定义实体如何能相互关联。 有 1:N（一对多）、N:1（多对一）和 N:N（多对多）关系类型。 例如，向实体中添加查找字段将在两个实体之间创建新的 1:N 关系，并使您能够将该查找字段放在窗体中。   | [!INCLUDE [powerapps](../../includes/powerapps.md)] 实体设计器        |
|选项集字段     | 这是一个特殊的字段类型，为用户提供一组预定的选项。 每个选项都有一个数字值和标签。 添加到窗体时，该字段显示一个控件，供用户选择选项。  有两类选项集；选项集，用户从中只能选择一个选项，多选选项集，允许选择多个选项。  | [!INCLUDE [powerapps](../../includes/powerapps.md)] 选项集设计器     |

详细信息：[为模型驱动应用程序定义数据](define-data-model-driven-app.md) 

## <a name="ui"></a>UI
这些组件确定用户如何与应用程序交互。 

|组件  |说明  |设计器  |
|---------|---------|---------|
|应用     | 确定应用程序的基础，如应用程序的组件、属性、客户端类型和 URL。      | 应用程序设计器   |
|站点地图     | 指定应用程序的导航。        | 站点地图设计器        |
|表单     | 一组与您的组织跟踪的实体项目匹配的指定实体的数据输入字段。 例如，一组数据输入字段，其中的用户输入相关信息跟踪客户之前的订单以及请求的特定重新排序日期。        | 窗体设计器        |
|视图     | 视图定义特定实体的记录列表如何在应用程序中显示。 视图定义要显示的列、每列的宽度、排序行为和默认筛选器。   |  视图设计器       |

![应用程序设计器和窗体设计器](media/model-driven-app-overview/app-and-form-designers.png)

## <a name="logic"></a>逻辑
确定应用程序将具有的业务流程、规则和自动化。 [!INCLUDE [powerapps](../../includes/powerapps.md)] 制造者使用特定于流程或规则类型的设计器。 


|逻辑类型  |说明  |设计器  |
|---------|---------|---------|
|业务流程     | 引导用户完成标准业务流程的在线流程。 例如，如果希望每个人处理客户服务请求的方式相同，或者要求员工在提交订单前获取发票批准，则使用业务流程。        | 业务流程设计器        |
|工作流     |  工作流可以实现无需用户干预的业务流程自动化。 设计器使用工作流来发起不需要任何用户交互的自动化。       | 工作流设计器        |
|操作    |  操作是让您可以直接从工作流手动调用操作（包括自定义操作）的一种流程。       |  流程设计器       |
|业务规则     | 用于将规则或建议逻辑应用到窗体，如设置字段要求、隐藏字段或验证数据。 应用程序设计器使用简单的界面来实施和维护快速更改和常用的规则。         |  业务规则设计器       |
|流     | 流是基于云的服务，让您可以创建应用程序与服务之间的自动工作流来获取通知、同步文件、收集数据等。        | Microsoft Flow        |

![工作流、操作和业务流程设计器](media/model-driven-app-overview/designer-mash.png)

详细信息：[在您的模型驱动应用程序中应用业务逻辑](guide-staff-through-common-tasks-processes.md)

## <a name="visualizations"></a>可视化
确定应用程序将有的可用数据可视化和报告类型。


|组件  |说明  |设计器  |
|---------|---------|---------|
|图表     | 可在视图内、窗体上显示或添加到仪表板的单个图形可视化项。        | 图表设计器        |
|仪表板     | 用作提供可行业务数据概览的一个或多个图形可视化项的板。        | 仪表板设计器        |
|嵌入式 Power BI     | 将嵌入式 Power BI 磁贴和仪表板添加到您的应用程序。 Power BI 是提供商业智能见解的基于云的服务。        |  图表设计器、仪表板设计器和 Power BI 的组合       |

![示例仪表板](media/model-driven-app-overview/dashboard-designer.png)

## <a name="advanced-model-driven-app-making"></a>高级模型驱动应用程序制造
解决方案资源管理器是一项用于构建高级模型驱动应用程序的综合工具。 在解决方案资源管理器中，可以使用工具左侧的导航窗格导航包含所有应用程序组件的层次结构。

![解决方案资源管理器](media/model-driven-app-overview/solutionexplorer-entitiescollapsed.png)

若要打开解决方案资源管理器，选择 [!INCLUDE [powerapps](../../includes/powerapps.md)] 左侧窗格的**模型驱动**。

  ![选择“模型驱动”](media/model-driven-app-overview/app-type-picker-mod.png)

然后选择**高级**选项卡。

详细信息：[高级应用程序制作和自定义](advanced-navigation.md)

## <a name="related-topics"></a>相关主题

[验证和发布模型驱动应用程序](validate-app.md)

[共享您的模型驱动应用程序](share-model-driven-app.md)
