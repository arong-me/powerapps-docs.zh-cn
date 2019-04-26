---
title: 开发人员：模型驱动应用的最佳做法和指南 | Microsoft Docs
description: PowerApps 中针对模型驱动应用开发人员的最佳做法和指南。
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
ms.date: 12/12/2018
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 152b7bc5e61a579bc06c02f60079ecfc7b05512b
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63320904"
---
# <a name="best-practices-and-guidance-for-model-driven-apps"></a>模型驱动应用的最佳做法和指南

模型驱动应用是一种专注于组件的应用开发方法，开发人员可扩展它来实现更加个性化的体验。 在自定义模型驱动应用时，开发人员应了解既有指南和最佳做法。 

在本部分中，你将学习到我们已确定的问题及其影响，并了解其解决指南。 我们将介绍为何应按特定方式实时操作的原因，同时避免未来的潜在问题。 这可提升你的环境的可用性、可支持性和性能。 本指南文档对开发人员和管理指南中的既有信息进行强化补充。

# <a name="targeted-customization-types"></a>目标自定义类型
本文档针对以下自定义类型：

- 模型驱动应用设计
- 实体窗体设计
- 客户端脚本
- Web 资源

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