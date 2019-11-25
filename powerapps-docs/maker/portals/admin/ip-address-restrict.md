---
title: 使用 IP 地址限制对门户的访问 | MicrosoftDocs
description: 使用 IP 地址限制门户访问的说明。
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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2756112"
---
# <a name="restrict-portal-access-by-ip-address"></a>使用 IP 地址限制门户访问

在设置并可由任何人从计算机访问时，门户是公共的。 现在，您可以从 IP 地址列表限制对您的门户的访问。 例如，政府组织可能希望仅在其公司网络内呈现内容。 商业组织可能希望仅在门户发布后显示门户，而不能在开发过程中显示，以避免任何数据泄漏。

在任何用户生成门户请求时，将根据允许列表对其 IP 地址进行评估。 如果 IP 地址不在列表中，门户将显示网页，并附带 HTTP 403 状态代码。

若要添加或移除 IP 地址，您必须被分派以下任何一个角色：
- Office 365 全局管理员 
-  服务管理员。 详细信息：[使用服务管理员角色来管理您的租户](https://technet.microsoft.com/library/mt793847.aspx)  
- 为门户选择的 Common Data Service 环境的系统管理员

## <a name="add-an-ip-address"></a>添加 IP 地址

若要从一个或一组 IP 地址允许对门户的访问，您可以向列表添加 IP 地址。 这将只允许从添加的 IP 地址列表访问门户。 如果不添加任何 IP 地址，可以从所有 IP 地址访问门户。

在将 IP 地址添加到限制列表后，仅指定的 IP 地址可以访问门户。 如果您尝试从任何其他 IP 地址访问门户，访问将被拒绝，带有 HTTP 403 状态代码的网页将显示。 此网页的内容是静态的，不能修改。

> [!div class=mx-imgBorder]
> ![HTML 403 错误](../media/ip-address-page-error.png "HTML 403 错误")  

> [!NOTE]
> 您必须指定可以由门户访问的公共 IP 地址。 专用 IP 地址不能由门户访问。

1.  打开 [PowerApps 门户管理中心](admin-overview.md)。

2.  转到**设置 IP 地址限制**。 IP 地址列表及其类型将显示。

    > [!div class=mx-imgBorder]
    > ![设置 IP 地址限制](../media/set-up-ip-address-restrict.png "设置 IP 地址限制")

3.  在“设置 IP 地址限制”页上，选择**新增**。

4.  在“添加 IP 地址”窗口中，输入下列值：

    - **选择 IP 地址的类型**：选择 IP 地址是 IPv4 还是 IPv6。

    - **使用 CIDR 表示法指定 IP 地址**：使用 CIDR 表示法指定 IP 地址。 详细信息：[不分类的内部域路由](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing)

      > [!div class=mx-imgBorder]
      > ![添加 IP 地址](../media/add-ip-address.png "添加 IP 地址")    

5.  选择**配置**。

## <a name="remove-an-ip-address"></a>删除 IP 地址

若要从以前允许的 IP 地址中删除对门户的访问，可以从列表中删除该 IP 地址。 如果删除了所有 IP 地址，可以从所有 IP 地址访问门户。

1.  打开 [PowerApps 门户管理中心](admin-overview.md)。

2.  转到**设置 IP 地址限制**。 IP 地址列表及其类型将显示。

    > [!div class=mx-imgBorder]
    > ![设置 IP 地址限制](../media/set-up-ip-address-restrict.png "设置 IP 地址限制")

3.  选择要删除的 IP 地址旁边的**删除 IP 地址 (x)**。

4.  在确认消息中选择**删除**。

