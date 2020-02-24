---
title: 升级门户 | MicrosoftDocs
description: 了解如何升级门户。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 7f8837179ccf9edb7376db88ee421e4cb424909f
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978533"
---
# <a name="upgrade-a-portal"></a>升级门户

本部分内容帮助您了解 Dynamics 365 门户发布流程，以为任何新发布做好适当准备并减少对您的客户的任何影响。 另外还讨论您的门户中的不同组件。

门户包括下列组件：

|组件|说明|更新流程|
|---------|-----------|--------------|
|门户解决方案|在 Common Data Service 环境中安装以及包含任何门户的元数据实体的解决方案。|客户自行在 Dynamics 365 管理中心页更新。|
|门户网站主机|门户网站主机是建立实际网站的门户代码。|门户网站主机为所有门户自动更新。<br>**注意**：门户网站主机的新版本与门户解决方案的所有支持版本向后兼容。 但是，当解决方案版本不受支持后，它不能证明可以使用新版本的门户网站主机运行。|
|||

## <a name="impact-of-new-releases-on-a-portal-solution"></a>新版本对门户解决方案的影响

作为任何门户发布的一部分，门户网站主机将在客户更新门户解决方案时自动更新为最新版本。 了解每个组件更新对您的实时门户的影响非常重要，以便您可以相应进行计划。

### <a name="portal-website-host-update"></a>门户网站主机更新

如果在运行门户的生产版本（可以在 Power Apps 门户管理中心查看），在更新门户时，实时门户不会有任何停机时间。 但是，如果您运行的是门户的试用版，则会出现大约 6-10 分钟的停机时间，您将无法访问门户。

### <a name="portal-solution-update"></a>门户解决方案更新

在安装或更新您的实例中的任何解决方案时，您可在实例中看到一些不稳定情况。 门户解决方案更新流程更新实例中可用的解决方案，将对反之也会影响您的门户的实例产生影响。 因此，始终建议在夜间执行实例中的解决方案更新。

## <a name="get-notified-about-new-releases"></a>获取新发布通知

每个客户都会通过 Office 365 消息中心（在 Microsoft 365 管理中心）收到有关新门户发布的通知。 请确保您有权访问 Office 365 消息中心（全局管理员和服务管理员有访问权），或已与全局管理员或服务管理员讨论，以通知您所有新门户的发布。

通知将在发布前约 2-5 个工作日发送。 通知只发送给计划更新门户的客户。 每个通知提供有关更新类型的详细信息，以及它将推出的日期/时间及发行说明链接。

## <a name="enable-a-portal-for-new-release"></a>为新发布启用门户

您可以启用开发或测试门户来在所有客户之前收到早期升级，以便可以在升级在实时门户中实施前在测试门户上测试所有核心场景。 早期升级会在全球推出任何发布前至少一周推出。 而且，也会发送早期升级通知，如[获取新发布通知](#get-notified-about-new-releases)一节所述。

若要启用门户以获得早期升级：

1.  打开 [Power Apps 门户管理中心](admin-overview.md)。

2.  在**门户操作**选项卡中，选择**启用门户，以便尽快升级**。

    > [!div class="mx-imgBorder"]
    > ![启用门户，以便尽快升级](../media/upgrade-portal.png "启用门户，以便尽快升级")

> [!NOTE]
> 您可以随时为早期升级启用或禁用门户。 但是，将获取标记为在任何发布前两天早期访问的所有门户的快照，任何在此后标记为早期访问的门户将不保证能够获得早期升级。

如果在早期升级阶段遇到任何问题，您可以通过 Microsoft 支持报告。


