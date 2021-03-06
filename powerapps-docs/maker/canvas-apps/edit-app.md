---
title: 编辑画布应用 | Microsoft Docs
description: 用于在 Power Apps 中编辑画布应用和会话锁定方案的分步说明。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/19/2017
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e68d34d6a8f6b6a115bdd272235e9c5c0f155a2c
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731570"
---
# <a name="edit-a-canvas-app-in-power-apps"></a>在 Power Apps 中编辑画布应用
编辑自己生成、拥有或拥有“可编辑”权限的任何画布应用。 可以在 Power Apps Studio 中编辑应用。 如果尝试编辑的应用已在别处打开以供编辑，将会看到一条消息，指明是你自己还是其他用户打开的。

## <a name="verify-your-permissions"></a>验证权限
1. 登录到[Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后在 "**文件**" 菜单（位于左边缘）上单击或点击 "**应用**"。
   
    ![“文件”菜单中的“应用”选项](./media/edit-app/file-apps.png)

2. 在应用类别选择器中，单击或点击“我可编辑的应用”。

    可以编辑随即显示的列表中的任何应用。 还可以在右上角附近的搜索框中键入一个或多个字符来搜索应用。

    > [!NOTE]
    > 如果仍未看到要编辑的应用，请验证是否已在右上角附近选择正确的环境。
   
    ![环境列表](./media/edit-app/environment-list.png)

1. 单击或点击想要编辑的应用的省略号图标 (...)，然后单击或点击“编辑”。

## <a name="collaborate-on-an-app"></a>针对应用展开协作
虽然对应用拥有“可编辑”权限的任何用户都可以进行编辑，但一次只能有一个人编辑应用。 如果尝试编辑其他人已在编辑的应用，则会看到以下消息。 只有当其他人关闭应用（或此人的会话超时），你才能继续编辑。

![](./media/edit-app/applock-otheruser.png)

此外，如果已打开应用以供编辑，然后又尝试在另一台设备或其他浏览器窗口中打开应用，则会看到以下消息。 虽然可以替代上一会话，但可能会丢失尚未保存的所有更改。

![](./media/edit-app/applock-selfuser.png)

## <a name="next-steps"></a>后续步骤
详细了解如何添加[屏幕](add-screen-context-variables.md)、[控件](add-configure-controls.md)或[数据连接](add-data-connection.md)。

