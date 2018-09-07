---
title: 使用模型驱动应用自定义命令 | Microsoft Docs
description: 了解如何使用模型驱动应用来自定义命令
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
ms.openlocfilehash: 4721ba49fe227d31f539eabd863b50842e7515b6
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42836245"
---
# <a name="customize-commands-with-model-driven-apps"></a>使用模型驱动应用来自定义命令 

窗体或列表命令栏中显示的命令是可自定义的。 命令基于在 Office 功能区中使用的 XML 架构，因此仍使用术语“功能区”。 创建命令时，可定义三个元素：

- 加载窗体或列表时，将评估显示规则，以确定命令或命令组是否可见。
- 启用规则根据各种条件（如 UI 中的当前所选项）控制是否启用命令。
- 每个命令的操作，用于描述在被选中时要执行什么操作。 命令可打开 URL 或执行在 JavaScript Web 资源中所定义的函数。

根据任何现有命令定位自定义命令。 必须撰写自定义操作，该操作定义应用于现有命令集的更改。 

没有为命令提供设计器。 幸运的是，社区提供了工具。 [功能区工作台](http://www.develop1.net/public/rwb/ribbonworkbench.aspx)提供图形界面，且它是用于自定义命令最常用的工具。

详细信息：[Dynamics 365 客户参与开发人员指南：自定义命令和功能区](/dynamics365/customer-engagement/developer/customize-dev/customize-commands-ribbon)


