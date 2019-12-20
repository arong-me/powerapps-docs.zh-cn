---
title: 在门户的网页上评级或投票 | MicrosoftDocs
description: 有关如何在门户的网页中启用和管理评级的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/11/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: e32d2e7969481c3aea4ab3abefb5bfc5c48e8852
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2866739"
---
# <a name="rate-or-vote-on-a-webpage-on-a-portal"></a>在门户的网页上评级或投票

评级为用户提供为网页评级或投票的能力。 还支持针对页面上的注释进行评级。 在默认情况下，此功能处于禁用状态，但是可以逐页启用。

评级是自定义的活动，因此使用方式与任何其他活动（电子邮件、电话呼叫，等等）相同。 由于评级是活动，因此可以通过自定义为您所选并呈现在门户上的任何实体（包括自定义实体）显示评级。

## <a name="enable-ratings-for-pages"></a>为页面启用评级

1. 打开[“门户管理”应用](configure-portal.md)。

2. 转至**门户** > **网页**。

3. 选择要在其中启用评级的**网页**。

4. 在**常规**选项卡的**页面选项**下，将**启用评级**设置为**是**。

5. 选择**保存并关闭**。

## <a name="use-ratings"></a>使用评级

对于已启用页面评级并且开发人员已将该控件应用到模板的网页，则用户可根据将控件添加到页面模板时所选的类型使用评级范围或轮询为页面评级。

### <a name="rating-type"></a>评级类型

![评级类型](../media/rating-type.png "评级类型")  

### <a name="vote-type"></a>投票类型

![投票类型](../media/vote-type.png "投票类型")  

## <a name="manage-ratings"></a>管理评级

可以在 Power Apps 门户中查看、修改或删除网页的评级。

1. 打开[“门户管理”应用](configure-portal.md)。

2. 导航到对查看其评级感兴趣的**网页**。

3. 在**相关**选项卡上，选择**活动**。 关联视图列出选择的网页的评级。 在此视图中，用户可修改或删除现有评级。
