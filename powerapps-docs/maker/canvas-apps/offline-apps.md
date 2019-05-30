---
title: 开发可脱机运行的画布应用 | Microsoft Docs
description: 开发可脱机运行的画布应用，无论联机还是脱机，用户都能高效工作。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/31/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8004a39e83ea3615ce8a77637a9f5c0271b67781
ms.sourcegitcommit: 157ab15738e2d0d1bf9097bbb7b9e3d9c29a4015
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2019
ms.locfileid: "66265727"
---
# <a name="develop-offline-capable-canvas-apps"></a>开发可脱机运行的画布应用

移动用户通常需要可以高效工作，即使当它们具有有限或者没有连接。 当你生成画布应用时，可以执行这些任务：

- 打开 PowerApps Mobile 并运行应用程序脱机时。
- 使用 [Connection](../canvas-apps/functions/signals.md#connection) 信号对象确定应用何时处于脱机、联机或按流量计费的连接状态中。
- 在脱机时使用[集合](../canvas-apps/create-update-collection.md)或利用 [LoadData 和 SaveData](../canvas-apps/functions/function-savedata-loaddata.md) 等函数进行基本数据存储。

## <a name="limitations"></a>限制

**LoadData**并**SaveData**组合起来形成一个简单的机制来存储在本地设备上的少量数据。 通过使用这些函数，可以将简单的离线功能添加到您的应用程序。

这些函数都受可用的应用的内存量，因为它们在内存中集合上运行。 具体取决于设备、 操作系统、 使用 PowerApps Mobile，内存和应用程序在屏幕和控件方面的复杂性而异的可用内存。 如果存储超过几兆字节的数据，请测试预期的情况下，根据您希望其运行的设备上使用对应用程序。 通常，您将有 30-70 兆字节的可用内存。

函数也不会自动解决合并冲突当设备处于联机状态。 编写表达式时，保存哪些数据以及如何处理重新连接上的配置将负责创建者。

对于脱机功能的更新，返回到本主题和订阅[PowerApps 博客](https://powerapps.microsoft.com/blog/)。

## <a name="overview"></a>概述

在设计时的脱机方案，应首先考虑您的应用程序如何处理的数据。 PowerApps 中的应用主要通过一组访问数据[连接器](../canvas-apps/connections-list.md)平台提供，如 SharePoint、 Office 365 和 Common Data Service。 还可以生成自定义连接器，让应用能够访问任何提供 RESTful 终结点的服务。 这可以是 Web API 或 Azure Functions 等服务。 所有这些连接器都通过 Internet 使用 HTTPS。也就是说，用户必须联机，才能访问数据，并使用服务提供的其他任何功能。

![使用连接器的 PowerApps 应用](./media/offline-apps/online-app.png)

### <a name="handling-offline-data"></a>处理脱机数据

在 PowerApps 中，可以筛选、 搜索、 排序、 聚合和数据源无关的一致方式处理数据。 源范围中应用的内存中集合复制到 SQL 数据库和 Common Data Service 的 SharePoint 列表。 由于这种一致性，你可以轻松地重定目标应用以使用不同的数据源。 更重要的是脱机的情况下，您可以使用本地集合进行数据管理，几乎不用更改到应用程序的逻辑。 实际上，本地集合是用于处理脱机数据的主要机制。

## <a name="build-an-offline-app"></a>生成脱机应用

为了突出应用开发的脱机方面，本主题说明了一个简单的方案主要围绕 Twitter。 你将生成的应用程序，可阅读 Twitter 帖子并提交推文时处于脱机状态。 处于联机状态时，此应用会发布推文并重新加载本地数据。

在高级别，该应用程序执行这些任务：

- 当用户打开应用程序：

  - 如果设备处于联机状态，该应用程序提取通过 Twitter 连接器的数据并填充与该数据的集合。
  - 如果设备处于脱机状态，应用将数据从本地缓存文件通过使用加载[ **LoadData** ](../canvas-apps/functions/function-savedata-loaddata.md)函数。
  - 用户可以提交推文。 如果应用程序处于联机状态，它将直接向 Twitter 发布推文并刷新本地缓存。

- 在应用处于联机状态时每隔五分钟：

  - 此应用在本地缓存中发布任何推文。
  - 应用程序刷新本地缓存，并将其保存通过使用[ **SaveData** ](../canvas-apps/functions/function-savedata-loaddata.md)函数。

### <a name="step-1-add-twitter-to-a-blank-phone-app"></a>步骤 1:将 Twitter 添加到空白手机应用

1. 在 PowerApps Studio 中选择**文件** > **新建**。
1. 在“空白应用”磁贴上，选择“手机布局”。
1. 在“视图”选项卡上，选择“数据源”。
1. 在中**数据**窗格中，选择**添加数据源**。
1. 选择**新的连接** > **Twitter** > **创建**。
1. 输入你的凭据，创建连接，然后关闭**数据**窗格。

### <a name="step-2-collect-existing-tweets"></a>步骤 2:收集现有推文

1. 在中**树视图**窗格中，选择**应用**，然后设置其**OnStart**属性设为此公式：

    ```powerapps-dot
    If( Connection.Connected,
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 10} ) );
            Set( statusText, "Online data" ),
        LoadData( LocalTweets, "LocalTweets", true );
            Set( statusText, "Local data" )
    );
    SaveData( LocalTweets, "LocalTweets" );
    ```

    > [!div class="mx-imgBorder"]
    > ![若要加载的推文的公式](./media/offline-apps/load-tweets.png)

1. 在中**树视图**窗格中，选择省略号菜单**应用**对象，并选择**运行 OnStart**运行该公式。

    > [!div class="mx-imgBorder"]
    > ![运行用于加载推文的公式](./media/offline-apps/load-tweets-run.png)

    > [!NOTE]
    > **LoadData**并**SaveData**函数可能会显示错误在 PowerApps Studio 中的浏览器不支持它们。 但是，它们将执行通常后将此应用部署到设备。

此公式会检查设备是否处于联机状态：

- 如果设备处于联机状态，该公式将具有搜索词"PowerApps"的最多 10 个推文加载到**localtweets**集合。
- 如果设备处于脱机状态，该公式从名为"localtweets"，如果可用的文件加载本地缓存。

### <a name="step-3-show-tweets-in-a-gallery"></a>步骤 3:显示库中的推文

1. 上**插入**选项卡上，选择**库** > **高度可调的空白**。

1. 设置**项**的属性[**库**](controls/control-gallery.md)控制对`LocalTweets`。

1. 在库模板后，添加三个[**标签**](controls/control-text-box.md)控件，并设置**文本**为下列值之一的每个标签的属性：

    - `ThisItem.UserDetails.FullName & " (@" & ThisItem.UserDetails.UserName & ")"`
    - `Text(DateTimeValue(ThisItem.CreatedAtIso), DateTimeFormat.ShortDateTime)`
    - `ThisItem.TweetText`

1. 将最后一个标签中的文本以粗体显示，以，使库类似于此示例。

    > [!div class="mx-imgBorder"]
    > ![库显示示例推文](./media/offline-apps/tweet-gallery.png)

### <a name="step-4-show-connection-status"></a>步骤 4：显示连接状态

1. 在库中，插入一个标签，并将其**颜色**属性设置为**Red**。

1. 设置最新标签**文本**属性设为此公式：

    `If( Connection.Connected, "Connected", "Offline" )`

此公式可确定设备是否处于联机状态。 如果是，标签显示**已连接**; 否则为它显示了**脱机**。

### <a name="step-5-add-a-box-to-compose-tweets"></a>步骤 5：添加一个框以撰写的推文

1. 连接状态标签下方插入[**文本输入**](controls/control-text-input.md)控件，并将其重命名**NewTweetTextInput**。

1. 将文本输入框的设置**默认**属性设置为`""`。

    > [!div class="mx-imgBorder"]
    > ![通过状态信息和文本输入框中的库](./media/offline-apps/status-input.png)

### <a name="step-6-add-a-button-to-post-the-tweet"></a>步骤 6:添加一个按钮即可发布推文

1. 在文本输入框中下, 添加**按钮**控件，并设置其**文本**属性设置为此值：

    `"Tweet"`

1. 设置按钮的**OnSelect**属性设为此公式：

    ```powerapps-dot
    If( Connection.Connected,
        Twitter.Tweet( "", {tweetText: NewTweetTextInput.Text} ),
        Collect( LocalTweetsToPost, {tweetText: NewTweetTextInput.Text} );
            SaveData( LocalTweetsToPost, "LocalTweetsToPost" )
    );
    Reset( NewTweetTextInput );
    ```  

1. 在中**OnStart**属性**应用**，公式的末尾添加一行：

    ```powerapps-dot
    If( Connection.Connected,
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 100} ) );
            Set( statusText, "Online data" ),
        LoadData( LocalTweets, "LocalTweets", true );
            Set( statusText, "Local data" )
    );
    SaveData( LocalTweets, "LocalTweets" );
    LoadData( LocalTweetsToPost, "LocalTweetsToPost", true );  // added line
    ```

    > [!div class="mx-imgBorder"]
    > ![运行用于加载推文与取消注释行的公式](./media/offline-apps/load-tweets-save.png)

此公式用于确定设备是否处于联机状态：

- 如果设备处于联机状态，它将立即发布推文。
- 如果设备处于脱机状态，它捕获在推文**LocalTweetsToPost**集合并将其保存到设备。

然后该公式将重置文本输入框中的文本。

### <a name="step-7-check-for-new-tweets"></a>步骤 7:检查新推文

1. 在按钮的右侧，添加**计时器**控件。

    > [!div class="mx-imgBorder"]
    > ![最终应用程序](./media/offline-apps/final-app.png)

1. 设置计时器**持续时间**属性设置为**300000**。

1. 设置计时器**AutoStart**和**重复**属性设置为**true**。

1. 设置计时器**OnTimerEnd**为以下公式：

    ```powerapps-dot
    If( Connection.Connected,
        ForAll( LocalTweetsToPost, Twitter.Tweet( "", {tweetText: tweetText} ) );
        Clear( LocalTweetsToPost );
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 10} ) );
        SaveData( LocalTweets, "LocalTweets" );
   )
    ```

此公式可确定设备是否处于联机状态。 如果是，应用程序推文中的所有项**LocalTweetsToPost**集合，然后再清除集合。

## <a name="test-the-app"></a>测试应用程序

1. 打开连接到 Internet 的移动设备上的应用。

    现有的推文会显示在库中，并且状态显示**已连接**。

1. 断开设备与 Internet 的启用设备的飞行模式和禁用的 wi-fi 连接。

    状态标签将显示在应用程序处于**脱机**。

1. 设备处于脱机状态，而编写的推文，其中包括**PowerApps**，然后选择**推文**按钮。

    推文中本地存储**LocalTweetsToPost**集合。

1. 通过禁用设备的飞行模式和启用的 wi-fi 重新连接到 Internet 的设备。

    在五分钟内，此应用发布推文，显示在库中。

我们希望这篇文章能够帮助你了解 PowerApps 提供的用于生成脱机应用的功能。 和以往一样，请在我们的[论坛](https://powerusers.microsoft.com/t5/PowerApps-Forum/bd-p/PowerAppsForum1)中提供反馈，并在 [PowerApps 社区博客](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/bg-p/PowerAppsBlog)中分享你的脱机应用示例。