---
title: 清除门户的服务器端缓存 |MicrosoftDocs
description: 强制门户立即刷新缓存的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 8351ca8d3befec80a9e97da03ca62980383b01b1
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975992"
---
# <a name="clear-the-server-side-cache-for-a-portal"></a>清除门户的服务器端缓存

作为门户管理员，你可以清除整个门户的服务器端缓存，以便 Common Data Service 中的已更新数据会立即反映到门户中。 Common Data Service 中的更新将以异步模式传递到门户，因此，在 Common Data Service 中更新数据的时间与在门户中显示更新数据的时间之间可能存在延迟。 若要消除此延迟&mdash;例如，当它干扰门户配置时&mdash;可以强制门户立即刷新其缓存。

> [!NOTE]
> 缓存刷新的 SLA （Common Data Service 和门户之间的数据传输）为15分钟。

清除服务器端缓存

1.  以管理员身份登录到门户。

2.  导航到 URL，如下所示： `<portal_path>/_services/about`

3.  选择 "**清除缓存**"。 

服务器端缓存会被删除，并从 Common Data Service 重新加载数据。 请注意，清除门户服务器端缓存会导致门户性能降低，同时从 Common Data Service 重新加载数据。

> [!div class=mx-imgBorder]
> ![清除门户缓存](../media/clear-portal-cache.png "清除门户缓存")
