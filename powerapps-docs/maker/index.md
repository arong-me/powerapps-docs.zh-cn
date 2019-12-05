---
title: 应用创建概述 | Microsoft Docs
description: 概述如何创建画布或模型驱动模式的应用并整合 Common Data Service
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.date: 07/18/2018
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: d41af83d0a6de68ac94327798e076b19039dadef
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74729818"
---
# <a name="overview-of-creating-apps-in-power-apps"></a>概述如何在 Power Apps 中创建应用

Power Apps 是商业应用的高效开发平台，主要有四个组成部分：

- [画布应用](canvas-apps/getting-started.md)：画布应用从用户体验入手，借助空白画布的功能设计出高度定制的界面，并将其连接到你选择的 200 个数据源。 你可以生成适用于 Web、移动设备和平板电脑应用程序的画布应用。
- [模型驱动应用](model-driven-apps/model-driven-app-overview.md)：模型驱动应用从数据模型入手，通过你的核心业务数据和流程在 Common Data Service 中的形态生成数据模型，对窗体、视图和其他组件建模。 模型驱动应用自动生成在各种设备中反应敏捷的好用 UI。
- [门户](portals/overview.md) 开始创建面向外部的网站，使组织外部的用户能够使用多种标识登录、在 Common Data Service 中创建和查看数据，甚或匿名浏览内容。
- [Common Data Service](common-data-service/data-platform-intro.md) 是 Power Apps 附带的数据平台，让你可以存储业务数据并对其进行建模。 这是生成 Dynamics 365 应用程序的平台，如果你是 Dynamics 客户，那么你的数据就已经在 Common Data Service 中了。

你可以简单轻松地尝试生成自己的第一个应用。 我们提供 30 天免费试用计划以及免费社区计划；了解你最适合哪一种并开始使用吧。

## <a name="canvas-apps"></a>画布应用

画布应用为你提供用户体验和界面方面的灵活性，你可以根据自己的需求进行设计。 发挥你的创造力和商业意识，设计应用理想的外观和感觉。

可以开始通过数据所在的 Microsoft 工具生成应用，例如：

- [通过 SharePoint 列表](canvas-apps/app-from-sharepoint.md#generate-an-app-from-within-sharepoint-online)
- [通过 Power BI 仪表板](canvas-apps/embed-powerapps-powerbi.md)

创建画布应用很简单，可以借助 Power Apps 通过多种方式查找或创建应用：

- [通过数据](canvas-apps/app-from-sharepoint.md)
- [通过示例](canvas-apps/open-and-run-a-sample-app.md)
- [通过 Common Data Service 源](canvas-apps/data-platform-create-app.md)
- [通过空白画布](canvas-apps/data-platform-create-app-scratch.md)
- [通过 AppSource](../user/app-source.md)

## <a name="model-driven-apps"></a>模型驱动应用

创建模型驱动应用时，可以借助 Common Data Service 的所有功能快速配置窗体、业务规则和流程。 通过 Power Apps 站点创建模型驱动应用。

模型驱动应用入门很简单，你还可以从下列主题开始学习：

- [创建应用](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-app)
- [创建并设计窗体](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-design-forms)
- [创建或编辑视图](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-views)
- [创建或编辑系统图表](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-system-chart)
- [创建或编辑仪表板](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-dashboards)
- [添加安全性](https://docs.microsoft.com/dynamics365/customer-engagement/customize/manage-access-apps-security-roles)
- [添加业务逻辑](https://docs.microsoft.com/dynamics365/customer-engagement/customize/guide-staff-through-common-tasks-processes)

## <a name="common-data-service"></a>Common Data Service

可以使用 Common Data Service 在一组标准实体和自定义实体中安全地存储和管理数据，还可以在需要时将字段添加到这些实体。

Common Data Service 入门很简单。 例如，你可以从下面几项开始了解：

- [创建自定义实体](common-data-service/data-platform-create-entity.md)
- [管理字段](common-data-service/data-platform-manage-fields.md)
- [创建自定义选项集](common-data-service/custom-picklists.md)
- [创建业务规则](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-business-rules-recommendations-apply-logic-form)

## <a name="canvas-and-model-driven-artifacts"></a>画布和模型驱动项目

虽然我们合并了画布和模型驱动应用的体验，但这些项目将与画布应用或模型驱动应用相关。

| 项目            | 应用类型     |
|---------------------|--------------|
| “实体”>“视图”      | 模型驱动 |
| “实体”>“窗体”      | 模型驱动 |
| “实体”>“仪表板” | 模型驱动 |
| 连接         | 画布       |
| 网关            | 画布       |
| 自定义连接器   | 画布       |
| “应用”>“导入”       | 画布       |

你可以在生成应用后与团队成员[共享应用](canvas-apps/share-app.md)。
