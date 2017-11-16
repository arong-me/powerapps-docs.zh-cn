---
title: "环境 | Microsoft 文档"
description: "使用应用、连接和其他资源的容器"
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
featuredvideoid: 32olG9uCmBU
courseduration: 8m
ms.service: powerapps
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/09/2016
ms.author: mblythe
ms.openlocfilehash: 3f17dd94359f9c6d20464662a860fd9f784991c3
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="powerapps-environments"></a>PowerApps 环境
学习本课程到现在，你已用过几次 web.powerapps.com。无论知道与否，你一直是在特定的*环境*中执行操作。 简单来说，环境就是应用和其他资源的分组（稍后将对此进行详细介绍）。 web.powerapps.com 屏幕右上角显示指明当前环境的下拉菜单。

![环境选取器](./media/learning-manage-environments/environment-picker.png)

如果刚开始接触 PowerApps，此时可能只会看到默认环境。 单击或点击下拉菜单，看看是否有其他环境。

## <a name="why-use-environments"></a>为什么要使用环境？
环境是应用和其他资源（如数据连接和 Microsoft Flow 流）的容器。 这是一种根据业务需求对资源进行分组的方法。 除默认环境之外，可出于以下几个原因创建其他环境：

* **各部门单独开发应用**：在大型组织中，每个部门都可以在不同的环境中工作。
* **支持应用程序生命周期管理 (ALM)**：可以将正在开发的应用和已经完成并共享的应用的环境区分开来。
* **管理数据访问**：每个环境都有自己的 Common Data Service 数据库，其他数据连接也专用于相应的环境（即无法跨环境共享数据）。

请注意一点，环境仅与应用创建者和 PowerApps 管理员相关。 与用户共享应用后，他/她只要拥有相应权限，即可运行应用。 无需担心应用源自什么环境。

## <a name="create-an-environment"></a>创建环境
到目前为止，本课程都以应用创建者为重，而环境则是由管理员进行创建和维护的。 如果不是管理员，此信息仍十分有用，因为需要就环境创建与管理员联系。 在 PowerApps 管理中心内，依次单击或点击“**环境**”和“**新建环境**”。 在“**新建环境**”屏幕上，输入环境名称，选择一个区域，以及是否为环境创建 Common Data Service 数据库，然后单击或点击“**创建环境**”。

![创建环境](./media/learning-manage-environments/create-environment.png)

就是这么简单！现在便可以在新环境中工作了。 此时，如果返回 web.powerapps.com，就可以在环境下拉菜单中看到它。

## <a name="manage-access-to-an-environment"></a>管理对环境的访问权限
拥有以下角色便可以访问环境：

* **环境管理员**：在环境中拥有全部权限。
* **环境创建者**：不仅可以查看所有应用、创建应用，还能使用 Common Data Service（其他权限适用）。

作为管理员，可以在“**环境**”选项卡中授予对环境的访问权限。首先，单击或点击一个环境。 若要添加某用户（在此示例中，添加到**环境创建者**角色），请依次单击或点击“**环境角色**”和“**环境创建者**”。 在这里，将用户或组添加到角色，然后单击“**保存**”。

![管理环境访问权限](./media/learning-manage-environments/environment-access.png)

至此，你已了解环境的优势、如何创建环境以及如何授予对环境的访问权限。 即使不是管理员角色，阅读此类信息也有助于了解此服务的工作原理。 至此，你已阅读完“管理应用”部分，可以继续阅读下一部分“管理数据”，此部分重点介绍了 Common Data Service。
