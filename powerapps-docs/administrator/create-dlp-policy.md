---
title: 创建数据丢失防护 (DLP) 策略的快速入门 | Microsoft Docs
description: 在本快速入门中，你将了解如何在 PowerApps 中创建数据丢失防护 (DLP) 策略
services: powerapps
suite: powerapps
documentationcenter: na
author: SKjerland
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
ms.openlocfilehash: 651510bbe4ed71dbdb267ebee04e10ea13d36e15
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="quickstart-create-a-data-loss-prevention-dlp-policy"></a>快速入门：创建数据丢失防护 (DLP) 策略
为了保护组织中的数据，PowerApps 允许创建和强制策略，该策略定义可以共享特定业务数据的客户连接器。 这些用于定义如何共享数据的策略称为数据丢失防护 (DLP) 策略。 DLP 策略确保整个组织的数据都以统一的方式管理，它们防止重要业务数据意外发布到连接器（例如社交媒体网站）。

在本快速入门中，你将了解如何创建 DLP 策略，该策略防止 Common Data Service 和 SharePoint 数据库中存储的数据发布到 Twitter。

## <a name="prerequisites"></a>先决条件
若要按照本快速入门教程，则需要以下项目：
* PowerApps 计划 2 或 Flow 计划 2。 此外，也可以注册 [PowerApps 计划 2 免费试用版](https://web.powerapps.com/signup?redirect=marketing&email=)。
* PowerApps 环境管理员或 Azure Active Directory 租户管理员权限和到至少一个环境的权限。 有关详细信息，请参阅 [PowerApps 中的环境管理](environments-administration.md)。

## <a name="sign-in-to-the-powerapps-admin-center"></a>登录到 PowerApps 管理中心
在 [https://admin.powerapps.com]([https://admin.powerapps.com) 上登录到管理中心。

## <a name="create-a-dlp-policy"></a>创建 DLP 策略
1. 在导航窗格中，单击或点击“数据策略”，然后单击或点击“新策略”。

    ![](./media/create-dlp-policy/new-data-policy.png)
2. 输入“Contoso 安全数据访问”作为数据策略名称。
3. 在“环境”选项卡上，从下拉列表选择一个环境，然后单击或点击“继续”。

    ![](./media/create-dlp-policy/select-environment.png)
4. 在“数据组”选项卡的“仅业务数据”下，单击或点击“添加”。

    ![](./media/create-dlp-policy/data-groups.png)
5. 在“添加连接器”窗口中，选择“Common Data Service”和“SharePoint”（可能需要向下滚动或搜索它们），然后单击或点击“添加连接器”将其添加到“仅业务数据”数据组。

    ![](./media/create-dlp-policy/add-connectors.png)

    连接器一次仅可以驻留在一个数据组中，且默认添加到“不允许业务数据”组。 通过将 Common Data Service 和 SharePoint 移动到“仅业务数据”，你阻止了用户创建通过“不允许业务数据”组中任意连接器合并这两种连接器的流和应用。
6. 单击“保存策略”。

    ![](./media/create-dlp-policy/save-policy.png)

Contoso 安全数据访问策略创建并显示在数据丢失防护策略列表中。 由于 Twitter 连接器驻留在“不允许业务数据”数据组中，所以此策略可以确保 Common Data Service 和 SharePoint 不与 Twitter 共享其数据。

这是一种管理员与组织共享 DLP 策略列表使得用户在创建应用前注意策略的好方法。

## <a name="next-steps"></a>后续步骤
在本快速入门中，你学习了如何创建 DLP 策略防止重要业务熟悉意外发布到 Twitter 等连接器。 若要了解有关 DLP 策略的详细信息，请查看有关如何管理它们的文章。

> [!div class="nextstepaction"]
> [管理数据丢失防护 (DLP) 策略](prevent-data-loss.md)
