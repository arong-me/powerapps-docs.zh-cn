---
title: 常见问题解答：转换到统一接口 | MicrosoftDocs
description: 有关将用户从旧的 Web 客户端转移到统一接口的转换过程的常见问题解答。
ms.custom: ''
ms.date: 03/04/2020
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
ms.openlocfilehash: 13bf17886ab44fb14f1b510615d538a48d8090fc
ms.sourcegitcommit: 310dd3dc68ffebe6a416450836ac0ba988b84fb4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "3162107"
---
# <a name="faqs-transition-to-unified-interface"></a>常见问题解答：转换到统一接口

本主题提供有关统一接口以及如何从旧 Web 客户端转移到统一接口的最常见问题的解答。

## <a name="faqs-unified-interface-and-legacy-web-client"></a>常见问题：统一接口和旧 Web 客户端

### <a name="why-should-i-move-to-unified-interface"></a>为什么我应该移到统一接口？

Microsoft 对高效工作场所的愿景需要一个现代接口，它包括统一接口中所含的功能和改进，这些功能和改进可以提供更加一致的用户体验、改进的性能和更高的用户效率。 有关详细信息，请参阅[统一接口 Playbook](https://docs.microsoft.com/powerapps/maker/model-driven-apps/unified-interface-playbook)

### <a name="are-my-isvs-compatible"></a>我的 ISV 是否兼容？

ISV 已收到需要在过渡到统一接口的过程中采取行动的通知。 请直接联系您的 ISV，了解他们有关统一接口兼容性的日程表。

### <a name="what-is-the-retraining-effort"></a>什么是重新培训工作？

从技术角度来看，重新培训应该尽可能简单，因为您的业务逻辑和架构是保持不变的。 重新培训应该着重介绍导航中的新增功能和整体外观。 如果您已做出业务决策来更改设计以针对新功能和特性进行优化，则可能需要进一步的培训。

### <a name="will-i-need-to-re-create-my-solution-customizations"></a>我需要重新创建我的解决方案自定义项吗？

不需要，您应该不需要重新创建任何自定义项，前提是您已按照 [Common Data Service 开发人员指南](/powerapps/developer/common-data-service/overview)操作，并让所有更改保持为最新。 不过，可能会有新的机会获得我们的最新投资，这可能会导致自定义项更改。

### <a name="how-long-will-it-take-to-transitionwhat-is-the-work-effort"></a>转移需要多长时间/工作量如何？

根据您的环境的复杂程度，这期间的工作量将有所不同。 建议您首先使用试生产/POC 模型驱动应用开始测试。 这样，您可以与业务部门共同计划统一接口的完全推行。 请参阅[统一接口 Playbook](https://docs.microsoft.com/powerapps/maker/model-driven-apps/unified-interface-playbook) 和[规划清单](https://aka.ms/UIChecklist)，获取有关如何开始的更多指导和我们的[白皮书](https://download.microsoft.com/download/A/F/3/AF3D45A7-4F38-41BE-8956-1DF7A4A5AFDB/approaching-unified-interface-transition.pdf)。

### <a name="where-can-i-find-public-information-about-the-unified-interface-direction"></a>在哪里可以找到有关统一接口方向的公共信息？

通过以下活动，统一接口的战略方向已经进入公共领域：
- [MBAS：BRK2073 Microsoft Power Apps：运行一个 UI – Power Apps 中画布、模型驱动和统一接口的未来](https://powerusers.microsoft.com/t5/MBAS-Gallery/Microsoft-PowerApps-Run-one-UI-the-future-of-canvas-model-driven/td-p/301580)
- [BRK3031 实现 Dynamics 365 的最佳实践：转向现代统一接口](https://powerusers.microsoft.com/t5/Microsoft-Business-Applications/Implementation-Best-Practices-for-Dynamics-365-Making-the-move/m-p/299928)


### <a name="as-an-on-premises-customer-looking-to-move-to-the-cloud-what-is-the-best-approach-to-adopt-unified-interface"></a>作为希望移到云的本地客户，采用统一接口的最佳方法是什么？

强烈建议您在迁移到云的同时规划向统一接口的转移。 首先在统一接口中测试您的旧 Web 客户端，在迁移后，先确认统一接口的兼容性，然后再向用户社区发布。 这将减少培训工作，并让用户可以采用统一接口必备的一些新特性和功能。 有关详细信息，请与 Microsoft 代表联系。

### <a name="when-will-isvs-be-notified-of-the-need-to-move-to-unified-interface"></a>何时会通知 ISV 需要移到统一接口？

ISV 已收到需要在过渡到统一接口的过程中采取行动的通知。 请直接联系您的 ISV，了解他们有关统一接口兼容性的日程表。

### <a name="how-are-language-translations-handled"></a>语言翻译会如何处理？

除站点地图外，语言翻译的过程基本不变。 站点地图区域、组和子区域在站点地图编辑器中本地化。

### <a name="i-dont-have-budget-or-resources-to-do-a-project-is-the-deadline-a-fixed-date"></a>我没有预算或资源来完成一个项目。 期限是固定的吗？

我们固定是在 2020 年 12 月 1 日之前离开旧 Web 客户端。 我们建议您尽早进行一些测试，来了解您组织的项目的复杂程度，进而实现兼容。 在大多数情况下，应该不需要进行大量重新设计即可有快速的进展并会开始看到用户从中受益。 请通过创建支持案例与 Microsoft 联系，提供可以停止您的转移的反馈。

### <a name="were-working-on-transitioning-to-unified-interface-but-have-hit-some-issues-how-can-we-report-to-microsoft"></a>我们正在努力转移到统一接口，但遇到了一些问题；应该如何向 Microsoft 报告？

请查看我们的[资源](https://community.dynamics.com/365/unified-interface/)来获取帮助指导，并在执行标准过程后提交支持案例。 您还可以通知合作伙伴、Microsoft 代表或 FastTrack 团队（如果适用）。

### <a name="when-should-i-start-moving-to-unified-interface"></a>应该在何时开始移到统一接口？

您可以立即转移；我们已经将很多处于生产过程的客户转移到了统一接口。 请尽早开始测试。 请访问我们的社区网站 <https://community.dynamics.com/365/unified-interface/> 获取有用的内容。 使用标准支持过程提交全部问题。

### <a name="what-are-the-risks-associated-with-moving-to-unified-interface"></a>移到统一接口会带来什么风险？

我们看到继续停留于旧 Web 客户端会存在风险，因为我们的投资和战略方向是针对统一接口。 如果您现在已经计划开始转移，请查看我们的[社区网站](https://community.dynamics.com/365/unified-interface/)和[快速入门指南](https://docs.microsoft.com/powerapps/maker/model-driven-apps/transition-web-app-existing)。 这将帮助您发现空白区（如果有），并在执行完整部署之前制定修复计划。

### <a name="i-have-a-new-feature-idea-for-unified-interface-where-do-i-log-it"></a>我对统一接口有一个功能上的新想法；可以在哪里提出？

请访问我们的建议门户 (<https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas>)，选择**给出建议**，并将项目标为“统一接口”类别。

### <a name="is-there-any-supporting-content-to-help-me-plan-and-execute-my-transition-to-unified-interface"></a>是否有支持内容可以帮助我规划和执行统一接口的转移？

有，我们有一个新的社区组 (<https://community.dynamics.com/365/unified-interface/>)，它提供有用的内容、互动论坛和博客，能够看到所有最新的更新和有关统一接口的信息。

### <a name="how-does-this-move-impact-on-premises-customer-and-what-will-happen-when-the-web-client-is-deprecated-do-web-client-forms-become-unsupported"></a>此次转移会对本地客户有怎样的影响？当 Web 客户端被弃用后会怎样（是否不支持 Web 客户端窗体）？

此次公告仅对目前的联机客户有效。 我们将继续为本地部署支持旧 Web 客户端。

### <a name="is-the-timeline-applicable-for-customers-using-government-community-cloud-gcc-and-other-data-centers-such-as-china"></a>日程表适用于使用政府社区云 (GCC) 和其他数据中心（如中国）的客户吗？

我们计划在标准发布计划中发布这些数据中心的统一接口更新。

### <a name="what-action-should-i-take-as-a-unified-service-desk-customer-who-is-still-on-the-web-client"></a>作为仍在 Web 客户端上的 Unified Service Desk 客户，我应该采取哪些行动？

仍在 Web 客户端上的 Unified Service Desk 客户需要将其配置从 Web 客户端迁移到统一接口。 这将需要升级到 [Unified Service Desk](https://docs.microsoft.com/dynamics365/unified-service-desk/download-unified-service-desk?view=dynamics-usd-4.1) 的最新版本（客户端和服务器组件）。 我们有一个[迁移助手](https://docs.microsoft.com/dynamics365/unified-service-desk/admin/migration-steps-web-client-unified-interface-configuration?view=dynamics-usd-4.1)帮助您完成这一工作。

### <a name="are-there-any-other-deprecations-that-i-should-plan-for"></a>还有其他弃用事项我应该计划吗？

请查看我们的[弃用通知页面](https://docs.microsoft.com/power-platform/important-changes-coming)，确定是否还有其他区域也需要计划。

### <a name="where-can-i-find-further-information-on-the-transition-service"></a>在哪里可以找到有关转移服务的更多信息？

为了帮助促进转移的动力，我们为通过我们的转移服务从旧 Web 客户端切换到统一接口的环境提供了建议的目标日期。 客户需要在采取行动之前批准日期，然后随着日期的临近，将会收到一系列的沟通提醒消息。 如果在 2020 年 12 月 1 日截止日期之前不适合转移，也可以重新安排日期。 有关详细信息，请参阅下一节。


## <a name="faqs-transitioning-to-unified-interface"></a>常见问题：转移到统一接口

### <a name="where-can-i-go-to-see-the-transition-dates-that-have-been-suggested-for-my-environments"></a>哪里可以看到已经为我的环境推荐的转换日期？ 

请使用转换门户管理环境转换日期：<https://runone.powerappsportals.com>。

### <a name="how-do-i-gain-access-to-the-portal"></a>如何获得对门户的访问权限？

请执行以下操作：
1. 访问 <https://runone.powerappsportals.com>。
2. 使用您要管理的租户的管理员凭据登录。
3. 选择**我的环境**，然后检查已经应用了建议日期的所有环境。

### <a name="i-see-my-environment-has-a-date-suggested-for-transition-can-i-change-this-date"></a>我发现我的环境有建议转换日期。 我可以更改这个日期吗？

可以，如果您有租户的**全局管理员**、**Dynamics 365 服务管理员**或 **Power Platform 管理员**角色。 

与环境关联的日期是需要审批才能使用。 如果日期适合您的组织，则批准。  

要更改日期，请选择环境旁边的下拉图标并查看记录。 然后，租户管理员角色就可以将转换日期重新安排为之前或之后的日期。

若要安排为之前日期，请将现有日期更新为列表中您的首选选项。 您也可以[手动切换](transition-web-app.md)   如果我们的日期不适合。 
 
若要安排为之后日期，请选择重新安排转换日期按钮。 建议的日期将在下拉列表中提供。 日期被批准后将在门户中相应更新。 如果您希望转移您的环境，请接受更新的日期。 
 
如果日期在 2020 年 12 月 1 日之前，将会查看并允许日期更改。 确认后，日期将在门户中更新。 

> [!NOTE]
> 如果转换已获得批准，并且计划的日期在 48 小时内，您可以更改该日期。 同样，您将无法请求 2020 年 12 月 1 日之后的日期，因为那时旧 Web 客户端将不能再使用。

### <a name="what-will-happen-if-i-dont-opt-in-and-approve-a-suggested-transition-date-for-my-environment"></a>如果不选择加入和批准为我的环境建议的转换日期会怎样？

如果您尚未批准建议的日期，门户内不会对您的环境进行任何更改。 当建议的日期过去后，我们将考虑再提供一个将来的日期供您考虑。  
 
> [!NOTE]
> 2020 年 12 月 1 日之后，所有环境都将更新为统一接口。

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
> 这 10 天需要在 2020 年 12 月 1 日之前，因为旧 Web 客户端在该日期之后将不能再使用。

### <a name="i-want-to-transition-after-december-1-2020-is-that-possible"></a>我想在 2020 年 12 月 1 日之后转移。 这样可以吗？

旧 Web 客户端在 2020 年 12 月 1 日之后将不能使用。 我们不能将日期推迟到该期间之后。

如果您遇到任何受阻的项目，请尽快使用标准支持流程进行记录。

### <a name="what-is-the-standard-reminder-procedure-throughout-this-process"></a>在此过程中，标准的提醒程序是什么？

传达信息将在建议的期限之前至少 30 天分波发出，不过您可以随时登录门户 (<https://runone.powerappsportals.com>) 查看状态。 Microsoft 将发送以下传达信息：

-    具有建议转换日期的每个环境的初始消息。
-    如果您已批准了日期，当日期在门户中锁定之前两天，您会收到一条提醒消息。 
-    最终提醒将在转移前两天发送。 这将说明转换日期已锁定，将进行转换。
-    转换后，将通过结束消息确认成功（或发生了问题）

可以使用以下渠道查看消息：
-    Microsoft 365 租户中的消息中心。 这通常对全局管理员、服务管理员、服务消息读者等角色可见。
-    电子直邮。  电子邮件仅发送给相关特定环境的系统管理员角色，或者环境管理门户中“通知”选项卡中已添加的电子邮件地址。

> [!NOTE]
> 对于您的用户帐户具有系统管理员角色的每个环境，您都会收到一封电子邮件。

### <a name="i-have-requested-a-date-to-postpone-but-still-receiving-e-mails-and-message-center-posts-that-my-environment-is-set-to-transition-should-i-be-concerned"></a>我已请求推迟日期，但仍然收到我的环境已设置为转换的电子邮件和消息中心公告。 我需要在意吗？

我们的第一个建议是查看转移门户 (<https://runone.powerappsportals.com/>)，因为它将是您所有环境的唯一真实情况来源。 如果日期已更新，则很有可能在更新通信列表之前，我们的通信系统已发送了消息。 

如果门户中的日期未更新为新日期，请按照标准程序提交支持请求。

仅转换管理员批准的日期。 

### <a name="if-i-already-have-an-environment-transitioned-to-unified-interface-will-i-still-be-able-to-switch-back-to-the-legacy-web-client-manually"></a>如果我已经将环境转换为统一接口，是否仍然可以手动切换回旧版 Web 客户端？

如果您的环境至少转换了 10 天，我们会注意禁用手动切换回旧版 Web 客户端的功能。 

如果您发现此功能已被禁用，并且需要切换回去，请提交[标准支持请求](https://admin.powerplatform.microsoft.com/support?referer=mbssupport)并将问题类型设置为“从旧 Web 客户端到统一接口的转换”。

### <a name="is-there-a-specific-day-and-time-when-approved-transitions-will-take-place"></a>已批准转换是否在具体日期和时间进行？

进行此转换时，我们预计不会出现任何停机时间。 但是，我们仅在星期五进行转换，并遵照我们的标准政策和通信中规定的相同维护时间线。 详细信息：[维护日程表](https://docs.microsoft.com/power-platform/admin/policies-communications#maintenance-timeline)

### <a name="are-environments-from-all-data-centers-included-within-this-transition-service"></a>此转换服务是否涵盖所有数据中心中的环境？

目前，门户中尚不包括来自特定数据中心（如政府社区云 (GCC)）的环境。 我们将在 2020 年 6 月之前提供为这些环境建议的日期。 想要迁移到统一接口的客户在 2020 年 12 月 1 日之前可以随时[手动切换](/power-platform/admin/enable-unified-interface-only#how-to-enable-unified-interface-only-mode)。


