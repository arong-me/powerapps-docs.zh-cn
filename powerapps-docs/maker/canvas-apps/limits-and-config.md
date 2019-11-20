---
title: 画布应用的系统要求、限制和配置值 | Microsoft Docs
description: PowerApps 中内置的画布应用的系统要求、限制和配置值
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/30/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1c8591790fe14d184f5d5e4ef5fc79ff0bfe0e2a
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2019
ms.locfileid: "74177900"
---
# <a name="system-requirements-limits-and-configuration-values-for-canvas-apps"></a>画布应用的系统要求、限制和配置值
本主题包含设备平台和 Web 浏览器要求，以及 PowerApps 的限制和配置值。

## <a name="supported-platforms-for-running-canvas-apps-using-the-powerapps-app"></a>支持使用 PowerApps 应用运行画布应用的平台

| **所需的最低版本** | **推荐版本** |
| --- | --- |
| iOS 12 or later |iOS 12 or later|
| Android 7 or later |Android 7 or later |
| Windows 8.1 或更高版本（仅 PC） |Windows 10 Fall Creators Update 且 RAM 至少为 8GB|

> [!NOTE]
> We currently don't support new features on Windows platform for PowerApps app. Features such as the Improved Common Data Service option and guest access are not available on this platform. We recommend using a web player on Windows to leverage the full set of capabilities. Updates to the PowerApps app for Windows platform will be announced in future.

## <a name="supported-browsers-for-running-canvas-apps"></a>支持运行画布应用的浏览器

| **浏览器** | **操作系统** |
| --- | --- |
| Google Chrome（最新版本）<br>（建议） |Windows 7 SP1、8.1 和 10 <br>Android 5 或更高版本 <br>iOS 8 或更高版本<br>macOS |
| Microsoft Edge（最新版本）<br>（建议） |Windows 10 |
| Microsoft Internet Explorer 11（关闭兼容性视图） |Windows 7 SP1、8.1 和 10 |
| Mozilla Firefox（最新版本） |Windows 7 SP1、8.1 和 10 <br> Android 5 或更高版本 <br>iOS 8 或更高版本 <br>macOS |
| Apple Safari（最新版本） |iOS 8 或更高版本 <br>macOS |

## <a name="supported-browsers-for-powerapps-studio"></a>支持 PowerApps Studio 的浏览器

| **浏览器** | **操作系统** |
| --- | --- |
| Google Chrome（最新版本）<br>（建议） |Windows 7 SP1、8.1 和 10 <br>macOS |
| Microsoft Edge（最新版本）<br>（建议） |Windows 10 |
| Microsoft Internet Explorer 11（关闭兼容性视图） |Windows 7 SP1、8.1 和 10 |

## <a name="request-limits"></a>请求限制
这些限制适用于每个单独的传出请求：

| 名称 | 限制 |
| --- | --- |
| 超时 |180 秒 |
| 重试尝试次数 |4 |

> [!NOTE]
> 重试值可能会因具体情况而异。 对于某些错误条件，不需要重试。

## <a name="ip-addresses"></a>IP 地址
PowerApps 请求使用的 IP 地址取决于该应用所在[环境](../../administrator/environments-overview.md)的区域。 我们未发布适用于 PowerApps 方案的完全限定的域名。

通过应用连接的 API（例如 SQL API 或 SharePoint AIP）的调用来自本主题后续部分中所指定的 IP 地址。

举例来说，如果必须要为 Azure SQL 数据库指定 IP 地址的允许列表，则应使用以下地址。

> [!IMPORTANT]
>   如果具有现有配置，请尽快于 2018 年 9 月 30 日前更新这些配置，以便它们包括和匹配此 PowerApps 应用所在区域列表中的 IP 地址。

