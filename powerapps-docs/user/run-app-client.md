---
title: 在移动设备上运行基于画布的应用 | Microsoft Docs
description: 了解如何在移动设备上运行画布应用。
author: mduelae
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 04/1/2020
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1494c1624fc37b59b5e20b0cdaa15a9c9edb33e3
ms.sourcegitcommit: 39f6feb699512e9c2bf71ef1a1238b32b639da02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2020
ms.locfileid: "80527473"
---
# <a name="run-a-canvas-app-on-a-mobile-device"></a>在移动设备上运行画布应用
在创建应用或与某人共享应用时，可以在 Windows、iOS、Android 上或 Web 浏览器中运行此应用。 本主题介绍如何在移动设备上运行画布应用。 在移动设备上运行的应用可以利用移动设备功能，如定位服务和照相机。

若要按照此步骤操作，请在开始之前先[免费注册](https://make.powerapps.com/signup?redirect=marketing&email=) Power Apps（如果还没有注册），然后从 [App Store](https://itunes.apple.com/app/powerapps/id1047318566?mt=8) 或 [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.msapps) 将 Power Apps 下载到运行[支持的操作系统](../maker/canvas-apps/limits-and-config.md)的 iPhone、iPad 或 Android 设备上。 此外请确保有权访问自己创建的应用或其他人创建并与你共享的应用。

## <a name="open-power-apps-and-sign-in"></a>打开 Power Apps 并登录
在移动设备上打开 Power Apps 并使用 Azure Active Directory 凭据登录。

![登录用户](./media/run-app-client/run-client-login.png)

如果移动设备上已安装 Microsoft Authenticator 应用，只需在出现提示时输入用户名，并通过随后发送至设备的通知来完成验证。

## <a name="find-the-app"></a>查找应用
为了更轻松地查找应用，请打开 PowerApps  菜单，并选择筛选器。

![应用筛选器](./media/run-app-client/filter-menu.png)

以下为可用筛选器：

* **所有应用**：显示你可以访问的所有应用，包括你创建的应用和其他人与你共享的应用。

* **我的应用**：显示至少运行了一次的应用。

* **示例应用**：显示 Microsoft 提供的示例应用，这些示例应用通过虚构数据展示真实的应用场景，可帮助发掘潜在的设计创意。

* **收藏夹**：通过点击应用磁贴上的省略号 (…)，然后点击“收藏夹”  ，显示已标记的应用。 若要从此列表中删除应用，点击应用磁贴上的省略号 (...)，然后点击“取消收藏”  。

    ![标记为收藏项](./media/run-app-client/favorite.png)

筛选应用后，可按应用的最近打开（或修改）时间或名称的字母顺序对筛选列表进行排序。 关闭和重新打开 Power Apps 后，这些首选项会予以保留。

![排序菜单](./media/run-app-client/sort-menu.png)

如果知道要运行的应用的名称，可点击 Powerapps 顶部的搜索图标，然后在搜索框中键入应用名称的一部分。

![搜索](./media/run-app-client/search.png)

如果已筛选应用，将在筛选的列表中进行搜索。

## <a name="run-an-app"></a>运行应用
若要在移动设备上运行画布应用，点击应用磁贴。 如果其他人创建了画布应用并在电子邮件中与你共享，你可以通过点击电子邮件中的链接来运行该应用。

首次使用 Power Apps 时，屏幕将显示通过轻扫手势关闭应用。

![启动应用](media/run_client.png)

## <a name="give-consent"></a>同意
如果应用需要连接数据源，或须具有相应权限才能使用设备功能（例如照相机或定位服务），必须先确认连接或予以同意，才能使用应用。 通常情况下，只会在首次连接时看到提示。

![连接](./media/run-app-client/app-connection.png)

## <a name="pin-an-app-to-the-home-screen"></a>将应用固定到主屏幕
可将应用固定到设备的主屏幕来实现快速访问。 点击应用磁贴上的省略号 (...)，点击“固定到主页”  ，然后按照显示的说明操作。

![固定应用](./media/run-app-client/run-client-pin.png)

## <a name="close-an-app"></a>关闭应用
若要关闭应用，用手指从应用的左边缘扫至右边缘。 在 Android 设备上，还可以按“后退”按钮，再确认要退出应用。

## <a name="next-steps"></a>后续步骤
本主题介绍如何在移动设备上运行画布应用。 还可以在移动设备上运行模型驱动应用。

> [!div class="nextstepaction"]
> [在移动设备上运行模型驱动应用](run-app-client-model-driven.md)
