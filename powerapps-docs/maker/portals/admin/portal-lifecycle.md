---
title: 关于 Power Apps 门户生命周期 | MicrosoftDocs
description: 有关 Power Apps 门户生命周期以及将其从试用转换为生产的信息。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 60300176f0a39258bbb7030c9e30d9b2e7711990
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "2874638"
---
# <a name="about-portal-lifecycle"></a>关于门户生命周期

门户总是作为试用创建。 试用门户会在 30 天后过期，其对于免费试用其功能很有用。 过期后，门户将被暂停并关闭。 暂停七天后，将删除试用门户。 在门户网站生命周期阶段的每个更改，例如即将暂停、已暂停、已删除以及从试用转换为生产，您都将收到通过电子邮件发送的 Toast 形式的通知。

作为管理员，您可以将试用或已暂停的门户转换为生产门户。 在将试用门户转换为生产时，请确保环境也是生产环境。 您无法在试用环境中将试用门户转换为生产门户。 如果删除在其中创建试用门户的环境，该门户也会被删除。

可以在租户的环境中自由创建第一个门户。 如果需要创建多个门户，则租户中必须有 1 GB 的未使用存储空间。

## <a name="stages-in-portal-lifecycle"></a>门户生命周期的各个阶段

### <a name="trial-portal"></a>试用门户

门户总是作为试用门户创建。 如果您具有必需的许可证，则可以从 Power Apps 门户管理中心将其转换为生产门户。 有关将试用门户转换为生产门户的信息，请参阅[将试用门户转换为生产门户](#convert-a-trial-portal-to-production)。

要将试用门户转换为生产门户，环境应具有外部用户所需的加载项或内部用户的许可证。 有关许可的详细信息，请参阅 [Power Apps 和 Power Automate 许可常见问题](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq)和 [Power Apps 门户许可](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-power-apps-portals-licensing)。

### <a name="suspended-portal"></a>暂停的门户

您将继续在 Power Apps 门户管理中心中看到有关试用门户过期的通知。 试用门户将在 30 天后过期。 如果您在试用期内没有将门户转换为生产门户，则该门户将关闭并进入暂停状态。 门户过期后，您将无法访问它。

但是，已暂停的门户仍可以在暂停后的 7 天内转换为生产门户。 

### <a name="deleted-portal"></a>删除的门户

如果您在 7 天的暂停期内没有将门户转换为生产门户，门户将被删除。 不会从环境中删除门户数据，但是将释放该门户在环境中使用的空间，您可以创建一个新门户。

## <a name="convert-a-trial-portal-to-production"></a>将试用门户转换为生产门户

您可以从 Power Apps 门户管理中心中显示的通知将试用门户网站转换为生产门户。

> [!NOTE]
> 您必须被分配以下角色之一才能将试用门户转换为生产门户：
> - 全局管理员
> - 系统管理员

当您打开 [Power Apps 门户管理中心](admin-overview.md)并导航至[门户详细信息](portal-details.md)选项卡时，您会看到有关试用过期的通知显示在**类型**字段下面。

> [!div class=mx-imgBorder]
> ![“门户详细信息”选项卡上的试用通知](../media/admin-center-convert-notif.png "“门户详细信息”选项卡上的试用通知")

在管理中心的其他页面上，通知显示在页面顶部。

> [!div class=mx-imgBorder]
> ![其他选项卡上的试用通知](../media/admin-center-convert-notif-all.png "其他选项卡上的试用通知")

要将试用门户转换为生产门户：

1.  在通知中，选择**转换**。

2.  选择**确认**。

    > [!div class=mx-imgBorder]
    > ![试用到生产确认](../media/trial-to-prod-confirm.png "试用到生产确认")
