---
title: 开发人员：面向应用程序的 Common Data Service 的最佳做法及指南 | Microsoft Docs
description: PowerApps 中针对面向应用程序的 Common Data Service 的开发人员最佳做法及指南。
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/07/2019
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: bf449f801e4e7617e7fe91d0884b3443559e71c6
ms.sourcegitcommit: 11486fb4c16095e3fef785126003cac3e3e06c0d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2019
ms.locfileid: "54271315"
---
# <a name="best-practices-and-guidance-for-the-common-data-service-for-apps"></a>面向应用程序的 Common Data Service 的最佳做法及指南

面向应用程序的 Common Data Service (CDS) 是一种可扩展的框架，可让开发人员构建可高度定制和自定义的体验。 在自定义、扩展面向应用程序的 Common Data Service (CDS) 或与之集成时，开发人员应了解既有指南和最佳做法。 

在本部分中，你将学习到我们已确定的问题及其影响，并了解其解决指南。 我们将介绍为何应按特定方式实时操作的原因，同时避免未来的潜在问题。 这可提升你的环境的可用性、可支持性和性能。 本指南文档对开发人员和管理指南中的既有信息进行强化补充。

# <a name="targeted-customization-types"></a>目标自定义类型
本文档针对以下自定义类型：

- 自定义工作流活动和插件
- 使用 CDS 数据
- 可扩展面向应用程序的 Common Data Service 的集成

# <a name="sections"></a>章节
每篇指南文档包含下面的全部或部分章节：

- 标题 - 指南说明
- 类别 - 因不遵循指南而受影响的一个或多个方面
- 影响级别 - 因不遵循指南而造成环境影响的风险级别（高、中等、低）
- 具体表现 - 可能表示未遵循指南的迹象
- 指南 - 相关建议（可能还包括示例）
- 存在问题的模式 - 有关未遵循指南的说明或示例
- 其他信息 - 便于更详尽阐述的支持信息
- 另请参阅 - 详细介绍文章中所提及内容的相关参考

# <a name="categories"></a>类别
每篇指南文档都划分成下面一个或多个类别：

- 用法 - 特定 API、模式或配置的不当用法
- 设计 - 自定义项中的设计缺陷
- 性能 - 可能在内存管理、CPU 使用率、网络流量或用户体验等方面对性能造成负面影响的自定义项或模式
- 安全性 - 自定义项中可能在运行时环境中被利用的潜在漏洞
- 升级就绪情况 - 可能增加版本升级失败风险的自定义项或模式
- 在线迁移 - 可能增加在线迁移失败风险的自定义项或模式
- 可维护性 - 不必要地增加开发人员进行更改所需的工作量、所需更改的频率或造成性能倒退的几率的自定义项
- 可支持性 - 未在已发布的可支持性声明涵盖范围内的自定义项或模式，包括对已删除的 API 的使用或对已禁止的技术的实施
