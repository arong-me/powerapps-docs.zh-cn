---
title: " Power Apps 门户管理中心概述 | MicrosoftDocs"
description: 有关 Power Apps 门户管理中心的信息。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 21e27be0c5c60d6c992c58839980283088f1c2b4
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977961"
---
# <a name="power-apps-portals-admin-center"></a>Power Apps 门户管理中心

Power Apps 门户管理中心允许您对门户执行高级管理操作。 成功配置门户后，可以使用管理中心。

## <a name="open-power-apps-portals-admin-center"></a>打开 Power Apps 门户管理中心

1. 转到 Power Apps 主页上的**最近应用程序**分区，然后找到您的门户。

    > [!div class=mx-imgBorder]
    > ![最近应用](../media/recent-apps.png "最近应用")  

2. 选择**更多命令 (...)** > **设置**。

    > [!div class=mx-imgBorder]
    > ![门户设置选项](../media/portal-settings-option.png "门户设置选项")

3. 在**门户设置**窗格中，选择**管理**。

    > [!div class=mx-imgBorder]
    > ![门户设置窗格](../media/portal-settings-admin.png "门户设置窗格")

## <a name="add-yourself-as-an-owner-of-the-azure-ad-application"></a>将自己添加为 Azure AD 应用程序的负责人

如果您不是全局管理员，但尝试管理已设置的门户或在失败后重新提交设置，您必须是连接到您的门户的 Azure Active Directory (Azure AD) 应用程序的负责人。

1. 转到 Power Apps 门户管理中心，打开**门户详细信息**选项卡。

2. 复制**应用程序 ID** 字段中的值。

    > [!div class=mx-imgBorder]
    > ![门户详细信息选项卡](../media/portal-details-admin.png "门户详细信息选项卡")

3. 转至与您的租户关联的 Azure AD。 [!include[](../../../includes/proc-more-information.md)] [作为 Azure Active Directory 中的管理员接管未托管目录](https://docs.microsoft.com/azure/active-directory/active-directory-manage-o365-subscription)

4. 在 Azure AD 中，使用复制的应用程序 ID 搜索应用注册。 可能需要从**我的应用程序**切换到**所有应用程序**。

5. 将用户或组添加为此应用注册的负责人。 [!include[](../../../includes/proc-more-information.md)] [管理应用的访问权限](https://docs.microsoft.com/azure/active-directory/active-directory-managing-access-to-apps)

    > [!Note]
    > 组织的全局管理员或此应用程序的现有负责人可执行此任务。

6. 将自己添加为负责人之后，重新打开 Power Apps 门户管理中心页面。