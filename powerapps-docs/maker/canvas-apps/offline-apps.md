---
title: 开发可脱机运行的画布应用 | Microsoft Docs
description: 开发可脱机运行的画布应用，无论联机还是脱机，用户都能高效工作。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 02/29/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6ec1a55713b3cce0a98c02058124b5b3d159b376
ms.sourcegitcommit: 129d004e3d33249b21e8f53e0217030b5c28b53f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2020
ms.locfileid: "78265571"
---
# <a name="develop-offline-capable-canvas-apps"></a>开发可脱机运行的画布应用

即使移动用户的连接受到限制或没有任何连接，它们也经常需要提高工作效率。 生成画布应用时，可以执行以下任务：

- 脱机时打开 Power Apps Mobile 并运行应用。
- 使用 [Connection](functions/signals.md#connection) 信号对象确定应用何时处于脱机、联机或按流量计费的连接状态中。
- 脱机时，使用[集合](create-update-collection.md)并利用[ **LoadData**和**SaveData** ](functions/function-savedata-loaddata.md)函数进行基本数据存储。

本文包含使用 Twitter 数据的示例。  [ **LoadData**和**SaveData**函数引用](functions/function-savedata-loaddata.md)中包含一个甚至不需要连接的更简单的示例。

## <a name="limitations"></a>限制

**LoadData**和**SaveData**组合起来形成一个简单的机制，用于在本地设备上存储少量数据。 通过使用这些函数，你可以向应用程序添加简单的脱机功能。

这些函数受可用应用内存量的限制，因为它们对内存中集合进行操作。 可用内存可能会根据设备、操作系统、Power Apps 移动使用的内存以及应用程序在屏幕和控件中的复杂性而有所不同。 如果存储的数据量超过了几 mb，请使用预期的方案在预期运行应用程序的设备上测试应用。 通常会有 30-70 mb 的可用内存。

当设备联机时，函数也不会自动解决合并冲突。 在编写表达式时，配置如何保存哪些数据以及如何处理重新连接。

有关脱机功能的更新，请返回到本主题，并订阅[Power Apps 博客](https://powerapps.microsoft.com/blog/)。

## <a name="overview"></a>概述

设计脱机方案时，应该首先考虑应用如何处理数据。 Power Apps 中的应用主要通过平台提供的一组[连接器](../canvas-apps/connections-list.md)（例如 SharePoint、Office 365 和 Common Data Service）来访问数据。 还可以生成自定义连接器，让应用能够访问任何提供 RESTful 终结点的服务。 这可以是 Web API 或 Azure Functions 等服务。 所有这些连接器都通过 Internet 使用 HTTPS。也就是说，用户必须联机，才能访问数据，并使用服务提供的其他任何功能。

![带有连接器的 Power Apps 应用](./media/offline-apps/online-app.png)

### <a name="handling-offline-data"></a>处理脱机数据

在 Power Apps 中，无论数据源如何，都可以通过一致的方式对数据进行筛选、搜索、排序、聚合和操作。 源范围从应用到 SharePoint 列表的内存中集合到 SQL 数据库和 Common Data Service。 由于这种一致性，你可以轻松地将应用重定向到使用不同的数据源。 更重要的是，对于脱机方案，你可以将本地集合用于数据管理，几乎不会更改应用的逻辑。 实际上，本地集合是用于处理脱机数据的主要机制。

## <a name="build-an-offline-app"></a>构建脱机应用

为了使重点关注应用程序开发的脱机方面，本主题介绍了一个围绕 Twitter 的简单方案。 你将构建一个应用程序，使你能够在脱机时读取 Twitter 帖子并提交推文。 处于联机状态时，此应用会发布推文并重新加载本地数据。

在高级别，应用程序执行以下任务：

- 当用户打开应用时：

  - 如果设备处于联机状态，则应用会通过 Twitter 连接器获取数据，并使用该数据填充集合。
  - 如果设备处于脱机状态，则应用会使用[**LoadData**](../canvas-apps/functions/function-savedata-loaddata.md)函数从本地缓存文件加载数据。
  - 用户可以提交推文。 如果应用处于联机状态，则会将推文直接发送到 Twitter 并刷新本地缓存。

- 在应用联机时每五分钟一次：

  - 此应用将发布本地缓存中的任何推文。
  - 应用会刷新本地缓存，并使用[**SaveData**](../canvas-apps/functions/function-savedata-loaddata.md)函数保存它。

### <a name="step-1-add-twitter-to-a-blank-phone-app"></a>步骤1：将 Twitter 添加到空白手机应用

1. 在 Power Apps Studio 中，选择 "**文件** > **新建**"。
1. 在“空白应用”磁贴上，选择“手机布局”。
1. 在“视图”选项卡上，选择“数据源”。
1. 在 "**数据**" 窗格中，选择 "**添加数据源**"。
1. 选择 "**新建连接** > **Twitter** > **创建**"。
1. 输入你的凭据，创建连接，然后关闭 "**数据**" 窗格。

### <a name="step-2-collect-existing-tweets"></a>步骤2：收集现有推文

1. 在**树视图**窗格中选择 "**应用**"，然后将其**OnStart**属性设置为以下公式：

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
    > ![公式加载推文](./media/offline-apps/load-tweets.png)

1. 在 "**树视图**" 窗格中，选择**应用**对象的省略号菜单，然后选择 "**运行 OnStart** " 以运行该公式。

    > [!div class="mx-imgBorder"]
    > ![运行公式以加载推文](./media/offline-apps/load-tweets-run.png)

    > [!NOTE]
    > 由于浏览器不支持**LoadData**和**SaveData**函数，因此它可能会在 Power Apps Studio 中显示错误。 但是，在将此应用部署到设备后，它们会正常执行。

此公式检查设备是否处于联机状态：

- 如果设备处于联机状态，则该公式会将搜索词 "PowerApps" 最多加载10个推文到**LocalTweets**集合中。
- 如果设备处于脱机状态，则该公式从名为 "LocalTweets" 的文件（如果有）加载本地缓存。

### <a name="step-3-show-tweets-in-a-gallery"></a>步骤3：在库中显示推文

1. 在 "**插入**" 选项卡上，选择 "**库** > **空的灵活高度**"。

1. 将[**库**](controls/control-gallery.md)控件的**Items**属性设置为 `LocalTweets`。

1. 在库模板中，添加三个[**标签**](controls/control-text-box.md)控件，并将每个标签的 " **Text** " 属性设置为以下值之一：

    - `ThisItem.UserDetails.FullName & " (@" & ThisItem.UserDetails.UserName & ")"`
    - `Text(DateTimeValue(ThisItem.CreatedAtIso), DateTimeFormat.ShortDateTime)`
    - `ThisItem.TweetText`

1. 将最后一个标签中的文本设置为粗体，使库类似于此示例。

    > [!div class="mx-imgBorder"]
    > 显示示例推文的 ![库](./media/offline-apps/tweet-gallery.png)

### <a name="step-4-show-connection-status"></a>步骤4：显示连接状态

1. 在库下插入标签，然后将其 "**颜色**" 属性设置为 "**红色**"。

1. 将最新标签的**Text**属性设置为以下公式：

    `If( Connection.Connected, "Connected", "Offline" )`

此公式确定设备是否处于联机状态。 如果是，则标签显示**已连接**;否则，它会显示为**脱机**。

### <a name="step-5-add-a-box-to-compose-tweets"></a>步骤5：添加框以组合推文

1. 在 "连接-状态标签" 下，插入一个[**文本输入**](controls/control-text-input.md)控件，并将其重命名为**NewTweetTextInput**。

1. 将文本输入框的**默认**属性设置为 `""`。

    > [!div class="mx-imgBorder"]
    > ![在状态信息和文本输入框上](./media/offline-apps/status-input.png)

### <a name="step-6-add-a-button-to-post-the-tweet"></a>步骤6：添加一个按钮以发布推文

1. 在文本输入框下，添加一个**按钮**控件，并将其**text**属性设置为以下值：

    `"Tweet"`

1. 将该按钮的**OnSelect**属性设置为以下公式：

    ```powerapps-dot
    If( Connection.Connected,
        Twitter.Tweet( "", {tweetText: NewTweetTextInput.Text} ),
        Collect( LocalTweetsToPost, {tweetText: NewTweetTextInput.Text} );
            SaveData( LocalTweetsToPost, "LocalTweetsToPost" )
    );
    Reset( NewTweetTextInput );
    ```  

1. 在**应用**的**OnStart**属性中，在公式末尾添加一行：

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
    > ![运行公式以通过取消注释行加载推文](./media/offline-apps/load-tweets-save.png)

此公式确定设备是否处于联机状态：

- 如果设备处于联机状态，它会立即发送推文。
- 如果设备处于脱机状态，它将捕获**LocalTweetsToPost**集合中的推文，并将其保存到设备。

然后，该公式将重置文本输入框中的文本。

### <a name="step-7-check-for-new-tweets"></a>步骤7：检查是否有新的推文

1. 在按钮右侧，添加**计时器**控件。

    > [!div class="mx-imgBorder"]
    > ![最终应用](./media/offline-apps/final-app.png)

1. 将计时器的**Duration**属性设置为**300000**。

1. 将计时器的**自动启动**和**重复**属性设置为**true**。

1. 将计时器的**OnTimerEnd**设置为此公式：

    ```powerapps-dot
    If( Connection.Connected,
        ForAll( LocalTweetsToPost, Twitter.Tweet( "", {tweetText: tweetText} ) );
        Clear( LocalTweetsToPost );
        ClearCollect( LocalTweets, Twitter.SearchTweet( "PowerApps", {maxResults: 10} ) );
        SaveData( LocalTweets, "LocalTweets" );
   )
    ```

此公式确定设备是否处于联机状态。 如果是，则应用推文**LocalTweetsToPost**集合中的所有项，然后清除该集合。

## <a name="test-the-app"></a>测试应用程序

1. 在连接到 Internet 的移动设备上打开应用。

    现有推文显示在库中，状态显示为 "**已连接**"。

1. 通过启用设备的飞行模式并禁用 wi-fi，断开设备与 Internet 的连接。

    状态标签显示应用处于**脱机**状态。

1. 当设备处于脱机状态时，编写包含**PowerApps**的推文，然后选择 "**推文**" 按钮。

    推文以本地方式存储在**LocalTweetsToPost**集合中。

1. 通过禁用设备的飞行模式并启用 wi-fi 将设备重新连接到 Internet。

    在5分钟内，应用会发布显示在库中的推文。

我们希望本文能让你了解 Power Apps 用于构建脱机应用程序的功能。 与往常一样，请在我们的[论坛](https://powerusers.microsoft.com/t5/PowerApps-Forum/bd-p/PowerAppsForum1)中提供反馈，并在[Power apps 社区博客](https://powerusers.microsoft.com/t5/PowerApps-Community-Blog/bg-p/PowerAppsBlog)中共享脱机应用的示例。