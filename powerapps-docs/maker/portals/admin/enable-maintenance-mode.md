---
title: 为门户启用维护模式 |MicrosoftDocs
description: 了解如何通过门户启用维护模式。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: e53380c39257645e9056a271226b6f7ef8c8c721
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976061"
---
# <a name="maintenance-mode-for-a-portal"></a>门户的维护模式

有时，你的网站处于计划的维护下，或由于临时服务中断而关闭。 当客户在维护期间访问网站时，可能会遇到不可预知的行为和间歇性的不可用情况。 

作为门户管理员，你可以配置门户以在维护活动正在进行时向客户显示适当的消息（例如，"解决方案包正在升级。"）可以通过在门户中启用维护模式来利用此功能。 启用维护模式后，将显示一条消息，并限制客户浏览除 `<portal URL>/_services/about` 页面之外的任何网页。

> [!div class=mx-imgBorder]
> ![默认维护模式页面](../media/default-maint-page.png "默认维护模式页面")

## <a name="enable-maintenance-mode"></a>启用维护模式

你可以在门户上启用维护模式，以提供一致的消息，而不是在你的网站处于计划的维护下时处理无法预测的行为。 这将为门户用户提供更好的体验。

1. 打开[PowerApps 门户管理中心](admin-overview.md)。

3.  > **启用维护模式**，请参阅**门户操作**。

    > [!div class=mx-imgBorder]
    > ![启用维护模式](../media/enable-maint-mode-button.png "启用维护模式")

4. 在 "**启用维护模式**" 窗口中，输入以下值：
    - **选择启用维护模式时要使用的页面**：选择以下值之一：

        - **默认页面**：如果希望在启用维护模式时显示默认页面，请选择此值。 默认情况下，此选项处于选中状态。

        - **自定义页面**：如果希望在启用维护模式时显示自定义 HTML 页面，请选择此值。

    - **自定义页面 URL**：只有当您选择用于显示自定义 HTML 页面的选项时，才会启用此字段。 您必须确保您提供的页面 URL 可公开访问。 如果无法访问指定的 HTML 页面，将显示默认页，其中包含对管理员的说明。

5. 选择 "**启用**"。 当维护模式处于启用状态时，门户将重新启动并在几分钟内不可用。 

    > [!div class=mx-imgBorder]
    > ![启用维护模式设置](../media/enable-maint-mode.png "启用维护模式设置")

## <a name="configure-or-disable-maintenance-mode"></a>配置或禁用维护模式

为门户启用维护模式后，可以更新维护模式设置并选择其他页面。

你还可以选择在网站的计划维护完成时在门户上禁用维护模式。 门户用户现在可以像平常一样浏览和访问所有网页。

1. 打开[PowerApps 门户管理中心](admin-overview.md)。

2.  > **配置或禁用维护模式**，请参阅**门户操作**。

    > [!div class=mx-imgBorder]
    > ![配置维护模式](../media/configure-maint-mode-button.png "配置维护模式")

3. 根据需要修改设置，然后选择 "**更新**"。 例如，如果已选择在前面显示自定义页，则可以选择显示默认页。

4. 若要禁用维护模式，请选择 "**禁用**"。 在更新或禁用维护模式时，门户会重新启动，并在几分钟内不可用。

    > [!div class=mx-imgBorder]
    > ![更新维护模式设置](../media/configure-maint-mode.png "更新维护模式设置")

