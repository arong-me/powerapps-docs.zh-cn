---
title: "限制和配置 | Microsoft 文档"
description: "PowerApps 的限制和配置值"
services: 
suite: PowerApps
documentationcenter: na
author: skjerland
manager: anneta
editor: 
tags: 
ms.service: PowerApps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/06/2017
ms.author: sharik
ms.openlocfilehash: 337f3fc00fe52e0008190e2144f21f40d1632f52
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="limits-and-configuration-in-microsoft-powerapps"></a>Microsoft PowerApps 中的限制和配置
本主题包含有关 PowerApps 的当前限制和配置的详细信息。

## <a name="requests"></a>请求
这些限制适用于每个单独的传出请求：

| 名称 | 限制 |
| --- | --- |
| 超时 |180 秒 |
| 重试尝试次数 |4 |

注意：重试值可能会有所不同。 对于某些错误条件，重试不起作用。

## <a name="ip-addresses"></a>IP 地址
PowerApps 请求使用的 IP 地址取决于该应用所在[环境](environments-overview.md)的区域。 我们未发布适用于 PowerApps 方案的完全限定的域名。

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

