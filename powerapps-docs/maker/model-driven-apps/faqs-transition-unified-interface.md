---
title: 常见问题解答：统一接口转换 | MicrosoftDocs
description: 与将用户从旧版 Web 客户端移动到统一接口的自动转换过程有关的常见问题解答。
ms.custom: ''
ms.date: 11/04/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.author: haybass
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 373201de630b46adc80b25eed10686da9112bad6
ms.sourcegitcommit: c094590862142155cbafa91c6ee0ade975c82083
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "2769428"
---
# <a name="faqs-unified-interface-transition"></a>常见问题解答：统一接口转换

本主题提供有关将用户从旧版 Web 客户端迁移到统一接口的转换过程的最常见问题的答案。

### <a name="where-can-i-go-to-see-the-transition-dates-that-have-been-assigned-to-my-environments"></a>在哪里可以查看分配给我的环境的转换日期？ 

请使用自动转换门户来管理环境转换日期：<https://runone.powerappsportals.com>。

### <a name="how-do-i-gain-access-to-the-portal"></a>如何获得对门户的访问权限？

请执行以下操作：
1. 访问 <https://runone.powerappsportals.com>。
2. 使用您要管理的租户的管理员凭据登录。
3. 选择**我的环境**，然后查看分配了目标日期的所有环境。

### <a name="i-see-my-environment-has-a-date-for-auto-transition-can-i-change-this-date"></a>我看到我的环境有一个自动转换日期。 我可以更改这个日期吗？

可以，如果您对租户具有**全局管理员**或**服务管理员**角色，则可以更改。 要更改日期，请选择环境旁边的下拉图标并查看记录。 然后，租户管理员角色将能够为更早或更晚的转换日期提交例外请求。

- 对于更早的转换日期，请将现有日期更新为列表中的首选日期。 这不需要审批。 如果我们的日期不适合，您也可以手动切换。

- 对于更晚的转换日期，您可以提交例外请求。 建议的日期将在下拉列表中提供。 批准后，日期将在门户中相应更新。

每个环境共计可以请求两个例外。 根据业务理由以及选定的建议日期同意例外请求。 确认后，日期将在门户中更新。

> [!NOTE]
> 如果计划的转换时间是 48 小时内，您将无法更改日期。 同样，您将无法请求 2020 年 10 月 1 日之后的日期，因为旧版 Web 客户端将不再可用。

### <a name="my-auto-transition-date-is-within-48-hours-and-i-cant-change-the-date-within-the-portal-how-can-i-stop-transition-taking-place"></a>我的自动转换日期是在 48 小时内，我无法在门户中更改日期。 如何停止转换？

更改环境的转换日期的功能仅在转换前 48 小时以上可用。 要在此时间段之后停止该过程，请提交支持案例。 

> [!NOTE]
> 如果在门户上锁定日期（48 小时或更短）后发出请求，我们不能保证可以停止转换。

### <a name="i-have-environments-without-a-target-auto-transition-date-can-i-update-these-to-include-a-date"></a>我的环境没有目标自动转换日期。 我可以更新环境来添加日期吗？

可以，如果您有租户的**全局管理员**或**服务管理员**角色，请选择环境，提交例外请求，并使用目标日期列表更新建议的期限。 

我们将更新门户的日期以确认。 临近转换日期时，通知电子邮件还将发送给全局租户管理员。 这将遵循本文档中详细介绍的标准提醒程序。

### <a name="is-there-a-recommended-checklist-i-should-run-through-before-transition"></a>在转换之前，是否会提供我应该参照的建议检查表？

请查看[社区站点](https://community.dynamics.com/365/unified-interface/)上提供的支持内容。 我们还有一个[转换检查表](https://aka.ms/UIChecklist)，可帮助您有效地进行计划。 请认真查看，以确保您对转换到统一接口感到适应。

### <a name="my-environment-has-been-transitioned-but-i-am-finding-blocking-issues-for-my-users-and-wish-to-move-back-to-the-legacy-web-client-is-this-possible"></a>我的环境已经完成转换，但是我发现用户遇到了阻塞性问题，我希望退回到旧版 Web 客户端。 这样可以吗？

可以，转换后 10 天内您仍可以切换回旧版 Web 客户端。 您可以在最初的前 4 天进行[手动切换](https://docs.microsoft.com/power-platform/admin/enable-unified-interface-only)，或在此之后，通过常规渠道提交支持请求，因为手动切换将被禁用。 

> [!NOTE]
> 这 10 天需要在 2020 年 10 月 1 日之前，因为旧版 Web 客户端在该日期之后将不再可用。

### <a name="i-want-to-transition-after-october-1-2020-is-that-possible"></a>我想在 2020 年 10 月 1 日之后转换。 这样可以吗？

可用的旧版 Web 客户端将在 2020 年 10 月 1 日之后不可用。 我们无法将转换时间推迟到该日期之后。

如果您遇到任何受阻的项目，请尽快使用标准支持流程进行记录。

### <a name="what-is-the-standard-reminder-procedure-throughout-this-process"></a>在此过程中，标准的提醒程序是什么？

Microsoft 将发送以下传达信息：

-   分配了转换日期的每个环境的初始消息
-   在门户中锁定日期前 2 天发送提醒消息
-   说明转换日期已锁定并会继续进行的最后提醒。
-   确认成功（或发生问题时）的结束消息

可以使用以下渠道查看消息：
-   Microsoft 365 租户中的消息中心。 这通常对全局管理员、服务管理员、服务消息读者等角色可见。
-   电子直邮。  电子邮件仅发送给相关特定环境的系统管理员角色，或者环境管理门户中“通知”选项卡中已添加的电子邮件地址。

> [!NOTE]
> 对于您的用户帐户具有系统管理员角色的每个环境，您都会收到一封电子邮件。

### <a name="i-have-requested-a-date-to-postpone-but-still-receiving-e-mails-and-message-center-posts-that-my-environment-is-set-to-transition-should-i-be-concerned"></a>我已请求推迟日期，但仍然收到我的环境已设置为转换的电子邮件和消息中心公告。 我需要在意吗？

我们的第一个建议是检查转换门户 (<https://runone.powerappsportals.com/>)，因为这将是您所有环境的唯一真实的信息来源。 如果日期已更新，则很有可能在更新通信列表之前，我们的通信系统已发送了消息。 

如果门户中的日期未更新为新日期，请按照标准程序提交支持请求。

### <a name="if-i-already-have-an-environment-transitioned-to-unified-interface-will-i-still-be-able-to-switch-back-to-the-legacy-web-client-manually"></a>如果我已经将环境转换为统一接口，是否仍然可以手动切换回旧版 Web 客户端？

如果您的环境至少转换了 4 天，我们会注意禁用手动切换回旧版 Web 客户端的功能。 

如果您发现此功能已被禁用并且需要切换回去，请从您通常的渠道提交支持请求以进行评估。

### <a name="is-there-a-specific-day-and-time-when-automatic-transitions-will-take-place"></a>进行自动转换时是否有具体的日期和时间？ 

进行此转换时，我们预计不会出现任何停机时间。 不过，我们只会在星期五进行自动转换，并遵循我们标准政策和通信中列出的相同维护日程表。 详细信息：[维护日程表](https://docs.microsoft.com/power-platform/admin/policies-communications#maintenance-timeline)




