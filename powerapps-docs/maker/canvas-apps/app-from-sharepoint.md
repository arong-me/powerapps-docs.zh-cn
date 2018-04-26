---
title: 快速入门：通过 SharePoint 在 PowerApps 中生成应用 | Microsoft Docs
description: 在 PowerApps 中自动生成管理 SharePoint 列表数据的应用
documentationcenter: na
author: AFTOwen
manager: kfile
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 03/12/2018
ms.author: anneta
ms.openlocfilehash: 314fa5a1a49aba3bc3d7f0f59d583f81283a67a0
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="quickstart-for-generating-an-app-in-powerapps-from-sharepoint"></a>快速入门：通过 SharePoint 在 PowerApps 中生成应用

本快速入门教程介绍如何基于 SharePoint 中创建的列表使用 PowerApps 自动生成第一个应用。 在此应用中，可以浏览列表中的所有项、显示单个项的详细信息以及创建、更新或删除项。

如果在 SharePoint 中拥有任何列表，可通过本快速入门教程了解相关概念和技术。 若要精确按照本快速入门教程操作，需要在 SharePoint Online 网站中创建一个名为“SimpleApp”的列表，其中包含名为“标题”的列。 在该列表中，创建“香草”、“巧克力”和“草莓”的条目。

可以创建更复杂的列表，包含更多的列，涵盖更多数据类型，例如文本、日期、数字和货币。 生成应用的原理不变。 如果通过数据网关[连接到站点](connect-to-sharepoint.md)，还可通过本地 SharePoint 站点上的列表生成应用。

如果没有适用于 PowerApps 的许可证，可以[免费注册](../signup-for-powerapps.md)。

## <a name="generate-an-app"></a>生成应用
1. 登录 [PowerApps](https://web.powerapps.com)。

    ![PowerApps 主页](./media/app-from-sharepoint/sign-in.png)

1. 在“生成类似应用”下，悬停在“从数据开始”上，然后选择“生成此应用”。

    ![用于创建应用的选项](./media/app-from-sharepoint/make-this-app.png)

1. 在 SharePoint 磁贴上选择“手机布局”。

    ![用于创建应用的选项](./media/app-from-sharepoint/sharepoint-tile.png)

1. 选中“直接连接”选项后，选择“创建”。

    ![创建连接](./media/app-from-sharepoint/create-connection.png)

1. 在“连接到 SharePoint 网站”下，输入或粘贴 SharePoint Online 站点的 URL，然后选择“转到”。

    其中仅包含站点 URL（不是列表名称），如以下示例所示：<br>`https://microsoft.sharepoint.com/teams/Contoso`

1. 在“选择列表”下选择“SimpleApp”，然后选择“连接”。

几分钟之后应用打开并显示为浏览屏幕，其中显示列表中创建的项。 如果除“标题”列外，列表中还有其他列中含有数据，应用会显示这些数据。 靠近屏幕顶部的标题栏显示对应于刷新列表、列表排序和在列表中创建项的图标。 标题栏下的一个搜索框提供一个选项，通过此选项可基于键入或粘贴的文本来筛选列表。 

![浏览屏幕](./media/app-from-sharepoint/browse-screen.png)

在使用此应用或与他人共享前，可能需要再作出一些更改。 最佳做法是在继续操作之前按 Ctrl-S 保存当前的工作。 为应用命名，并选择“保存”。

## <a name="next-steps"></a>后续步骤
本快速入门教程创建了一个应用，用于管理 SharePoint 列表中的数据。 下一步是通过更复杂的列表生成应用，并自定义该应用（从浏览屏幕开始）以更好地满足需求。

> [!div class="nextstepaction"]
> [自定义默认浏览屏幕](customize-layout-sharepoint.md)