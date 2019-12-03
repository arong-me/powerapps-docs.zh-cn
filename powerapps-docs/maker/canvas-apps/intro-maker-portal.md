---
title: 首次登录 | Microsoft Docs
description: 所有应用创作者的新家。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 08/06/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0f745516ab0c282ab6519f0bac8ac8cfd5f46598
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675745"
---
# <a name="sign-in-to-power-apps-for-the-first-time"></a>首次登录到 Power Apps

登录到 [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 后，站点会为你提供各种选项，用于创建自己的应用、打开你或他人创建的应用和执行相关任务。 这些任务涵盖了从最简单的任务（如标识一个或多个提供访问权限的许可证）到更高级的功能（如创建与特定数据源的自定义连接）。

你可以在以下三个常规区域中选择选项：

- 页面顶部的标题

    ![标题](media/intro-maker-portal/header.png)

- 页面左边缘的导航栏

    ![导航栏](media/intro-maker-portal/nav-bar.png)

- 页面中间突出显示的大图标

    ![主页的中心区域](media/intro-maker-portal/center-area.png)

为了获得最佳结果，请先确保将主页设置为正确的环境。

## <a name="choose-an-environment"></a>选择环境

无论是在 Common Data Service 中创建应用、流、数据连接还是实体，在 Power Apps 中执行的大部分操作都包含在特定环境中。 环境会创建不同类型工作之间的边界；例如，组织可能有单独的环境用于不同的部门。 许多组织会使用环境将仍处于开发中的应用与已准备好广泛使用的应用进行分隔。 你可能有权限访问多个环境或只能访问一个环境。如果你具有相应权限，则可能能够创建自己的环境。

若要验证你所在的环境，请查找标题右侧附近的环境切换器。

![环境切换器](media/intro-maker-portal/environment-switcher.png)

如果在一个环境中创建某个应用，则无法在另一个环境中查看该应用。 此外，想要运行应用的人员必须有权限访问在其中创建该应用的环境。

> [!IMPORTANT]
> 请先确保你位于正确的环境中，然后再创建应用、流或类似组件。 你无法轻松地将组件从一个环境移至另一个环境。

有关详细信息，请参阅[环境概述](../../administrator/environments-overview.md)。

## <a name="choose-an-app-type"></a>选择应用类型

在 Power Apps 中，你可以创建并运行以下类型的应用：

- 画布应用支持设计自定义 UI 并连接到来自各种源的数据。
- **模型驱动应用**具有标准 UI，并且仅在 Common Data Service 中连接到数据。 但是，你可以较轻松地创建其他元素，如视图、仪表板以及不同类型的业务逻辑。

如果选择的环境具有 Common Data Service 数据库，则可以从同一**主页**构建画布或模型驱动的应用。

## <a name="play-or-edit-an-app"></a>播放或编辑应用

如果已创建应用（或其他人已创建并与你共享应用），可以在“主页”或“应用”页中播放或编辑应用。

在“应用”页上，可以按最近是否打开过应用等条件筛选应用列表。

![应用列表](./media/intro-maker-portal/find-apps.png)

此外，还可以在右上角附近的搜索栏中键入一个或多个字符，从而搜索应用。 找到所需应用后，选择横幅图标，以播放或编辑应用。

## <a name="create-an-app"></a>创建应用

在“主页”页面中，可以采用多种方式创建应用：

- [自动从一组数据生成画布应用](data-platform-create-app.md)
- [自定义画布应用的预建示例](open-and-run-a-sample-app.md)
- [从空白屏幕生成画布应用](data-platform-create-app-scratch.md)
- [创建自己的模型驱动应用](../model-driven-apps/overview-model-driven-samples.md)
- [自定义模型驱动应用的预建示例](../model-driven-apps/build-first-model-driven-app.md)

## <a name="learn-more"></a>了解更多

你可以采用以下两种方式找到有关画布应用或模型驱动应用的详细信息：

- 在左侧导航栏中，选择“了解”。
- 在标题中，选择问号图标。

    ![带有省略号的模型驱动应用列表菜单打开](media/intro-maker-portal/help-icon.png)

这两个选项都显示了此文档集的链接、Power Apps 社区（你可以在其中与其他组织中的用户共享信息）和 Power Apps 博客（其中宣布了最新功能）。

## <a name="other-common-tasks"></a>其他常见任务

通过在标题和左侧导航栏中选择选项，可以执行除创建和打开应用以外的操作。

### <a name="from-the-header"></a>在标题中

- 选择向下箭头以下载可在其中运行应用的移动客户端和其他客户端。

    有关详细信息，请参阅[查找和运行应用](../../user/index.md)。

- 选择齿轮图标以执行任务，如连接到数据源、标识 Power Apps 许可证或许可证，以及打开可执行管理任务的页面。

    有关详细信息，请参阅以下主题：

  - [画布应用连接器的概述](connections-list.md)
  - [生成并认证画布应用的自定义连接器](register-custom-api.md)
  - [管理本地数据网关](gateway-management.md)
  - [管理 PowerApps](../../administrator/index.md)
  - [许可概述](../../administrator/pricing-billing-skus.md)
  - [生成模型驱动应用的概述](../model-driven-apps/model-driven-app-overview.md)

### <a name="from-the-left-navigation-bar"></a>在左侧导航栏中

通过执行这些任务来扩展应用的功能：

- 管理[Common Data Service](../common-data-service/data-platform-intro.md)中的实体、选项集和数据集成。
- 在[电源自动执行](https://docs.microsoft.com/flow/getting-started)中配置业务逻辑。
- 创建、打包和维护[解决方案](../../developer/common-data-service/introduction-solutions.md)。
