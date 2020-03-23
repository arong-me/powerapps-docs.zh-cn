---
title: 常见问题解答：转换到统一接口 | MicrosoftDocs
description: 有关将用户从旧的 Web 客户端转移到统一接口的转换过程的常见问题解答。
ms.custom: ''
ms.date: 02/26/2020
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
ms.openlocfilehash: 003bc58cc0c4db717a92d75d6157b7b53eb3629c
ms.sourcegitcommit: bb1a684d4ce2d342ad092a29ebca2bb502736e6e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/26/2020
ms.locfileid: "3087780"
---
# <a name="faqs-transition-to-unified-interface"></a>常见问题解答：转换到统一接口

此主题提供有关用于将用户从旧 Web 客户端转移到统一接口的转换选项的最常见问题的答案。

### <a name="where-can-i-go-to-see-the-transition-dates-that-have-been-suggested-for-my-environments"></a>哪里可以看到已经为我的环境推荐的转换日期？ 

请使用转换门户管理环境转换日期：<https://runone.powerappsportals.com>。

### <a name="how-do-i-gain-access-to-the-portal"></a>如何获得对门户的访问权限？

请执行以下操作：
1. 访问 <https://runone.powerappsportals.com>。
2. 使用您要管理的租户的管理员凭据登录。
3. 选择**我的环境**，然后检查已经应用了建议日期的所有环境。

### <a name="i-see-my-environment-has-a-date-suggested-for-transition-can-i-change-this-date"></a>我发现我的环境有建议转换日期。 我可以更改这个日期吗？

可以，如果您有租户的**全局管理员**、**Dynamics 365 服务管理员**或 **Power Platform 管理员**角色。 

与环境关联的日期是需要审批才能使用。 如果日期适合您的组织，请批准。  

要更改日期，请选择环境旁边的下拉图标并查看记录。 然后，租户管理员角色就可以将转换日期重新安排为之前或之后的日期。

若要安排为之前日期，请将现有日期更新为列表中您的首选选项。 您也可以[手动切换](transition-web-app.md)   如果我们的日期不适合。 
 
若要安排为之后日期，请选择重新安排转换日期按钮。 建议的日期将在下拉列表中提供。 日期被批准后将在门户中相应更新。 然后，如果要转换环境，请接受更新后的日期。 
 
如果日期早于 2020 年 10 月 1 日，将审查和授权日期更改。 确认后，日期将在门户中更新。 

> [!NOTE]
> 如果转换已获得批准，并且计划的日期在 48 小时内，您可以更改该日期。 同样，不能申请 2020 年 10 月 1 日后的日期，因为从该日期开始不再提供旧 Web 客户端。

### <a name="what-will-happen-if-i-dont-opt-in-and-approve-a-suggested-transition-date-for-my-environment"></a>如果不选择加入和批准为我的环境建议的转换日期会怎样？

如果您尚未批准建议的日期，门户内不会对您的环境进行任何更改。 当建议的日期过去后，我们将考虑再提供一个将来的日期供您考虑。  
 
> [!NOTE]
> 2020 年 10 月 1 日后，将按照 2020 年发行波次更新所有环境。

### <a name="my-transition-date-is-within-48-hours-and-i-cant-change-the-date-within-the-portal-how-can-i-stop-the-transition-from-taking-place"></a>我的转换日期在 48 小时内，我不能在门户内更改此日期。 如何阻止转换？

更改环境的转换日期的功能仅在转换前 48 小时以上可用。 要在此时间段之后停止该过程，请提交支持案例。 

> [!NOTE]
> 如果在门户上锁定日期（48 小时或更短）后发出请求，我们不能保证可以停止转换。

### <a name="i-have-environments-without-a-scheduled-date-can-i-update-these-to-include-a-date"></a>尚未为我的环境安排日期。 我可以更新环境来添加日期吗？

可以，如果您有租户的**全局管理员**、**Dynamics 365 服务管理员**或 **Power Platform 管理员**角色，请选择环境，然后选择日期，方法是单击重新安排转换日期按钮。

我们将更新门户的日期以确认。 临近转换日期时，通知电子邮件还将发送给全局租户管理员。 这将遵循本文档中详细介绍的标准提醒程序。

### <a name="is-there-a-recommended-checklist-i-should-run-through-before-transition"></a>在转换之前，是否会提供我应该参照的建议检查表？

