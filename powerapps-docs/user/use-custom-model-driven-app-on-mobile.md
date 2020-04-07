---
title: 如何在移动设备上使用模型驱动应用 | Microsoft Docs
description: 了解如何在移动设备上使用自定义模型驱动应用。
author: mduelae
manager: kvivek
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
ms.openlocfilehash: 84fe0685f9a128fb0cbbeadfbea01aceaa86cb19
ms.sourcegitcommit: 39f6feb699512e9c2bf71ef1a1238b32b639da02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2020
ms.locfileid: "80530414"
---
# <a name="user-guide-for-model-driven-apps-running-on-the-power-apps-mobile-app"></a>在 Power Apps 移动应用上运行的模型驱动应用的用户指南

[!INCLUDE [cc-beta-prerelease-disclaimer](../includes/cc-beta-prerelease-disclaimer.md)]

使用 Power Apps 移动应用在移动设备上运行模型驱动应用。 要详细了解如何安装和开始使用应用，请参阅[在移动设备上运行画布应用和模型驱动应用](run-canvas-and-model-apps-on-mobile.md)。

> [!IMPORTANT]
> 用于 Dynamics 365 Sales、Dynamics 365 Customer Service 和 Dynamics 365 Field Service 的模型驱动应用<!--For sure this list doesn't include Dynamics 365 Marketing, and Dynamics 365 Project Service Automation? That's the list of model-driven apps according to the Dynamics Style Guide.--> 不在 Power Apps 移动应用中运行。 你此时要使用适用于手机和平板电脑应用的 Dynamics 365。 有关详细信息，请参阅[适用于手机和平板电脑的 Dynamics 365 用户指南](https://docs.microsoft.com/dynamics365/mobile-app/dynamics-365-phones-tablets-users-guide)。

## <a name="home-screen"></a>主屏幕 

可在 Power Apps 移动应用中轻松浏览。 下图显示了主屏幕上主要的导航元素。 

![导航控件，展开的视图](media/pa_mobile_main_nav_android.png "导航控件，展开的视图")

图例：

1. **站点地图**：打开菜单并在应用之间移动，获取你收藏的和最近使用的记录，还可访问设置等等。
2. **搜索**：在 Common Data Service 中搜索应用记录。
3. **快速创建**：创建新记录，并将几乎任何类型的信息快速输入到系统中。
4. **全局命令**：访问管理员自定义的全局命令。
5. **更多**：访问更多适用于正在使用的记录的命令，例如排序、搜索、删除、刷新等。<!--There really are "more"? Or can you end the list at "refresh"?-->
6. **对记录排序**：按字母顺序排序和查看记录。

## <a name="site-map"></a>站点地图 

在主屏幕中，选择站点地图 ![站点地图图标](media/pa_mobile_sitemap_icon.png "站点地图图标") 可访问实体、收藏的或最常用的记录、其他应用以及设置。

   > [!div class="mx-imgBorder"]
   > ![站点地图屏幕](media/pa_mobile_site_map.gif "站点地图屏幕")

下图显示了站点地图屏幕上主要的导航元素。 

![站点地图屏幕](media/pa_mobile_sitemap_android.png "站点地图屏幕")

图例

1. **应用选择器**：打开此菜单可关闭应用并切换到其他应用。
2. **主屏幕**：选择此项可返回到主屏幕。
3. **配置文件**：转到配置文件屏幕注销或重新配置应用。 
4. **最近记录**：查看最近使用的记录的列表。 
5. **固定的记录**：查看并打开你收藏（已固定）的记录。 
6. **实体导航器**：此区域列出了应用中可用的实体。
7. **帮助**：要详细了解如何使用 Power Apps 移动应用，请访问帮助内容。
8. **脱机状态**：在脱机模式下处理数据，即使你未访问 Internet 也能处理。 更多信息：[在移动设备上脱机工作](https://docs.microsoft.com/dynamics365/mobile-app/work-in-offline-mode)
9. **设置**：访问设置。

## <a name="pin-favorite-records"></a>固定收藏的记录

通过“固定的记录”和“最近使用的记录”列表，可快速访问你最近使用或固定到收藏夹的记录   。 使用“最近使用的记录”列表来固定收藏的记录  。  

1. 从站点地图 ![站点地图图标](media/pa_mobile_sitemap_icon.png "站点地图图标")中，选择“最近使用的记录”![最近使用的记录图标](media/pa_mobile_recent_icon.png "“最近使用的记录”图标")  。

2. 在“最近使用的记录”屏幕上，选择记录旁边的图钉图标，将相应记录添加到收藏夹（固定的记录）  。

3. 若要查看新固定的记录，请选择 ![“返回”图标](media/mobile_go_back_icon.png "“返回”图标")，然后选择“固定的记录”![“固定的收藏项”图标](media/mobile_pinned_favs_icon.png "“固定的收藏项”图标")  。

   > [!div class="mx-imgBorder"]
   > ![将记录固定到收藏夹](media/pin_favs.gif "将记录固定到收藏夹")

### <a name="unpin-a-record"></a>取消固定记录

1. 从站点地图 ![站点地图图标](media/pa_mobile_sitemap_icon.png "站点地图图标")中，选择“固定的记录”![“固定的收藏项”图标](media/mobile_pinned_favs_icon.png "“固定的收藏项”图标")  。

2. 选择记录旁边的“删除固定”图标 ![“删除固定”图标](media/pa_mobile_remove_pin_icon.png "“删除固定”图标") 可将其从收藏夹（固定的记录）中删除。

   > [!div class="mx-imgBorder"]
   > ![取消固定记录](media/unpin_favs.gif "取消固定记录")

## <a name="change-views"></a>更改视图

- 在主屏幕中，选择当前视图旁边的向下箭头 ![“更改视图”图标](media/mobile_view_selector_icon.png "“更改视图”图标")，然后选择一个新视图。

   > [!div class="mx-imgBorder"]
   > ![更改视图](media/pa_mobile_change_view.gif "更改视图")

## <a name="add-a-record-quickly"></a>快速添加记录

1. 在主屏幕中，选择“新建”![“创建记录”按钮](media/create-record-button.png "“创建记录”按钮")  。
2. 填写字段，然后选择“保存”  。
3. 创建记录后，可以查看新记录。 

   > [!div class="mx-imgBorder"]
   > ![创建记录](media/pamobile_add_record.gif "创建记录")

-  若要保存并打开创建的记录，请选择“更多”![“更多命令”图标](media/pa_mobile_more_commands_icon.png "“更多命令”图标")，然后选择“保存并打开”   。

- 要保存并创建其他记录，请选择“更多”![“更多命令”图标](media/pa_mobile_more_commands_icon.png "“更多命令”图标")，然后选择“保存并新建”   。

   > [!div class="mx-imgBorder"]
   > ![创建记录](media/pa_mobile_save_create_new.gif "创建记录")

## <a name="view-commands-for-a-record"></a>查看记录的命令

1. 在主屏幕中，打开记录。
2. 在打开的记录上，选择“更多”![“更多记录”命令图标](media/access_record_commands_icon.png "“更多记录命令”图标") 以访问更多命令  。

   > [!div class="mx-imgBorder"]
   > ![记录上的命令](media/pa_mobile_view_record_commands.gif "记录上的命令")

## <a name="edit-a-record"></a>编辑记录

1. 在主屏幕上，打开要编辑的记录。 
2. 编辑完记录后，选择“保存”  。 若要取消所做的更改，请选择“放弃”  。

   > [!div class="mx-imgBorder"]
   > ![编辑记录](media/pa_mobile_edit_record.gif "编辑记录")

## <a name="go-back-to-the-home-screen"></a>返回主屏幕

- 若要在处于记录中时返回主屏幕，请选择“返回”![“返回”图标](media/pa_mobile_back_icon.png "“返回”图标")  。
- 可随时按住“返回”![“返回”图标](media/pa_mobile_back_icon.png "“返回”图标") 来返回主屏幕  。 

   > [!div class="mx-imgBorder"]
   > ![返回主屏幕](media/go_back_home.gif "返回主屏幕")

## <a name="sign-out"></a>注销

从站点地图 ![站点地图图标](media/pa_mobile_sitemap_icon.png "站点地图图标") 中，选择配置文件图标 ![配置文件图标](media/profile_icon.png "站点地图图标")，然后选择“注销”  。
