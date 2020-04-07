---
title: 在移动设备上运行画布应用和模型驱动应用 |Microsoft Docs
description: 了解如何在移动设备上运行画布应用或自定义模型驱动应用。
author: mduelae
ms.service: powerapps
ms.component: pa-user
ms.topic: quickstart
ms.date: 03/12/2020
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 5523ef67ed6912f7eae36228884b0c9a300d0785
ms.sourcegitcommit: 39f6feb699512e9c2bf71ef1a1238b32b639da02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2020
ms.locfileid: "80530000"
---
# <a name="run-canvas-apps-and-model-driven-apps-on-a-mobile-device"></a>在移动设备上运行画布应用和模型驱动应用

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

在你创建应用或有人与你共享应用&mdash;画布应用或模型驱动应用&dash;时，你可以使用 Power Apps 移动应用在 iOS 和 Android 设备上运行该应用。 如果你使用的是 Windows 设备，则只能运行画布应用；用于 Windows 设备的 Power App 移动应用不支持模型驱动应用。 在本主题中，你将了解如何开始并在移动设备上运行画布应用和模型驱动应用。 

要了解如何使用在 Power Apps 移动应用上运行的模型驱动应用，请参阅[有关在 Power Apps 移动应用上运行的模型驱动应用的用户指南](use-custom-model-driven-app-on-mobile.md)。

> [!IMPORTANT]
> 用于 Dynamics 365 Sales、Dynamics 365 Customer Service、Dynamics 365 Field Service、Dynamics 365 Marketing 和 Dynamics 365 Project Service Automation 的模型驱动应用<!--Via Dynamics Style Guide. If this sentence doesn't apply to all these products, maybe only mention Sales, Customer Service, and Field Service as you do in use-custom-model-driven-app-on-mobile.md? "Dynamics verticals" is out of brand.--> 不在 Power Apps 移动应用中运行。 你此时要使用适用于手机和平板电脑应用的 Dynamics 365。 详细信息：[适用于手机和平板电脑的 Dynamics 365 用户指南](https://docs.microsoft.com/dynamics365/mobile-app/dynamics-365-phones-tablets-users-guide)

![移动版 Power Apps](media/powerappsmobile.png "Power Apps 移动用户界面")

图例：

1. **模型驱动应用**
2. **画布应用**

**注册 Power Apps 移动预览版**

