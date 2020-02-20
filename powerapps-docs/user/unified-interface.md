---
title: 针对模型驱动应用使用统一接口增强了用户体验 |MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 1/29/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 66888b11d3dc3f62dcc174fbf0f2827c9d9f4867
ms.sourcegitcommit: d0f02fdaa125feaea884932e1ef31b8fea1bd10c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2020
ms.locfileid: "76886480"
---
# <a name="enhanced-user-experience-with-the-unified-interface-for-model-driven-apps"></a>针对模型驱动应用使用统一接口增强了用户体验 

模型驱动应用的统一接口提供跨设备的一致且可访问的用户体验，无论是在台式机、笔记本电脑、平板电脑还是手机上都是如此。 应用会重排屏幕上的组件来进行缩放。 响应式设计根据屏幕大小适应环境，因此拥有的可用空间越大，显示的信息就越多。

> [!div class="mx-imgBorder"]
> ![统一接口适应屏幕](media/Reflow.png "统一接口适应屏幕")

有关模型驱动应用中统一接口的概述，请观看此视频：[统一接口简介](https://www.youtube.com/watch?v=_VPOi_Iq6ko)

> [!NOTE]
> 将弃用旧的 Web 客户端，客户必须在 2020 年 10月 1日之前过渡到统一界面。 有关详细信息，请参阅[博客：宣布移动到统一接口的时间线](https://cloudblogs.microsoft.com/dynamics365/it/2019/09/10/announcing-the-timeline-to-move-to-unified-interface/)。 若要了解有关如何转换的详细信息，请参阅[转换快速入门](https://docs.microsoft.com/powerapps/maker/model-driven-apps/transition-web-app)。

## <a name="navigation"></a>导航

借助菜单选项，可快速浏览系统中的不同应用。 它们提供对最近查看的记录和固定收藏夹的快速访问。

![导航控件，展开的视图](media/nav-expanded.png "导航控件，展开的视图")

图例：

1. **应用选择器**：打开此菜单以在应用间移动。
1. **折叠/展开按钮**：选择此按钮可以折叠导航器，从而为页面的主体部分留出更多空间。 如果导航器已折叠，选择此按钮可将其再次展开。
1. **最近记录**：展开此项可以查看最近使用的记录的列表。 在此处选择要打开的记录。 选择此处列出的记录旁的图钉图标，将其添加到收藏夹（已固定记录）。
1. **收藏的记录**：展开此项可以查看并打开你收藏（已固定）的记录。 使用“最近记录”列表在此处添加记录  。 选择此处列出的记录旁边的删除固定图标，可将相应记录从此列表中删除。
1. **实体导航器**：此区域列出了可用于当前工作区的每个实体和仪表板。 在此处选择任何条目以打开该实体的命名仪表板或列表视图。
1. **工作区选择器**：打开此菜单以移动到其他工作区。 在此处为当前工作区命名。

有关详细信息，请参阅[模型驱动应用中的基本导航](navigation.md)。

## <a name="dashboards-and-charts"></a>仪表板和图表
你可以从统一接口应用中访问所有系统和用户仪表板。 交互式仪表板现可用于所有记录类型，且具有更丰富交互式仪表板功能。 有关详细信息，请参阅[跟踪仪表板和图表的进度](track-your-progress-with-dashboard-and-charts.md)。

## <a name="timeline-control"></a>时间线控件 
使用时间线视图，可在易于阅读的视图中在单个页面上的记录中跟踪客户沟通，帮助你与团队进行协作。 可查看帖子和语音附件，以及电子邮件和笔记的内容。 它提供了快速查看整个沟通会话的方法。 有关详细信息，请参阅[将约会、电子邮件、通话、备注或任务活动添加到时间线](add-activities.md)。

## <a name="business-process"></a>业务流程 
业务流程流已通过停靠机制进行了改进。 可将业务流程阶段停靠在屏幕上，帮助你集中精力处理业务流程流中的任务。 当流程处于需要执行复杂步骤的阶段时，这特别有用。 有关详细信息，请参阅[处理业务流程](work-with-business-processes.md)。

## <a name="accessibility"></a>辅助功能
通过改进的辅助功能体验，可使用屏幕阅读器将屏幕上的信息转换为声音、打印到盲文阅读器，以便更多人可以使用该应用。 有关详细信息，请参阅[使用屏幕阅读器](screen-reader.md)。

## <a name="create-a-unified-interface-app"></a>创建统一接口应用
如果需要创建自己的统一接口体验，可以使用应用设计器创建模型驱动应用。 请参阅[生成模型驱动应用的概述](https://docs.microsoft.com/powerapps/maker/model-driven-apps/model-driven-app-overview)。

![创建新的统一接口应用](media/uci-model-driven-app.png "创建新的统一接口应用")

## <a name="unified-interface-community"></a>统一接口社区

转到[统一接口社区网站](https://community.dynamics.com/365/unified-interface/)，以获取有关计划和执行平稳转换到统一接口的帮助，并通过博客、网络研讨会、视频、活动等与专家和同行交流。
