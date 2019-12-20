---
title: 重置门户 | MicrosoftDocs
description: 了解如何重置门户。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 31ae1238638ed4d10401f1c0a0fb5922a95263e5
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2867174"
---
# <a name="reset-a-portal"></a>重置门户

设置门户后，您可能在某些情况下需要从门户中删除资源，例如，如果您将组织移动到其他租户或其他数据中心，或如果您要将门户从组织中删除。

为此，您可以重置门户，这将删除所有与之关联的托管资源。 然后可以重新设置门户。 重置操作完成后，您的门户 URL 将无法再进行访问。

请务必注意，重置您的门户不会移除实例中呈现的门户配置或解决方案，它们将保持不变。

您可以重置完全配置的门户，为其设置或更新实例失败的门户。

要重置配置的门户：

1.  打开 [Power Apps 门户管理中心](admin-overview.md)。

2.  转到**门户操作** > **重置门户**。

    > [!div class=mx-imgBorder]
    > ![重置门户](../media/reset-portal.png "重置门户")

3.  在确认窗口中选择**重置**。

> [!NOTE]
> - 如果您不具有关联的 Azure Active Directory 应用程序的适当权限，将显示错误。 您必须与全局管理员联系获得适当权限。
> - 如果已使用较低版本门户加载项预配了门户，并且已成功重置了门户，则 **Dynamics 365 管理中心**页**应用程序**选项卡上的门户名称和门户状态不变。 例如，如果您的门户名称和状态分别为门户 1 和已配置，那么在重置门户后，这些值不会更改。 如果您要更改门户名称，您可以在 Power Apps 门户管理中心的**门户详细信息**选项卡上进行更改。 但是，状态值无法还原到“未配置”。
> - 请务必注意，**应用程序**选项卡上的门户状态不表示其设置状态，不会影响门户的功能。 它只显示您是否曾访问相应门户的 Power Apps 门户管理中心。

如果您的门户未正确设置，其将进入错误状态，并显示以下屏幕。 在这种情况下，您可以通过选择错误屏幕上的**重置门户**来重置门户。

> [!div class=mx-imgBorder]
> ![设置门户时出错](../media/provision-portal-error.png "设置门户时出错")

## <a name="troubleshooting"></a>疑难解答

本节提供有关重置门户时进行问题疑难解答的信息。

### <a name="reset-request-could-not-be-submitted"></a>无法提交重置请求

如果门户重置请求无法提交，错误将如下图所示。 在这种情况下，您必须关闭并重新打开 Power Apps 门户管理中心，然后尝试再次重置门户。 如果此问题仍然存在，请与 Microsoft 支持联系。

> [!div class=mx-imgBorder]
> ![重置门户时出错](../media/reset-portal-request-error.png "重置门户时出错")

### <a name="reset-portal-job-fails"></a>重置门户作业失败

如果重置门户作业失败，错误消息以及**重置门户**操作将显示。

> [!div class=mx-imgBorder]
> ![重置门户时出错](../media/reset-portal-error.png "重置门户时出错")

通常，这些是暂时错误，您必须选择**重置门户**重新启动作业。 如果此问题仍然存在，请与 Microsoft 支持联系。

