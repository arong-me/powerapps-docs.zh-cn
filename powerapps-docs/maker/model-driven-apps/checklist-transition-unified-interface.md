---
title: 检查表：统一接口转换 | MicrosoftDocs
description: 确保您已准备好转换到统一接口的检查表。
ms.custom: ''
ms.date: 11/04/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: haybass
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 03b3db348ff88b7fd2c5e89e2b94a7d16a1fee17
ms.sourcegitcommit: bcaffcb3135251ea3c2e828f8b59926d19520bec
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2761804"
---
# <a name="checklist-unified-interface-transition"></a>检查表：统一接口转换

请按照本文中的步骤确保您已准备好转换到统一接口。 转换到统一接口的准备取决于您是要实现基本兼容性还是要重新设计以充分利用新功能。 有关更多详细信息，请参阅[统一接口 Playbook](https://docs.microsoft.com/powerapps/maker/model-driven-apps/unified-interface-playbook) 和[用户体验白皮书](https://docs.microsoft.com/powerapps/maker/model-driven-apps/approaching-unified-interface)。

这些说明适用于 Dynamics 365 中的以下模型驱动应用：

- Dynamics 365 Sales

- Dynamics 365 Customer Service

- Dynamics 365 Field Service

- Dynamics 365 Project Service Automation

## <a name="run-the-powerapps-solution-checker-on-your-solutions"></a>在您的解决方案上运行 PowerApps 解决方案检查器

[PowerApps 解决方案检查器](https://docs.microsoft.com/powerapps/maker/common-data-service/use-powerapps-checker)根据一组最佳实践规则对解决方案执行各种静态分析检查，并快速确定这些问题模式。 检查完成后，将收到详细报告，其中列出了确定的问题，受影响的组件和代码，以及介绍各问题解决方法的文档的链接。

解决方案检查器分析以下解决方案组件：

-   Common Data Service 插件

-   Common Data Service 自定义工作流活动

-   Common Data Service Web 资源（HTML 和 JavaScript）

-   Common Data Service 配置，如 SDK 消息步骤

**考虑事项** 

-   解决方案检查器检测到的潜在问题可能并不只适用于统一接口，在检查结果时请注意会影响转换的因素。

-   就像在任何自动代码审查中一样，某些问题可能是虚假警报，并不意味着您的应用程序无法在统一接口中运行。

-   在服务器端执行的逻辑（例如插件、自定义工作流活动和 SDK 消息步骤的配置）不会影响用户界面，因此也不会影响向统一接口的转换。

-   即使并非所有问题都与统一接口直接相关，我们还是建议您花一些时间对其进行检查，以改善应用程序的整体运行状况。

## <a name="check-third-party-solutions-compatibility-with-unified-interface"></a>检查第三方解决方案与统一接口的兼容性


在转换到统一接口之前，重要的是要确保您在应用程序中使用的任何第三方解决方案都可以在统一接口中工作。

-   如果您通过 [AppSource](https://appsource.microsoft.com) 安装了 ISV（独立软件供应商）加载项，请在 [Power Platform 管理中心](https://admin.powerplatform.microsoft.com)检查升级是否可用，方法是选择**环境** > [环境名称] > **管理解决方案**。

-   如果您使用的是 AppSource 外部提供的第三方解决方案，请与提供商（合作伙伴或 ISV）联系，以获取将应用更新为统一接口的新版本。

> [!NOTE]
> 如果没有计划将您的第三方解决方案更新为与统一接口兼容的版本，那么确定使用本机平台功能或兼容的替代解决方案来替换这些功能的路径很重要。

## <a name="identify-replacements-for-deprecated-client-api-code-and-features"></a>确定弃用的客户端 API 代码和功能的替换

基于 **PowerApps 解决方案检查器**的输出以及弃用的客户端 API 代码和功能[即将做出的重要更改（弃用）](https://docs.microsoft.com/power-platform/important-changes-coming)，您应该对在统一接口项目中需要更正或替换的自定义项和功能有很好的了解。

以下是需要注意的一些最常见区域：

-   **客户端 API**：建议的替换方法在[此处](https://docs.microsoft.com/power-platform/important-changes-coming#some-client-apis-are-deprecated)有记录。

-   **流程对话**：建议的对话替换在[此处](https://docs.microsoft.com/flow/replace-dialogs)有记录。

-   **任务流**：考虑使用[业务流程](https://docs.microsoft.com/power-platform-release-plan/2019wave2/microsoft-flow/business-process-immersive-experiences)替换任务流。

-   **服务计划**：考虑使用 [Universal Resource Scheduling](https://docs.microsoft.com/dynamics365/common-scheduler/schedule-anything-with-universal-resource-scheduling) 替换旧服务计划。

> [!NOTE]
> 您可能还考虑用轻量级 [Dynamics 365 App for Outlook](https://docs.microsoft.com/dynamics365/outlook-app/overview) 替换 Dynamics 365 for Outlook（COM 加载项）。

## <a name="test-your-application-in-unified-interface"></a>在统一接口中测试您的应用程序

在统一接口中测试应用程序最简单的方法之一，就是在生产环境的副本上打开[**启用“仅统一接口”**](https://docs.microsoft.com/power-platform/admin/enable-unified-interface-only)选项。 启用统一接口后，您应该能够使用 **Dynamics 365 – 自定义**应用访问您的应用程序，并测试与您的上下文相关的用例。

### <a name="test-your-business-and-technical-scenarios"></a>测试您的业务和技术方案

关注可能受到影响的方面：

-   **业务流程**例如业务流程、业务规则

-   **自定义**例如窗体、视图、命令栏按钮、Web 资源和图表

> [!TIP]
> 在进行这些早期测试的同时，质疑用户体验：一切都有意义并增加了价值吗？ 应该删除/改进/添加什么？ 例如，当前视图列表是否相关？ 或者我的用户是否被迫创建自己的视图？

### <a name="identify-gaps"></a>找出不足

-   解决方案检查器和第三方解决方案更新尚未发现的任何潜在的退化。

-   用户难点可能导致优化（例如通过重新组织部分和选项卡来呈现新窗体）或特定的培训。

-   对旧版 Web 客户端的任何其他依赖性，例如使用旧版 Outlook COM 加载项，而不是用于轻量级 Dynamics 365 App for Outlook。

## <a name="define-your-app-strategy-and-settings"></a>定义您的应用策略和设置

我们建议您使用 Microsoft 推出的第一方应用或开发自己的应用，而不要使用未针对统一接口进行优化而是以兼容模式运行的 **Dynamics 365 – 自定义**应用。

以下是针对统一接口进行了优化的 Dynamics 365 第一方应用：

-   Dynamics 365 销售中心

-   Dynamics 365 客户服务中心

-   Dynamics 365 Marketing

-   Dynamics 365 Field Service（版本 8.x 及更高版本）

-   Dynamics 365 Project Service Automation（版本 3.x 及更高版本）

### <a name="what-are-model-driven-apps"></a>什么是模型驱动应用？

**模型驱动应用**是您可以使用 PowerApps 创建的一种类型的应用，可帮助您根据用户在组织中的角色为他们提供量身定制的体验。 例如，通过不同的模型驱动应用，即使销售人员使用的是来自同一环境的数据，他们的体验也可能与客户服务代表的体验完全不同。 可以在 Common Data Service 环境中创建多个模型驱动应用。 更多信息请参阅：[什么是模型驱动型应用？](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)

前面列出的 Dynamics 365 第一方应用是模型驱动应用的示例。

### <a name="how-to-define-your-app-strategy"></a>如何定义您的应用策略？

下面列出了您需要考虑的问题：

1.  您可以将用户分为具有特定业务流程的多个组吗？

2.  这些组对他们应该看到和做什么有不同的要求吗？

3.  您是否发现不使用应用就很难拥有不同的用户体验？

如果您对这些问题的回答为“是”，请考虑使用多个应用。

这是重新思考每个组或角色在业务流程上下文中的体验的机会。

### <a name="out-of-the-box-apps-for-example-sales-hub-or-customized-apps"></a>现成的应用（例如，销售中心）还是自定义的应用？

-   这取决于您希望体验如何定制。

-   如果您的自定义很少，或者想从第一方应用更新中受益，请考虑使用本机应用。

-   如果您想要更好地控制标准应用和自定义的体验和更新，请创建自己的应用。

### <a name="once-you-have-defined-your-app-strategy-what-should-be-the-next-steps"></a>定义了应用策略后，下一步应该做什么？

1.  自定义您的目标应用，仅包含用户需要的功能。 越少越好。 减少混乱，使用户能够高效地工作。

2.  取消安全角色与未使用的应用的关联。

## <a name="review-your-apps-settings-and-user-experience-fundamentals"></a>查看您的应用设置和用户体验的基础

### <a name="app-settings"></a>应用设置

-   将所有必需的实体包括在您的应用中，即使它们不在站点地图中也是如此。  
    
-   在**安全角色**对话框的**自定义**选项卡中，为**模型驱动应用**提供**读取**权限。

-   如果您的用户不需要使用旧版网络客户端，请启用**仅统一接口**模式。 您仍然可以通过选择**设置** > **高级设置**来访问管理功能。

-   创建一个更简单的应用 URL。 例如：https://\*.crm.dynamics.com/apps/MyApp*

-   尝试限制用户可以访问的应用数量。  
    
    > [!TIP]
    > 当**仅使用统一接口**设置为**是**且用户仅有权访问一个应用时，他们在访问根 URL (https://\*.crm.dynamics.com)* 时将被自动重定向到该应用

### <a name="optimize-navigation-sitemap"></a>优化导航（站点地图）

-   定义一个主要**区域**，其中包含最常用的在**组**中管理的**子区域**（仪表板、实体等）

-   为较少使用的功能（配置、设置等）创建一个或多个其他区域。 这样做的目的是帮助您的用户只关注对他们的工作重要的事情。

### <a name="update-icons"></a>更新图标

-   转换为统一接口是刷新图标的好机会。

-   我们建议使用 **SVG** 格式，因为无论屏幕分辨率如何，它们都能很好地呈现。

    > [!TIP]
    > SVG 图标格式的示例：  
    > 宽度和高度：16 像素；边距：0 像素；背景：透明；图标颜色：\#FF000000  
    为避免出现呈现问题，请使用编辑器（例如，记事本）打开 SVG 文件，然后删除 fill="\#000000"

## <a name="enrich-your-app-with-unified-interface-exclusive-features"></a>借助统一接口独有的功能扩充您的应用

-   创建一个**欢迎页**，让用户在访问您的每个应用时看到。 这是指导用户初次使用的好机会。

-   使用现有的**自定义控件**可以改善大多数字段类型的可用性，尤其是在移动设备上。 例如，用星号替换 0 到 5 的字段评级，用日历视图替换约会视图，用卡窗体替换子网格视图。

-   利用窗体上的**参考面板**将多个视图、快速视图和知识库搜索功能捆绑在一个地方。

-   利用 [PowerApps Component Framework](https://docs.microsoft.com/powerapps/developer/component-framework/overview) 添加更多自定义控件。 您可以从社区或合作伙伴和 ISV 那里获得一些东西。

-   在您的窗体中嵌入[画布应用](https://docs.microsoft.com/powerapps/maker/canvas-apps/getting-started)以轻松扩展您的应用程序。 应用的无码或低码扩展，无需开发自定义 HTML/JS Web 资源。

-   在窗体中嵌入 **Power BI** 报表和磁贴：在单个视图中合并多个系统中的数据。

-   考虑利用**交互式仪表板**配置一站式工作场所，以允许跨仪表板组件进行全局筛选。

-   配置**自定义帮助窗格和向导型任务**，以便用户快速获得帮助和指导。

## <a name="conduct-user-acceptance-testing"></a>执行用户接受测试

非常重要的是，您的应用程序、业务场景和技术场景必须由业务用户在与生产环境相似的条件下在统一接口中进行测试。 这些用户可以充当业务支持者，以帮助在整个业务范围内扩展知识。

测试将帮助您确定所有要处理的剩余项目，然后再将所有用户转换到统一接口。

## <a name="update-user-training-materials"></a>更新用户培训材料

对您现有和计划的培训材料进行审查，以确保它们具有最新的屏幕截图，并反映您对用户流程所做的任何更改。

## <a name="check-your-transition-date"></a>检查您的转换日期

2020 年 10 月 1 日，[旧版 Web 客户端将不再可用](https://docs.microsoft.com/power-platform/important-changes-coming#legacy-web-client-is-deprecated)。
请务必提前进行迁移，以确保有时间解决所有问题。
