---
title: 将 InfoPath 窗体转换为画布应用 | Microsoft Docs
description: 借助常见方案的相关信息以及在画布应用中创建这些项的方法，开始将 InfoPath 窗体转换为 PowerApps。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/05/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a5b9ddb2006a53796f782db3c620fa592f2a5aed
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71994887"
---
# <a name="transform-your-infopath-form-to-powerapps"></a>将 InfoPath 窗体转换为 PowerApps

是否在 InfoPath 中创造了出色的内容，很想了解如何在更可靠的平台上交付这些内容？

## <a name="key-advantages-of-powerapps-over-infopath"></a>PowerApps 相较于 InfoPath 的主要优点

如果你和大多数 InfoPath Power 用户一样，使用独特的技能组合构建出色的窗体已有一段时日。 虽然你对窗体感到十分满意，但也发现存在一定的局限性：设计传统，移动设备体验不够完美，未来可用性不明确，以及如果不编写代码，连接到其他服务时总会受到重重束缚&quot;&quot;。

PowerApps 团队已知晓这些问题及其他许多难题。 他们努力改善体验，旨在让你能够利用现有业务和技术技能创建画布应用。 借助 PowerApps，你可以快速生成和部署适合的业务解决方案，而无需编写代码。

**通过 PowerApps 成就辉煌未来**  
PowerApps 是一个软件即服务 (SaaS) 平台，用户无需增添任何额外工作，即可通过该平台快速构建功能强大的应用并将其部署到 Web、SharePoint、Dynamics 365、Teams、Power BI 或移动设备。 由于你只需向他人提供已发布应用的 URL 即可完成部署，因此，更新也异常简单。

**共享应用**  
你曾经尝试过生成应用，然后将其发布到 iOS 或 Android 设备吗？ 这个操作很复杂。 如果你想部署第二个应用或更新现有应用，你的用户必须执行更多的步骤。 使用 PowerApps 就不存在这些问题。 你的用户可在其设备上安装 PowerApps Mobile 并登录。 他们就可拥有你与之共享的所有功能强大的应用。 在此之后，当你更新这些应用或向用户推送新应用时，这些应用会在用户设备上显示。 无需进行设备管理的移动应用能为你和你的业务带来巨大优势。

**关于移动**  
通过 PowerApps，你可以利用用户移动设备的功能。 你可以从应用内访问加速功能、照相机、指南针、连接信息和位置信号。 这为生成用于完成工作的应用创造了无限可能性。 当然，触摸是 PowerApps 中的自动功能，生成应用时无需任何编码操作。

