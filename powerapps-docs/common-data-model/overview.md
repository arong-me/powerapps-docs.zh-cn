---
title: 通用数据模型概述 | Microsoft Docs
description: 了解通用数据模型如何连接 Common Data Service for Apps 和 Common Data Service for Analytics。
services: ''
suite: powerapps
documentationcenter: na
author: RobertBruckner
manager: lmollico
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/14/2018
ms.author: jdaly
ms.openlocfilehash: 5fb747d94b5af47717debba2341a9914664a27bd
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="common-data-model-overview"></a>通用数据模型概述

通用数据模型 (CDM) 是标准实体的开源定义，这些实体代表跨多种企业和应用程序域的常用概念和活动。 通用数据模型提供明确定义、模块化和可扩展的业务实体（例如帐户、业务部门、用例、联系人、潜在客户、机会和产品），还提供供应商、员工和客户之间的交互和关系（例如活动和服务级别协议）。 

Microsoft 的 [Common Data Service for Apps](../maker/common-data-service/data-platform-intro.md) 和 Common Data Service for Analytics <!-- TODO add link when available  --> 实现通用数据模型。 这些服务保存符合通用数据模型定义的数据。 打包的应用程序和分析解决方案以这些服务为基础生成，可以处理明确定义的实体形状和共享数据，而无论数据最初源于哪里或者被谁控制。 自定义业务线应用和分析解决方案可以利用相同的实体共享数据，从而支持你的特定需求和业务需求。 

Microsoft 和我们的合作伙伴致力于以 Common Data Service 为基础生成应用程序，并将业务数据存储为 CDM 形式。 将数据存储为 CDM 形式时，大量且持续增长的解决方案集合高效协作，这意味着可以快速实现新的业务流程，并轻松简单地获取业务运营见解。 下图显示基于 Common Data Services 开发的应用程序如何利用通用数据模型实体。

![基于 Common Data Services 开发的应用程序如何利用通用数据模型实体](media/cdm-overview.png)

通用数据模型通过跨应用程序和部署的结构和语义一致性将数据统一为已知的形式，从而简化数据管理的挑战。 它可以帮助集成从业务流程、数字交互、产品遥测、人员交互等收集的数据并消除歧义。 

Common Data Service for Apps 中存储的数据轻松、自动与针对使用两个服务的客户的 Common Data Service for Analytics 集成。 你可以从已有的企业和交易数据开始（例如潜在客户、营销活动信息、以前的客户采购），并结合其他源的数据（例如网络日志或产品遥测），以获得统一的结果。

通用数据模型还可扩展 - 你可以将字段添加到任意可自定义实体（可能是 CDM 附带的或者自己创建的）。 CDM 标准为业务实体（涵盖从销售、服务、营销、运营、财务、人才到商务的整个业务流程）以及客户、人员和产品实体（公司业务流程的核心）定义公共语言。 通用数据模型促进跨多个通道、服务实现和供应商的数据互操作性。

通用数据模型和 Common Data Service 通过以下功能提供一个丰富且高效的开发平台：

- **标准实体的定义** - 通用数据模型提供一种实体定义，表示跨业务和生产力应用程序最常用的实体。 通过跨整个业务流程（横向）的核心实体、其他垂直行业数据模型和跨越资源（例如调查、搜索引擎和产品遥测），继续增强公共 CDM GitHub 存储库[(https://github.com/Microsoft/CDM)](https://github.com/Microsoft/CDM)。
- **数据集成** - 使用 Power Query 作为内置 Web 体验，从现有系统导入数据，以直观方式转换数据，并在无代码或少代码的情况下合并在线和本地资源的数据。 将无缝应用你的 Excel 和 Power BI 数据转换技能。 请参阅[使用 Power Query 将数据添加到 Common Data Service 中的实体](../maker/common-data-service/data-platform-cds-newentity-pq.md)。
    
    将数据导入到 Common Data Service 时，可以将其映射到标准的通用数据模型实体，也可以创建并映射到新实体。 现成可用的数据集成和映射模板可以简化到通用数据源（例如 Salesforce）的连接。 这些映射模板可完全自定义并可扩展。 以下屏幕截图显示如何导入外部数据并将其映射到 Power Query 中的标准实体。 
    
    ![导入外部数据并将其映射到 Power Query 中的标准实体 ](media/cdm-mapping-entities.png)<br />

- **可扩展性** - 你可以扩展实体，且不会中断与其他应用共享数据。
- **可靠性** - 由于可以依赖常用实体，因此可以生成绑定到这些实体的可重用组件。 通用数据模型支持可扩展性和保护开发投资的版本控制。
- **跨部署的实体一致性** - 解决方案可以连接生产力平台的信息和商业应用程序的信息。 例如，可以连接日历约会或 Microsoft Outlook 任务和销售机会。 

[Common Data Service for Apps](../maker/common-data-service/data-platform-intro.md) 实现通用数据模型，允许商业应用程序开发：

- **利用打包的业务应用程序** - 针对营销、销售、服务、人才、财务和运营应用的 Dynamics 365 和第三方应用程序利用 Common Data Service for Apps 和/或基于其生成。
- **按需自定义应用程序和生成本机扩展** - 定制员和开发人员分发明确定义了应用程序生命周期的应用程序解决方案。 解决方案是应用程序和扩展的分发方式。 请参阅[解决方案简介](../developer/common-data-service/introduction-solutions.md)。
- **借助 PowerApps 生成无代码/少代码的模型驱动和 WYSIWYG 画布应用** - 使用由打包的应用程序或其他第三方应用程序创建/使用的相同共享实体并创建其他独立应用。 请参阅： 
    - [生成模型驱动应用](../maker/model-driven-apps/model-driven-app-overview.md)
    - [生成画布应用](../maker/canvas-apps/getting-started.md) 
- **借助 Flow 自动化业务流程** - 使用业务流程流定义一组阶段和步骤以实现所需结果。 请参阅[创建使用 Common Data Service 的流](/flow/common-data-model-intro)
 
即将发布的 Common Data Service for Analytics<!-- TODO add link when available  --> 公共预览版也实现通用数据模型，支持标准形式的业务数据分析，包括：

- **基于标准数据实体的打包和自定义的分析解决方案** - 跟踪历史销售业绩的分析应用程序（例如 Sales Insights）提供一致的见解（无论数据最初在哪里被控制），因为数据集成体验将数据从其他源（例如 Salesforce.com）集成到通用数据模型实体形状。 这可以将分析解决方案简化为专注于明确定义的实体（例如潜在客户和机会）的数据语义。
- **无代码/少代码 Power Query 数据集成** - 使用内置体验创建、填充、转换和丰富实体。 
- **自带 Azure 存储** - 充分利用 Azure 数据堆栈向 Common Data Service for Analytics 提供数据。 实体以分析解决方案可识别的相同通用数据模型格式存储。

