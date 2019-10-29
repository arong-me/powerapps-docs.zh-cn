---
title: 关于 PowerApps 门户生命周期 |MicrosoftDocs
description: PowerApps 门户生命周期的相关信息，并将其从试用版转换为生产环境。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: c2ee82be5526cce41451c8a703971c0f97d32ea0
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977303"
---
# <a name="about-portal-lifecycle"></a>关于门户生命周期

门户始终创建为试用版。 试用门户在30天后过期，适用于免费试用其功能。 过期后，将挂起门户并关闭。 暂停后的七天后，将删除该试用门户。 对于门户生命周期阶段的每个更改，如 "挂起"、"已暂停"、"已删除" 和 "从试用版转换到生产"，你将收到一条 toast 和电子邮件形式的通知。

作为管理员，你可以将试用或挂起的门户转换为生产门户。 将试用门户转换为生产环境时，请确保该环境也是生产环境。 无法在试用环境中将试用门户转换为生产环境。 如果删除创建了试用门户的环境，则还会删除该门户。

可在租户的环境中自由创建第一个门户。 如果需要创建多个门户，租户中必须有 1 GB 的未使用存储空间。

## <a name="stages-in-portal-lifecycle"></a>门户生命周期中的阶段

### <a name="trial-portal"></a>试用门户

门户始终创建为试用门户。 如果拥有所需的许可证，可以从 PowerApps 门户管理中心将其转换为生产。 有关将试用门户转换为生产环境的信息，请参阅[将试用门户转换为生产](#convert-a-trial-portal-to-production)。

若要将试用门户转换为生产环境，环境应为外部用户提供必需的加载项，或者为内部用户提供许可证。 有关授权的详细信息，请参阅[PowerApps 和 Microsoft Flow 许可常见问题](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq)和[powerapps 门户许可](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-powerapps-portals-licensing)。

### <a name="suspended-portal"></a>挂起的门户

你将继续在 PowerApps 门户管理中心查看有关试用门户过期的通知。 试用门户在30天后过期。 如果在试用期内未将门户转换为生产环境，门户将关闭并置于挂起状态。 过期后，你将无法访问门户。

但是，挂起的门户仍可在暂停后的七天内转换为生产。 

### <a name="deleted-portal"></a>已删除门户

如果在七天的暂停期内未将门户转换为生产，则会删除门户。 门户数据不会从环境中删除，但是，将在环境中释放该门户使用的空间，你可以创建新的门户网站。

## <a name="convert-a-trial-portal-to-production"></a>将试用门户转换为生产

可以从在 PowerApps 门户管理中心显示的通知中将试用门户转换为 "生产"。

> [!NOTE]
> 你必须被分配了以下角色之一，才能将试用门户转换为生产：
> - 全局管理员
> - 系统管理员

打开[PowerApps 门户管理中心](admin-overview.md)并导航到 "[门户详细信息](portal-details.md)" 选项卡时，你将看到有关 "**类型**" 字段下显示的试用过期通知。

> [!div class=mx-imgBorder]
> ![门户详细信息选项卡上的试用通知](../media/admin-center-convert-notif.png "门户详细信息选项卡上的试用通知")

在管理中心的其他页面上，通知会显示在页面顶部。

> [!div class=mx-imgBorder]
> ![其他选项]卡上的试用通知其他(../media/admin-center-convert-notif-all.png "选项卡上的试用通知")

将试用门户转换为生产环境：

1.  在通知中，选择 "**转换**"。

2.  选择 "**确认**"。

    > [!div class=mx-imgBorder]
    > ![试用生产确认](../media/trial-to-prod-confirm.png "试用到生产确认")
