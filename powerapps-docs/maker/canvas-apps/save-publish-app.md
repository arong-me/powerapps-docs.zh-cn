---
title: 保存并发布画布应用 | Microsoft Docs
description: 保存和发布面向应用开发者的画布应用的分步说明
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/23/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 740107af85e59baf44c6cfbe89eb62a42daa08a2
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "79211977"
---
# <a name="save-and-publish-a-canvas-app-in-power-apps"></a>在 Power Apps 中保存并发布画布应用
每当保存画布应用的更改时，都将只对你自己和有权限编辑此应用的其他所有人自动发布更改。 完成更改后，必须显式发布更改，以便应用的所有共享对象都能使用。

若要了解如何共享应用，请参阅[共享应用](share-app.md)。

## <a name="save-changes-to-an-app"></a>保存应用更改
在 Power Apps Studio 中，选择“文件”菜单（位于左侧边缘）上的“保存”，然后按以下任一步骤操作：

* 如果之前从未保存过应用，请输入应用名称，然后选择“保存”。

    ![保存新应用](./media/save-publish-app/save-as.png)
* 如果之前保存过应用，请选择“保存”。 你还可以保留版本特定的说明或注释。  

    ![保存更新后的应用](./media/save-publish-app/save-app.png)

Power Apps 也可以每 2 分钟定期保存一次应用。 如果已保存过一次应用，Power Apps 会继续定期保存应用的版本，用户无需点按“保存”操作。 作者可以在“帐户”选项卡上的“文件”菜单中，启用或禁用“自动保存”设置。

![“自动保存”设置](./media/save-publish-app/autosave.png)

## <a name="publish-an-app"></a>发布应用
1. 在 Power Apps Studio 中，选择“文件”菜单（位于左侧边缘）上的“保存”，然后选择“发布”。

    ![发布应用](./media/save-publish-app/publish-app.png)
2. 在“发布”对话框中，选择“发布此版本”，向将共享应用的所有用户发布应用。

   ![检查发布信息](./media/save-publish-app/publish-review.png)

   > [!NOTE]
   > 每次发布画布应用时，应用都将升级为在最新版 Power Apps 上运行，这意味着它将获得所有最新功能的好处和自上次发布后的性能升级。 如果几个月内未发布更新，现在重新发布可能会体验到即时性能提升这一好处。

## <a name="identify-the-live-version"></a>确定实时版本
在 [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 中，依次选择“文件”菜单（位于左侧边缘）上的“应用”、应用详细信息图标和“版本”选项卡。

“实时”版本会向所有作为应用共享对象的用户发布。 任何应用的最新版本都只会向拥有编辑权限的用户发布。

![从门户发布](./media/save-publish-app/publish-portal.png)

若要发布最新版本，请突出显示版本，然后选择省略号（...）。然后从下拉菜单中选择 "**发布此版本**"。

## <a name="next-steps"></a>后续步骤
* 在[浏览器](../../user/run-app-browser.md)或[手机](../../user/run-app-client.md)上查找并运行应用。
* 在 powerapps.com 中[重命名应用](set-name-tile.md)。
* [还原应用](restore-an-app.md)（如果有多版应用的话）。
