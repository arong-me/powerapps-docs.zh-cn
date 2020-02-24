---
title: 下载门户的公钥 | MicrosoftDocs
description: 了解如何下载门户的公钥。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 8b74e1943e6a356884be167be033b7e633660b40
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977873"
---
# <a name="download-public-key-of-portal"></a>下载门户公钥

门户的公钥用于在 Dynamics 365 中为模型驱动应用程序配置 Live Assist 来处理通过身份验证的门户访问者。 [Live Assist](https://www.cafex.com/en/products/live-assist-dynamics-365/) 由 CafeX 提供，通过哪些用户可以在他们的门户中嵌入实时聊天助手来提供聊天解决方案。 有关如何使用公钥在门户中嵌入聊天的更多信息：[Dynamics 客户门户中通过身份验证的访问者](https://www.liveassistfor365.com/en/support/authenticated-visitors-in-the-dynamics-customer-portal/)

1. 打开 [Power Apps 门户管理中心](admin-overview.md)。

2.  转到**门户操作** > **获取公钥**。 然后将显示密钥。

    > [!div class=mx-imgBorder]
    > ![获取门户公钥](../media/get-public-key.png "获取门户公钥")

3.  选择**下载为文本**在文本文件中下载密钥。

此外，您也可以通过转到 URL：`<portal_base_URL>/_ services/auth/publickey` 获取公钥 

> [!NOTE]
> 如果组织中当前正在设置门户或包安装未完成，如果您尝试下载公钥将显示错误。 您必须等待门户设置完成并且门户启动并运行。
