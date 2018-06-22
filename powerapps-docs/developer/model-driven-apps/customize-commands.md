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
ms.openlocfilehash: 7ad955ed5858cab69aaf8b2993ae3f98a04147fb
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
ms.locfileid: "30024544"
---
# <a name="customize-commands-with-model-driven-apps"></a>使用模型驱动应用来自定义命令 

窗体或列表命令栏中显示的命令是可自定义的。 命令基于在 Office 功能区中使用的 XML 架构，因此仍使用术语“功能区”。 创建命令时，可定义三个元素：

- 加载窗体或列表时，将评估显示规则，以确定命令或命令组是否可见。
- 启用规则根据各种条件（如 UI 中的当前所选项）控制是否启用命令。
- 每个命令的操作，用于描述在被选中时要执行什么操作。 命令可打开 URL 或执行在 JavaScript Web 资源中所定义的函数。

根据任何现有命令定位自定义命令。 必须撰写自定义操作，该操作定义应用于现有命令集的更改。 

没有为命令提供设计器。 幸运的是，社区提供了工具。 [功能区工作台](http://www.develop1.net/public/rwb/ribbonworkbench.aspx)提供图形界面，且它是用于自定义命令最常用的工具。

详细信息：[Dynamics 365 客户参与开发人员指南：自定义命令和功能区](/dynamics365/customer-engagement/developer/customize-dev/customize-commands-ribbon)


