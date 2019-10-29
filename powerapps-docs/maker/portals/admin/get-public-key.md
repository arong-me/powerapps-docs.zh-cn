---
title: 下载门户的公钥 |MicrosoftDocs
description: 了解如何下载门户的公钥。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 39e909acb325bd870f73e16a72da78b4bec07c79
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975969"
---
# <a name="download-public-key-of-portal"></a>下载门户公钥

门户的公钥用于为 Dynamics 365 中的模型驱动应用配置实时协助，以使用门户的经过身份验证的访问者。 [现场助手](https://www.cafex.com/en/products/live-assist-dynamics-365/)CafeX 提供了一个聊天解决方案，用户可以通过该解决方案将实时聊天助手嵌入到门户中。 有关如何使用公钥在门户上嵌入聊天的详细信息，请[访问 Dynamics Customer 门户中经过身份验证的用户](https://www.liveassistfor365.com/en/support/authenticated-visitors-in-the-dynamics-customer-portal/)

1. 打开[PowerApps 门户管理中心](admin-overview.md)。

2.  转到**门户操作** > **获取公钥**"。 将显示密钥。

    > [!div class=mx-imgBorder]
    > ![获取门户的公钥](../media/get-public-key.png "获取门户的公钥")

3.  选择 "**下载为文本**" 以下载文本文件中的密钥。

或者，还可以通过转到 URL 来获取公钥： `<portal_base_URL>/_ services/auth/publickey` 

> [!NOTE]
> 如果当前正在设置门户，或者组织中未完成包安装，则当你尝试下载公钥时，会显示错误。 您必须等到门户预配完成并且门户启动并运行。
