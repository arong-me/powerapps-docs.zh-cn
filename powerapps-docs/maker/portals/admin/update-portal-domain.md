---
title: 从 Dynamics 365 域更新为 Power Apps 门户域 | MicrosoftDocs
description: 有关从 Dynamics 365 域更新为 Power Apps 门户域的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: cddb04f048c9af2a3c5873577a36a3929d6c6a34
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978577"
---
# <a name="update-to-power-apps-portals-domain"></a>更新为 Power Apps 门户域

如果使用较低版本的门户加载项预配门户，门户的域将为 `microsoftcrmportals.com`。 在此 Power Apps 门户版本中，现在可将 Dynamics 365 域 `microsoftcrmportals.com` 更新为 Power Apps 门户域 `powerappsportals.com`。

> [!NOTE]
> `microsoftcrmportals.com` 域已弃用，只有使用旧版门户加载项的门户才支持。 弃用期间，此功能在该版本正式删除前将继续有效并完全受支持。 此弃用通知可能跨几年。

1. 打开 [Power Apps 门户管理中心](admin-overview.md)。

2. 转到**门户操作** > **更新为 Power Apps 门户域**。

    > [!div class=mx-imgBorder]
    > ![更新为 Power Apps 门户域](../media/update-portal-domain-button.png "更新为 Power Apps 门户域")

3. 在**门户 URL** 中，输入网站的地址，然后选择**确定**。

    > [!div class=mx-imgBorder]
    > ![更新为 Power Apps 门户域](../media/update-portal-domain.png "更新为 Power Apps 门户域")

如果已在使用 Power Apps 门户域，但希望恢复为原来的域，可以使用**更新为 Power Apps 门户域**操作恢复为原来的域。 在此情况下，将显示如下消息：

> [!div class=mx-imgBorder]
> ![恢复为原来的域](../media/revert-portal-domain.png "恢复为原来的域")
