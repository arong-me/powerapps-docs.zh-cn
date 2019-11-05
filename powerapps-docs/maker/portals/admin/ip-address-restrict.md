---
title: 使用 IP 地址限制对门户的访问 |MicrosoftDocs
description: 按 IP 地址限制门户访问权限的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: da8e6ac6d4e86a12ba196393073706c3705e4a92
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543017"
---
# <a name="restrict-portal-access-by-ip-address"></a>按 IP 地址限制门户访问

此门户在由任何计算机的任何用户预配和访问时是公共的。 现在可以从 IP 地址列表限制对门户的访问。 例如，政府组织可能希望仅在企业网络中显示其内容。 商业组织可能只希望在发布时显示门户，而不是在开发过程中显示，以避免任何数据泄露。

从任何用户生成对门户的请求时，将根据允许列表评估其 IP 地址。 如果 IP 地址不在列表中，门户会显示一个包含 HTTP 403 状态代码的网页。

若要添加或删除 IP 地址，必须分配有以下角色之一：
- Office 365 全局管理员 
- 服务管理员。 详细信息：[使用 "服务管理员" 角色管理租户](https://technet.microsoft.com/library/mt793847.aspx)  
- 为门户选择的 Common Data Service 环境的系统管理员

## <a name="add-an-ip-address"></a>添加 IP 地址

若要允许从 IP 地址或一组 IP 地址访问门户，可以将 IP 地址添加到列表。 这只允许从添加的 IP 地址列表访问门户。 如果未添加任何 IP 地址，则将从所有 IP 地址访问该门户。

向限制列表添加 IP 地址后，只能通过指定的 IP 地址访问门户。 如果尝试从任何其他 IP 地址访问门户，将拒绝访问，并显示带有 HTTP 403 状态代码的网页。 此网页的内容是静态的，不能修改。

> [!div class=mx-imgBorder]
> ![HTML 403 错误](../media/ip-address-page-error.png "HTML 403 错误")  

> [!NOTE]
> 你必须指定门户可以访问的公共 IP 地址。 门户无法访问专用 IP 地址。

1.  打开[PowerApps 门户管理中心](admin-overview.md)。

2.  请参阅**设置 IP 地址限制**。 将显示 IP 地址及其类型的列表。

    > [!div class=mx-imgBorder]
    > ![设置 IP 地址限制](../media/set-up-ip-address-restrict.png "设置 IP 地址限制")

3.  在 "设置 IP 地址限制" 页上，选择 "**新增**"。

4.  在 "添加 IP 地址" 窗口中，输入以下值：

    - **选择 ip 地址类型**：选择 ip 地址是 IPv4 还是 IPv6。

    - **指定 cidr 表示法中的 ip 地址**：以 cidr 表示法指定 ip 地址。 详细信息：无[类别域间路由](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

      > [!div class=mx-imgBorder]
      > ![添加 IP 地址](../media/add-ip-address.png "添加 IP 地址")    

5.  选择 "**配置**"。

## <a name="remove-an-ip-address"></a>删除 IP 地址

若要从以前允许的 IP 地址中删除对门户的访问权限，可以从列表中删除该 IP 地址。 如果删除了所有 IP 地址，则可以从所有 IP 地址访问该门户。

1.  打开[PowerApps 门户管理中心](admin-overview.md)。

2.  请参阅**设置 IP 地址限制**。 将显示 IP 地址及其类型的列表。

    > [!div class=mx-imgBorder]
    > ![设置 IP 地址限制](../media/set-up-ip-address-restrict.png "设置 IP 地址限制")

3.  选择 "删除要删除的 IP 地址" 旁边**的 ip 地址（x）** 。

4.  在确认消息中选择 "**删除**"。

