---
title: "查看用户许可证 | Microsoft 文档"
description: "管理员可以下载 PowerApps 和 Microsoft Flow 的用户许可证列表"
services: 
suite: powerapps
documentationcenter: na
author: manasmamsft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/02/2017
ms.author: manasma
ms.openlocfilehash: bc3d1c94deec6cf5e7c0ba5b73e65cab67d3ee25
ms.sourcegitcommit: 6afca7cb4234d3a60111c5950e7855106ff97e56
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2018
---
# <a name="identify-powerapps-users-in-your-organization"></a>识别组织中的 PowerApps 用户
如果你是 Office 365 全局管理员或 Azure Active Directory 租户管理员，可以下载组织中不仅被授权使用 PowerApps 和/或 Microsoft Flow，而且已访问过其中任一产品的用户列表。 此列表包含每个用户的用户名、电子邮件地址、许可证类型和其他信息。 例如，用户可能：

* 拥有 PowerApps 或 Microsoft Flow 的试用许可证
* 有权通过 Office 365 许可证访问这两种产品
* 有权通过 Dynamics 365 许可证访问这两种产品
* 有权通过 PowerApps 和 Microsoft Flow 计划进行访问

### <a name="download-the-list-of-users"></a>下载用户列表
1. 在 PowerApps 管理中心内，单击或点击左边缘附近的“用户许可证”。
   
    > [!IMPORTANT]
> 此选项仅适用于 Office 365 全局管理员和 Azure Active Directory 租户管理员。
   
    ![文件和共享](./media/admin-view-user-licenses/leftnav.png)
2. 单击或点击“下载活跃用户许可证列表”。
   
    ![文件和共享](./media/admin-view-user-licenses/download-list.png)
   
    文件可能需要几分钟的时间才能下载完毕。 请等待几分钟，直到 .csv 文件下载完毕，然后在 Excel 中打开。
   
    > [!NOTE]
> 如果文件未下载完毕就关闭窗口，可能需要重新开始执行此流程。

此示例展示了两位通过不同方式获得 PowerApps 和 Microsoft Flow 许可证的用户。 Jane Doe 通过 Office 365 订阅获得了访问权限，John Doe 获得的是每个产品的试用许可证。

![文件和共享](./media/admin-view-user-licenses/table2.png)

此列表不包含拥有 PowerApps 和 Microsoft Flow 许可证，但从未访问过这两种产品的用户。 可以在 [Office 365 管理中心][1]内查看所有用户许可证。

如果用户已从组织离职，此列表中的“用户名”和“电子邮件地址”等列中显示的是“未知”。 如果此列表中显示“未知”，但没有人从组织离职，请先等待几分钟，然后再次下载此列表。

若要添加用户许可证，请打开 [Office 365管理中心][1]。

<!--Reference links in article-->
[1]:https://support.office.com/article/Assign-or-remove-licenses-for-Office-365-for-business-997596b5-4173-4627-b915-36abac6786dc
