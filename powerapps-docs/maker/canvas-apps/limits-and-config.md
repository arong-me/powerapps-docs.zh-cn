---
title: 画布应用的系统要求、限制和配置值 | Microsoft Docs
description: 在 Power Apps 中内置的画布应用的系统要求、限制和配置值
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
ms.openlocfilehash: 18abbc91426c74b48aefd51f1867d8bff806d718
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404566"
---
# <a name="system-requirements-limits-and-configuration-values-for-canvas-apps"></a>画布应用的系统要求、限制和配置值
本主题包含设备平台和 web 浏览器要求，以及画布应用的限制和配置值。

## <a name="supported-platforms-for-running-canvas-apps-using-the-power-apps-mobile-app"></a>使用 Power Apps 移动应用运行画布应用的受支持平台

| **所需的最低版本** | **推荐版本** |
| --- | --- |
| iOS 12 或更高版本 |iOS 12 或更高版本|
| Android 7 或更高版本 |Android 7 或更高版本 |
| Windows 8.1 或更高版本（仅 PC） |Windows 10 Fall Creators Update 且 RAM 至少为 8GB|

> [!NOTE]
> 目前，我们不支持 Windows 平台上适用于[Power Apps 移动应用](/powerapps/user/run-app-client)的新功能。 改进的 Common Data Service 选项和来宾访问等功能在此平台上不可用。 建议在 Windows 上使用 web 播放器来利用完整的功能集。 适用于 Windows 平台的 Power Apps 移动应用的更新将在将来公布。

## <a name="supported-browsers-for-running-canvas-apps"></a>支持运行画布应用的浏览器

| **浏览器** | **操作系统** |
| --- | --- |
| Google Chrome（最新版本）<br>（推荐） |Windows 7 SP1、8.1 和 10 <br>Android 5 或更高版本 <br>iOS 8 或更高版本<br>macOS |
| Microsoft Edge（最新版本）<br>（推荐） |Windows 10 |
| Microsoft Internet Explorer 11（关闭兼容性视图） |Windows 7 SP1、8.1 和 10 |
| Mozilla Firefox（最新版本） |Windows 7 SP1、8.1 和 10 <br> Android 5 或更高版本 <br>iOS 8 或更高版本 <br>macOS |
| Apple Safari（最新版本） |iOS 8 或更高版本 <br>macOS |

## <a name="supported-browsers-for-power-apps-studio"></a>支持的 Power Apps Studio 浏览器

| **浏览器** | **操作系统** |
| --- | --- |
| Google Chrome（最新版本）<br>（推荐） |Windows 7 SP1、8.1 和 10 <br>macOS |
| Microsoft Edge（最新版本）<br>（推荐） |Windows 10 |
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
来自电源应用的请求使用的 IP 地址取决于应用所在[环境](../../administrator/environments-overview.md)的区域。 我们不会发布适用于电源应用方案的完全限定的域名。

通过应用连接的 API（例如 SQL API 或 SharePoint AIP）的调用来自本主题后续部分中所指定的 IP 地址。

举例来说，如果必须要为 Azure SQL 数据库指定 IP 地址的允许列表，则应使用以下地址。

> [!IMPORTANT]
>   如果你有现成的配置，请在2018年9月30日之前尽快更新它们，以使它们包括并匹配此列表中存在适用于你的 Power Apps 应用的区域的 IP 地址。

| 区域 | 出站 IP |
| --- | --- |
| 亚洲 | 13.75.36.64-13.75.36.79、13.67.8.240-13.67.8.255、52.175.23.169、52.187.68.19、127.0.0。1 |
| 澳大利亚  | 13.70.72.192-13.70.72.207，13.72.243.10，13.77.50.240-13.77.50.255，13.70.136.174，127.0.0。1 |
| 巴西 | 191.233.203.192-191.233.203.207、104.214.19.48-104.214.19.63、13.65.86.57、104.41.59.51、127.0.0。1 |
| 加拿大 | 13.71.170.208-13.71.170.223，13.71.170.224-13.71.170.239，52.237.24.126，40.69.106.240，40.69.106.255，52.242.35.152，127.0.0。1|
| 欧洲 | 13.69.227.208-13.69.227.223，52.178.150.68，13.69.64.208-13.69.64.223，52.174.88.118，137.117.161.181，127.0.0。1|
| 印度  | 104.211.81.192-104.211.81.207、52.172.211.12、40.78.194.240-40.78.194.255、13.71.125.22、104.211.146.224-104.211.146.239、104.211.189.218、127.0.0。1 |
| 日本 | 13.78.108.0-13.78.108.15，13.71.153.19，40.74.100.224-40.74.100.239，104.215.61.248，127.0.0。1 |
| 南美洲 | 191.233.203.192-191.233.203.207、104.214.19.48-104.214.19.63、13.65.86.57、104.41.59.51、127.0.0。1 |
| 英国 | 51.140.148.0-51.140.148.15，51.140.80.51，51.140.211.0-51.140.211.15，51.141.47.105，127.0.0。1 |
| 美国 | 13.89.171.80-13.89.171.95、52.173.245.164、40.71.11.80-40.71.11.95、40.71.249.205、40.70.146.208-40.70.146.223、52.232.188.154、52.162.107.160-52.162.107.175、52.162.242.161、40.112.243.160、40.112.243.175、104.42.122.49、127.0.0。1 |
| 美国（提前访问）  | 13.71.195.32-13.71.195.47，52.161.102.22，13.66.140.128-13.66.140.143，52.183.78.157，127.0.0。1 |

## <a name="required-services"></a>所需的服务
此列表标识了 Power Apps Studio 讨论的所有服务及其使用情况。 你的网络**不应**阻止这些服务。

| 域 | 协议 | 使用 |
| --- | --- | --- |
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |连接器运行时/API |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph-用于获取用户信息（例如，个人资料照片） |
| gallery.azure.com |https |示例和模板应用 |
| \*. azure-apim.net |https |API 中心 - 每个区域设置的不同子域 |
| \*. powerapps.com |https | create.powerapps.com、make.powerapps.com、content.powerapps.com 和 make.powerapps.com |
| \*. azureedge.net |https | create.powerapps.com、make.powerapps.com、content.powerapps.com 和 make.powerapps.com |
| \*. blob.core.windows.net |https | Blob 存储 |
| \*. flow.microsoft.com | https | create.powerapps.com、make.powerapps.com、content.powerapps.com 和 make.powerapps.com |
| *. dynamics.com | https | Common Data Service |
| vortex.data.microsoft.com |https |遥测 |
| localhost | https | Power Apps Mobile

> [!NOTE]
> 如果使用的是 VPN，则必须将其配置为从适用于移动设备的隧道上排除 localhost。

## <a name="size-limits"></a>大小限制

可以在[数据类型](functions/data-types.md#text-hyperlink-image-and-media)中找到有关文本、超链接、图像和媒体的大小限制的信息。

## <a name="power-apps-per-app-plan"></a>每个应用计划的电源应用

此信息现已在 Power Platform 管理员指南的[每个应用计划](/power-platform/admin/signup-for-powerapps-admin#power-apps-per-app-plan)部分中提供。
