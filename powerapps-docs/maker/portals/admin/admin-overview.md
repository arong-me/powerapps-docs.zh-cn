---
title: PowerApps 门户管理中心概述 |MicrosoftDocs
description: PowerApps 门户管理中心的相关信息。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6f8434a6a395931fc4edfe02913f47536b4a709d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543076"
---
# <a name="powerapps-portals-admin-center"></a>PowerApps 门户管理中心

PowerApps 门户管理中心允许您在门户上执行高级管理操作。 成功设置门户后，可使用管理中心。

## <a name="open-powerapps-portals-admin-center"></a>打开 PowerApps 门户管理中心

1. 在 PowerApps 主页上，中转到 "**最近使用的应用**" 部分，找到你的门户。

    > [!div class=mx-imgBorder]
    > ![最新应用](../media/recent-apps.png "最新应用")  

2. 选择 "**更多命令" （...）**  > **设置**。

    > [!div class=mx-imgBorder]
    > ![门户网站设置选项](../media/portal-settings-option.png "门户网站设置选项")

3. 在门户的 "**设置**" 窗格中，选择 "**管理**"。

    > [!div class=mx-imgBorder]
    > ![门户设置窗格](../media/portal-settings-admin.png "门户设置窗格")

## <a name="add-yourself-as-an-owner-of-the-azure-ad-application"></a>将自己添加为 Azure AD 应用程序的所有者

如果你不是全局管理员，并且尝试管理已设置的门户，或者在失败时重新提交预配，则必须是连接到门户的 Azure Active Directory （Azure AD）应用程序的所有者。

1. 请切换到 PowerApps 门户管理中心并打开**门户详细信息**选项卡。

2. 复制 "**应用程序 ID** " 字段中的值。

    > [!div class=mx-imgBorder]
    > ![门户详细信息选项卡](../media/portal-details-admin.png "门户详细信息选项卡")

3. 中转到与租户关联的 Azure AD。 [!include[](../../../includes/proc-more-information.md)] 以[管理员身份在 Azure Active Directory 中接管非托管目录](https://docs.microsoft.com/azure/active-directory/active-directory-manage-o365-subscription)

4. 在 Azure AD 中，使用复制的应用程序 ID 搜索应用注册。 可能需要从 **"我的应用"** 切换到 "**所有应用**"。

5. 添加用户或组作为此应用注册的所有者。 [!include[](../../../includes/proc-more-information.md)][管理对应用的访问](https://docs.microsoft.com/azure/active-directory/active-directory-managing-access-to-apps)

    > [!Note]
    > 此任务可以由组织的全局管理员或此应用程序的现有所有者执行。

6. 将自己添加为所有者后，请重新打开 PowerApps 门户管理中心页面。