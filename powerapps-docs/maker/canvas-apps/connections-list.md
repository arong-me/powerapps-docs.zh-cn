---
title: 连接器概述 | Microsoft 文档
description: 可用于构建应用的所有可用连接概述
documentationcenter: ''
author: lancedMicrosoft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 08/28/2017
ms.author: lanced
ms.openlocfilehash: baa4c71efb54cea6f04cd45b895009a3c3ce17c7
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2018
ms.locfileid: "37899286"
---
# <a name="overview-of-connectors-for-powerapps"></a>PowerApps 连接器概述
数据是大多数应用（包括在 PowerApps 中生成的应用）的关键所在。 数据存储在数据源中，应用是通过创建的连接来连接数据。 连接使用特定的连接器与数据源进行通信。 PowerApps 提供连接器，适用于许多常用服务和本地数据源，包括 SharePoint、SQL Server、Office 365、Salesforce、Twitter 等。 若要开始向应用添加数据，请参阅[在 PowerApps 中添加数据连接](add-data-connection.md)。

单击下表中列出的链接，可详细了解最常用的连接器。 若要获取连接器的完整列表，请参阅[所有的连接器](#all-connectors)。

| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
| --- | --- | --- | --- | --- |
| ![Common Data Service](./media/connections-list/cdm.png) |[**Common Data Service**](../common-data-service/data-platform-intro.md) |&nbsp; |![Office 365 Outlook](./media/connections-list/office365.png) |[**Office 365 Outlook**](connections/connection-office365-outlook.md) |
| ![SharePoint](./media/connections-list/sharepoint.png) |[**SharePoint**](connections/connection-sharepoint-online.md) |&nbsp; |![Excel](./media/connections-list/excel.png) |[**Excel**](connections/connection-excel.md) |
| ![SQL Server](./media/connections-list/sql.png) |[**SQL Server**](connections/connection-azure-sqldatabase.md) |&nbsp; |![OneDrive for Business](./media/connections-list/onedrive.png) |[**OneDrive for Business**](connections/cloud-storage-blob-connections.md) |
| ![Dynamics 365](./media/connections-list/dynamics-365.png) |[**Dynamics 365**](connections/connection-dynamics-crmonline.md) |&nbsp; |![OneDrive](./media/connections-list/onedrive.png) |[**OneDrive**](connections/cloud-storage-blob-connections.md) |
| ![Office 365 用户](./media/connections-list/office365.png) |[**Office 365 用户**](connections/connection-office365-users.md) |&nbsp; |![Dropbox](./media/connections-list/dropbox.png) |[**Dropbox**](connections/cloud-storage-blob-connections.md) |

## <a name="types-of-connectors"></a>连接器类型
PowerApps 提供以下两类连接器：标准连接器（如上面所列）和自定义连接器。 若要使用标准连接器连接到 PowerApps 支持的数据源，请使用标准连接器。 如果需要连接到另一个源（如已生成的服务），请参阅[注册和使用自定义连接器](../canvas-apps/register-custom-api.md)。

标准连接器的行为各异，具体取决于连接到的数据源类型，以及数据源如何返回数据：

* 一些连接器支持连接到表格数据源，如 SharePoint、SQL Server 和 Excel。 如果连接的是这些数据源，数据以表的形式返回给 PowerApps。 PowerApps 使用自己的函数（如 [Patch()](functions/function-patch.md)、[Collect()](functions/function-clear-collect-clearcollect.md)、[Update()](functions/function-update-updateif.md) 等）与数据进行交互。 还可以在窗体和库中轻松使用表格数据，这样表中的字段就会显示为库或窗体中的字段。 有关详细信息，请参阅以下文章：

    [了解 PowerApps 中的数据源](working-with-data-sources.md)

    [通过 Excel 数据生成应用](get-started-create-from-data.md)

    [从头开始创建应用](get-started-create-from-blank.md)

    > [!NOTE]
  > 若要连接到 Excel 数据，工作簿必须托管在 OneDrive 等云存储服务中。 有关详细信息，请参阅[从 PowerApps 连接到云存储](connections/cloud-storage-blob-connections.md)。

* 另一些连接器支持连接到基于函数的数据源，如 Twitter、Facebook 和 Office 365 Outlook。 如果连接的是这些数据源，数据根据基础服务中的特定函数调用返回给 PowerApps。 例如，如果使用 Twitter 连接器，需要调用 `Twitter.MyFollowers()` 才能返回关注者名单。 仍可以在窗体或库中使用此类数据，但与表格数据相比，需要再执行一些操作。 有关详细信息，请参阅[从 PowerApps 连接到 Twitter](connections/connection-twitter.md)。

## <a name="all-connectors"></a>所有的连接器
下表列出了所有的连接器。 有关每个连接器的详细信息，请参阅 [Microsoft 连接器参考](https://docs.microsoft.com/connectors/)。 高级连接器需要具备 PowerApps 计划 1 或计划 2。 有关详细信息，请参阅 [PowerApps 计划](https://powerapps.microsoft.com/pricing/)。

| &nbsp; | &nbsp; |
| --- | --- |
| 10to8 预约计划<br>行动！<br>Adobe Creative Cloud ![高级连接器](./media/connections-list/premium.png)<br>Adobe 登录<br>Amazon Redshift ![高级连接器](./media/connections-list/premium.png)<br>Apache Impala ![高级连接器](./media/connections-list/premium.png)<br>AppFigures<br>审批<br>Asana<br>AWeber ![高级连接器](./media/connections-list/premium.png)<br>Azure AD<br>Azure Application Insights<br>Azure 自动化<br>Azure Blob 存储<br>Azure Cosmos DB<br>Azure Data Lake<br>Azure 事件网格<br>Azure 事件网格发布<br>Azure 文件存储<br>Azure Log Analytics<br>Azure Log Analytics 数据收集器<br>Azure 队列<br>Azure 资源管理器<br>Azure 表存储<br>Basecamp 2<br>Basecamp 3<br>基准检验电子邮件 ![高级连接器](./media/connections-list/premium.png)<br>必应地图<br>必应搜索<br>Bitbucket ![高级连接器](./media/connections-list/premium.png)<br>Bitly<br>Bizzy (H3 Solutions, Inc.)<br>Blogger<br>Box<br>bttn<br>缓冲区<br>Calendly ![高级连接器](./media/connections-list/premium.png)<br>Campfire<br>Capsule CRM ![高级连接器](./media/connections-list/premium.png)<br>Chatter ![高级连接器](./media/connections-list/premium.png)<br>Cognito Forms<br>Common Data Service ![高级连接器](./media/connections-list/premium.png)<br>计算机影像 API<br>内容转换<br>内容审查器<br>DB2 ![高级连接器](./media/connections-list/premium.png)<br>Disqus<br>DocFusion365 – SP ![高级连接器](./media/connections-list/premium.png)<br>DocuSign ![高级连接器](./media/connections-list/premium.png)<br>Dropbox<br>Dynamics 365<br>Dynamics 365 for Financials<br>Dynamics for Operations<br>Dynamics NAV<br>Easy Redmine ![高级连接器](./media/connections-list/premium.png)<br>Elastic Forms<br>事件中心<br>Eventbrite ![高级连接器](./media/connections-list/premium.png)<br>Excel<br>人脸 API<br>Facebook<br>文件系统<br>Flic<br>FlowForma ![高级连接器](./media/connections-list/premium.png)<br>FreshBooks ![高级连接器](./media/connections-list/premium.png)<br>Freshdesk<br>Freshservice ![高级连接器](./media/connections-list/premium.png)<br>FTP<br>GitHub<br>Gmail<br>Google 日历<br>Google 联系人<br>Google Drive<br>Google 表<br>Google 任务<br>GoToMeeting ![高级连接器](./media/connections-list/premium.png)<br>GoToTraining ![高级连接器](./media/connections-list/premium.png)<br>GoToWebinar ![高级连接器](./media/connections-list/premium.png)<br>Harvest ![高级连接器](./media/connections-list/premium.png)<br>HelloSign ![高级连接器](./media/connections-list/premium.png)<br>HipChat<br>使用 Azure AD 的 HTTP ![高级连接器](./media/connections-list/premium.png)<br>Informix ![高级连接器](./media/connections-list/premium.png)<br>Infusionsoft ![高级连接器](./media/connections-list/premium.png) |Inoreader<br>Insightly<br>Instagram<br>Instapaper<br>Intercom<br>JIRA ![高级连接器](./media/connections-list/premium.png)<br>JotForm ![高级连接器](./media/connections-list/premium.png)<br>LeanKit ![高级连接器](./media/connections-list/premium.png)<br>LinkedIn<br>LiveChat ![高级连接器](./media/connections-list/premium.png)<br>LUIS<br>邮件<br>MailChimp ![高级连接器](./media/connections-list/premium.png)<br>Mandrill ![高级连接器](./media/connections-list/premium.png)<br>中型<br>Microsoft Forms<br>Microsoft StaffHub<br>Microsoft Teams<br>Microsoft Translator<br>MSN 天气<br>Muhimbi PDF<br>MySQL ![高级连接器](./media/connections-list/premium.png)<br>Nexmo ![高级连接器](./media/connections-list/premium.png)<br>通知<br>Office 365 Bookings<br>Office 365 组<br>Office 365 Outlook<br>Office 365 用户<br>Office 365 视频<br>OneDrive<br>OneDrive for Business<br>OneNote（企业版）<br>Oracle 数据库 ![高级连接器](./media/connections-list/premium.png)<br>Outlook Customer Manager<br>Outlook 任务<br>Outlook.com<br>PagerDuty<br>Parserr<br>Paylocity ![高级连接器](./media/connections-list/premium.png)<br>Pinterest<br>Pipedrive ![高级连接器](./media/connections-list/premium.png)<br>Pitney Bowes 数据验证 ![高级连接器](./media/connections-list/premium.png)<br>Pivotal Tracker<br>Planner<br>Plivo ![高级连接器](./media/connections-list/premium.png)<br>PostgreSQL ![高级连接器](./media/connections-list/premium.png)<br>Power BI<br>PowerApps 通知 ![高级连接器](./media/connections-list/premium.png)<br>Project Online<br>Redmine<br>RSS<br>Salesforce ![高级连接器](./media/connections-list/premium.png)<br>SendGrid<br>服务总线<br>SFTP<br>SharePoint<br>Skype for Business<br>Slack<br>SmartSheet<br>SMTP<br>SparkPost<br>SQL Server<br>Stripe ![高级连接器](./media/connections-list/premium.png)<br>SurveyMonkey ![高级连接器](./media/connections-list/premium.png)<br>团队合作项目 ![高级连接器](./media/connections-list/premium.png)<br>Teradata ![高级连接器](./media/connections-list/premium.png)<br>文本分析<br>Todoist<br>Toodledo<br>Trello<br>Twilio<br>Twitter<br>TypeForm<br>UserVoice ![高级连接器](./media/connections-list/premium.png)<br>视频索引器<br>Vimeo<br>Visual Studio Team Services<br>WebMerge<br>WordPress<br>Wunderlist<br>Yammer<br>YouTube<br>Zendesk ![高级连接器](./media/connections-list/premium.png) |

若对特定连接器有疑问，请访问 [PowerApps 论坛](https://powerusers.microsoft.com/t5/PowerApps-Community/ct-p/PowerApps1)。 若对新连接器有意见或有改进建议，请访问 [PowerApps 观点](https://powerusers.microsoft.com/t5/PowerApps-Ideas/idb-p/PowerAppsIdeas)。
