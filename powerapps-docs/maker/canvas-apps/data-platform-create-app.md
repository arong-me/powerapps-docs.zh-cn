---
title: 从 Common Data Service for Apps 生成画布应用 | Microsoft Docs
description: 在 PowerApps 中自动生成画布应用，用于管理 Common Data Service for Apps 中的数据
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
ms.openlocfilehash: bf19983217afad23b75a0f0dbd1e307e6539d3f5
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42825939"
---
# <a name="generate-a-canvas-app-from-common-data-service-for-apps-in-powerapps"></a>在 PowerApps 中从 Common Data Service for Apps 生成画布应用

在 PowerApps 中，基于 [Common Data Service (CDS) for Apps](../common-data-service/data-platform-intro.md) 中的示例帐户列表自动生成画布应用。 在此应用中，可以浏览所有帐户、显示单个帐户的详细信息以及创建、更新或删除帐户。

如果没有注册 PowerApps，请在开始使用之前先[免费注册](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

## <a name="prerequisites"></a>先决条件

若要按照本快速入门操作，须[切换到满足以下条件的环境](working-with-environments.md)：已在 CDS for Apps 中创建数据库、包含数据并允许更新。 如果不具备此环境但拥有管理权限，则可按此要求[创建环境](../../administrator/environments-administration.md#create-an-environment)。

## <a name="generate-an-app"></a>生成应用

1. 登录到 [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) ，如有必要，按本主题前文所述切换环境。

    ![PowerApps 主页](./media/data-platform-create-app/sign-in.png)

1. 在“生成类似应用”下，悬停在“从数据开始”上，然后选择“生成此应用”。

    ![用于创建应用的选项](./media/data-platform-create-app/make-this-app.png)

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
本快速入门创建了一个应用，可管理 CDS for Apps 中帐户的相关示例数据。 下一步将自定义库和默认浏览屏幕的其他元素，以更好地满足需求。

> [!div class="nextstepaction"]
> [自定义库](customize-layout-sharepoint.md)。
