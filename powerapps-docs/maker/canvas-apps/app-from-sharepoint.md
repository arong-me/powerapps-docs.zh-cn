---
title: 从 SharePoint 列表创建画布应用 |Microsoft Docs
description: 在 Power Apps 中，自动创建一个画布应用以管理 SharePoint 列表中的数据
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 12/05/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 346bb27911549715b6c4fdc40f64552c524527be
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "79211908"
---
# <a name="create-a-canvas-app-in-power-apps-from-a-sharepoint-list"></a>从 SharePoint 列表在 Power Apps 中创建画布应用

在本主题中，你将使用 Power Apps 基于 SharePoint 列表中的项创建画布应用。 可以从 Power Apps 或 SharePoint Online 中创建应用。 如果你通过数据网关[连接到](connections/connection-sharepoint-online.md#create-a-connection)本地 SharePoint 站点中的列表，则可在 Power Apps 中创建基于该列表的应用。

你创建的应用将包含三个屏幕：

- 在浏览屏幕中，可以滚动浏览列表中的所有项目。
- 在详细信息屏幕中，可以显示有关列表中的单个项目的所有信息。
- 在编辑屏幕中，可以创建项目或更新有关现有项目的信息。

你可以将本主题中的概念和技术应用于 SharePoint 中的任何列表。 完全遵循以下步骤：

1. 在 SharePoint Online 站点中，创建名为 SimpleApp 的列表。
2. 在名为 Title 的列中，创建“香草”、“巧克力”和“草莓”的条目。

即使创建更复杂的列表（包含更多的列，涵盖更多数据类型，例如文本、日期、数字和货币），也不会更改生成应用的原则。

> [!IMPORTANT]
> Power Apps 不支持所有类型的 SharePoint 数据。 有关详细信息，请参阅 [已知问题](connections/connection-sharepoint-online.md#known-issues)。

## <a name="create-an-app-from-within-power-apps"></a>从 Power Apps 中创建应用

1. 登录到 [Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

1. 在“生成自己的应用”下，将鼠标悬停在“从数据开始”上，然后选择“生成此应用”。

    ![用于创建应用的选项](./media/app-from-sharepoint/start-from-data.png)

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

## <a name="create-an-app-from-within-sharepoint-online"></a>从 SharePoint Online 中创建应用

如果从 SharePoint Online 命令栏创建自定义列表的应用，则应用会显示为该列表的视图。 除了 Web 浏览器，也可在 iOS 或 Android 设备上运行应用。

1. 在 SharePoint Online 中，打开自定义列表，选择命令栏中的“PowerApps”，然后选择“创建应用”。

    ![创建应用](./media/app-from-sharepoint/generate-new-app.png)

2. 在显示的面板中，键入应用的名称，然后选择“创建”。

    ![命名应用](./media/app-from-sharepoint/app-name.png)

    Web 浏览器中将显示一个新选项卡，其中显示了基于 SharePoint 列表创建的应用。 应用会出现在 Power Apps Studio 中，你可以在其中自定义应用。

    ![默认应用](./media/app-from-sharepoint/default-app.png)

3. （可选）刷新 SharePoint 列表的浏览器选项卡（通过选中该列表，然后按 F5），然后执行以下步骤来运行或管理应用：

    - 若要运行应用（在单独的浏览器选项卡中），请选择“打开”。
    - 若要让组织中的其他人运行应用，请选择“使此视图公开”。

        若要让他人编辑应用，请使用“可以编辑”权限[共享它](share-app.md)。

    - 若要从 SharePoint 中删除视图，请选择“删除此视图”。

        若要从电源应用删除应用，请[删除该应用](delete-app.md)。

> [!NOTE]
> 从 SharePoint 列表创建的应用当前不会显示在 Power Apps Mobile 中。

## <a name="next-steps"></a>后续步骤
本主题创建了一个应用，用于管理 SharePoint 列表中的数据。 下一步，从更复杂的列表创建应用，然后自定义应用（从浏览屏幕开始）以更好地满足你的需求。

> [!div class="nextstepaction"]
> [自定义默认浏览屏幕](customize-layout-sharepoint.md)
