---
title: 在 Dynamics 365 门户中创建网站访问权限 |MicrosoftDocs
description: 了解如何在门户中创建网站访问权限并将其关联到元素。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0ac02992498204efc42a52e736284ea134ed42f5
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551016"
---
# <a name="create-website-access-permissions"></a>创建网站访问权限

网站访问权限是一个与[web 角色](create-web-roles.md)关联的权限集，它允许在不只是网页的情况下编辑门户中的各种内容托管元素。 权限设置确定哪些组件可在门户中进行管理。

| 名称                         | 描述                                                                                      |
|------------------------------|--------------------------------------------------------------------------------------------------|
| 管理内容片段      | 允许编辑代码段控件。                                                          |
| 管理站点标记          | 允许编辑使用站点标记的超链接                                           |
| 管理 Web 链接集         | 允许编辑[web 链接集](manage-web-links.md)，包括添加从 web 链接集中删除 web 链接。 |
| 预览未发布的实体 | 允许查看已发布状态为 "草稿" 的门户公开的实体。             |
|||

若要创建网站访问权限并将其添加到 web 角色，请执行以下操作：

1. 打开[门户管理应用](configure-portal.md)。

2.  > **网站访问权限**中转到**门户**。

3. 选择“新建”。

4. 在 "**常规**" 下，输入 "名称" 和 "网站"，然后选择所需的权限。

5. 在 " **Web 角色**" 下，选择并添加要与权限关联的 Web 角色。

6. 保存更改。

    ![创建网站访问权限](../media/website-access-permission.png "创建网站访问权限")  
