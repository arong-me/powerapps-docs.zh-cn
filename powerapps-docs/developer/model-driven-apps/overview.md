---
title: 模型驱动应用开发人员概述 | Microsoft Docs
description: 了解开发人员如何将值添加到模型驱动应用中。
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/17/2018
ms.author: jdaly
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 39fe83cdb059e0f1df634b9933f4a2f4251bca7b
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42852405"
---
# <a name="model-driven-apps-developer-overview"></a>模型驱动应用开发人员概述

PowerApps 为用户、企业、合作伙伴、独立软件供应商 (ISV) 和系统集成商 (SI) 提供了用于生成业务线应用的功能强大的平台。 此版本中 PowerApps 的新增功能是使用新的 Common Data Service for Apps 生成的模型驱动应用。 Common Data Service for Apps 现在包含 Dynamics 365 Customer Engagement 应用程序的核心功能。 借助模型驱动应用，可构建使用与这些应用程序相同的可扩展性功能的应用。

模型驱动应用主要是针对应用开发的无代码或低代码组件。 开发人员可通过扩展应用程序提供值。 开始编写代码前，先学习如何构建模型驱动应用，以及在没有代码的情况下可应用哪些选项。 

## <a name="get-started"></a>入门
如果你已对 Dynamics 365 客户参与应用有所了解，将发现可应用你的经验来构建模型驱动应用。 有一些新的设计器可供使用，但通常这些概念是相同的。

> [!NOTE]
> 模型驱动应用可连接 Common Data Service for Apps。 有关开发人员如何在服务级别添加值的信息，请参阅[Common Data Service for Apps 开发人员概述](../common-data-service/overview.md)。
> 本节中的内容仅涉及开发人员可执行的适用于模型驱动应用的用户体验的扩展。 

如果你不熟悉 Dynamics 365 客户参与应用程序，本节中的主题精准地概述了帮助开发人员开始使用模型驱动应用的重要概念。 

> [!NOTE]
> 由于 Common Data Service for Apps 使用的平台与 Dynamics 365 Customer Engagement 使用的平台相同，因此可在 [Dynamics 365 Customer Engagement 开发人员指南](/dynamics365/customer-engagement/developer/developer-guide)中找到更完整的开发人员信息。 这些主题提供相关概述和链接，可通过链接访问开发人员指南和其他指南，获取详细信息。


## <a name="community-tools-for-model-driven-apps"></a>用于模型驱动应用的社区工具

Dynamics 365 社区创建工具！ 许多最常见的工具通过在 [XrmToolBox](https://www.xrmtoolbox.com/) 中进行分发。 XrmToolBox 是连接到 Common Data Service for Apps 的 Windows 应用程序，提供用于简化自定义、配置和操作任务的工具。 它附带 30 多个插件，使管理、自定义或配置任务变得更容易、更省时。

以下是通过 XrmToolBox 分发的社区工具所选列表，可在使用模型驱动应用时使用它们

|工具  |描述  |
|---------|---------|
|[简易翻译程序](https://www.xrmtoolbox.com/plugins/MsCrmTools.Translator/)|使用与上下文相关的信息导出和导入翻译|
|[导出到 Excel](https://www.xrmtoolbox.com/plugins/Ryr.XrmToolBox.ExportToExcel/)|轻松将记录从所选视图/fetchxml 导出到 Excel 中。|
|[Iconator](https://www.xrmtoolbox.com/plugins/MscrmTools.Iconator/)|在单个屏幕中管理自定义实体图标|
|[功能区工作台 2016](https://www.xrmtoolbox.com/plugins/RibbonWorkbench2016/)|从 XrmToolbox 中编辑 Dynamics CRM 功能区或命令栏|
|[视图设计器](https://www.xrmtoolbox.com/plugins/Cinteros.XrmToolBox.ViewDesigner/)|使用 FetchXML 生成器设计视图布局和更改查询的简单用户界面|
|[视图布局复制器](https://www.xrmtoolbox.com/plugins/MsCrmTools.ViewLayoutReplicator/)|在单个操作中将相同布局应用于同一实体的多个视图|
|[WebResources 管理器](https://www.xrmtoolbox.com/plugins/MsCrmTools.WebResourcesManager/)|轻松地管理 Web 资源|

另一个不通过 XrmToolBox 分发的工具是 Jason Lattimer 的 [CRM REST 生成器](https://github.com/jlattimer/CRMRESTBuilder)。 此工具生成用于 Web API 的 JavaScript 代码。

> [!NOTE]
> Microsoft 不支持社区创建的工具。 如果对社区工具有任何疑问，请联系该工具的发布者。




