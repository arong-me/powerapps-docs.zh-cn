---
title: 危机通信应用-示例模板 |Microsoft Docs
description: 了解 Power Apps 中的危机通信示例模板。
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/04/2020
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a547eac25e71467fb751e0a0c6eb30eccdac48ec
ms.sourcegitcommit: efb05dbd29c4e4fb31ade1fae340260aeba2e02b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2020
ms.locfileid: "78293456"
---
# <a name="set-up-and-learn-about-the-crisis-communication-sample-template-in-power-apps"></a>设置并了解 Power Apps 中的危机通信示例模板

有关安装和配置适用于电源应用的危机通信应用的分步说明。

完成这些步骤所需的估计时间： **20-25 分钟**

## <a name="overview-of-the-app"></a>应用概述

*危机通信*应用提供用户友好的体验，将最终用户与有关危机的信息联系起来。 快速获取内部公司新闻的更新，获取常见问题的答案，并获取对链接和紧急联系人等重要信息的访问权限。 要拥有此应用，需完成少量设置。

在本演练中，您将学习如何：
- 创建数据的位置
- 导入危机通信应用及其管理应用
- 为应用程序创建内容
- 导入流以向用户发送通知
- 创建集中管理的团队，以聚合数据并有效响应问题

## <a name="prerequisites"></a>先决条件