1. [安装 Power Apps for iOS](https://go.microsoft.com/fwlink/?linkid=2125171) 或[安装 Power Apps for Android](https://go.microsoft.com/fwlink/?linkid=2125172)。
2. 如果已安装应用，则安装的应用将替换为该应用的预览版本。
3. 请确保手动更新到可用的最新版本，以从最新的改进中获益。 
3. 安装应用后，可以开始测试。 有关任何反馈，请在 [pamobsup@microsoft.com](mailto:pamobsup@microsoft.com) 联系我们。 

## <a name="open-power-apps-and-sign-in"></a>打开 Power Apps 并登录

在移动设备上打开 Power Apps，再使用 Azure Active Directory 凭据登录。

![登录到 Power Apps](media/powerapps_mobile_app_signin_screen.png "登录到 Power Apps")

如果移动设备上已安装 Microsoft Authenticator 应用，只需在出现提示时输入用户名，并通过随后发送至设备的通知来完成验证。


## <a name="find-the-app"></a>查找应用

登录应用时，默认情况下会设置“我的应用”筛选器  。 如果找不到要查找的应用，可打开“Power Apps”菜单，然后选择其他筛选器  。 


![应用筛选器](media/filter-menu.png "应用筛选器")

以下为可用筛选器：

* **所有应用**：显示你可访问的所有画布应用和模型驱动应用，包括你创建的应用以及其他人与你共享的应用。

* **我的应用**：对于画布应用，这将显示你已打开的画布应用、你所拥有的应用以及你可编辑的应用。 对于模型驱动应用，这将显示你有权访问的所有模型驱动应用。 

* **示例应用**（仅限画布应用）：显示 Microsoft 提供的示例画布应用，这些示例应用通过虚构数据展示真实的应用场景，可帮助发掘潜在的设计创意。

* **收藏夹**（仅限画布应用）：选择画布应用磁贴上的省略号 (…)，然后选择“收藏夹”来显示已标记的应用  。 若要从此列表中删除应用，请选择应用磁贴上的省略号 (...)，然后选择“取消收藏”  。

    ![标记为收藏项](media/add_favorite_app.png "标记为收藏项")

* **特别推荐的应用**（仅限画布应用）：显示管理员标记为特别推荐的应用的画布应用。

### <a name="sort-apps"></a>对应用进行排序

筛选应用后，可按应用的最近打开（或修改）时间或名称的字母顺序对筛选列表进行排序。 关闭再重新打开应用后，这些首选项保持不变。 可对画布应用和模型驱动应用进行排序。

![对菜单进行排序](media/sort_apps.png "排序菜单")

### <a name="search-apps"></a>搜索应用

如果知道要运行的应用的名称，可选择顶部的“搜索”图标，然后在搜索框中键入应用名称的一部分。 可搜索画布应用和模型驱动应用。

![搜索应用](media/search_apps.png "搜索应用")

如果已筛选应用，将在筛选的列表中进行搜索。

### <a name="refresh-the-list-of-apps"></a>刷新应用列表

选择“刷新”图标 ![“刷新”图标](media/refresh_icon.png) 刷新应用列表。 这将刷新画布应用和模型驱动应用的列表。 

## <a name="pin-an-app-to-the-home-screen"></a>将应用固定到主屏幕

可将画布应用和模型驱动应用固定到设备的主屏幕上，以便快速访问。 选择应用磁贴上的省略号 (...)，选择“固定到主页”，然后按照显示的说明操作  。

![固定应用](media/pin_to_home.png "固定应用")

## <a name="see-non-production-apps"></a>查看非生产应用

默认情况下，应用列表中只显示生产模型驱动应用。

若要查看非生产环境中的模型驱动应用，请选择“设置”菜单 ![设置图标](media/settings_icon.png)，然后打开“显示非生产应用”   。 按照显示的说明操作。

![非生产应用切换](media/non_prod_toggle.png "非生产应用切换")

## <a name="run-an-app"></a>运行应用

若要在移动设备上运行应用，请选择应用磁贴。 如果其他人创建了一个应用并通过电子邮件与你共享，你可以通过选择电子邮件中的链接来运行该应用。

### <a name="run-a-canvas-app"></a>运行画布应用

如果这是你第一次使用 Power Apps 移动应用运行画布应用，屏幕将显示轻扫手势。

#### <a name="close-a-canvas-app"></a>关闭画布应用

用手指从应用的左边缘扫至右边缘可关闭该应用。 在 Android 设备上，还可以按“后退”按钮，再确认要退出应用。

![关闭应用](media/swipe.gif "关闭应用")

#### <a name="pinch-and-zoom-in-on-a-canvas-app"></a>捏合手指放大画布应用

![使用捏合手势进行缩放](media/pinchtozoom.jpg "使用捏合手势进行缩放")

#### <a name="give-consent-to-a-canvas-app"></a>向画布应用授予许可

如果应用需要连接数据源，或须具有相应权限才能使用设备功能（例如照相机或定位服务），必须先确认连接或予以同意，才能使用应用。 通常情况下，只会在首次运行应用时看到提示。

![同意](media/give_consent_canvas.jpg "同意")

### <a name="run-a-model-driven-app"></a>运行模型驱动应用 

下图显示了登录后模式驱动应用屏幕的示例。 要了解如何使用在 Power Apps 移动应用上运行的模型驱动应用，请参阅[有关在 Power Apps 移动应用上运行的模型驱动应用的用户指南](use-custom-model-driven-app-on-mobile.md)。 

![模型驱动应用主页](media/model-driven-app-opened.png "模型驱动应用主页")

#### <a name="give-consent-to-a-model-driven-app"></a>同意模型驱动应用

如果应用需要连接数据源，或须具有相应权限才能使用设备功能（例如照相机或定位服务），必须先确认连接或予以同意，才能使用应用。 通常情况下，只会在首次使用应用时看到提示。

![同意](media/give_consent.png "同意")

#### <a name="close-a-model-drive-app"></a>关闭模型驱动应用

选择站点地图 ![站点地图图标](media/pa_mobile_sitemap_icon.png "站点地图图标")，然后选择“应用”  。

![关闭模型驱动应用](media/pa_mobile_close_app.png "关闭模型驱动应用")

## <a name="known-issues"></a>已知问题

我们仍在解决一些已知问题，并将随着时间的推移发布修复程序。 请确保在最新的预览版本可用时立即手动更新到该版本。 

一些已知问题包括：

- 在脱机模式下打开 Power Apps 应用时，应用列表中不显示任何应用
- 模型驱动应用中的图标有时会消失。