请查看[社区站点](https://community.dynamics.com/365/unified-interface/)上提供的支持内容。 我们还有一个[转换检查表](https://aka.ms/UIChecklist)，可帮助您有效地进行计划。 请认真查看，以确保您对转换到统一接口感到适应。

### <a name="my-environment-has-been-transitioned-but-i-am-finding-blocking-issues-for-my-users-and-want-to-move-back-to-the-legacy-web-client-is-this-possible"></a>我的环境已转换，但是我发现我的用户有阻止问题，我希望恢复为旧 Web 客户端。 这样可以吗？

可以，转换后 10 天内您仍可以切换回旧版 Web 客户端。 您可以将[切换手动](https://docs.microsoft.com/power-platform/admin/enable-unified-interface-only)设置为前 10 天，或者提交[标准支持请求](https://admin.powerplatform.microsoft.com/support?referer=mbssupport)并将问题类型设置为“从旧 Web 客户端到统一接口的转换”，因为手动切换将被禁用。 

> [!NOTE]
> 这 10 天需要在 2020 年 10 月 1 日之前，因为旧版 Web 客户端在该日期之后将不再可用。

### <a name="i-want-to-transition-after-october-1-2020-is-that-possible"></a>我想在 2020 年 10 月 1 日之后转换。 这样可以吗？

2020 年 10 月的发行波次后，最终用户不能使用旧 Web 客户端。 我们不能将日期推迟到该期间之后。

如果您遇到任何受阻的项目，请尽快使用标准支持流程进行记录。

### <a name="what-is-the-standard-reminder-procedure-throughout-this-process"></a>在此过程中，标准的提醒程序是什么？

建议的时间段之前至少 30 天将进行多轮通信，但是您随时可以登录门户 (<https://runone.powerappsportals.com>) 查看状态。 Microsoft 将发送以下传达信息：

-   具有建议转换日期的每个环境的初始消息。
-   如果您已批准日期，将在门户内锁定日期之前 2 天收到提醒消息。 
-   转换前 2 天将发送最后提醒。 这将说明转换日期已锁定，将进行转换。
-   转换后，将通过结束消息确认成功（或发生了问题）

可以使用以下渠道查看消息：
-   Microsoft 365 租户中的消息中心。 这通常对全局管理员、服务管理员、服务消息读者等角色可见。
-   电子直邮。  电子邮件仅发送给相关特定环境的系统管理员角色，或者环境管理门户中“通知”选项卡中已添加的电子邮件地址。

> [!NOTE]
> 对于您的用户帐户具有系统管理员角色的每个环境，您都会收到一封电子邮件。

### <a name="i-have-requested-a-date-to-postpone-but-still-receiving-e-mails-and-message-center-posts-that-my-environment-is-set-to-transition-should-i-be-concerned"></a>我已请求推迟日期，但仍然收到我的环境已设置为转换的电子邮件和消息中心公告。 我需要在意吗？

我们的第一个建议是检查转换门户 (<https://runone.powerappsportals.com/>)，因为这将是您所有环境的唯一真实的信息来源。 如果日期已更新，则很有可能在更新通信列表之前，我们的通信系统已发送了消息。 

如果门户中的日期未更新为新日期，请按照标准程序提交支持请求。

仅转换管理员批准的日期。 

### <a name="if-i-already-have-an-environment-transitioned-to-unified-interface-will-i-still-be-able-to-switch-back-to-the-legacy-web-client-manually"></a>如果我已经将环境转换为统一接口，是否仍然可以手动切换回旧版 Web 客户端？

如果您的环境至少转换了 10 天，我们会注意禁用手动切换回旧版 Web 客户端的功能。 

如果您发现此功能已被禁用，并且需要切换回去，请提交[标准支持请求](https://admin.powerplatform.microsoft.com/support?referer=mbssupport)并将问题类型设置为“从旧 Web 客户端到统一接口的转换”。

### <a name="is-there-a-specific-day-and-time-when-approved-transitions-will-take-place"></a>已批准转换是否在具体日期和时间进行？ 

进行此转换时，我们预计不会出现任何停机时间。 但是，我们仅在星期五进行转换，并遵照我们的标准政策和通信中规定的相同维护时间线。 详细信息：[维护日程表](https://docs.microsoft.com/power-platform/admin/policies-communications#maintenance-timeline)

### <a name="are-environments-from-all-data-centers-included-within-this-transition-service"></a>此转换服务是否涵盖所有数据中心中的环境？

目前，门户中尚不包括来自特定数据中心（如政府社区云 (GCC)）的环境。 我们将在 2020 年 6 月之前提供为这些环境建议的日期。 希望转移到统一接口的客户始终可以在 2020 年 10 月 1 日之前随时[手动切换](/power-platform/admin/enable-unified-interface-only#how-to-enable-unified-interface-only-mode)。


