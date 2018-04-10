---
title: 有关下载租户中活动用户列表的快速入门 | Microsoft Docs
description: 本快速入门教程介绍如何下载租户中活动用户的列表
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
ms.openlocfilehash: 8d1f04f5b559e179e1549c92e75c16dac79210df
ms.sourcegitcommit: a9d33322228c398d29964429602dc3fe19fa67d2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/28/2018
---
# <a name="quickstart-download-a-list-of-active-users-in-your-tenant"></a>快速入门：下载租户中活动用户的列表
若为 365 全局管理员或 Azure Active Directory 租户管理员，可以下载租户中活跃用户的列表，这样不仅能确定谁访问过 PowerApps 和/或 Microsoft Flow，还能查看分配给这些用户的许可证。

本快速入门教程介绍如何将活动用户列表下载到 .csv 文件，然后在 Excel 中查看该列表。

要按照此本快速入门教程操作，需具有 Office 365 全局管理员或 Azure Active Directory 租户管理员权限。

## <a name="sign-in-to-the-powerapps-admin-center"></a>登录到 PowerApps 管理中心
在 [https://admin.powerapps.com]([https://admin.powerapps.com) 处登录到管理中心。

## <a name="download-the-list-of-users"></a>下载用户列表
在导航窗格中，单击或点击“用户许可证”，然后单击或点击“下载活动用户许可证列表”。

![文件和共享](./media/admin-view-user-licenses/download-list.png)

用户列表下载到 .csv 文件中。 此进程需要花费几分钟时间。 确保此列表下载完之前不要关闭窗口，否则可能需要重新启动该进程。

## <a name="view-the-list"></a>查看列表
.csv 文件生成后，在 Excel 中打开。 此列表包含每个用户的用户名、电子邮件地址、许可证类型和其他信息。

至少访问过一次产品的用户视为活动用户。 由于这是一个活动用户列表，因此该列表不包含拥有 PowerApps 和 Microsoft Flow 许可证，但从未访问过这两种产品的用户。 可以在 [Office 365 管理中心](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)内查看所有用户许可证。

以下示例展示了同时持有 PowerApps 和 Microsoft Flow 许可证的两位用户。 Jane Doe 通过订阅 Office 365 获得了访问权限，并持有每个产品的试用许可证。

![文件和共享](./media/admin-view-user-licenses/table2.png)

如果用户已从组织离职，此列表中的“用户名”和“电子邮件地址”列中将显示“未知”。 如果此列表中显示“未知”，但没有人从组织离职，请先等待几分钟，然后再次下载此列表。

若要添加用户许可证，请打开 [Office 365 管理中心](https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc)。

## <a name="next-steps"></a>后续步骤
在本快速入门教程中，将学习如何下载并查看租户中的活动用户列表。 要了解如何下载并查看环境中创建的应用的列表，请继续学习下一个快速入门教程。

> [!div class="nextstepaction"]
> [下载在环境中创建的应用的列表](admin-view-apps.md)
