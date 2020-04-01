---
title: 危机通信应用-示例模板 |Microsoft Docs
description: 了解 Power Apps 中的危机通信示例模板。
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/31/2020
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fedcec7c8f3f093bf59b3ef607cbe4fbeea6ac54
ms.sourcegitcommit: f5d15c973b2a129a0cc29a74cf8eaf6b24fbf36d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2020
ms.locfileid: "80516720"
---
# <a name="set-up-and-learn-about-the-crisis-communication-sample-template-in-power-apps"></a>设置并了解 Power Apps 中的危机通信示例模板

危机通信应用提供用户友好的体验，以将用户连接到有关危机的信息。 快速获取内部公司新闻的更新，获取常见问题的答案，并获取对链接和紧急联系人等重要信息的访问权限。 要拥有此应用，需完成少量设置。

在本演练中，您将学习如何：

- 创建数据的位置。
- 同时导入危机通信应用和管理应用。
- 为应用程序创建内容。
- 导入流以向用户发送通知。
- 创建集中管理的团队，以聚合数据并有效地响应问题。

完成这些步骤所需的估计时间： **20&ndash;25 分钟**。

> [!NOTE]
> "危机通信示例" 模板还适用于 "美国政府和电源自动化美国政府计划"。 适用于 Power Apps 和 Power Apps 的服务 Url 与商业版本不同。 详细信息： [Power APPS Us 政府服务 url](https://docs.microsoft.com/power-platform/admin/powerapps-us-government#power-apps-us-government-service-urls)和[电源自动化美国政府服务 url](https://docs.microsoft.com/power-automate/us-govt#power-automate-us-government-service-urls)

## <a name="demo-crisis-communication-app"></a>演示：危机通信应用

观看如何使用危机通信解决方案。

> [!VIDEO https://www.youtube.com/embed/23SypLXiOTw]

## <a name="prerequisites"></a>先决条件

- [注册](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)电源应用的 。
- 您必须具有有效的 SharePoint Online 许可证和权限才能创建列表。
- 您必须有一个公共 SharePoint 站点，您可以在其中存储应用程序的数据。
- 从[aka.ms/CrisisCommunicationSolution](https://aka.ms/CrisisCommunicationSolution)下载资产。

> [!IMPORTANT]
> 有关与危机通信应用相关的任何反馈或问题，请使用以下链接：
> - **[意见](https://aka.ms/crisis-communication-feedback)**
> - **[发放](https://aka.ms/crisis-communication-issues)**

## <a name="demo-build-and-deploy-the-crisis-communication-app"></a>演示：构建和部署危机通信应用

观看如何生成和部署危机通信应用。

> [!VIDEO https://www.youtube.com/embed/Wykrwf9dZ-Y]

## <a name="create-a-home-for-your-data"></a>为数据创建家庭

应用的数据存储在 SharePoint 列表中，因此第一步是创建新的 SharePoint 站点。

### <a name="create-a-sharepoint-site"></a>创建 SharePoint 站点

1. 登录到[Office online](https://www.office.com)，然后选择 " **SharePoint**"。
1. 选择 "**创建网站**"。

    ![示例 SharePoint 站点](media/sample-crisis-communication-app/01-Create-Site.png)

1. 选择 "**团队网站**"。

    ![团队网站](media/sample-crisis-communication-app/02-Team-Site.png)

1. 输入站点的名称和描述。
1. 将**隐私设置**设置为 "**公共**"，以便公司中的每个人都可以获取必要的信息。

    ![网站设置](media/sample-crisis-communication-app/03-Privacy-Settings.png)

1. 选择 **“下一步”** 。
1. 添加站点的其他所有者（可选）。
1. 选择“完成”。

### <a name="create-sharepoint-lists-for-the-app"></a>为应用程序创建 SharePoint 列表

此应用使用多个列表存储其数据。 可以使用已下载的 "[资产包](#prerequisites)" 中提供的 DeploySPLists 流来自动创建这些列表。

#### <a name="import-the-sharepoint-list-deployment-flow"></a>导入 SharePoint 列表部署流

1. 请参阅[flow.microsoft.com](https://flow.microsoft.com)。
1. 从左侧导航窗格中选择 **"我的流**"。
1. 在命令栏上选择 "**导入**"。
1. 上传**DeploySPLists**<!--edit to the file name okay, here and in the following instances?--> GitHub 存储库中的包。

    ![导入包](media/sample-crisis-communication-app/import-package.png)

1. 通过选择 "**在导入期间选择**" 链接并完成窗体，为新流添加 SharePoint 连接。

    ![导入设置](media/sample-crisis-communication-app/import-settings.png)

1. 如果需要创建新的 SharePoint 连接，请在 "**导入设置**" 窗格中选择 "**新建**"。
1. 在命令栏上选择 "**新建连接**"。

    ![创建新连接](media/sample-crisis-communication-app/create-connection.png)

1. 搜索连接的名称，例如*SharePoint*。
1. 选择创建的连接。<!--edit okay?-->
1. 选择“保存”。
1. 选择“导入”。

#### <a name="edit-the-sharepoint-list-deployment-flow"></a>编辑 SharePoint 列表部署流

1. 导入完成后，请切换到 **"我的流**" 并刷新流的列表。
1. 选择新导入的流**DeploySPLists**。
1. 在命令栏上选择 "**编辑**"。
1. 打开 "**变量–列表的目标网站**" 卡。
1. 对于 "**值**"，请输入 SharePoint 站点的名称。
1. 打开**变量–应用名称**卡。
1. 对于 "**值**"，请输入应用的名称;默认情况下，该名称为**危机通信**。

    ![流参数](media/sample-crisis-communication-app/04-Flow-Settings.png)

1. 选择“保存”。

#### <a name="run-the-sharepoint-list-deployment-flow"></a>运行 SharePoint 列表部署流

1. 返回到**DeploySPLists**流的详细信息屏幕。
1. 在命令栏上选择 "**运行**"。
1. 选择 "**继续**"，然后选择 "**运行流**"。

    ![登录以运行流](media/sample-crisis-communication-app/sign-in-flow.png)

    ![运行流](media/sample-crisis-communication-app/run-flow.png)

> [!NOTE]
> 你可能会收到一条错误，指出需要位置服务。
如果出现这种情况，则允许位置服务访问<!--edit okay? I wasn't sure what this meant.--> 在重试之前，请先关闭并刷新页面。

流在 SharePoint 站点中创建以下 SharePoint 列表。<!--general note; You don't need to introduce tables or graphics with colons, only lists.-->

| **显示标题**| 用途 | **说明** |
|-|-|-|
| CI_LogosAssets| 若要从应用程序中引用徽标和/或其他图像，则为。 徽标将通过直接链接在 Power Apps 中引用，或通过要使用的徽标的 ID 号来引用。 | 适用于 *[App Name]* 应用的相关徽标和其他图像资产的库。 |
| CI_configAdminSetup | 用于由应用程序的管理员进行的功能配置。<br>**注意**：对于非管理员成员，此列表应为只读。 | *[应用名称]* 应用的管理配置列表。
| CI_Contacts | 使用默认的 "联系人" 内容类型来捕获有关联系人的信息。 （不包括人员选取器，因此可能需要手动维护此列表<!--edit okay?--> 确保其数据是最新的。）<br>**注意**：这取决于全局联系人列表类型在列表中的默认内容类型。 | *[应用名称]* 应用的联系人列表。|
| CI_CompanyNews | **公司新闻**项的集合。 | 用于管理 *[App Name]* 应用中显示的新闻项目的列表。 你可以使用 "已**弃用**" 列从应用程序视图中删除新闻项<!--edit okay, here and below? You use this pattern ("remove ___ from the app views") in the "Helpful tips" description, and it seems a bit more descriptive than "filter ___ out of the app".-->，同时将它们作为记录保留。 | 
| CI_FAQ  | 常见问题。 | *[应用名称]* 应用的常见问题列表。 您可以使用 "已**弃用**" 列从应用程序视图中删除 FAQ 项，同时将它们作为记录保留。 |
| CI_UsefulLinks<!--edit okay? The sharepoint-lists.png screenshot later in this article shows it as "Usefulinks," which probably isn't correct either.--> | 有用的超链接列表。 | *[应用名称]* 应用的有用超链接列表。 您可以使用 "已**弃用**" 列从应用程序视图中删除超链接项，同时将它们作为记录保留。 |
| CI_Employee | 跟踪当前员工状态。 示例：**在家工作** **、请假、** 休假和**on personal leave** **休假**。  **注意**：假设状态为 "正在**工作**"，并且不包含在列表选项中。 | <!--Please check the following edit carefully. This cell was duplicated by mistake from the previous row. Does the note about the "Deprecated" column apply here?-->指示 *[App Name]* 应用的员工状态的消息列表。 您可以使用 "已**弃用**" 列从应用程序视图中删除状态消息，同时将它们作为记录保留。 |
| CI_HelpfulTips             | 用户为其对等方提供的有用提示。 | *[应用名称]* 应用的共享提示管理列表。 您可以使用 "已**弃用**" 列从应用程序视图中删除提示，同时将它们作为记录保留。  |

> [!NOTE]
> - 应将所有这些列表列视为依赖项。
    防止列表意外进行架构更改（例如，允许添加新列，但删除列可能会破坏应用。）
> - 删除列表项时请小心;删除列表项会删除历史记录。 可以打开 "弃用值" 切换 <!--Style Guide-->从**No** "否 **" 到 "是"** 以从联系人、新闻、faq 或链接中删除记录。<!--Should this include status messages too?-->

## <a name="import-and-set-up-the-crisis-communication-app"></a>导入并设置危机通信应用

创建所有 SharePoint 列表后，可以导入应用并将其连接到新的数据源。

> [!NOTE]
> 如果不想使用管理应用，则可以通过手动编辑 SharePoint 列表来编辑这些相同的属性。

### <a name="import-the-app"></a>导入应用

1. 登录到 [Power Apps](https://make.powerapps.com)。
1. 从左侧导航窗格中选择 "**应用**"。
1. 在命令栏上选择 "**导入**"。
1. 上传 GitHub 存储库中的**CrisisCommunication**文件。

    > [!NOTE]
    > 如果你的租户在 GCC 环境下，请上传**CrisisCommunicationGCC**。

    ![导入应用程序包](media/sample-crisis-communication-app/31-Import-App.png)

1. 通过使用 "**在导入期间选择**" 超链接选择适当的连接，完成**Microsoft 团队连接**和**Office 365 用户连接**的导入设置。 可能需要创建[新的连接](add-data-connection.md)（如果它尚不存在）。
1. 选择“导入”。

### <a name="update-the-sharepoint-connections"></a>更新 SharePoint 连接

1. 返回到**应用**列表。
1. 为**危机通信**应用选择**更多命令**（...）。
1. 从上下文菜单中选择 "**编辑**"。

    ![编辑应用](media/sample-crisis-communication-app/05-Edit-App.png)

1. 登录或创建任何所需的连接，然后选择 "**允许**"。

1. 在左窗格中转到 "数据源"。

    ![数据源](media/sample-crisis-communication-app/data-sources.png)

1. 删除应用内的现有 SharePoint 列表<!--Alternatively, this could be "Right-click the name of each existing SharePoint list, and then select **Remove**" if that's how the context menu works here. I think the graphic will be clear enough for the reader, though.-->，因为它们不指向当前的 SharePoint 站点。

    ![删除数据源](media/sample-crisis-communication-app/remove-data-source.png)

1. 从您自己的 SharePoint 站点添加列表。 首先，在搜索栏中搜索**SharePoint** 。

    ![搜索 SharePoint](media/sample-crisis-communication-app/sharepoint.png)

1. 选择 " **SharePoint**"，然后选择连接。

    ![SharePoint 连接](media/sample-crisis-communication-app/sharepoint-connection.png)

1. 将 URL 复制并粘贴到 SharePoint 站点的 "文本" 字段中，然后选择 "**连接**"。

    ![SharePoint 站点 URL](media/sample-crisis-communication-app/site-url.png)

1. 选择所有 SharePoint 列表和库，然后选择 "**连接**"。

    ![连接 SharePoint 列表](media/sample-crisis-communication-app/sharepoint-lists.png)

1. 选择 "**保存**"，然后选择 "**发布**"。

### <a name="optional-enable-location-updates"></a>可选：启用位置更新

此应用允许你记录用户的位置，并在用户设置其状态时将其存储在 SharePoint 站点中。 危机管理团队可以在 Power BI 报表中查看此数据。

> [!NOTE]
> 启用位置更新是可选的。 如果你不想跟踪用户位置，则可以跳过此部分。

**启用位置更新**

1. 搜索**btnDateRange**控件。
1. 在编辑栏中打开**btnDateRange**控件的**OnSelect**属性。
1. 在**OnSelect**属性的编辑栏中复制并粘贴以下代码片段。

    > [!NOTE]
    > 下面的代码片段用于处理早于2020.03.16 的解决方案版本。


    ```
        UpdateContext({locSaveDates: true});
    // Store the output properties of the calendar in static variables and collections.
    ClearCollect(submittedDates,Sort(Filter(selectedDates,ComponentId=CalendarComponent.Id),Date,Ascending));
    Set(varStartDate,First(submittedDates).Date);
    Set(varEndDate,First(Sort(submittedDates,Date,Descending)).Date);
    // Create a new record for work status for each date selected in the date range.
    ForAll(
        Filter(
            RenameColumns(submittedDates,"Date","DisplayDate"),
            ComponentId=CalendarComponent.Id,
            !(DisplayDate in colDates.Date)
        ),
        Patch('CI_Employee Status',Defaults('CI_Employee Status'),
            {
                Title: varUser.userPrincipalName,
                Date: DisplayDate,
                Notes: "",
                PresenceStatus: LookUp(colWorkStatus,Value=WorkStatusComponent.Selected.Value)
                
                // To implement location, add a comma to the line above and uncomment the lines below for latitude and longitude.
                // Latitude: Text(Location.Latitude),
                // Longitude: Text(Location.Longitude)
            }
        )
    );
        // Update existing dates with the new status.
        ForAll(
            AddColumns(
                Filter(
                    RenameColumns(submittedDates,"Date","DisplayDate"),
                    ComponentId=CalendarComponent.Id,
                    DisplayDate in colDates.Date
                ),
                
                // Get the current record for each existing date.
                "LookUpId",LookUp(RenameColumns(colDates,"ID","DateId"),And(Title=varUser.userPrincipalName,Date=DisplayDate)).DateId
            ),
            Patch('CI_Employee Status',LookUp('CI_Employee Status',ID=LookUpId),
                {
                    PresenceStatus: LookUp(colWorkStatus,Value=WorkStatusComponent.Selected.Value)
                }
            )
        );
        If(
            IsEmpty(Errors('CI_Employee Status')),
            
            // Update the list of work status for the logged-in user.
            ClearCollect(colDates,Filter('CI_Employee Status',Title=varUser.userPrincipalName));
            // Send an email receipt to the logged-in user.
            UpdateContext(
                {
                    locReceiptSuccess: 
                    Office365Outlook.SendEmailV2(
                        // To: send an email to oneself
                        varUser.mail,
                        // Subject
                        Proper(WorkStatusComponent.Selected.Value) & ": " & varStartDate & If(varStartDate<>varEndDate," - " & varEndDate),
                        // Body
                        WorkStatusComponent.Selected.DateRangeReceipt & ": " &
                        // Create a bulleted list of dates
                        "<ul>" & 
                            Concat(submittedDates,"<li>" & Date & Char(10)) &
                        "</ul>"
                    )
                }
            );
            If(
                locReceiptSuccess,
                Notify("You successfully submitted your work status. An email has been sent to you with a summary.",NotificationType.Success,3000),
                Notify("There was an error sending an email summary, but you successfully submitted your work status.",NotificationType.Success,3000);
            );
            
            Navigate('Share to Team Screen',LookUp(colStyles,Key="navigation_transition").Value),
            
            // Case: Error submitting work status
            Notify(varString.WorkStatusError,NotificationType.Warning)
        );
        UpdateContext({locSaveDates: false})
    ```

### <a name="optional-add-additional-work-status-messages"></a>可选：添加其他工作状态消息

如果要添加更多工作状态<!--Interesting fact: there is no plural of "status."--> 除了**在家中**和**外出**以外，还可以通过完成以下步骤来执行此操作。 若要开始，您需要更新您的 SharePoint 站点。

1. 返回到您的 SharePoint 站点，然后选择 "**站点内容**"。
1. 选择**CI_Employee 状态**。
1. 如果**PresenceStatus**列不存在，请选择 "**添加列**"。
1. 选择 "**显示/隐藏列**"。

    ![显示/隐藏列](media/sample-crisis-communication-app/36-hide-show-columns.png)

1. 选择<!--edit okay? I didn't know what "Check" meant here.--> **PresenceStatus**。
1. 选择**应用**。
1. 选择**PresenceStatus**列。

    ![选择 PresenceStatus 列](media/sample-crisis-communication-app/37-show-presence.png)

1. 选择 "**列设置**"，然后选择 "**编辑**"。

    ![编辑 PresenceStatus 列](media/sample-crisis-communication-app/38-edit-column.png)

1. 在 "**选择**" 字段中添加其他工作状态消息。

> [!NOTE]
> 记录新选项的名称;你将在后续步骤中使用它们。

现在，您需要对应用程序本身进行一些调整，以便显示您的新工作状态消息。

1. 在 Power Apps Studio 中打开应用<!--edit okay?-->.
1. 选择 "**工作状态**" 屏幕。
1. 将编辑栏设置为**OnVisible**函数。

    ![显示状态](media/sample-crisis-communication-app/39-onvisible-for-screen.png)

1. 编辑以下模板，并将值替换为自己的值。
<!--I took the liberty of editing these strings to use contractions, which is Microsoft style now.-->
    ```
        ,"<Name of option in SharePoint list; case sensitive>",
        Table(
            {
                Icon: <Image file>,
                DateRangeQuestion: "Select the dates you'll be <Name of status>.",
                DateRangeReceipt: "You're currently <Name of status>.",
                ShareToTeamEmail: "I'll be <Name of status> on these dates",
                AutoReplyMessage: "I'll be <Name of status> on these dates"
            }
        )
    ```

1. 将 `/* TEMPLATE FOR ADDITIONAL WORK STATUS OPTIONS */` 字符串替换为模板。
1. 选择 "**保存**"，然后选择 "**发布**"。

### <a name="update-the-request-for-help-flow"></a>更新帮助流的请求

此流将向中心团队团队发送一个自适应卡，并请求帮助。

![请求帮助](media/sample-crisis-communication-app/21-Request-Help.png)

在完成以下步骤之前，请在团队中创建危机管理团队。 创建团队后，可以获取该团队的 ID 并将其导入到流中。 有关创建团队团队的详细信息：[创建中心危机管理团队团队](#create-a-central-crisis-management-teams-team)

1. 请参阅要将所有帮助请求发布到的团队渠道。
1. 选择通道的 "**更多选项**" （...）。
1. 选择 "**获取通道的链接**"。

    ![获取指向通道的链接](media/sample-crisis-communication-app/17-Get-link-to-channel.png)

1. 复制链接，并将其粘贴到文本编辑器中。

    ![复制团队链接](media/sample-crisis-communication-app/18-Copy-link.png)

1. 提取**团队 ID**，该 ID 是 `groupId=` 之后和 `&tenantId=`之前的所有内容。 <br> 例如，在以下 URL 中，通道 ID 是<!--suggest using a line break here and in the next step so you don't have to include any closing punctuation.--> <br>`8bc7c0c2-0d4c-4fb8-af99-32da74c9237b`
   
   `https://teams.microsoft.com/l/channel/19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2/General?groupId=8bc7c0c2-0d4c-4fb8-af99-32da74c9237b&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47`
   
1. 提取**通道 ID**，该 ID 是 `https://teams.microsoft.com/l/channel/` 之后和 `/General`之前的所有内容。 <br> 例如，在以下 URL 中，通道 ID 是<br> `19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2`
   
   `https://teams.microsoft.com/l/channel/19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2/General?groupId=8bc7c0c2-0d4c-4fb8-af99-32da74c9237b&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47`，

1. 请参阅[flow.microsoft.com](https://flow.microsoft.com)。

1. 从左侧导航窗格中选择 **"我的流**"。

1. 选择**更多命令**（...） 对于**CrisisCommunication**，然后选择 "**编辑**"。

    ![编辑帮助流请求](media/sample-crisis-communication-app/20-Edit-Flow.png)

1. 打开 "**团队 Id** " 卡。

1. 将团队 ID 粘贴到 "**值**" 字段中。

1. 打开**通道 ID**卡。

1. 将通道 ID 粘贴到 "**值**" 字段中。

    ![设置团队和通道 Id](media/sample-crisis-communication-app/22-Set-Team-IDs.png)

1. 向下滚动到 "**获取时间**" 操作，并使用你选择的源和目标时间更新 "**转换时区**" 的操作。

    ![转换时区设置](media/sample-crisis-communication-app/convert-time-zone.png)

## <a name="optional-configure-a-shared-inbox"></a>可选：配置共享收件箱<a name="optional-configure-shared-inbox"></a>

在将收件箱发送给团队之前，CrisisCommunication 流将请求从收件箱拉取请求。 如果希望将请求电子邮件发送到共享收件箱，请遵循以下步骤。

> [!NOTE]
> 如果你不想将请求电子邮件发送到共享收件箱，则可以跳过此部分。

1. 在编辑模式下打开**CrisisCommunication**流。
1. 从**电子邮件到达 V3 后**，选择 "**更多命令**（...）"。
1. 选择“删除”。

     ![删除连接器](media/sample-crisis-communication-app/33-delete-connector.png)

1. 搜索并选择**新电子邮件到达共享邮箱（V2）的时间**。
1. 在 "**邮箱地址**" 中输入共享收件箱地址。
1. 打开**注释**卡。
1. 选择 "为**值** **添加动态值**"。
1. 搜索并选择 "**正文**"。

     ![选择正文](media/sample-crisis-communication-app/35-body.png)

1. 打开 "**获取用户配置文件卡（V2）** " 卡。
1. 选择 "**添加动态值**"。
1. 搜索并选择 "**从**"。

     ![选择来源](media/sample-crisis-communication-app/34-from.png)

## <a name="import-and-set-up-the-admin-app"></a>导入并设置管理应用

若要管理已导入的应用，请对管理应用重复相同的步骤。

1. 登录到 [Power Apps](https://make.powerapps.com)。
1. 从左侧导航窗格中选择 "**应用**"。
1. 在命令栏上选择 "**导入**"。
1. 上传 GitHub 存储库中的**CrisisCommunicationAdmin**文件。

    ![导入管理应用程序包](media/sample-crisis-communication-app/import-app.png)

1. 选择“导入”。

### <a name="update-sharepoint-connections-for-the-admin-app"></a>更新管理应用程序的 SharePoint 连接

1. 返回到**应用**列表。
1. 为**危机通信管理应用**选择**更多命令**（...）。
1. 从上下文菜单中选择 "**编辑**"。

    ![编辑管理应用](media/sample-crisis-communication-app/08-Edit-Admin-App.png)

1. 登录或创建任何所需的连接，然后选择 "**允许**"。

1. 在左窗格中转到 "数据源"。

    ![数据源](media/sample-crisis-communication-app/data-sources.png)

1. 删除应用内的现有 SharePoint 列表，因为它们不指向当前的 SharePoint 站点。<!--Please see previous editor's note.-->

    ![删除数据源](media/sample-crisis-communication-app/remove-data-source.png)

1. 从您自己的 SharePoint 站点添加列表。 首先，在搜索栏中搜索**SharePoint** 。

    ![搜索 SharePoint](media/sample-crisis-communication-app/sharepoint.png)

1. 选择 " **SharePoint**"，然后选择连接。

    ![SharePoint 连接](media/sample-crisis-communication-app/sharepoint-connection.png)

1. 将 URL 复制并粘贴到 SharePoint 站点的 "文本" 字段中，然后选择 "**连接**"。

    ![SharePoint 站点 URL](media/sample-crisis-communication-app/site-url.png)

1. 选择 "所有 SharePoint 列表和库"，然后选择 "**连接**"。

    ![连接 SharePoint 列表](media/sample-crisis-communication-app/sharepoint-lists.png)

1. 选择 "**保存**"，然后选择 "**发布**"。

## <a name="create-initial-content-for-the-app"></a>创建应用的初始内容

此时，你已成功导入危机通信应用及其管理应用。 你现在可以开始创建初始内容。 若要开始，请打开危机通信管理应用。

如果你有一个 GCC 环境，则需要启用 GCC 模式。 详细信息：[如何配置适用于 GCC 环境的移动客户端](https://docs.microsoft.com/power-platform/admin/powerapps-us-government#configure-mobile-clients)。

![危机通信管理应用](media/sample-crisis-communication-app/09-Admin-App.png)

使用管理应用自定义危机通信应用中的所有信息，还可以为随附的流配置密钥设置。

> [!NOTE]
> 提醒&mdash;如果你不想使用管理应用，则可以通过手动编辑 SharePoint 列表来编辑这些属性。

### <a name="set-up-key-parameters-under-admin-settings"></a>在管理设置下设置密钥参数

若要初始化你的应用，你需要通过导航到 "**管理设置**" 提供所有必需的字段。

完成下表中所示的所有字段，然后选择 "**保存**"。

| **字段名称** | **SharePoint 中的逻辑名称** | 用途 | **示例** |
|-|-|-|-|
| 管理员电子邮件 | AdminContactEmail | 这是发送电子邮件请求的位置。 它们应设置为你的电子邮件地址。 如果要将通知发送到其他收件箱，请参阅本文前面的[可选共享收件箱配置](#optional-configure-shared-inbox)。 | admin@contoso.com |
| 徽标 URL | Logo | 在左上角显示的应用的徽标。 | https://contoso.com/logo.png |
| AAD 组 ID | AADGroupID | 用于向用户发送有关内部公司更新的通知，并通过**通知用户了解有关新的危机通信新闻**<!--Can you rename this flow to "Notify users of new crisis communication news"? Or maybe even "Notify users of breaking news about the crisis"?--> 流. 按照以下说明获取组的 Azure Active Directory （Azure AD） ID。 | c0ddf873-b4fe-4602-b3a9-502dd944c8d5 |
| 应用程序 URL | AppURL | 用户应用的位置，以便在**新的危机通信新闻流上通知用户**可以在他们选择 "**阅读更多**" 后重定向用户。 | https://apps.preview.powerapps.com/play/<app URL>？ tenantId =<tenant ID>
| 政府 RSS 源 | GovernmentRSSFeed | 用于在应用程序中填充世界上的新闻功能。 如果你想要从受信任的源向你的员工提供其他信息，则此方法很有用。 | https://www.who.int/rss-feeds/news-english.xml |
| 通知方法 | PreferredSentNotification | 由在**新的危机通信新闻流上通知用户**，用于确定它在发出通知时应使用哪个分发通道。 此字段为必填字段。 | 电子邮件，团队通知，推送通知 |
| 功能标志 | Feature1 .。。8 | 用于禁用或启用应用程序中的每个功能。 |  |

> [!NOTE]
> GCC 当前不支持团队通知和推送通知。


#### <a name="finding-the-azure-ad-id-for-your-distribution-group"></a>查找通讯组的 Azure AD ID
<!--note from editor: The Cloud Style Guide says don't use "AAD" for "Azure AD."-->
1. 请参阅[aad.portal.azure.com](https://aad.portal.azure.com)。
1. 从左侧导航窗格中选择 " **Azure Active Directory** "。
1. 选择**组**。
1. 搜索并选择你的通讯组。
1. 复制 "**对象 Id** " 字段。

    ![获取 Azure AD ID](media/sample-crisis-communication-app/11-AAD-Group-ID.png)

1. 将该 ID 粘贴到管理应用中的**AAD 组 ID**字段。<!--Can you have this changed to "Azure AD group ID"? -->

### <a name="set-up-emergency-contacts"></a>设置紧急联系人

1. 请参阅**公司联系人**。
1. 选择 "**新建联系人**"。
1. 使用联系人详细信息完成表单。

*列表架构：*

| **字段名称** | **SharePoint 中的逻辑名称** | 用途 |
|-|-|-|
| 全名 | FullName | 联系人的姓名。 |
| E-mail | E-mail | 为联系人显示的电子邮件地址。 |
| Country | Country | 联系人所在的国家/地区。 此字段用于对联系人进行分组;如果国家/地区没有什么意义，则可以使用其他值对联系人进行分组。 |
| Comments | Comments | 显示有关联系人的其他信息;用于描述何时与此联系人进行联系。 |
| 不推荐使用 | 不推荐使用 | 用于隐藏现有紧急联系人。 |

### <a name="set-up-initial-company-news"></a>设置初始公司资讯

1. 请参阅**公司新闻**。
1. 选择 "**新建发布**"。
1. 填写表单。

*列表架构：*

| **字段名称** | **SharePoint 中的逻辑名称** | 用途 |
|-|-|-|
| 职务 | 职务 | 更新的标题。 |
| 详细信息 | 详细信息 | 完整更新。 您可以在此字段中使用 HTML。 |
| 简介 | 简介 | 有关更新的简短消息。 此项在**通知用户有关新的危机通信新闻**流和更新库中使用。 |
| 不推荐使用 | 不推荐使用 | 用于隐藏现有帖子。 |

### <a name="set-up-helpful-tips"></a>设置有用的提示

1. 请参阅**有用提示**。
1. 选择 "**新提示**"。
1. 填写表单。

*列表架构：*

| **字段名称** | **SharePoint 中的逻辑名称** | 用途 |
|-|-|-|
| 职务 | 职务 | 有用提示的标题。 |
| 资源 URL | ResourceURL | 指向附加阅读材料的链接。 (可选) |
| 子标题 | 标题 | 提示的副标题。 (可选) |
| 说明 | 说明 | 有用提示的完整说明。 |
| 不推荐使用 | 不推荐使用 | 使用可以隐藏有用提示。 |

### <a name="set-up-links"></a>设置链接

1. 请参阅**链接**。
1. 选择 "**创建新链接**"。
1. 填写表单。

*列表架构：*

| **字段名称** | **SharePoint 中的逻辑名称** | 用途 |
|-|-|-|
| 职务 | 职务 | 链接的文本。 |
| URL | URL | 链接的 URL。 |
| 说明 | 说明 | 有关链接的其他详细信息。 (可选) |
| 不推荐使用 | 不推荐使用 | 用于隐藏链接。 |

### <a name="set-up-faqs"></a>设置常见问题

1. 请参阅**常见问题解答**。
1. 选择 "**创建新的常见问题**"。
1. 填写表单。

*列表架构：*

| **字段名称** | **SharePoint 中的逻辑名称** | 用途 |
|-|-|-|
| 职务 | 职务 | 常见问题解答中的问题。 |
| 级别 | 级别 | 问题在常见问题解答中的顺序。 |
| Answer | Answer | 常见问题解答中的问题的答案。 |
| 不推荐使用 | 不推荐使用 | 用于隐藏常见问题中的问题。 |

## <a name="test-and-share-the-app"></a>测试并共享应用

现在，您已成功设置了所有数据，可以测试应用程序以确保其正常运行。

1. 登录到 [Power Apps](https://make.powerapps.com)。
2. 从左侧导航窗格中选择 "**应用**"。
3. 选择要播放应用的**危机通信**。

成功测试应用后，可以将其与公司中的每个人共享。

## <a name="import-and-set-up-the-notification-flow"></a>导入和设置通知流

只要有新的公司更新，应用程序就会使用 flow 向最终用户发送通知。

### <a name="import-the-news-notification-flow"></a>导入新闻通知流

1. 请参阅[flow.microsoft.com](https://flow.microsoft.com)。
1. 从左侧导航窗格中选择 **"我的流**"。
1. 在命令栏上选择 "**导入**"。
1. 从 GitHub 存储库上传**CrisisCommunicationNewsNotification**包。

    > [!NOTE]
    > 如果你的租户在 GCC 环境下，请上传**CrisisCommunicationNewsNotificationGCC**。

    ![上传 CrisisCommunicationNewsNotification](media/sample-crisis-communication-app/upload-news-notification.png)

1. 通过选择每个连接的 "**导入**" 链接，然后完成表单，为新流添加连接。

    ![导入期间选择](media/sample-crisis-communication-app/select-during-import.png)

1. 如果需要创建新连接，请在 "**导入设置**" 窗格中选择 "**新建**"。
1. 在命令栏上选择 "**新建连接**"。

    ![创建新连接](media/sample-crisis-communication-app/create-connection.png)

1. 搜索连接的名称;例如， **PowerApps 通知（预览）** 。

    ![连接名称示例](media/sample-crisis-communication-app/notifications.png)

1. 选择所需的连接。
1. 如果要创建到**PowerApps 通知（预览版）** 的连接，将看到如下图所示的对话框。

    !["通知" 对话框](media/sample-crisis-communication-app/notifications-dialog.png)

1. 若要获取 ID，请转到**应用**列表。
1. 为**危机通信**应用选择 "**更多命令**" （...），然后选择 "**详细信息**"。

    ![连接的详细信息](media/sample-crisis-communication-app/06-App-Details.png)

1. 复制“应用 ID”。

    ![应用 ID](media/sample-crisis-communication-app/07-App-ID.png)

1. 将应用 ID 粘贴到 "连接创建" 对话框中，然后选择 "**创建**"。

    ![创建连接](media/sample-crisis-communication-app/target-app-id.png)

1. 创建新连接后，返回到 "**导入设置**" 窗格，然后选择 "**刷新列表**"。
1. 此时应显示新连接。 选择它，然后选择 "**保存**"。
1. 添加完所有连接后，选择 "**导入**"。

    ![导入连接](media/sample-crisis-communication-app/imported-connections.png)

### <a name="edit-the-news-notification-flow"></a>编辑新闻通知流

1. 导入完成后，请切换到 **"我的流**"。
1. 选择新导入的流，并**通知用户新的危机通信新闻**。

    > [!NOTE]
    > 如果上传了 GCC 包，则流名称将**通知用户有关新的危机通信新闻**。

1. 在命令栏上选择 "**编辑**"。
1. **在发布新项时**打开。
1. 对于 "**站点地址**"，请输入 SharePoint 站点的名称。
1. 对于 "**列表名称**"，请输入**CI_CompanyNews**。
1. 打开 "**获取管理配置" 设置**卡。
1. 对于 "**站点地址**"，请输入 SharePoint 站点的名称。
1. 对于 "**列表名称**"，请输入**CI_configAdminSetup**。
1. 打开 "**初始化变量–了解更多文本**卡"。
1. 对于 "**值**"，输入 "**详细信息**" （采用本机语言）。

    ![流设置](media/sample-crisis-communication-app/flow-options.png)

1. 选择“保存”。

> [!NOTE]
> 如果你的某个连接尚未获得授权，你可能会收到错误。
如果出现这种情况，请打开包含未经授权的连接和重新授权的卡。


### <a name="optional-sending-notifications-to-more-than-5000-users"></a>可选：向超过5000个用户发送通知

当前的 "**获取组成员**" 操作仅限为5000用户拉取 "Power 自动" 办公室许可证。 即使对于高级许可证，如果尝试将通知发送给过多用户，则可能会遇到团队连接器的限制。 若要分发给更多用户，可以改为改为将电子邮件发送到通讯组列表。

1. 删除以下卡：**获取组成员**并**在首选发送通知设置上切换**：

    ![删除操作](media/sample-crisis-communication-app/36-delete-actions.png)

1. 添加新操作。

1. 搜索并选择 "**发送电子邮件（V2）** "：

    ![添加发送电子邮件](media/sample-crisis-communication-app/37-add-send-an-email.png)

1. 在 "**到**" 字段中，键入你的通讯组的名称。

1. 在 "**使用者**" 字段中，选择 "**添加动态值**" 按钮，然后添加 "**当新闻项目发布时**" 卡上的 "**标题**" 字段：

    ![添加标题](media/sample-crisis-communication-app/38-add-title.png)

1. 在 "**正文**" 字段中，选择 "**添加动态值**" 按钮，然后添加 "**当新闻项目发布时**" 卡时的 "**详细信息**" 字段。

1. 选择“保存”。

### <a name="optional-deep-link-teams-notification-into-teams-app"></a>可选：深层链接团队通知到团队应用

如果希望团队通知直接在团队内部打开画布应用，请执行以下步骤：

1. 更新应用 URL，使其指向管理应用中的 "团队" 深层链接。 <br>
在管理应用程序中，将 "应用程序 URL" 更改为以下位置，其中 `App ID` 是应用的 ID。

    ```
    https://teams.microsoft.com/l/entity/<APP ID>/<APP ID>
    ```

    ![管理应用](media/sample-crisis-communication-app/42-admin-app.png)

1. 更新在通知流内生成的应用程序链接。 <br> 打开 "设置应用链接变量" 卡，将 "值" 表达式更改为以下内容：

    ```
    concat(items('Apply_to_each')?['AppUrl'], if(greater(indexOf(items('Apply_to_each')?['AppUrl'], '?'),0),'&','?'), 'context=%7B%22subEntityId%22%3A%22',triggerBody()?['ID'],'%22%7D')
    ```
    ![更改流设置](media/sample-crisis-communication-app/43-flow-settings.png)

1. 更新画布应用以使用团队上下文变量深入链接到正确的新闻文章。 <br> 对于应用的**OnStart**属性，请将参数从 `newsid` 更改为 `subEntityId`。

    ![更改 OnStart](media/sample-crisis-communication-app/44-onstart.png)

### <a name="test-the-news-notification-flow"></a>测试新闻通知流

若要测试新闻通知流，请参阅管理应用并创建新的内部公司更新。 稍后，你的通讯组列表中的所有用户都将收到你的首选通知方法的更新。

> [!NOTE]
> 如果遇到错误，请确保已在管理应用的设置中成功输入了通讯组列表的组 ID。

## <a name="monitor-office-absences-with-power-bi"></a>用 Power BI 监视办公室请假

部署应用后，用户开始发送通知，因为各种原因（例如，病假或在家工作），因此，你可以使用 Power BI 报表来跟踪已发送通知的用户数以及他们所在的位置。  
请注意，你需要[启用位置跟踪](#optional-enable-location-updates)以使地图控件正常工作。 

> [!IMPORTANT]
> 要使 Power BI 报表有效，必须在 " **CI_Employee 状态**列表中至少有一个条目。

我们将需要我们之前创建的**CI_Employee 状态**SharePoint 列表中的某些信息，因此让我们先来了解一下。 在网站中打开列表，然后选择 "**设置**" 图标下的 "**列表设置**"。

![员工状态列表设置](media/sample-crisis-communication-app/001-SharePointList-ListSettings-nolines.PNG)

记下浏览器地址栏上的 "站点名称" 和 "列表 ID"，如下图所示。

![员工状态列表和站点 Id](media/sample-crisis-communication-app/002-SharePointList-AddressAndId-nolines.PNG)

此时，我们已准备好打开 Power BI 报表。 打开 Power BI，然后打开**状态报告 .pbix**文件。 将鼠标悬停在**CI_Employee 状态**数据源的右侧，直到看到省略号。 选择它，然后选择 "**编辑查询**"。

![编辑查询](media/sample-crisis-communication-app/003-PowerBI-EditQuery-nolines.PNG)

打开 Power Query 编辑器后，右键单击**CI_Employee 状态**数据源，然后选择 "**高级编辑器**"。

![Power Query 高级编辑器](media/sample-crisis-communication-app/004-PowerQuery-AdvancedEditor-nolines.PNG)

我们使用 SharePoint 列表中的 "站点名称" 和 "列表 ID"。

将新的 SharePoint 站点复制到 "Tables" 字符串中，如下图所示<!--Edit okay? This is a case where the image shows information that the text doesn't, so I'm not sure how to make this descriptive enough for people who aren't looking at the graphics, or people with low vision.--> 和在其中突出显示 GUID 的三个位置中的列表 ID，然后选择 "**完成**"。

![Power Query 高级编辑器更新](media/sample-crisis-communication-app/005-PowerQuery-AdvancedEditorUpdates-nolines.PNG)

如果在更新连接信息后看到任何连接错误，则可能需要更新用于连接到 SharePoint 列表的凭据。 

**更新连接**

1. 在 "**文件**" 菜单上，选择 "**选项和设置**"，然后选择 "**数据源设置**"。

    ![数据源设置](media/sample-crisis-communication-app/PBI-1-DataSourceSettings.PNG)

1. 选择 "**编辑权限**"。

    ![编辑权限](media/sample-crisis-communication-app/PBI-2-DataSourceSettings-EditPermissions.PNG)

1. 确保 "**凭据**类型" 设置为 "**组织帐户**"，并使用凭据访问 SharePoint 列表。

    ![编辑权限](media/sample-crisis-communication-app/PBI-3-OrganizationalAccount.PNG)

选择 "**关闭 & 应用**" 以更新报表以从 SharePoint 列表中提取数据。

![Power Query 关闭并应用](media/sample-crisis-communication-app/006-PowerQuery-CloseAndApply-nolines.PNG)

现在，我们有了一个 Power BI 报表，其中显示当天办公室缺勤的地理信息，以及一段时间内此类缺勤的趋势。 我们可以发布报表，以便组织中的其他人可以查看该报表。

![Power BI 发布报表](media/sample-crisis-communication-app/007-PowerBI-Publish-nolines.PNG)

你的报表现在已发布。 可以与组织中的其他人共享它。 您还可以[计划报表刷新频率](https://docs.microsoft.com/power-bi/refresh-scheduled-refresh)。

## <a name="integrate-your-app-into-teams"></a>将你的应用集成到团队

现在，你已拥有一个已与所有人共享的有效应用，你可以通过在团队内创建危机管理团队来对问题进行部署，从而部署该应用。

### <a name="deploy-the-app-to-the-app-bar"></a>将应用部署到应用栏

如果你是团队管理员，则可以将应用推送到团队应用栏中的所有用户。

![团队中的应用栏](media/sample-crisis-communication-app/19-App-in-Teams.png)

1. 登录到 [Power Apps](https://make.powerapps.com)。
1. 从左侧导航窗格中选择 "**应用**"。
1. 为**危机通信**应用选择**更多命令**（...）。
1. 选择 "**添加到团队**"。

    ![添加到团队](media/sample-crisis-communication-app/24-Add-to-Teams.png)

1. 选择 "**下载应用**"。

    ![下载应用](media/sample-crisis-communication-app/25-Download-App.png)

1. 打开团队。
1. 在应用栏上，中转到 "**应用**"。
1. 选择 "**上传自定义应用**"。
1. 如果你是团队管理员，则可以为整个租户上载应用。 **为 "contoso** " 选择 "上载" （其中*contoso*表示租户的名称）。<!--Edit okay? The screenshot said "Contoto," which I fixed.-->.

    ![上传应用](media/sample-crisis-communication-app/26-Upload-for-Contoso.png)

1. 上传从 Power Apps 下载的文件。
1. 请前往[团队管理中心](https://admin.teams.microsoft.com/dashboard)。
1. 在 "**团队应用**" 下的左侧导航窗格中，选择 "**安装策略**"。

    ![应用安装策略](media/sample-crisis-communication-app/27-Setup-Policies.png)

1. 选择 "**全局（组织范围设置）** "。
1. 选择 "**添加应用**"。

    ![添加应用](media/sample-crisis-communication-app/28-Add-App.png)

1. 搜索并选择已上传的**危机信息**应用。

    ![添加固定应用](media/sample-crisis-communication-app/29-Add-Pinned-App.png)

1. 选择“添加”。
1. 选择“保存”。

> [!NOTE]
> 用户最长可能需要24小时才会在应用程序栏中看到应用自动固定。

### <a name="create-a-central-crisis-management-team-in-teams"></a>在团队中创建中心危机管理团队<a name="create-a-central-crisis-management-teams-team"></a>

为了协调你的危机响应，你需要在团队中创建一个中心危机管理团队，并使用所有相关信息来填充它。 此团队只需与中心响应团队共享。

1. 中转到团队。
1. 选择左侧应用栏中的 "**团队**"。
1. 选择 "**加入" 或 "创建团队**"。
1. 选择 "**创建团队**"，然后完成剩余步骤。

    ![创建团队](media/sample-crisis-communication-app/23-Create-Team.png)

成功创建团队后，可以将相关信息固定为选项卡。 例如，你可能想要将危机管理管理应用或 Power BI 报表固定到你的团队。

**以选项卡的形式添加管理应用**

1. 选择 " **+** " 按钮。
1. 搜索并选择 "**电源应用**"。
1. 搜索并选择 "**危机信息管理员**"。

    ![固定应用](media/sample-crisis-communication-app/32-Pin-Teams-app.png)

1. 选择“保存”。

**将 Power BI 报表作为选项卡添加**

1. 选择 " **+** " 按钮。
1. 搜索并选择**Power BI**。
1. 搜索并选择 Power BI 报表。
1. 选择“保存”。

## <a name="faq"></a>常见问题

* **运行此解决方案需要哪些许可证？**

    - 此应用中的解决方案使用 Office 连接器，因此，Office 中的一个具有种子的 Power Apps 许可证足以运行和播放用户和管理应用程序。 详细信息：[电源平台授权概述](https://docs.microsoft.com/power-platform/admin/pricing-billing-skus)
    - 如果要使用 Power BI 报表（打包为解决方案的一部分），则需要 Power BI 许可证。 详细信息： [Power BI 定价](https://powerbi.microsoft.com/pricing/)

* **如果我有关于解决方案的反馈，我应该怎么办？**

    我们想知道你在部署和自定义此解决方案时的体验。 若要分享你的体验，请参阅[aka.ms/crisis-communication-feedback](https://aka.ms/crisis-communication-feedback)。

* **我似乎在应用中发现了 bug;我应该从哪里着手？**

   若要使用解决方案提交 bug，请参阅[aka.ms/crisis-communication-issues](https://aka.ms/crisis-communication-issues)。

* **GCC 当前不支持哪些功能？**

    适用于团队和推送通知连接器的电源自动机器人连接器当前不适用于 GCC。 使用电子邮件选项来通知用户有关内部新闻更新的信息。

* **如何更新应用程序？**

    若要更新应用程序，请按照[aka.ms/CrisisCommunicationSolution](https://aka.ms/CrisisCommunicationSolution)上概述的步骤进行操作。

## <a name="issues-and-feedback"></a>问题和反馈

- 有关危机通信示例模板的反馈，请参阅[aka.ms/crisis-communication-feedback](https://aka.ms/crisis-communication-feedback)。
- 若要报告危机通信应用的问题，请参阅[aka.ms/crisis-communication-issues](https://aka.ms/crisis-communication-issues)。

***免责声明：*** *此应用是一个示例，可与 Microsoft Power Apps 和团队一起使用，以仅分发参考信息。此应用程序不适用于本应用，也不能用作医疗设备、临床支持、诊断工具或其他旨在用于诊断、硬化、缓解、治疗或防范疾病或其他情况的技术，Microsoft 不会出于此目的向使用此应用程序授予任何许可或权利。 此应用程序的设计不是专业的医疗建议、诊断、治疗或毋庸置疑的替代方案，因此不应如此。 客户对此应用程序的任何使用承担了唯一的风险和责任。 Microsoft 不保证在连接与之中提供的应用程序或任何材料将足以满足任何医疗目的或满足任何人的健康或医疗要求。* 

### <a name="see-also"></a>另请参阅
<!--note from editor: "Next steps" would work if you gave the reader some action items, but reference topics are random access by nature, so the heading is rightly "See also." -->
- [公式参考](formula-reference.md)
- [控件参考](reference-properties.md)
