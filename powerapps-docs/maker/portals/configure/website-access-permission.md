---
title: 在 Power Apps 门户创建网站访问权限 | MicrosoftDocs
description: 了解如何在门户中创建网站访问权限并将其与元素关联。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: c333039eddb7e0e8bb376a8b6850b18f9d1a46ad
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977829"
---
# <a name="create-website-access-permissions"></a>创建网站访问权限

网站访问权限是权限集，与 [Web 角色](create-web-roles.md)关联，允许对门户中的各个内容管理元素进行前端编辑，而不只是网页。 权限设置确定哪些组件可以在门户中管理。

| 客户                         | 说明                                                                                      |
|------------------------------|--------------------------------------------------------------------------------------------------|
| 管理内容片段      | 允许编辑片段控件。                                                          |
| 管理网站标记          | 允许编辑使用站点标记的超链接                                           |
| 管理 Web 链接集         | 允许编辑 [Web 链接集](manage-web-links.md)，包括从 Web 链接集添加或删除 Web 链接。 |
| 预览尚未发布的实体 | 允许查看发布状态为草稿的门户公开的实体。             |
|||

若要创建网站访问权限并将它添加到 Web 角色：

1. 打开[“门户管理”应用](configure-portal.md)。

2. 转到**门户** > **网站访问权限**。

3. 选择**新建**。

4. 在**常规**下，输入名称、网站，并选择所需的权限。

    ![创建网站访问权限](../media/website-access-permission.png "创建网站访问权限")

5. 在 **Web 角色**下，选择**添加现有 Web 角色**，然后添加要与其关联权限的 Web 角色。

6. 保存更改。

    
