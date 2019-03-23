---
title: 生成基于 Common Data Service 的画布应用 |Microsoft Docs
description: 在 PowerApps 中，可以自动生成画布应用来管理 Common Data Service 中的数据
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: quickstart
ms.custom: canvas
ms.reviewer: ''
ms.date: 05/06/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 38e2798ae60206ff0584254916e4f750096155e4
ms.sourcegitcommit: 5b2b70c3fc7bcba5647d505a79276bbaad31c610
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2019
ms.locfileid: "58356853"
---
# <a name="generate-a-canvas-app-from-common-data-service-in-powerapps"></a>从 PowerApps 中的 Common Data Service 生成画布应用

在 PowerApps 中，自动生成画布应用中的示例帐户列表基于[Common Data Service](../common-data-service/data-platform-intro.md)。 在此应用中，可以浏览所有帐户、显示单个帐户的详细信息以及创建、更新或删除帐户。

如果没有注册 PowerApps，请在开始使用之前先[免费注册](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

## <a name="prerequisites"></a>先决条件

若要遵循本快速入门中，您必须分配给[环境创建者](https://docs.microsoft.com/power-platform/admin/database-security.md#predefined-security-roles)安全角色，并且你必须[切换到环境](working-with-environments.md)的 Common Data Service 中已创建了一个数据库，在包含数据，并允许更新。 如果不具备此环境但拥有管理权限，则可按此要求[创建环境](https://docs.microsoft.com/power-platform/admin/environments-administration.md#create-an-environment)。

## <a name="generate-an-app"></a>生成应用

1. 登录到 [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) ，如有必要，按本主题前文所述切换环境。

1. 在“生成自己的应用”下，将鼠标悬停在“从数据开始”上，然后选择“生成此应用”。

    ![用于创建应用的选项](./media/data-platform-create-app/start-from-data.png)

1. 在“Common Data Service”磁贴中，选择“手机布局”。

    ![连接磁贴](./media/data-platform-create-app/connection-tile.png)

1. 在“选择表”下选择“帐户”，然后选择“连接”。

1. 如果出现“欢迎使用 PowerApps Studio”对话框，则单击“跳过”。

应用打开并显示浏览屏幕，其中的控件中将显示帐户列表，这称为一个库。 屏幕顶部附近的标题栏中将显示用于以下用途的图标：刷新库中的数据，按字母顺序对库中的数据进行排序，以及向库中添加数据。 标题栏下的一个搜索框提供一个选项，通过此选项可基于键入或粘贴的文本来筛选库中的数据。 

默认情况下，该库显示一个电子邮件地址、一个城市和一个帐户名称。 如[后续步骤](data-platform-create-app.md#next-steps)中所示，可以自定义库以更改数据的显示方式，甚至可以显示其他类型的数据。

![浏览屏幕](./media/data-platform-create-app/browse-screen.png)

## <a name="save-the-app"></a>保存应用
在使用此应用或与他人共享前，可能需要再作出一些更改。 最佳做法是在继续操作之前保存当前的工作。

1. 在左上角附近，选择“文件”选项卡。

1. 在“应用设置”页上，将应用名称设置为“AppGen”，将背景色更改为深红色，并将图标更改为一个选中标记。

    ![应用设置页面](./media/data-platform-create-app/app-settings.png)

1. 在左边缘附近，选择“保存”，然后在左下角，选择“保存”。

## <a name="next-steps"></a>后续步骤
在本快速入门，创建了一个应用来管理 Common Data Service 中的帐户的相关示例数据。 下一步将自定义库和默认浏览屏幕的其他元素，以更好地满足需求。

> [!div class="nextstepaction"]
> [自定义库](customize-layout-sharepoint.md)。
