---
title: 将 InfoPath 表单转换为 PowerApps | Microsoft Docs
description: 要开始将 InfoPath 表单转换为 PowerApps，请参阅有关常见 InfoPath 方案以及如何在 PowerApps 中创建这些项的详细信息。
author: richardriley99
ms.service: powerapps
ms.topic: article
ms.component: canvas
ms.date: 04/05/2018
ms.author: rriley
ms.openlocfilehash: 10fe4e9052b9c029046c515c229e95075988597a
ms.sourcegitcommit: 91a102426f1bc37504142cc756884f3670da5110
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/26/2018
ms.locfileid: "34803503"
---
# <a name="transform-your-infopath-forms-to-powerapps"></a>将 InfoPath 表单转换为 PowerApps

是否在 InfoPath 中创造了出色内容，很想了解如何在更可靠的平台上交付这些内容？

## <a name="key-advantages-of-powerapps-over-infopath"></a>PowerApps 相较于 InfoPath 的主要优点

如果你和大多数 InfoPath Power 用户一样，使用独特的技能组合构建出色的表单已有一段时日。 虽然对生成的表单感到十分满意，但也发现存在一定的局限性：设计“经典”（老旧），移动设备体验不够完美，未来可用性不明确，以及如果不编写代码，连接到其他服务时总会受到重重束缚。

PowerApps 团队已了解到这些问题以及许多其他问题。 他们一直努力为用户提供更好的 PowerApps 体验。 他们的目标是使用户能够利用其业务和现有技术技能创建应用。 让用户能够使用 PowerApps 快速生成和部署适合的业务解决方案，而无需编写代码。

**通过 PowerApps 成就辉煌未来**  
PowerApps 是一个服务型软件 (SaaS) 平台，用户通过该平台可以快速构建功能强大的应用并能够将这些应用部署到 Web、SharePoint、Dynamics 365、Teams、Power BI 或移动设备，这一切都无需任何额外工作。 而且由于它们部署起来非常容易（只需向他人提供已发布的应用的 URL 即可），因此更新也非常简单。

**共享应用**  
是否曾尝试生成应用并将其发布到 Google 或 Apple App Store？ 这个操作很复杂。 另一个难题是，如果要部署下一个应用或更新现有应用，你的用户需要执行更多步骤。 PowerApps 就不存在这些问题。 你的用户可通过其 App Store 安装 Microsoft PowerApps 应用，然后使用 Microsoft 帐户的用户名和密码登录，随后即可获取你与其共享的所有功能强大的应用。 在此之后，当你更新这些应用或向用户推送新应用时，新应用会在用户设备上显示。 无需进行设备管理的移动应用能为你和业务带来巨大优势。

**关于移动**  
通过 PowerApps，你可以利用用户移动设备的功能。 可以从应用内访问加速功能、照相机、指南针、连接信息和位置信号。 这为生成用于完成工作的应用创造了无限可能性。 当然，触摸是 PowerApps 中的自动功能，生成应用时无需任何编码操作。