- [注册](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)电源应用的 。
- 您必须具有有效的 SharePoint Online 许可证和权限才能创建列表。
- 您必须有一个公共 SharePoint 站点，您可以在其中存储应用程序的数据。
- 从[aka.ms/CrisisCommunicationSolution](https://aka.ms/CrisisCommunicationSolution)下载资产。

## <a name="create-a-home-for-your-data"></a>为数据创建家庭

应用的数据将驻留在 SharePoint 列表中。 首先，我们需要创建新的 SharePoint 网站才能开始。

### <a name="create-a-sharepoint-site"></a>创建 SharePoint 站点

1. 登录到[Office online](https://www.office.com)并选择 " **SharePoint**"。
1. 选择 "创建网站"，然后选择 "下一步"：

    ![示例 SharePoint 站点](media/sample-crisis-communication-app/01-Create-Site.png)

1. 选择团队网站：

    ![团队网站](media/sample-crisis-communication-app/02-Team-Site.png)

1. 为站点指定名称和说明。
1. 将隐私设置设置为 "公共"，以便公司中的每个人都可以获取所需的信息：

    ![网站设置](media/sample-crisis-communication-app/03-Privacy-Settings.png)

1. 选择“下一步”。
1. 选择性地添加其他所有者。
1. 选择“完成”。

### <a name="create-the-sharepoint-lists-for-app"></a>为应用创建 SharePoint 列表
应用需要多个列表来存储所有数据。 若要自动创建 SharePoint 列表，可以使用 "已下载的[资产" 包](#prerequisites)中提供的*DeploySPLists*流。

#### <a name="import-the-sharepoint-list-deployment-flow"></a>导入 SharePoint 列表部署流
1. 中转到[flow.microsoft.com](https://flow.microsoft.com)
1. 从左侧导航栏中选择 **"我的流**"。
1. 选择命令栏中的 "**导入**" 按钮。
1. 从 GitHub 存储库上传**DeploySPList**包。

    ![导入包](media/sample-crisis-communication-app/import-package.png)

1. 通过选择 "**在导入期间选择**" 链接并完成窗体，为新流添加 SharePoint 连接。

    ![导入设置](media/sample-crisis-communication-app/import-settings.png)

1. 如果需要创建新的 SharePoint 连接，请首先在 "导入设置" 窗格中选择 "**新建**"。
1. 在命令栏中选择 "**新建连接**"：

    ![创建新连接](media/sample-crisis-communication-app/create-connection.png)

1. 搜索连接的名称，例如*SharePoint*。
1. 选择适当的连接。
1. 选择“保存”。
1. 选择“导入”。

#### <a name="edit-the-sharepoint-list-deployment-flow"></a>编辑 SharePoint 列表部署流

1. 导入完成后，返回到 **"流**" 并刷新流列表
1. 选择新导入的流**DeploySPList**。
1. 从命令栏中选择 "**编辑**"。
1. 打开名为 "**变量–列表的目标站点**" 的卡。
1. 将值更改为您的 SharePoint 站点的名称。
1. 打开名为 "**变量–应用名称**" 的卡片。
1. 将值更改为您的应用程序的名称;默认情况下，它是 "危机通信"。

    ![流参数](media/sample-crisis-communication-app/04-Flow-Settings.png)

1. 选择 "**保存**" 以提交更改。

#### <a name="run-the-sharepoint-list-deployment-flow"></a>运行 SharePoint 列表部署流

1. 返回到**DeploySPList 流**的详细信息屏幕。
1. 从命令栏中选择 "**运行**"。
1. 选择 "**继续**"，然后**运行 "流**" 来触发流。

    ![登录以运行流](media/sample-crisis-communication-app/sign-in-flow.png)

    ![运行流](media/sample-crisis-communication-app/run-flow.png)

> [!NOTE]
> 你可能会收到一条错误，指出需要位置服务。
如果发生这种情况，请在重试之前允许定位服务自动启动并刷新页面。

然后，流将在 SharePoint 站点中创建以下 SharePoint 列表：

| **显示标题**| 用途 | **说明** |
|-|-|-|
| CI_LogosAssets| 保存应用程序中引用的徽标和/或其他图像。 徽标将通过直接链接或所需徽标的 ID 号在 Power Apps 中引用。 | 适用于 [App Name] 应用的相关徽标和其他图像资产的库。 |
| CI_configAdminSetup | 此工具的管理员的功能配置。 **注意**：此列表应仅读取到非管理员成员。 | [应用名称] 应用的管理配置列表。
| CI_Contacts | 使用默认的 "联系人" 内容类型来捕获有关联系人的信息。 （不包括人员选取器–因此可能需要维护才能确保数据是最新的。） **注意**：这取决于全局联系人列表类型作为列表中的默认内容类型。 | [应用名称] 应用的联系人列表。|
| CI_CompanyNews | 公司新闻项的集合。 | [应用名称] 应用中可见的新闻项目管理列表。 不推荐使用的列可用于筛选出应用程序中的新闻项（将这些项保留为记录）。 | 
| CI_FAQ  | 常见问题。 | [应用名称] 应用的常见问题。 不推荐使用的列可用于筛选应用外的 FAQ 项（将它们作为记录保留）。 |
| CI_UsefullLinks | 有用的超链接列表 | [App Name] 应用的有用超链接列表。 不推荐使用的列可用于筛选应用中的超链接项（将其作为记录保留）。 |
| CI_Employee | 跟踪当前员工状态。 示例：*在家工作*;*out 病假*;*个人休假*;*休假*。  **注意**：假定为 "*工作*"，但不包括在列表选项中。 | [App Name] 应用的有用超链接列表。 不推荐使用的列可用于筛选应用程序（将它们作为记录保留）中的链接项。 |
| CI_HelpfulTips             | 用户可能会向对等方提供有用的提示。 | [应用名称] 应用的共享提示管理列表。 不推荐使用的列可用于从应用视图中删除提示（在 SPO 中将它们保留为一条记录）。  |

> [!NOTE]
> - 上面列出的所有列表列都应被视为依赖项。
    请防止列表意外进行架构更改（例如，允许添加新列，但删除列可能会破坏应用程序。）
> - 删除列表项时请小心;删除列表项会删除历史记录。 可以将弃用值从 "*否*" 切换为 *"是"* 以从联系人、新闻、faq 或链接中删除记录。

## <a name="import-and-set-up-the-crisis-communication-app"></a>导入并设置危机通信应用

现在，已创建了所有 SharePoint 列表，接下来可以导入应用并将其连接到新的数据源。

> [!NOTE]
> 如果不想使用管理应用，还可以通过手动编辑 SharePoint 列表来编辑这些相同的属性。

### <a name="import-the-app"></a>导入应用

1. 登录到 [Power Apps](https://make.powerapps.com)。
1. 从左侧导航栏中选择 "**应用**"。
1. 从命令栏中选择 "**导入**"。
1. 上传 GitHub 存储库中的**CrisisCommunication**文件：

    ![导入应用程序包](media/sample-crisis-communication-app/31-Import-App.png)

1. 选择“导入”。

### <a name="update-the-sharepoint-connections"></a>更新 SharePoint 连接

1. 返回到**应用**列表。
1. 为**危机通信**应用选择**更多命令**（...）。
1. 从上下文菜单中选择 "**编辑**"：

    ![编辑应用](media/sample-crisis-communication-app/05-Edit-App.png)

1. **登录**或创建任何所需的连接，并选择 "**允许**"：

    ![允许连接](media/sample-crisis-communication-app/allow-connections.png)

1. 在左窗格中导航到数据源：

    ![数据源](media/sample-crisis-communication-app/data-sources.png)

1. **删除**应用内现有的 sharepoint 列表，因为它们不指向当前的 sharepoint 站点：

    ![删除数据源](media/sample-crisis-communication-app/remove-data-source.png)

1. 从您自己的 SharePoint 站点添加列表。 首先在搜索栏中搜索 SharePoint：

    ![搜索 SharePoint](media/sample-crisis-communication-app/sharepoint.png)

1. 选择 " **SharePoint** " 并选择一个连接：

    ![SharePoint 连接](media/sample-crisis-communication-app/sharepoint-connection.png)

1. 将 URL 复制并粘贴到 SharePoint 站点的 "文本" 字段中，然后选择 "**连接**"：

    ![SharePoint 站点 URL](media/sample-crisis-communication-app/site-url.png)

1. 选择所有 SharePoint 列表和库，并选择 "**连接**"：

    ![连接 SharePoint 列表](media/sample-crisis-communication-app/sharepoint-lists.png)

1. **保存**并**发布**应用。

### <a name="update-the-request-help-flow"></a>更新请求帮助流

此流将向请求帮助的中心团队团队发送自适应卡。

![导入应用程序包](media/sample-crisis-communication-app/21-Request-Help.png)

在完成以下步骤之前，请先为危机管理团队创建团队团队。 完成后，可以获取该 ID 并将其导入到流中。 如果需要帮助创建团队团队，请跳转到[创建中心危机管理团队团队](#create-a-central-crisis-management-teams-team)。

1. 导航到要将所有帮助请求发布到的 "团队" 通道。
1. 选择通道的 " **...** " 菜单。
1. 选择 "**获取通道的链接**"。

    ![获取通道链接](media/sample-crisis-communication-app/17-Get-link-to-channel.png)

1. 复制链接，并将其粘贴到文本编辑器中。

    ![复制链接](media/sample-crisis-communication-app/18-Copy-link.png)

1. 提取团队 ID，该 ID 是 `groupId=` 之后和 `&tenantId=`之前的所有内容。 <br> 例如，在以下 URL 中，通道 ID `8bc7c0c2-0d4c-4fb8-af99-32da74c9237b`：
   
   `https://teams.microsoft.com/l/channel/19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2/General?groupId=8bc7c0c2-0d4c-4fb8-af99-32da74c9237b&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47`，
   
1. 提取通道 ID，该 ID 是 `https://teams.microsoft.com/l/channel/` 之后和 `/General`之前的所有内容。 <br> 例如，在以下 URL 中，通道 ID `19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2`：
   
   `https://teams.microsoft.com/l/channel/19%3ab2fa9fc20f3042a9b63fc5890e1813f8%40thread.tacv2/General?groupId=8bc7c0c2-0d4c-4fb8-af99-32da74c9237b&tenantId=72f988bf-86f1-41af-91ab-2d7cd011db47`，
   
1. 导航到[flow.microsoft.com](https://flow.microsoft.com)。
1. 从左侧导航栏中选择 **"我的流**"。
1. 选择**更多命令**（...） 对于**RequestHelp** ，选择 "**编辑**"。
    ![编辑应用](media/sample-crisis-communication-app/20-Edit-Flow.png)
1. 打开 "**团队 Id** " 卡。
1. 将团队 ID 粘贴到 "**值**" 字段中。
1. 打开**通道 ID**卡。
1. 将通道 ID 粘贴到 "**值**" 字段中。
    ![设置团队 Id](media/sample-crisis-communication-app/22-Set-Team-IDs.png)

## <a name="import-and-set-up-the-admin-app"></a>导入并设置管理应用
若要管理已导入的应用，需要对管理应用重复相同的步骤。

1. 登录到 [Power Apps](https://make.powerapps.com)。
1. 从左侧导航栏中选择 "**应用**"。
1. 从命令栏中选择 "**导入**"。
1. 上传 GitHub 存储库中的**CrisisCommunicationAdminApp**文件：

    ![导入应用程序包](media/sample-crisis-communication-app/import-app.png)

1. 选择“导入”。

### <a name="update-the-sharepoint-connections"></a>更新 SharePoint 连接

1. 返回到**应用**列表。
1. 选择 "**更多命令**" （...），了解**危机通信管理应用**程序应用。
1. 从上下文菜单中选择 "**编辑**"：

    ![编辑应用](media/sample-crisis-communication-app/08-Edit-Admin-App.png)

1. **登录**或创建任何所需的连接，然后选择 "**允许**"。

1. 在左窗格中导航到数据源：

    ![数据源](media/sample-crisis-communication-app/data-sources.png)

1. **删除**应用内现有的 sharepoint 列表，因为它们不指向当前的 sharepoint 站点：

    ![删除数据源](media/sample-crisis-communication-app/remove-data-source.png)

1. 从您自己的 SharePoint 站点添加列表。 首先在搜索栏中搜索 SharePoint：

    ![搜索 SharePoint](media/sample-crisis-communication-app/sharepoint.png)

1. 选择 " **SharePoint** " 并选择一个连接：

    ![SharePoint 连接](media/sample-crisis-communication-app/sharepoint-connection.png)

1. 将 URL 复制并粘贴到 SharePoint 站点的 "文本" 字段中，然后选择 "**连接**"：

    ![SharePoint 站点 URL](media/sample-crisis-communication-app/site-url.png)

1. 选择所有 SharePoint 列表和库，并选择 "**连接**"：

    ![连接 SharePoint 列表](media/sample-crisis-communication-app/sharepoint-lists.png)

1. **保存**并**发布**管理应用。

## <a name="create-initial-content-for-the-app"></a>创建应用的初始内容

你已成功导入危机通信应用及其管理应用。

你现在可以开始创建初始内容。 若要开始，请打开危机通信管理应用。

![管理应用](media/sample-crisis-communication-app/09-Admin-App.png)

利用管理应用程序，你可以自定义危机通信应用内的所有信息，还可以为随附的流设置密钥设置。

> [!NOTE]
> 提醒你，如果不想使用管理应用，还可以通过手动编辑 SharePoint 列表来编辑这些相同的属性。

### <a name="setup-key-parameters-under-admin-settings"></a>在管理设置下设置密钥参数

若要初始化你的应用，你需要通过导航到 "**管理设置**" 提供所有必需的字段。

填写所有字段，然后选择 "**保存**"。

| **字段名称** | **SharePoint 中的逻辑名称** | 用途 |
|-|-|-|
| 管理员电子邮件 | AdminContactEmail | 用于通知其他正在管理应用程序的用户。 |
| 徽标 URL | Logo | 将在左上角显示的应用的徽标。 |
| AAD 组 ID | AADGroupID | 用于向最终用户发送通知，告知最终用户有关内部公司更新的信息，请通过*通知用户了解新的危机通信新闻*流。 |  
| 应用程序 URL | AppURL | 应用的位置，以便在新的*危机通信新闻流上通知用户*可以在选择 "**阅读更多**" 后重定向用户。 | 
| 政府 RSS 源 | GovernmentRSSFeed | 用于在应用程序中填充世界上的新闻功能。 如果你想要从受信任的源向你的员工提供其他信息，则此方法很有用。 |
| 通知方法 | PreferredSentNotification | 由在*新的危机通信新闻流上通知用户*，用于确定它在发出通知时应使用哪个分发通道。 |
| 功能标志 | Feature1 .。。8 | 用于禁用或启用应用程序中的每个功能。 |

#### <a name="finding-the-aad-of-your-distribution-group"></a>查找通讯组的 AAD
1. 导航到[aad.portal.azure.com](https://aad.portal.azure.com)
1. 从左侧导航栏中选择 " **Azure Active Directory** "。
1. 选择**组**。
1. 搜索并选择你的通讯组。
1. 复制 "**对象 Id** " 字段。

    ![获取 Azure 中的 AAD ID](media/sample-crisis-communication-app/11-AAD-Group-ID.png)

1. 将该 ID 粘贴到管理应用程序中的**AAD 组 ID**字段。

### <a name="setup-emergency-contacts"></a>设置紧急联系人

1. 导航到 "**公司联系人**"
1. 选择 "**新建联系人**"
1. 填写包含联系人详细信息的窗体。

*列表架构：*

| **字段名称** | **SharePoint 中的逻辑名称** | 用途 |
|-|-|-|
| 全名 | FullName | 联系人的姓名。 |
| E-mail | E-mail | 将为该联系人显示的电子邮件。 |
| Country | Country | 联系人所在的国家/地区。 这将用于对联系人进行分组，因此，如果国家/地区没有任何意义，则可以将此字段用于其他分组。 |
| Comments | Comments | 显示有关联系人的其他信息;用于描述何时与此联系人进行联系。 |
| 不推荐使用 | 不推荐使用 | 允许您隐藏现有的紧急联系人。 |

### <a name="setup-initial-company-news"></a>设置初始公司新闻

1. 导航到**公司资讯**
1. 选择 "**新建发布**"
1. 填写表单。

*列表架构：*

| **字段名称** | **SharePoint 中的逻辑名称** | 用途 |
|-|-|-|
| 职务 | 职务 | 更新的标题。 |
| 详细信息 | 详细信息 | 完整更新。 您可以在此字段中使用 HTML。 |
| 简介 | 简介 | 有关更新的简短消息。 这将在*通知用户有关新的危机通信新闻*流和更新库中使用。 |
| 不推荐使用 | 不推荐使用 | 允许您隐藏现有帖子。 |

### <a name="setup-helpful-tips"></a>设置有用提示

1. 导航至**有用提示**。
1. 选择 "**新提示**"。
1. 填写表单。

*列表架构：*

| **字段名称** | **SharePoint 中的逻辑名称** | 用途 |
|-|-|-|
| 职务 | 职务 | 有用提示的标题。 |
| 资源 URL | ResourceURL | 指向附加阅读材料的链接。 （可选） |
| 子标题 | 标题 | 提示的子标题。 （可选） |
| 说明 | 说明 | 有用提示的完整说明。 |
| 不推荐使用 | 不推荐使用 | 允许您隐藏有帮助的提示。 |

### <a name="setup-links"></a>设置链接

1. 导航到 "**链接**"。
1. 选择 "**创建新链接**"。
1. 填写表单。

*列表架构：*

| **字段名称** | **SharePoint 中的逻辑名称** | 用途 |
|-|-|-|
| 职务 | 职务 | 链接的文本。 |
| URL | URL | 链接的 URL。 |
| 说明 | 说明 | 有关链接的其他详细信息。 （可选） |
| 不推荐使用 | 不推荐使用 | 允许您隐藏链接。 |

### <a name="setup-faqs"></a>设置常见问题

1. 导航到**FAQ**。
1. 选择 "**创建新的常见问题**"。
1. 填写表单。

*列表架构：*

| **字段名称** | **SharePoint 中的逻辑名称** | 用途 |
|-|-|-|
| 职务 | 职务 | 常见问题的问题。 |
| 级别 | 级别 | 常见问题的顺序。 |
| Answer | Answer | 常见问题的答案 |
| 不推荐使用 | 不推荐使用 | 允许您隐藏常见问题。 |

## <a name="test-and-share-the-app"></a>测试并共享应用

现在，您已成功设置了所有数据，现在可以测试应用程序以确保其正常工作：

1. 登录到 [Power Apps](https://make.powerapps.com)。
2. 从左侧导航栏中选择 "**应用**"。
3. 选择要播放应用的**危机通信**。

成功测试应用后，可以与公司中的每个人共享应用。

## <a name="import-and-set-up-the-notification-flow"></a>导入和设置通知流

只要有新的公司更新，应用程序就会使用 flow 向最终用户发送通知。

### <a name="import-the-news-notification-flow"></a>导入新闻通知流

1. 导航到[flow.microsoft.com](https://flow.microsoft.com)
1. 从左侧导航栏中选择 **"我的流**"。
1. 选择命令栏中的 "**导入**" 按钮。
1. 从 GitHub 存储库上传**CrisisCommunicationNewsNotification**包：

    ![上传 CrisisCommunicationNewsNotification](media/sample-crisis-communication-app/upload-news-notification.png)

1. 通过为每个连接选择 "**在导入时选择**" 链接并完成表单，为新流添加连接：

    ![导入期间选择](media/sample-crisis-communication-app/select-during-import.png)

1. 如果需要创建新的连接，请首先在 "导入设置" 窗格中选择 "**新建**"。
1. 在命令栏中选择 "**新建连接**"：

    ![创建新连接](media/sample-crisis-communication-app/create-connection.png)

1. 搜索连接的名称;例如， **PowerApps 通知（预览）** ：

    ![通知](media/sample-crisis-communication-app/notifications.png)

1. 选择适当的连接。
1. 如果要创建到**PowerApps 通知（预览）** 的连接，你将看到以下对话框：

    ![通知对话框](media/sample-crisis-communication-app/notifications-dialog.png)

1. 若要获取 ID，请导航到**应用**列表。
1. 为**危机通信**应用选择**更多命令**（...），并选择 "详细信息"：

    ![更多命令](media/sample-crisis-communication-app/06-App-Details.png)

1. 复制**应用 ID**：

    ![应用 ID](media/sample-crisis-communication-app/07-App-ID.png)

1. 将**应用 ID**粘贴到 "连接创建" 对话框中，然后选择 "**创建**"：

    ![粘贴应用程序 ID](media/sample-crisis-communication-app/target-app-id.png)

1. 创建新连接后，返回到 "**导入设置**" 面板，然后选择 "**刷新列表**" 按钮。
1. 现在，你的新连接应会出现，你可以选择它，然后选择 "**保存**"。
1. 添加完所有连接后，选择 "**导入**"。

    ![导入连接](media/sample-crisis-communication-app/imported-connections.png)

### <a name="edit-the-news-notification-flow"></a>编辑新闻通知流

1. 导入完成后，返回到 **"我的流**"。
1. 选择新导入的流**通知用户有关新的危机通信新闻**。
1. 从命令栏中选择 "**编辑**"。
1. 打开**发布新项时**调用的卡片。
1. 将**站点地址**更改为你的 SharePoint 站点的名称。
1. 将**列表名称**更改为**CI_CompanyNews**。
1. 打开名为 **"获取管理配置设置"** 的卡。
1. 将**站点地址**更改为你的 SharePoint 站点的名称。
1. 将**列表名称**更改为**CI_configAdminSetup**。
1. 打开名为 "**初始化变量–读取更多文本**" 的卡。
1. 将此**值**更改为您的本地语言中的 "阅读更多"。

    ![流设置](media/sample-crisis-communication-app/flow-options.png)

1. 选择 "**保存**" 以提交更改。

> [!NOTE]
> 如果某个连接尚未获得授权，则可能会收到错误。
如果发生这种情况，请打开包含未经授权的连接和重新授权的卡。

### <a name="test-the-news-notification-flow"></a>测试新闻通知流

若要测试新闻通知流，请返回到管理应用并创建新的内部公司更新。
稍后，你的通讯组列表中的所有用户都将收到你首选的通知首选项的更新。

> [!NOTE]
> 如果遇到错误，请确保已在管理应用内的 "管理员" 设置中成功输入了你的通讯组 ID。

## <a name="monitor-office-absences-with-power-bi"></a>用 Power BI 监视办公室请假

部署了应用后，人们开始通知他们出于各种原因（例如，病假或在家工作），就可以使用 Power BI 报表来跟踪这些人员所在的数量和位置，你现在可以使用报表来跟踪这些人员的位置。

若要开始，可以使用已下载的[资产包](#prerequisites)中提供的示例报表 "状态报告 .pbix"。
如果需要，请下载[Power BI Desktop](https://powerbi.microsoft.com/downloads)。 我们还需要在之前创建的**CI_Employee 状态**SharePoint 列表中显示一些信息，因此让我们先来了解一下。 在网站中打开列表，并在 "设置" 图标下选择 "列表设置"：

![员工状态列表设置](media/sample-crisis-communication-app/001-SharePointList-ListSettings-nolines.PNG)

记下浏览器地址栏上的**站点名称**和**列表 id** ：

![员工状态列表和站点 Id](media/sample-crisis-communication-app/002-SharePointList-AddressAndId-nolines.PNG)

此时，我们已准备好打开 Power BI 报告;启动 Power BI 并打开**状态报告 .pbix**文件。 将鼠标移到**CI_Employee 状态**数据源的右侧，直到看到省略号，选择它，然后选择 "编辑查询" 选项：

![编辑查询](media/sample-crisis-communication-app/003-PowerBI-EditQuery-nolines.PNG)

打开 Power Query 编辑器后，右键单击**CI_Employee 状态**数据源，并选择**高级编辑器**：

![Power Query 高级编辑器](media/sample-crisis-communication-app/004-PowerQuery-AdvancedEditor-nolines.PNG)

在这里，我们将使用 SharePoint 列表中的站点名称和列表 id：复制表中的新 SharePoint 站点，以及三个位置中的列表 id，其中 GUID 为突出显示，然后选择 "**完成**"。

![Power Query 高级编辑器更新](media/sample-crisis-communication-app/005-PowerQuery-AdvancedEditorUpdates-nolines.PNG)

选择 "**关闭 & 应用**" 以更新报表以从 SharePoint 列表中提取数据。

![Power Query 关闭并应用](media/sample-crisis-communication-app/006-PowerQuery-CloseAndApply-nolines.PNG)

现在，我们有了一个 Power BI 报表，其中显示当天办公室缺勤的地理信息，以及一段时间内此类请假的趋势。 现在，我们可以发布报表，以便组织中的其他人可以看到它。

![Power BI 发布报表](media/sample-crisis-communication-app/007-PowerBI-Publish-nolines.PNG)

## <a name="integrate-your-app-into-teams"></a>将你的应用集成到团队

现在，你已拥有一个已与所有人共享的有效应用，你可以使用团队部署该应用，并在 Microsoft 团队中创建危机管理团队以响应问题。

### <a name="deploy-the-app-to-the-app-bar"></a>将应用部署到应用栏

如果你是团队管理员，则可以将应用推送到团队应用栏中的所有用户。

![团队应用](media/sample-crisis-communication-app/19-App-in-Teams.png)

1. 登录到 [Power Apps](https://make.powerapps.com)。
1. 从左侧导航栏中选择 "**应用**"。
1. 为**危机通信**应用选择 " **...** " 菜单。
1. 选择 "**添加到团队**"。

    ![添加到团队](media/sample-crisis-communication-app/24-Add-to-Teams.png)

1. 选择 "**下载应用**"。

    ![下载应用](media/sample-crisis-communication-app/25-Download-App.png)

1. 打开**团队**
1. 导航到左侧应用栏中的 "**应用**"。
1. 选择 "**上传自定义应用**"。
1. 如果你是团队管理员，你将看到为整个租户上载应用的能力。 选择 "**为 Contoso 上传**"。

    ![上载](media/sample-crisis-communication-app/26-Upload-for-Contoso.png)

1. 上传从 Power Apps 下载的文件。
1. 导航到[团队管理中心](https://admin.teams.microsoft.com/dashboard)
1. 在左侧导航栏中选择 "**团队应用**" 下的 "**设置策略**"。

    ![应用安装策略](media/sample-crisis-communication-app/27-Setup-Policies.png)

1. 选择 "**全局（组织范围设置）** "。
1. 选择 "**添加应用**"。

    ![添加应用](media/sample-crisis-communication-app/28-Add-App.png)

1. 搜索并选择已上传的**危机信息**应用。

    ![添加固定应用](media/sample-crisis-communication-app/29-Add-Pinned-App.png)

1. 选择“添加”。
1. 选择“保存”。

> [!NOTE]
> 用户可能需要长达24小时的时间才能让应用程序在其应用栏中自动固定。

### <a name="create-a-central-crisis-management-teams-team"></a>创建中心危机管理团队团队

为了协调你的危机响应，你需要为危机管理团队创建一个中心团队团队，并为其填充所有相关信息。

1. 导航到团队。
1. 选择左侧应用栏中的 "**团队**"。
1. 选择 "**加入" 或 "创建团队**"。
1. 选择 "**创建团队**" 并完成剩余步骤。

    ![创建团队](media/sample-crisis-communication-app/23-Create-Team.png)

成功创建团队后，可以将相关信息固定为选项卡。 例如，你可能想要将危机管理管理应用或 Power BI 报表固定到你的团队。 若要将管理应用添加为选项卡：

1. 选择 " **+** " 按钮。
1. 搜索并选择 "**电源应用**"。
1. 搜索并选择 "**危机信息管理员**"。

    ![固定应用](media/sample-crisis-communication-app/32-Pin-Teams-app.png)

1. 选择“保存”。

添加 Power BI 报表：

1. 选择 " **+** " 按钮。
1. 搜索并选择**Power BI**。
1. 搜索并选择 Power BI 报表。
1. 选择“保存”。

## <a name="next-steps"></a>后续步骤
- [公式参考](https://docs.microsoft.com/powerapps/maker/canvas-apps/formula-reference)
- [控件参考](https://docs.microsoft.com/powerapps/maker/canvas-apps/reference-properties)
