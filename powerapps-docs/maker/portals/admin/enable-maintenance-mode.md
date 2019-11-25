---
title: 为门户启用维护模式 | MicrosoftDocs
description: 了解如何使用您的门户启用维护模式。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: e53380c39257645e9056a271226b6f7ef8c8c721
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2709923"
---
# <a name="maintenance-mode-for-a-portal"></a>门户的维护模式

有时，您的网站可能需要进行计划的维护，或由于临时断电而停机。 当客户在维护期间访问网站时，可能遇到不可预测的行为和间歇性不可用情况。 

作为门户管理员，您可以配置门户以在每次进行维护活动时都向客户显示适当的消息（例如，“解决方案包正在升级”。）您可以通过在您的门户上启用维护模式来利用此功能。 在维护模式启用时，将显示消息，客户被限制浏览 `<portal URL>/_services/about` 页面以外的任何网页。

> [!div class=mx-imgBorder]
> ![默认维护模式页面](../media/default-maint-page.png "默认维护模式页面")

## <a name="enable-maintenance-mode"></a>启用维护模式

您可以在您的门户上启用维护模式来提供一致的消息，而不是当网站进行计划维护时处理不可预测的行为。 这将为您的门户用户提供更好的体验。

1. 打开 [PowerApps 门户管理中心](admin-overview.md)。

3. 转到**门户操作** > **启用维护模式**。

    > [!div class=mx-imgBorder]
    > ![启用维护模式](../media/enable-maint-mode-button.png "启用维护模式")

4. 在**启用维护模式**窗口中，输入下列值：
    - **选择启用维护模式时使用的页面**：选择以下值之一：

        - **默认页**：如果您希望在启用维护模式时显示默认页，则选择此值。 默认情况下选择此选项。

        - **自定义页**：如果您希望在启用维护模式时显示自定义 HTML 页，则选择此值。

    - **自定义页 URL**：只有当您选择显示自定义 HTML 页面的选项时，此字段才启用。 必须确保您提供的页面 URL 可以公开访问。 如果指定的 HTML 页无法访问，默认页将显示，其中包含为管理员提供的注释。

5. 选择**启用**。 在启用维护模式时，将重新启动门户，并且门户有几分钟不可用。 

    > [!div class=mx-imgBorder]
    > ![启用维护模式设置](../media/enable-maint-mode.png "启用维护模式设置")

## <a name="configure-or-disable-maintenance-mode"></a>配置或禁用维护模式

在启用您的门户的维护模式后，您可以更新维护模式设置并选择另一个页面。

当您的网站的计划维护完成时，您还可以选择禁用门户的维护模式。 您的门户用户现在可以照常浏览和访问所有网页。

1. 打开 [PowerApps 门户管理中心](admin-overview.md)。

2. 转到**门户操作** > **配置或禁用维护模式**。

    > [!div class=mx-imgBorder]
    > ![配置维护模式](../media/configure-maint-mode-button.png "配置维护模式")

3. 根据需要修改设置，然后选择**更新**。 例如，如果您之前选择了显示自定义页，您可能选择显示默认页。

4. 若要禁用维护模式，请选择**禁用**。 在更新或禁用维护模式时，将重新启动门户，并且门户有几分钟不可用。

    > [!div class=mx-imgBorder]
    > ![更新维护模式设置](../media/configure-maint-mode.png "更新维护模式设置")

