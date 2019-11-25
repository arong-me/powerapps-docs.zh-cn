---
title: 更改门户的基础 URL | MicrosoftDocs
description: 了解如何更改门户的基础 URL。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: cfc2fd0ca753aebfe7bc77b73c7e7ec1ca011387
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2709967"
---
# <a name="change-the-base-url-of-a-portal"></a>更改门户的基础 URL

您可以在配置门户后更改门户的基础 URL。 例如，如果您在配置门户时选择 `contosocommunity.microsoftcrmportals.com` 作为基础 URL，则可以在以后将其更改为 `contosocommunityportal.microsoftcrmportals.com` 以满足您的要求。

> [!NOTE]
> 更改门户的基础 URL 后，之前的 URL 无法再访问，其可由其他客户用于他们的门户。

1.  打开 [PowerApps 门户管理中心](admin-overview.md)。

2.  转到**门户操作** > **更改基础 URL**。 

    > [!div class=mx-imgBorder]
    > ![更改门户的基础 URL](../media/change-base-url-action.png "更改门户的基础 URL")

3.  在更改基础 URL 窗口，为门户输入新基础 URL。

    > [!div class=mx-imgBorder]
    > ![指定门户的新的基本 URL](../media/change-base-url.png "指定门户的新的基本 URL")

4.  在确认窗口中选择**更改 URL**。

## <a name="troubleshooting"></a>疑难解答​​

本节提供有关在更改门户的基础 URL 时问题疑难解答的信息。

### <a name="changing-the-base-url-fails"></a>更改基础 URL 失败

如果更改门户的基础 URL 失败，会显示错误，如下图所示：

> [!div class=mx-imgBorder]
> ![更改门户的基本 URL 时出错](../media/change-base-url-error.png "更改门户的基本 URL 时出错")

通常，这是暂时性的错误，您必须选择**更改基础 URL** 来重试更改基础 URL。 如果此问题仍然存在，请与 Microsoft 支持联系。
