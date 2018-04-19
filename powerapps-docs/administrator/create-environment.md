---
title: 创建环境的快速入门 | Microsoft Docs
description: 在本快速入门中，你将了解如何创建环境
services: powerapps
suite: powerapps
documentationcenter: na
author: skjerland
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: quickstart
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: sharik
ms.openlocfilehash: a9138c636d70ea4701cbf685c3d7c7965c0e8469
ms.sourcegitcommit: d7ed5144f96d1ecc17084c30ed0e2ba3c6b03c26
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/19/2018
---
# <a name="quickstart-create-an-environment"></a>快速入门：创建环境
环境是用来存储、管理和共享组织的业务数据、应用和流的空间。 还可以将环境用作分隔具有不同角色、安全要求或目标受众的应用的容器。 PowerApps 自动为每个租户创建一个默认环境，并由相应租户中的所有用户共享。

每个环境可以有 0 或 1 个 Common Data Service 数据库，从而为应用提供存储空间。 用户在环境中创建应用时，该应用可以连接到任何数据源，包括连接、网关和流。 但是，仅允许应用连接到同一环境中的 Common Data Service 数据库。 环境的使用方式视组织和要生成的应用而定。 有关详细信息，请参阅[环境概述](environments-overview.md)。

在本快速入门中，你将了解如何创建环境以及该环境的数据库。

## <a name="prerequisites"></a>先决条件
 若要按照本快速入门教程，则需要以下项目：
 * PowerApps 计划 2 或 Microsoft Flow 计划 2 许可证。 此外，也可以注册 [PowerApps 计划 2 免费试用版](https://web.powerapps.com/signup?redirect=marketing&email=)。
 * PowerApps 环境管理员、Office 365 全局管理员或 Azure Active Directory 租户管理员权限。 有关详细信息，请参阅 [PowerApps 中的环境管理](environments-administration.md)。

## <a name="sign-in-to-the-powerapps-admin-center"></a>登录到 PowerApps 管理中心
在 [https://admin.powerapps.com]([https://admin.powerapps.com) 上登录到管理中心。

## <a name="create-an-environment-and-database"></a>创建环境和数据库
1. 在导航窗格中，单击或点击“环境”，然后单击或点击“新环境”。

    ![文件和共享](./media/create-environment/new-environment.png)
2. 在“新环境”对话框中，为环境输入一个名称，然后从下拉列表中选择一个区域和环境类型。 区域默认为 Azure Active Directory 租户主区域，但可以从下拉列表中选择任何区域。 环境创建后，将无法更改区域。 完成后，单击或点击“创建环境”。

    ![文件和共享](./media/create-environment/new-environment-dialog.png)
3. 环境创建后，会在对话框中收到一条确认消息并且会提示你创建数据库。 单击或点击“创建数据库”启用对 Common Data Service 的访问。

    **注意：**此时，仅可以在 Azure Active Directory 租户主区域中创建数据库。

    ![文件和共享](./media/create-environment/create-database-dialog.png)
4. 为数据库中存储的数据选择货币和语言。 数据库创建后，将无法更改货币或语言。 完成后，单击或点击“创建数据库”。

    ![文件和共享](./media/create-environment/create-database-dialog2.png)

    在 Common Data Service 上创建数据库可能需要几分钟。 数据库创建后，新环境将出现在“环境”页的环境列表中。

    ![文件和共享](./media/create-environment/new-environment-created.png)

    单击或点击环境查看环境详细信息。

## <a name="next-steps"></a>后续步骤
在本快速入门中，你了解了如何创建环境以及该环境的数据库。 接下来，了解如何管理组织中的环境。

> [!div class="nextstepaction"]
> [管理 PowerApps 中的环境](environments-administration.md)
