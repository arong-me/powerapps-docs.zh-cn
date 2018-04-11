---
title: 为 Common Data Service for Apps 在 PowerApps 中生成应用（快速入门）| Microsoft Docs
description: 在 PowerApps 中自动生成应用，用于管理 Common Data Service for Apps 中的数据
services: powerapps
documentationcenter: na
author: AFTOwen
manager: kfile
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/10/2018
ms.author: anneta
ms.openlocfilehash: 78429fc5d0220b5cc9e8dc726583c2e9e543f85a
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="quickstart-for-generating-an-app-in-powerapps-for-the-common-data-service-for-apps"></a>快速入门：为 Common Data Service for Apps 在 PowerApps 中生成应用

在本快速入门中，使用 PowerApps 基于 [Common Data Service for Apps](../common-data-service/data-platform-intro.md) 中的示例帐户列表自动生成第一个应用。 在此应用中，可以浏览所有帐户、显示单个帐户的详细信息以及创建、更新或删除帐户。

若要执行本快速入门，须切换到满足后列条件的[环境](working-with-environments.md)：Common Data Service 中已创建数据库并包含数据。 如果不具备此环境但拥有管理权限，则可按此要求[创建环境](../../administrator/environments-administration.md#create-an-environment)。

如果没有适用于 PowerApps 的许可证，可以[免费注册](../signup-for-powerapps.md)。

## <a name="generate-an-app"></a>生成应用
1. 登录 [PowerApps](https://web.powerapps.com)。

    ![PowerApps 主页](./media/data-platform-create-app/sign-in.png)

1. 在“生成类似应用”下，悬停在“从数据开始”上，然后选择“生成此应用”。

    ![用于创建应用的选项](./media/data-platform-create-app/make-this-app.png)

1. 在“开始使用数据”下，选择向右箭头。

    ![箭头图标](./media/data-platform-create-app/right-arrow.png)

1. 在“连接”下，选择到 Common Data Service 的连接。

1. 在搜索框（近右边缘）中键入“帐户”，在“选择表格”下选择“帐户”，然后选择“连接”。

    ![选择实体](./media/data-platform-create-app/select-entity.png)

几分钟之后应用打开并显示为浏览屏幕，其中显示帐户列表。 靠近屏幕顶部的标题栏显示用于刷新列表、排序列表和创建帐户的图标。 标题栏下的一个搜索框提供一个选项，通过此选项可基于键入或粘贴的文本来筛选列表。 

默认情况下，列表显示该帐户的图像、电子邮件地址、城市和 ID。 但也可以将列表（此时称为“库”）自定义为显示其他类型的数据。

![浏览屏幕](./media/data-platform-create-app/browse-screen.png)

## <a name="save-the-app"></a>保存应用
在使用此应用或与他人共享前，可能需要再作出一些更改。 最佳做法是在继续操作之前保存当前的工作。

1. 在左上角附近，单击或点击“文件”选项卡。

1. 在“应用设置”页上，将应用名称设置为“AppGen”，将背景色更改为深红色，并将图标更改为一个选中标记。

    ![应用设置页面](./media/data-platform-create-app/app-settings.png)

1. 在左边缘附近单击或点击“保存”。

## <a name="next-steps"></a>后续步骤
本快速入门创建了一个应用，可管理 Common Data Service for Apps 中帐户的相关示例数据。 下一步将自定义默认浏览屏幕，以更好地满足需求。

> [!div class="nextstepaction"]
> [自定义默认浏览屏幕](customize-layout-sharepoint.md)。
