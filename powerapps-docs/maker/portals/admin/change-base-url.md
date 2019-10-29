---
title: 更改门户的基 URL |MicrosoftDocs
description: 了解如何更改门户的基 URL。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: cfc2fd0ca753aebfe7bc77b73c7e7ec1ca011387
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977464"
---
# <a name="change-the-base-url-of-a-portal"></a>更改门户的基 URL

你可以在设置门户的基础 URL 之后更改其基 URL。 例如，如果在设置门户时选择 "`contosocommunity.microsoftcrmportals.com` 作为基 URL"，则稍后可以将其更改为 "`contosocommunityportal.microsoftcrmportals.com` 以满足你的要求。

> [!NOTE]
> 更改门户的基本 URL 后，将无法再访问旧的 URL，其他客户也可以使用该 url 作为门户。

1.  打开[PowerApps 门户管理中心](admin-overview.md)。

2.  转到**门户操作** > **更改基 URL**。 

    > [!div class=mx-imgBorder]
    > ![更改门户的门户](../media/change-base-url-action.png "更改")基 url

3.  在 "更改基 URL" 窗口中，输入门户的新基 URL。

    > [!div class=mx-imgBorder]
    > ![指定门户的新基 url](../media/change-base-url.png "指定门户的新基 url")

4.  在确认窗口中选择 "**更改 URL** "。

## <a name="troubleshooting"></a>故障排除

本部分提供有关在更改门户的基 URL 时解决问题的信息。

### <a name="changing-the-base-url-fails"></a>更改基 URL 失败

如果更改门户的基 URL 失败，会显示一个错误，如下图所示：

> [!div class=mx-imgBorder]
> 更改(../media/change-base-url-error.png "门户基 url 时")![更改门户网站错误的基 url 时出错]

通常，这些是暂时性错误，你必须选择 "**更改基 url** " 来重试更改基 url。 如果问题仍然存在，请联系 Microsoft 支持部门。
