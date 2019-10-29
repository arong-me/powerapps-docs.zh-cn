---
title: 重置门户 |MicrosoftDocs
description: 了解如何重置门户。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 7b5bbc05ca7adf7fad9725215f8a7d6c06c035bb
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975716"
---
# <a name="reset-a-portal"></a>重置门户

预配门户后，你可能需要在某些情况下从门户中删除资源，例如，如果将组织移到另一个租户或另一个数据中心，或者要从组织中删除门户。

为此，可以重置门户，这会删除与之关联的所有托管资源。 然后，你可以重新设置门户。 重置操作完成后，将不再能够访问门户 URL。

需要注意的一点是，重置门户不会删除实例中存在的门户配置或解决方案，它们将保持不变。

可以重置完全配置的门户，或设置或更新实例的门户网站。

若要重置配置的门户：

1.  打开[PowerApps 门户管理中心](admin-overview.md)。

2.  请参阅**门户操作** > **重置门户**。

    > [!div class=mx-imgBorder]
    > ![重置门户](../media/reset-portal.png "重置门户")

3.  在确认窗口中选择 "**重置**"。

> [!NOTE]
> - 如果在关联的 Azure Active Directory 应用程序上没有相应的权限，则会显示错误。 您必须与全局管理员联系以获取适当的权限。
> - 如果已使用较旧的门户网站加载项预配了门户并成功重置了门户，则 Dynamics 365 管理中心上的 "**应用程序**" 选项卡上的门户名称及其状态不会更改。 例如，如果你的门户名称和状态分别为门户1并配置，则在重置门户之后，这些值不会更改。 如果要更改门户网站名称，可在 PowerApps 门户管理中心的 "**门户详细信息**" 选项卡上进行更改。 但是，status 值不能还原为 "未配置"。
> - 请务必注意，门户在 "**应用程序**" 选项卡上的状态不表示其设置状态，并且不会影响门户的功能。 它仅显示是否曾访问过相应门户的 PowerApps 门户管理中心。

如果门户未正确预配，则会进入错误状态，并且将显示以下屏幕。 在这种情况下，还可以通过在错误屏幕上选择 "**重置门户**" 来重置门户。

> [!div class=mx-imgBorder]
> (../media/provision-portal-error.png "设置门户时")![设置门户时出错]

## <a name="troubleshooting"></a>故障排除

本部分提供有关重置门户时解决问题的信息。

### <a name="reset-request-could-not-be-submitted"></a>无法提交重置请求

如果无法提交门户重置请求，则会显示一个错误，如下图所示。 在这种情况下，必须关闭并重新打开 PowerApps 门户管理中心，然后再次尝试重置门户。 如果问题仍然存在，请联系 Microsoft 支持部门。

> [!div class=mx-imgBorder]
> 重置(../media/reset-portal-request-error.png "门户时")![重置门户时出错]

### <a name="reset-portal-job-fails"></a>重置门户作业失败

如果重置门户作业失败，将显示一条错误消息以及**重置门户**操作。

> [!div class=mx-imgBorder]
> 重置(../media/reset-portal-error.png "门户时")![重置门户时出错]

通常，这些是暂时性错误，你必须选择 "**重置门户**" 才能重新启动该作业。 如果问题仍然存在，请联系 Microsoft 支持部门。