| 区域 | 出站 IP |
| --- | --- |
| 亚洲 | 13.75.36.64 - 13.75.36.79, 13.67.8.240 - 13.67.8.255, 52.175.23.169, 52.187.68.19 |
| 澳大利亚  | 13.70.72.192 - 13.70.72.207, 13.72.243.10, 13.77.50.240 - 13.77.50.255, 13.70.136.174 |
| Brazil | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| 加拿大 | 13.71.170.208 - 13.71.170.223, 13.71.170.224 - 13.71.170.239, 52.237.24.126, 40.69.106.240 - 40.69.106.255, 52.242.35.152|
| 欧洲 | 13.69.227.208 - 13.69.227.223, 52.178.150.68, 13.69.64.208 - 13.69.64.223, 52.174.88.118, 137.117.161.181|
| 印度  | 104.211.81.192 - 104.211.81.207, 52.172.211.12, 40.78.194.240 - 40.78.194.255, 13.71.125.22, 104.211.146.224 - 104.211.146.239, 104.211.189.218 |
| 日本 | 13.78.108.0 - 13.78.108.15, 13.71.153.19, 40.74.100.224 - 40.74.100.239, 104.215.61.248 |
| 南美洲 | 191.233.203.192 - 191.233.203.207, 104.214.19.48 - 104.214.19.63, 13.65.86.57, 104.41.59.51 |
| United Kingdom | 51.140.148.0 - 51.140.148.15, 51.140.80.51, 51.140.211.0 - 51.140.211.15, 51.141.47.105 |
| 美国 | 13.89.171.80 - 13.89.171.95, 52.173.245.164, 40.71.11.80 - 40.71.11.95, 40.71.249.205, 40.70.146.208 - 40.70.146.223, 52.232.188.154, 52.162.107.160 - 52.162.107.175, 52.162.242.161, 40.112.243.160 - 40.112.243.175, 104.42.122.49 |
| 美国（提前访问）  | 13.71.195.32 - 13.71.195.47, 52.161.102.22, 13.66.140.128 - 13.66.140.143, 52.183.78.157 |

## <a name="required-services"></a>所需的服务
此列表标识了 PowerApps Studio 所谈及的所有服务及其用途。 你的网络**不应**阻止这些服务。

| 域 | 协议 | 使用情况 |
| --- | --- | --- |
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |连接器运行时/API |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph - For getting user info (e.g., profile photo) |
| gallery.azure.com |https |示例和模板应用 |
| \*.azure-apim.net |https |API 中心 - 每个区域设置的不同子域 |
| \*.powerapps.com |https | create.powerapps.com, make.powerapps.com, content.powerapps.com, and make.powerapps.com |
| \*.azureedge.net |https | create.powerapps.com, make.powerapps.com, content.powerapps.com, and make.powerapps.com |
| \*.blob.core.windows.net |https | Blob 存储 |
| \*.flow.microsoft.com | https | create.powerapps.com, make.powerapps.com, content.powerapps.com, and make.powerapps.com |
| *.dynamics.com | https | Common Data Service |
| vortex.data.microsoft.com |https |遥测 |
| localhost | https | PowerApps Mobile

> [!NOTE]
> 如果你使用的是 VPN，则必须将其配置为从 PowerApps Mobile 的隧道中排除 localhost。

## <a name="size-limits"></a>Size limits

You can find information about size limits on text, hyperlinks, images, and media in [Data types](functions/data-types.md#text-hyperlink-image-and-media).

## <a name="powerapps-per-app-plan"></a>PowerApps per app plan

PowerApps per app plan allows individual users to run 2 applications on a single portal for a specific business scenario based on the full capabilities of PowerApps. This plan provides an easy way for users to get started with the platform before broader scale adoption.

After an admin allocates PowerApps per app plan to an environment, they're assigned to unlicensed users when an app in that environment is shared with them. You can see how an admin allocates per app plans [here](https://docs.microsoft.com/power-platform/admin/capacity-add-on).

Follow these steps to turn off the assigning per app plans for users when an app is shared with them:

- Choose the **App**.
- Select **Settings**.
- Change the **Auto assign per app passes** toggle under **Pass assignment**.

The **Auto assign per app passes** toggle appears in all app setting.

> [!NOTE]
> Disabling the per app plan is currently available for only canvas apps.  Model-driven apps and Portals will have this ability in the future.
>
> The ability to control per app plan assignment for an app is only available for apps that are in an environment that had Per app plans allocated in the [Power Platform Admin center](https://admin.powerplatform.microsoft.com).  

### <a name="app-settings"></a>App Settings

![Canvas app settings](./media/limits-and-config/app_settings.png "Canvas app settings")

### <a name="pass-assignment"></a>Pass assignment

![Canvas app settings pass assignment](./media/limits-and-config/app_settings_pass_assignment.png "Canvas app settings pass assignment")
