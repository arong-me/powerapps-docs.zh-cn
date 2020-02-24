---
title: 清除门户的服务器端缓存 | MicrosoftDocs
description: 有关强制门户立即刷新缓存的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: ab1e3a278127105b338893bbbc989774756d3fca
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978269"
---
# <a name="clear-the-server-side-cache-for-a-portal"></a>清除门户的服务器端缓存

作为门户管理员，您可清除整个门户的服务器端缓存，以便从 Common Data Service 更新的数据立即在门户中反映出来。 来自 Common Data Service 的更新以异步模式传递到门户，因此在 Common Data Service 中更新的时间与在门户上显示的更新数据的时间之间可能存在延迟。 若要消除延时 &mdash; 例如当它干扰门户配置时 &mdash; 您可以强制门户立即刷新缓存。

> [!NOTE]
> 缓存刷新（Common Data Service 与门户之间的数据传输）的 SLA 为 15 分钟。

若要清除服务器端缓存

1.  以管理员身份登录到门户。

2.  导航到如下 URL：`<portal_path>/_services/about`

3.  选择**清除缓存**。 

服务器端缓存删除，且从 Common Data Service 重新加载数据。 请注意，清除门户服务器端缓存将暂时导致门户性能低下，因为正从 Common Data Service 重新加载数据。

> [!div class=mx-imgBorder]
> ![清除门户缓存](../media/clear-portal-cache.png "清除门户缓存")