**摆脱束缚**  
通过 InfoPath，你通常处理的是来自一个源的数据。 但是，如果你想更新另一个源（如另一个站点集合中的 SharePoint 列表）或连接到外部服务，事情就会变得比较棘手。 代码后面的诸多概念会让你夜不能寐。 PowerApps 的设计宗旨是允许在一个应用中使用多个数据源和建立多个服务连接。 目前，[200 多个连接器](connections-list.md#all-standard-connectors)支持本地数据和云数据的组合，包括 Microsoft Flow 和 Dynamics 365 等 Microsoft Office 365 和 Azure 服务。 此外，你还可以连接到众多第三方服务，如 Dropbox、Google、Salesforce、Slack 和其他常用的目标。

现在可在用户所需的位置而不仅是原始数据所在的位置生成可缩放的解决方案。

## <a name="powerapps-and-sharepoint-even-better-together"></a>PowerApps 和 SharePoint：配合使用，效果更佳

PowerApps 是一款很棒的工具，可通过两种方式提供更好的 SharePoint 体验。 可选择自定义 SharePoint 列表的表单或创建独立应用以使用 SharePoint 数据。

如果想要自定义用户添加、查看或编辑其日常工作中所用列表中各项的方式，建议使用“自定义 SharePoint 表单”功能。 单击“自定义表单”会创建一个单屏&quot;表单应用&quot;，该应用将基于上下文更改模式（新建/编辑/查看）。 由 SharePoint 管理这些应用；其权限与列表编辑/查看权限相同。

**通过 SharePoint 创建 PowerApps 画布应用**支持应用在移动设备上自行运行。 你还可以在 SharePoint 页中嵌入应用程序。 单击这个功能将创建一个三屏应用（浏览列表、查看详细信息和创建/更新项）。 这些应用的权限/共享模型不依赖于 SharePoint，而是通过 PowerApps 进行管理。

至此，已介绍两种选项的区别，下面的部分将概述二者的使用方法。

## <a name="sharepoint-forms"></a>SharePoint 表单

PowerApps 团队和 SharePoint 团队协作创造了 SharePoint 自定义使用体验。 如果你与大多数 InfoPath 开发人员一样，那么应该已了解如何使用 InfoPath 与 SharePoint 进行交互。 虽然 SharePoint 很出色，但默认表单略显呆板，并且不允许在不使用 InfoPath 的情况下使用自定义或业务逻辑。 然而现在不一样了。

现在可以使用 PowerApps 自定义列表表单（作为本机功能）。 并且执行此操作时可以获得 PowerApps 的完整功能。 下面的屏幕截图显示了嵌入 Power BI 报表的 PowerApps 表单示例。 整个解决方案在 15 分钟内完成。

![SharePoint 集成](./media/transform-infopath/sharepoint-integration.png)

PowerApps 的另一个重要功能是，能够轻松从同一表单连接到其他 SharePoint 站点集合或其他环境。 比如，是否希望一个表单能够同时在 SharePoint Online 和 SharePoint 本地环境中显示和更新数据？ 没关系。 如果安装[本地数据网关](gateway-management.md)，几分钟后便可正常运行，然后实现 PowerApps、Power BI、Microsoft Flow 和 Azure 逻辑应用与本地数据之间的连接。 不需要更改防火墙规则。 你可以通过将此应用与 Microsoft Flow 连接做进一步的设置。

## <a name="a-standalone-sharepoint-app"></a>独立 SharePoint 应用

如果想要基于 SharePoint 数据生成完整独立的应用，而不只是更新列表表单体验，则建议使用此方法。 这也是入门的最佳途径，你可以开始了解 PowerApps 画布如何工作，以及如何通过诸多数据源中的任何一个来生成未来的应用。

若要开始使用，请执行以下这些步骤：

1. 打开要从其中生成应用的 SharePoint 列表。
1. 在菜单栏上，选择“PowerApps”，然后选择“创建应用”。
1. 提供一个名称，然后选择“创建”。

PowerApps 将生成一个可自定义的应用。

对于第一个应用，请从仅包含几个不同类型字段的简单自定义列表入手。 这样既可以获得完善的基础认知，又不会觉得难以应付。 不用担心；你很快就能成为能够创建和处理复杂应用的专业人士。 如需获取有关第一个应用的演练帮助，请查看此[文档](app-from-sharepoint.md#generate-an-app-from-within-sharepoint-online)或此社区[视频](https://youtu.be/BnYe_7fpZRM)。 下面的示例将演示常见的 InfoPath 任务以及如何在 PowerApps 中完成这些任务。 所有示例均基于简单的 SharePoint 列表应用生成。

## <a name="how-do-you-do-that-with-powerapps"></a>如何使用 PowerApps 完成任务？

至此，基本概念已介绍完毕，接下来将进行深入探索。 在已经创建第一个应用的基础上，本部分将帮助你在 PowerApps 中应用一些常见的 InfoPath 概念。

基于值隐藏/显示/锁定字段  
成功的表单通常会通过基于值或操作更改字段的状态等来强制实施强大的业务逻辑。 利用 PowerApps，你可以将控件的 DisplayMode 属性设置为“Edit”或“View”，以指定用户是否可以更改该字段。 此外，也可以使用简单的 If 公式有条件地执行此操作。 首先，选择要编辑的卡，然后选择锁定图标。 此步骤会解锁卡，以便可以更改值。

![隐藏显示锁定数据卡](./media/transform-infopath/hide-show-lock.png)

在右侧窗格中，滚动到 " **DisplayMode** " 属性以便对其进行编辑。

![If Else 语句表达式](./media/transform-infopath/if-else-statement.png)

此示例使用 If 公式：

```If(ThisItem.Color = "Blue", DisplayMode.View, DisplayMode.Edit)```

此公式表示，如果当前项的“颜色”字段是“蓝色”，“动物”字段将是只读的。 否则，该字段是可编辑的。

若要隐藏卡而不是使其只读，请在 DisplayMode 正上方的 Visible属性中插入相似函数。

另外，你还可以显示批准按钮，只要用户的电子邮件地址与审批者的电子邮件地址相匹配即可。 提示使用**用户（）。通过电子邮件**访问当前用户的电子邮件地址。）因此，你可以将审批者的电子邮件地址存储在 YourDataCard 中，然后将按钮的 Visible 属性设置为此公式：

```If( YourDataCard.Text = User().Email, true, false )```

**条件格式设置**  
按照上述隐藏字段的相似方式，还可以向用户提供可视反馈。 当输入的值不在可接受范围内时，可能需要用红色突出显示文本；或者，在用户上传文件后，需要更改上传按钮的文本和颜色。 你可以在 Color 或 Visible 等属性中使用一个函数，如 If 来完成这两个操作。

例如，当用户在输入框中输入格式不正确的电子邮件时，可以配合使用 If 函数和 [IsMatch](functions/function-ismatch.md) 函数将电子邮件字段的文本颜色改为红色。 通过将 TextInput1（用户在此处键入电子邮件地址）的 Color 值设置为下面这个公式来执行此操作：

```If( IsMatch(TextInput1.Text, Email), Black, Red )```

IsMatch支持大量预定义模式（如电子邮件）或创建自己的模式。 有关条件格式设置的详细信息，请查看此[社区视频](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Conditional-Formatting-and-Popups/m-p/84962)。

**实现基于角色的安全性**  
第一个要考虑的函数是 [DataSourceInfo](functions/function-datasourceinfo.md)。 从数据源返回的信息将各不相同，但是通常可以使用此公式确认用户是否有权限编辑数据（将 YourDataSource 替换为你的数据源名称）：

```DataSourceInfo( YourDataSource, DataSourceInfo.EditPermission )```

这样，只要用户有权限编辑，你就能显示表单或按钮。 查看 [DataSourceInfo](functions/function-datasourceinfo.md) 文档，了解你可以在此函数中进行查询的完整信息列表。

如果想要使用 Active Directory 组来管理对应用中的按钮或表单的访问权限，则需要做深入了解。 为此，你不仅需要利用 PowerApps 的灵活性，还要使用 Microsoft Graph API 创建自己的连接器。 如果觉得有些难，可以按照此[博客文章](https://powerapps.microsoft.com/blog/implementing-role-based-permission/)获取分步指南。

**从应用发送电子邮件**  
你可以通过多种方式从 PowerApps 发送电子邮件，但最简单的方式是使用 Office 365 Outlook 连接器。 利用此连接器，可以用本人身份从应用发送电子邮件。 还可以获取电子邮件和与邮箱交互的其他任务。 有关如何发送电子邮件的说明，请参考[文档](connections/connection-office365-outlook.md)或此社区[视频](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Send-an-email-from-PowerApps/m-p/74349)。

你可以通过 Microsoft Flow 并将应用连接到创建的流来发送更为复杂的邮件（例如，作为 SharePoint 审批工作流的一部分）。 将应用连接到 Microsoft Flow 后，便可使用已与外部数据和服务建立良好连接的工作流引擎（如 PowerApps）的完整功能。 有关如何连接 PowerApps 和 Microsoft Flow 的详细信息，请查看此[文档](using-logic-flows.md)。

如果仍未找到要查找的电子邮件选项，还可以使用适用于 Benchmark Email、Gmail、MailChimp、Outlook.com、SendGrid 或 SMTP 的 PowerApps 连接器。 连接性就是 PowerApps 的魅力。

**工作流**  
说到商业应用程序和业务逻辑就不得不提工作流引擎。 好消息是，PowerApps 团队并未大费周章地重新创建另一个工作流引擎。 相反，他们提供可连接 Microsoft Flow 服务的可靠连接器。 通过其易于使用的工作流引擎，可跨超过 [200 种不同服务](https://flow.microsoft.com/connectors/)自动执行进程和任务。 有关如何连接 PowerApps 和 Microsoft Flow 的详细信息，请查看此[文档](using-logic-flows.md)。

**PowerApps 的变量**  
生成解决方案时，我们会很自然地认为必须使用变量。 PowerApps 提供了多个类型的变量，但请仅在必要时使用。 与其考虑获取数据，在变量中存储数据并引用该变量，不如考虑直接引用该数据。 如果将其与 Excel 比较，就可以更好地了解此模型。 在 Excel 中，“合计”不是变量，而是其他字段的总和。 因此，如果要在工作表的其他位置使用该值，则需指定在其中计算该合计值的单元格。 [文档](working-with-variables.md)中对此有很好的解释。 体验不同的思维过程。

如果仍然需要变量（很多情况都是如此），可通过这种方式了解不同的操作选项。 请牢记，使用 PowerApps 时无需定义变量。 只需使用一个函数指定要存储的名称和值即可创建变量。 通过选择“查看”选项卡上的“变量”，可以查看你创建的变量。变量保留在内存中，其值会在应用关闭后丢失。 可以创建这几类变量：

- 全局变量往往是用户首先想到的变量。 使用 [Set](functions/function-set.md) 函数指定全局变量的值，并使此值可在整个应用中使用：

    ```Set( YourVariable, YourValue )```

    然后可在整个应用中通过名称引用 YourVariable。

- 上下文变量仅在其被定义的屏幕上可用。 离开屏幕时，此类变量就会重置。 这些变量通常用于存储上一屏幕传递的信息，或跟踪表单是否已提交等。 若要设置上下文变量，请使用 [UpdateContext](functions/function-updatecontext.md)，如此示例所示：

    ```UpdateContext( { Submitted: "true" } )```

    此示例将名为“Submitted”的变量值设置为 true。 你可能会将此公式添加到提交按钮的 OnSelect 属性，用于跟踪信息是否已提交并将所有字段更改为只读。

- 集合用来存储可以单独更新的信息表。 使用 [Collect](functions/function-clear-collect-clearcollect.md) 创建一个购物车就是一个用例，因为用户会对其想要发送的各种 SharePoint 项进行标记等。 社区[视频](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/Learn-about-PowerApps-Collections/m-p/89180)通过实际操作演示这一概念。

**级联下拉列表**  
级联下拉列表非常有用，例如，你可以基于在上一个下拉列表中选择的值筛选一个下拉列表中的选择。 在 PowerApps 中，通常可通过在应用中包含两个数据源来创建级联下拉列表。 第一个数据源是你正在查看或更新的数据，第二个数据源用于存储生成级联效果所需的值。 此图表显示了具有选择选项的第二个数据源的示例。

![级联下拉列表](./media/transform-infopath/cascading-dropdowns.png)

在此示例中，可以添加一个名为“ddSelectType”的下拉列表，并将其“Items”属性设置为此公式：

```Distinct( Impacts, Title )```

下拉列表中将仅显示成本、程序影响和计划。 然后可以添加第二个下拉列表并将其“Items”属性设置为此公式：

```Filter( Impacts, ddSelectType.Selected.Value in SCategory )```

这样便创建了级联下拉列表。 有关详细信息，请查看 PowerApps 团队 [SharePoint：4个简单步骤中的级联下拉菜单！ ](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/SharePoint-Cascading-Dropdowns-in-4-Easy-Steps/ba-p/16248) 或此[社区视频](https://powerusers.microsoft.com/t5/Video-Webinar-Gallery/PowerApps-Cascading-Dropdown/m-p/92813)。 别担心，不使用 SharePoint 也同样可以轻松完成此操作。

**不要生成一个超级应用**  
PowerApps 支持从另一个应用调用应用。 你可以生成一组能够相互调用甚至传递数据的应用，从而简化开发工作，而无需使用“泡泡糖”式的方法粘接出一个大型 InfoPath 表单。

## <a name="next-steps"></a>后续步骤

利用 PowerApps 和本主题中的信息，现在便可投入实际工作，并开始逐一攻克一系列应用。 当你继续你的旅程时，下面提供了一些方便有用的链接，如指向 PowerApps 社区站点的链接。 与孤军奋战相比，现在加入社区，就可快速提升你的技能。

[**公式参考**](formula-reference.md) - 只需浏览某些默认函数，便能让灵感迸发。

[**PowerApps 社区**](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1) - 查看示例，与他人互动，提出和解答问题，帮助壮大 PowerApps 社区。
