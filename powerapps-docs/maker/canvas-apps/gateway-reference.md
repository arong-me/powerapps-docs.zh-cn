---
title: 本地数据网关 |Microsoft Docs
description: 本文概述了电源应用的本地数据网关。
author: arthiriyer
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/16/2019
ms.author: arthii
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4dc5afc49ba1ee38889d0eb6d86bf1cde6687135
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732209"
---
# <a name="what-is-an-on-premises-data-gateway"></a>什么是本地数据网关？

本地数据网关充当桥，以提供本地数据（不在云中的数据）和几个 Microsoft 云服务之间的快速、安全的数据传输。 这些云服务包括 Power BI、电源应用、电源自动化、Azure Analysis Services 和 Azure 逻辑应用。 通过使用网关，组织可以在其本地网络中保留数据库和其他数据源，但在云服务中安全地使用本地数据。

## <a name="how-the-gateway-works"></a>网关工作原理

![网关概述](media/gateway-reference/on-premises-data-gateway.png)

有关网关工作原理的详细信息，请参阅[本地数据网关体系结构](/data-integration/gateway/service-gateway-onprem-indepth)。

## <a name="types-of-gateways"></a>网关类型

有两种不同类型的网关，每种类型都适用于不同的方案：

- **本地数据网关**允许多个用户连接到多个本地数据源。 可以将本地数据网关与所有支持的服务结合使用，只需要安装单个网关即可。 此网关非常适合包含多个用户访问多个数据源的复杂方案。

- **本地数据网关（个人模式）** 允许一位用户连接到源，并且不能与其他用户共享。 本地数据网关（个人模式）只能与 Power BI 一起使用。 此网关非常适合只是创建报表的人员，无需与其他人共享任何数据源。

## <a name="use-a-gateway"></a>使用网关

使用网关需要四个主要步骤。

1. 在本地计算机上[下载并安装网关](/data-integration/gateway/service-gateway-install)。
2. 根据防火墙和其他网络要求[配置](/data-integration/gateway/service-gateway-app)网关。
3. 添加还可以管理和管理其他网络要求的[网关管理员](/data-integration/gateway/service-gateway-manage)。
4. 出现错误时对网关[进行故障排除](/data-integration/gateway/service-gateway-tshoot)。

## <a name="next-steps"></a>后续步骤

- [安装本地数据网关](/data-integration/gateway/service-gateway-install)