**摆脱束缚**  
使用 InfoPath 时，标准做法就是使用来自一个数据源的数据。 但是，如果要在其他位置（如另一个站点集合中的 SharePoint 列表）进行更新 或连接到外部服务，情况就会变得棘手，所需的编码等操作会让你难以入眠。 使用 PowerApps 就不存在这些问题。 它允许在一个应用中使用多个数据源和建立多个服务连接。 目前提供[超过 150 台连接器](https://docs.microsoft.com/powerapps/connections-list#all-connectors)，支持同时使用本地数据和云数据、Microsoft Office 365 和 Azure 服务（如 Flow 和 Dynamics 365 ）以及多种第三方服务（包括 Dropbox、Google、Salesforce 和 Slack 等常用服务）。 现在可在用户所需的位置而不仅是原始数据所在的位置生成可缩放的解决方案。

## <a name="powerapps-and-sharepoint-even-better-together"></a>PowerApps 和 SharePoint：配合使用，效果更佳

PowerApps 是一款很棒的工具，可通过两种方式提供更好的 SharePoint 体验。 可选择自定义 SharePoint 列表的表单或创建独立应用以使用 SharePoint 数据。

**自定义 SharePoint 表单**非常适合以下情形：你的用户需要在日常工作中使用列表，但是你希望自定义他们在 SharePoint 列表中添加/查看/编辑项的方式。 单击“自定义表单”会创建一个单屏“表单应用”，该应用基于上下文更改模式（新建/编辑/查看）。 这些应用由 SharePoint 进行管理；其权限与列表编辑/查看权限相同。

**通过 SharePoint 创建 PowerApps 画布应用**支持应用在移动设备上自行运行。 也可在 SharePoint 页面嵌入应用。 单击此功能可创建一个三屏应用（列表视图、新建/编辑表单、查看表单）。  这些应用的权限/共享模型不依赖于 SharePoint，而是通过 PowerApps 进行管理。

现已介绍两种选项的区别，下面的部分将概述二者的使用方法。

## <a name="sharepoint-forms"></a>SharePoint 表单

PowerApps 团队和 SharePoint 团队合作创造了新的 SharePoint 自定义使用体验。  如果你与大多数 InfoPath 开发人员一样，那么应该已了解如何使用 InfoPath 与 SharePoint 进行交互。 虽然 SharePoint 很出色，但默认表单略显呆板，并且不允许在不使用 InfoPath 的情况下使用自定义或业务逻辑。 然而现在不一样了。

现在可以使用 PowerApps 自定义列表表单（作为本机功能）。 并且执行此操作时可以获得 PowerApps 的完整功能。 下面的屏幕截图显示了嵌入 Power BI 报表的 PowerApps 表单示例。  整个解决方案在 15 分钟内完成。

![SharePoint 集成](./media/transform-infopath/sharepoint-integration.png)

PowerApps 的另一个重要功能是，能够轻松从同一表单连接到其他 SharePoint 站点集合或其他环境。 比如，是否希望一个表单能够同时在 SharePoint Online 和 SharePoint 本地环境中显示和更新数据？ 没问题。 安装[本地数据网关](https://docs.microsoft.com/powerapps/gateway-management)，几分钟后便可启动和运行，然后实现 PowerApps、Power BI、Microsoft Flow 和 Azure 逻辑应用与本地数据之间的连接。 无需更改防火墙规则。 通过将此应用与 Microsoft Flow 连接，可以利用另一级别的功能。

## <a name="a-standalone-sharepoint-app"></a>独立 SharePoint 应用

如果想要基于 SharePoint 数据生成完整独立的应用，而不只是更新列表表单体验，则需要使用此方法。 这也是入门的最佳方法，可以开始了解 PowerApps 画布以及如何通过诸多数据源中的任何一个来生成未来的应用。

要开始此过程，请转到要与其进行交互的 SharePoint 列表，然后：

1. 单击菜单栏中的“PowerApps”
2. 选择“创建应用”
3. 提供名称。
4. 单击“创建”

PowerApps 随即生成可自定义的默认应用。

从简单操作入手。 对于第一个应用，使用仅包含几个不同类型字段的简单自定义列表。 这样既可以获得完善的基础认知，又不会觉得难以应付。 不用担心；你很快就能成为能够创建和处理复杂应用的专业人士。  如需获取有关第一个应用的演练帮助，请查看此[文档](https://docs.microsoft.com/powerapps/generate-app-from-sharepoint-list-interface)或此社区[视频](https://youtu.be/BnYe_7fpZRM)。 下面的示例将演示常见的 InfoPath 任务以及如何在 PowerApps 中完成这些任务。 所有示例均基于简单的 SharePoint 列表应用生成。

# <a name="how-do-you-do-that-with-powerapps"></a>如何使用 PowerApps 完成任务

现已介绍完基本概念，接下来将进行深入探索。 在已创建第一个应用的前提下，下面的部分可帮助你在 PowerApps 中应用一些常见的 InfoPath 概念。

**基于值隐藏/显示/锁定字段**  
制作成功表单的最常见方法之一就是使用强大的业务逻辑并能够强制执行该逻辑。 实现此操作的一种方法是基于值或操作更改字段状态。 利用 PowerApps，可以选择控件并将 DisplayMode 设置为“编辑”或“查看”，以指定用户是否可以更改该字段。 另一种方法是使用简单的 If 公式有条件地执行此操作。 首先，选择要编辑的标签，然后单击锁定图标将卡进行解锁，以便更改值。

![隐藏显示锁定数据卡](./media/transform-infopath/hide-show-lock.png)

现在，从右侧滚动到卡的底部，然后编辑 DefaultMode 属性。

![If Else 语句表达式](./media/transform-infopath/if-else-statement.png)

此示例使用 If 语句。 If(ThisItem.Color = &quot;Blue&quot;, DisplayMode.View, DisplayMode.Edit) 此语句表示，如果当前项“颜色”字段为“蓝色”，则“动物”字段为只读，否则该字段为可编辑。

如果不希望显示此卡，则可以直接在 DisplayMode 上的“可见”字段插入相似函数。

还可以在此处隐藏“审批”按钮，以便仅在用户电子邮件地址与审批者电子邮件匹配时显示该按钮。 提示：User().Email 指访问当前用户的电子邮件地址的方式。 因此，可将按钮的“可见”值设置为 If(YourDataCard.Text = User().Email, true, false)，其中 YourDataCard 是存储审批者电子邮件地址的卡。

**条件格式设置**  
按照上述隐藏字段的相似方式，还可以向用户提供可视反馈。 当输入值不在可接受范围内时，可能需要用红色突出显示文本；或者，可能需要更改上传按钮的文本和颜色以在上传文件后将其删除。 所有这些操作都可以通过在“颜色”或“可见”等字段中使用 If 等函数来实现。

例如，当用户在输入框中输入格式不正确的电子邮件时，可以配合使用 If 函数和 [IsMatch](https://docs.microsoft.com/powerapps/functions/function-ismatch) 函数来将电子邮件字段的文本颜色改为红色。 可以通过将 TextInput1 的“颜色”值设置为 If(IsMatch(TextInput1.Text, Email), Black, Red) 来实现此操作，其中 TextInput1 是用户键入电子邮件地址的字段。 IsMatch 支持大量预定义模式（如电子邮件）或创建自己的模式。 有关条件格式设置的详细信息，请查看此[社区视频](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Conditional-Formatting-and-Popups/m-p/84962)。

**实现基于角色的安全性**  
第一个要考虑的函数是 [DataSourceInfo](https://docs.microsoft.com/powerapps/functions/function-datasourceinfo)。 从数据源获取的信息会基于数据源而有所不同，但通常可以使用 DataSourceInfo(YourDataSource, DataSourceInfo.EditPermission) 检查用户是否有权编辑数据。 将 YourDataSource 替换为数据源名称。 通过此操作，可以仅显示用户有权编辑的表单或按钮。 有关可在此函数中查询的完整信息列表，请查看 DataSourceInfo 文档。

但是，如果要使用 Active Directory 组管理对应用中的按钮或表单的访问权限，则需要进一步操作。 执行此操作需要利用 PowerApps 的灵活性，还需使用 Microsoft Graph API 创建自己的连接器。 尽管听起来有些困难，但可通过参阅一个提供分布操作的[文档](https://powerapps.microsoft.com/blog/implementing-role-based-permission/)来获取指导。

**从应用发送电子邮件**  
可通过多种方法从 PowerApps 中发送电子邮件。 最简单的方法是使用 Office 365 Outlook 连接器。 利用此连接器，可以按本人身份从应用发送电子邮件。 还可以获取电子邮件和与邮箱交互的其他任务。 有关如何发送电子邮件，请参考[文档](https://docs.microsoft.com/powerapps/connections/connection-office365-outlook)或此社区[视频](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Send-an-email-from-PowerApps/m-p/74349)。

如果需要发送较复杂的电子邮件，例如通过创建 SharePoint 审批工作流批准链来发送，则需要创建 Microsoft Flow 并将应用与其相连接。 将应用连接到 Microsoft Flow 后，便可使用已与外部数据和服务建立良好连接的工作流引擎（如 PowerApps）的完整功能。 有关连接 PowerApps 和 Microsoft Flow 的详细信息，请查看此[文档](https://docs.microsoft.com/powerapps/using-logic-flows)。

如果仍未找到要查找的电子邮件选项，还可以使用适用于 Benchmark Email、Gmail、MailChimp、Outlook.com、SendGrid 或 SMTP 的 PowerApps 连接器。 这就是 PowerApps 的魅力 - 连接性。

**工作流**  
说到商业应用程序和业务逻辑则不得不提工作流引擎。 好消息是，PowerApps 团队并未大费周章地重新创建另一个工作流引擎。 相反，他们提供可连接 Microsoft Flow 服务的可靠连接器。 现在，通过其易于使用的工作流引擎，可跨超过 [200 种不同服务](https://flow.microsoft.com/connectors/)自动执行进程和任务。 有关连接 PowerApps 和 Microsoft Flow 的详细信息，请查看此[文档](https://docs.microsoft.com/powerapps/using-logic-flows)。

**PowerApps 的变量**  
生成解决方案时，我们往往认为必须使用变量。 虽然 PowerApps 提供三种类型的变量，但仅需在必要时使用。 与其考虑获取数据，在变量中存储数据并引用该变量，不如考虑直接引用该数据。 实现此目的的最佳方法是使用 Excel。 在 Excel 中，“合计”不是变量，而是其他字段的总和。 因此，如果要在工作表的其他位置使用该值，则需指定用于计算该合计值的字段。 可阅读[文档](https://docs.microsoft.com/powerapps/working-with-variables)，获取与此相关的说明。 体验不同的思维过程。

如果仍然需要变量（很多情况都是如此），可通过这种方式了解不同的操作选择。 请牢记，使用 PowerApps 时无需定义变量。 只需使用一个函数指定要存储的名称和值即可创建变量。 通过单击菜单栏中的“查看”，然后选择“变量”，即可查看已创建的变量。 变量保留在内存中，其值会在应用关闭后丢失。 三种变量类型如下：

- 全局变量往往是用户首先想到的变量。 此处可使用 [Set](https://docs.microsoft.com/powerapps/functions/function-set) 函数指定变量的值，随后此值可在整个应用中使用。 该函数的一个用例是 Set(YourVariable, YourValue)。 然后可在整个应用中通过名称引用 YourVariable。
- 上下文变量是仅在其被定义的屏幕上可用的变量。 离开屏幕时，上下文变量会重置。 这些变量通常用于存储上一屏幕传递的信息，或跟踪表单是否已提交等。 [UpdatedContext](https://docs.microsoft.com/powerapps/functions/function-updatecontext) 的常见用例为 UpdateContext( { Submitted: "true" } ) 这会将 Submitted 变量设置为 true。 你可能会在页面上设置提交按钮的这一部分，用于跟踪信息是否已提交并将所有字段更改为只读。 注意：使用“:”集合存储可以单独更新的信息表。 请参阅 [Collect](https://docs.microsoft.com/powerapps/functions/function-clear-collect-clearcollect) 了解相关信息。 创建购物车就是一个用例，因为用户会对其想要发送的各种 SharePoint 项进行标记。 此社区[视频](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Learn-about-PowerApps-Collections/m-p/89180)通过实际操作演示这一概念。

**级联下拉列表**  
级联下拉列表非常有用。 使用级联下拉列表可基于在上一下拉列表中选择的值筛选某一下拉列表中的选项。 在 PowerApps 中，通常可通过在应用中包含两个数据源来创建级联下拉列表。 第一个数据源是正在使用或更新的数据，第二个数据源用于存储生成所需的级联效果所需的值。 下面是具有选择选项的第二个数据源的示例。

![级联下拉列表](./media/transform-infopath/cascading-dropdowns.png)

现在创建第一个下拉列表控件，对“项”属性使用公式 Distinct(Impacts, Title)，以便仅在下拉列表中显示“成本”、“程序影响”和“计划”。 接下来，添加第二个下拉列表，将“项”属性设置为 Filter(Impacts,ddSelectType.Selected.Value in SCategory)，其中 ddSelectType 是第一个下拉列表框的名称。 这样便创建了级联下拉列表。 有关详细信息，请查看 PowerApps 团队的博客文章 [SharePoint: Cascading Dropdowns in 4 Easy Steps!](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/SharePoint-Cascading-Dropdowns-in-4-Easy-Steps/ba-p/16248)（SharePoint：4 步轻松创建级联下拉列表！） 或此[社区视频](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Cascading-Dropdown/m-p/92813)，别担心，不使用 SharePoint 也同样可以轻松完成此操作。

**不要生成一个超级应用**  
PowerApps 支持从一个应用调用另一个应用。可以生成可相互调用甚至传递数据的一组应用，从而简化开发工作，而无需使用“泡泡糖”式的方法“粘贴”出一个大型 InfoPath 表单。

## <a name="next-steps"></a>后续步骤

利用上述信息，现在便可投入实际工作，并开始逐一攻克一系列 PowerApps 应用。 在继续探索的过程中，可借助以下便捷的链接。 其中包括 PowerApps 社区站点的链接。 立刻加入社区，与孤军奋战相比，社区可快速提升技能。

[**公式参考**](https://docs.microsoft.com/en-us/powerapps/formula-reference) - 只需浏览某些默认函数，便能让灵感迸发。

[**PowerApps 社区**](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1) - 查看示例，与他人互动，提出和解答问题，帮助壮大 PowerApps 社区。