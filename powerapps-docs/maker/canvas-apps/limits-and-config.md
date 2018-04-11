---
title: 系统要求、限制和配置值 | Microsoft Docs
description: PowerApps 的系统要求、限制和配置值
services: ''
suite: PowerApps
documentationcenter: na
author: skjerland
manager: kfile
editor: ''
tags: ''
ms.service: PowerApps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/07/2018
ms.author: sharik
ms.openlocfilehash: 84115ea98ec5d7d0fd60d36fc0cd3cc9196980ff
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="system-requirements-limits-and-configuration-values"></a>系统要求、限制和配置值
本主题包含设备平台和 Web 浏览器要求，以及 PowerApps 的限制和配置值。

## <a name="supported-platforms-for-running-apps-using-the-powerapps-app"></a>支持使用 PowerApps 应用运行应用的平台
| **所需的最低版本** | **推荐版本** |
| --- | --- |
| iOS 9.3 或更高版本 |iOS 10 或更高版本且 RAM 至少为 2GB |
| Android 5 或更高版本 |Android 7 或更高版本且 RAM 至少为 4GB |
| Windows 8.1 或更高版本（仅 PC） |Windows 10 Fall Creators Update 且 RAM 至少为 8GB|

## <a name="supported-browsers-for-running-apps"></a>支持运行应用的浏览器
| **浏览器** | **操作系统** |
| --- | --- |
| Google Chrome（最新版本）<br>（建议） |Windows 7 SP1、8.1 和 10 <br>Android 5 或更高版本 <br>iOS 8 或更高版本<br>macOS |
| Microsoft Edge（最新版本）<br>（建议） |Windows 10 |
| Microsoft Internet Explorer 11（关闭兼容性视图） |Windows 7 SP1、8.1 和 10 |
| Mozilla Firefox（最新版本） |Windows 7 SP1、8.1 和 10 <br> Android 5 或更高版本 <br>iOS 8 或更高版本 <br>macOS |
| Apple Safari（最新版本） |iOS 8 或更高版本 <br>macOS |

## <a name="supported-browsers-for-powerapps-studio-for-web"></a>支持适用于 Web 的 PowerApps Studio 的浏览器
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

| 区域 | 出站 IP |
| --- | --- |
| 亚洲 |52.163.91.227, 52.163.89.40, 52.163.89.65, 52.163.95.29, 13.75.89.9, 13.75.91.198, 13.75.92.202, 13.75.92.124 |
| 澳大利亚 |13.77.7.172, 13.70.191.49, 13.70.189.7, 13.70.187.251, 13.70.82.210, 13.73.203.158, 13.73.207.42, 13.73.205.35 |
| 加拿大 |52.233.30.222, 52.233.30.148, 52.233.30.199, 52.233.29.254, 52.232.130.205, 52.229.126.118, 52.229.126.28, 52.229.123.56 |
| 欧洲 |52.166.241.149, 52.166.244.232, 52.166.245.173, 52.166.243.169, 40.69.45.126, 40.69.45.11, 40.69.45.93, 40.69.42.254 |
| 印度 |52.172.54.172, 52.172.55.107, 52.172.55.84, 52.172.51.70, 52.172.158.185, 52.172.159.100, 52.172.158.2, 52.172.155.245 |
| 日本 |104.214.137.186, 104.214.139.29, 104.214.140.23, 104.214.138.174, 13.78.85.193, 13.78.84.73, 13.78.85.200, 13.78.86.229 |
| 美国 |104.43.232.28, 104.43.232.242, 104.43.235.249, 104.43.234.211, 52.160.93.247, 52.160.91.66, 52.160.92.131, 52.160.95.100, 40.117.101.91, 40.117.98.246, 40.117.101.120, 40.117.100.191 |
| 美国（提前访问） |52.161.26.191, 52.161.27.42, 52.161.29.40, 52.161.26.33, 13.66.213.240, 13.66.214.51, 13.66.210.166, 13.66.213.29 |

## <a name="required-services"></a>所需的服务
此列表标识了 PowerApps Studio 所谈及的所有服务及其用途。 你的网络**不应**阻止这些服务。

| 域 | 协议 | 使用情况 |
| --- | --- | --- |
| management.azure.com |https |RP |
| msmanaged-na.azure-apim.net |https |连接器运行时/API |
| login.microsoft.com<br>login.windows.net<br>login.microsoftonline.com<br>secure.aadcdn.microsoftonline-p.com |https |ADAL |
| graph.microsoft.com<br>graph.windows.net |https |Azure Graph - 用于获取用户信息（例如个人资料照片） |
| gallery.azure.com |https |示例和模板应用 |
| *.azure-apim.net |https |API 中心 - 每个区域设置的不同子域 |
| *.powerapps.com |https |WebAuth + 门户 |
| *.azureedge.net |https |WebAuth |
| *.blob.core.windows.net |https |Blob 存储 |
| vortex.data.microsoft.com |https |遥测 |
