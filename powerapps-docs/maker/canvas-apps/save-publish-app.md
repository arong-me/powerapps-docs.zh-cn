---
title: 保存并发布应用 | Microsoft 文档
description: 面向应用开发者的应用保存和发布分步说明
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 09/14/2017
ms.author: anneta
ms.openlocfilehash: faaf3ef6eefc41ad5b1d7cb2e6e34db57632cfaf
ms.sourcegitcommit: 0e9af8cace2bdc04750f4c5a70a3c4af8e3d2292
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2018
ms.locfileid: "39194797"
---
# <a name="save-and-publish-an-app-in-powerapps"></a>在 PowerApps 中保存并发布应用
每当保存应用更改时，都只会对你自己和有权编辑此应用的其他所有人自动发布更改。 完成更改后，必须显式发布更改，以便应用的所有共享对象都能使用。

若要了解如何共享应用，请参阅[共享应用](share-app.md)。

## <a name="save-changes-to-an-app"></a>保存应用更改
在 PowerApps Studio 中，单击或点击左侧边缘上“文件”菜单中的“保存”，再根据需要按照下列任一步骤操作：

* 如果之前从未保存过应用，请输入应用名称，再单击或点击“保存”。

    ![保存新应用](./media/save-publish-app/save-as.png)
* 如果之前保存过应用，请单击或点击“保存”。  

    ![保存更新后的应用](./media/save-publish-app/save-app.png)

PowerApps 也可以每 2 分钟定期保存一次应用。 如果已保存一次应用，那么 PowerApps 会继续定期保存应用的版本，用户无需点按“保存操作”。 作者可以在“帐户”选项卡上的“文件”菜单中，启用或禁用“自动保存”设置。

![“自动保存”设置](./media/save-publish-app/autosave.png)

## <a name="publish-an-app"></a>发布应用
1. 在 PowerApps Studio 中，依次单击或点击左侧边缘上“文件”菜单中的“保存”和“发布此版本”。

    ![发布应用](./media/save-publish-app/publish-app.png)
2. 在“发布”对话框中，点击或单击“发布此版本”，向所有作为应用共享对象的用户发布应用。

   ![检查发布信息](./media/save-publish-app/publish-review.png)

   > [!NOTE]
   > 每次发布画布应用时，应用都将升级为在最新版 PowerApps 上运行，这意味着它将获得所有最新功能的好处和自上次发布后的性能升级。 如果几个月内未发布更新，现在重新发布可能会体验到即时性能提升这一好处。

## <a name="identify-the-live-version"></a>确定实时版本
在 [powerapps.com](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 中，依次单击或点击左侧边缘上“文件”菜单中的“应用”、应用详细信息图标和“版本”选项卡。

“实时”版本会向所有作为应用共享对象的用户发布。 任何应用的最新版本都只会向拥有编辑权限的用户发布。

![从门户发布](./media/save-publish-app/publish-portal.png)

若要发布最新版本，请依次单击或点击“发布此版本”和“发布”对话框中的“发布此版本”。

## <a name="next-steps"></a>后续步骤
* 在 powerapps.com 中[重命名应用](set-name-tile.md)。
* [还原应用](restore-an-app.md)（如果有多版应用的话）。
