---
title: Twitter 连接概述 | Microsoft 文档
description: 了解如何连接到 Twitter，逐步完成部分示例，并查看所有函数
services: ''
suite: powerapps
documentationcenter: ''
author: archnair
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/12/2017
ms.author: archanan
ms.openlocfilehash: 7d39d971cf52c673e6d54dee10d72802de6d9450
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="connect-to-twitter-from-powerapps"></a>从 PowerApps 连接到 Twitter
![Twitter](./media/connection-twitter/twittericon.png)

可以通过 Twitter 发布推文，并获取 Twitter 帐户的推文、时间线、好友和关注者。

可以在应用上的标签中显示此信息。 例如，可以添加一个输入文本框，要求用户输入一些推文文本，然后添加用于“发布”推文的按钮。 可以使用类似的方法来获取推文或搜索推文，然后在应用中的标签或库控件中显示文本。

本主题演示如何创建 Twitter 连接，如何在应用中使用 Twitter 连接，并列出可用的函数。

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

## <a name="connect-to-twitter"></a>连接到 Twitter
1. 打开 PowerApps，选择“新建”，然后创建一个“空白应用”。 选择手机或平板电脑布局。 平板电脑布局为你提供了多个工作区：  
   
   ![打开一个空白应用](./media/connection-twitter/blank-app.png)
2. 在右侧窗格中，单击或点击“数据源”选项卡，然后单击或点击“添加数据源”。
3. 选择“新建连接”，然后选择“Twitter”：  
   
    ![连接到 Twitter](./media/connection-twitter/addconnection.png)
   
    ![连接到 Twitter](./media/connection-twitter/add-twitter.png)
4. 选择“连接”，输入 Twitter 登录凭据，然后选择“授权应用”。
5. 选择“添加数据源”。 连接显示在“数据源”下：  
    ![关闭选项窗格](./media/connection-twitter/twitterdatasource.png)

Twitter 连接已创建并已添加到你的应用。 现在可供使用。

## <a name="use-the-twitter-connection-in-your-app"></a>在应用中使用 Twitter 连接
### <a name="show-a-timeline"></a>显示时间线
1. 在“插入”菜单上，选择“库”，然后添加任意**带有文本**的库。
2. 我们来看一些时间线：  
   
   * 若要显示当前用户的时间线，将库的 **[Items](../controls/properties-core.md)** 属性设置为以下公式：
     
       `Twitter.HomeTimeline().TweetText`  
       `Twitter.HomeTimeline({maxResults:3}).TweetText`  
   * 若要显示其他用户的时间线，将库的 **[Items](../controls/properties-core.md)** 属性设置为以下公式：  
     
       `Twitter.UserTimeline( *TwitterHandle* ).TweetText`
     
       输入用双引号括住的 Twitter 用户名或等效值。 例如，直接在公式表达式中输入 `"satyanadella"` 或 `"powerapps"`。
   * 添加一个名为“Tweep”的文本输入控件，并将其 Default 属性设置为 `Tweep.Text`。 在 Tweep 文本框中，键入 Twitter 用户名，如 `satyanadella`（不加引号和 @ 符号）。
     
       在库控件中，将 Items 属性设置为以下公式：  
     
       `Twitter.UserTimeline(Tweep.Text, {maxResults:5}).TweetText`
     
       库控件将自动显示键入的 Twitter 用户名的推文。
     
     > [!TIP]
> 部分公式使用 maxResults 参数显示时间线中最新推文的 x 数量。
3. 将库的 **Items** 属性设置为 `Twitter.HomeTimeline()`。
   
    选择库后，右侧窗格显示该库的选项。
4. 在第一个列表中选择“TweetText”，在第二个列表中选择“TweetedBy”，然后在第三个列表中选择“CreatedAt”。
   
    库现在显示所选属性的值。

### <a name="show-followers"></a>显示关注者
1. 通过使用**带有文本**的库，可以显示部分关注者：  
   
   * 若要显示当前用户的关注者，将库的 **[Items](../controls/properties-core.md)** 属性设置为以下公式：  
     
       `Twitter.MyFollowers()`  
       `Twitter.MyFollowers({maxResults:3})`
   * 若要显示其他用户的关注者，将库的 **[Items](../controls/properties-core.md)** 属性设置为以下公式：  
     
       `Twitter.Followers( *TwitterHandle* )`
     
       输入用双引号括住的 Twitter 用户名或等效值。 例如，直接在公式表达式中输入 `"satyanadella"` 或 `"powerapps"`。
   * 添加一个名为“Tweep”的文本输入控件，并将其 Default 属性设置为 `Tweep.Text`。 在 Tweep 文本框中，键入 Twitter 用户名，如 `satyanadella`（不加引号和 @ 符号）。
     
       在库控件中，将 Items 属性设置为以下公式：  
     
       `Twitter.Followers(Tweep.Text, {maxResults:5})`
     
       库控件自动显示关注你所键入的 Twitter 用户名的用户。
     
     > [!TIP]
> 部分公式使用 maxResults 参数显示时间线中最新推文的 x 数量。
2. 将库的 **Items** 属性设置为 `Twitter.MyFollowers()`。
   
    选择库后，右侧窗格显示该库的选项。
3. 在第二个列表中选择“UserName”，在第三个列表中选择“FullName”。
   
    库现在显示所选属性的值。

### <a name="show-followed-users"></a>显示关注的用户
1. 通过使用**带有文本**的库，可以显示一些关注的用户：  
   
   * 若要显示当前用户关注了哪些用户，将库的 **[Items](../controls/properties-core.md)** 属性设置为以下公式：  
     
       `Twitter.MyFollowing()`  
       `Twitter.MyFollowing({maxResults:3})`
   * 若要显示其他用户关注了哪些用户，将库的 **[Items](../controls/properties-core.md)** 属性设置为以下公式：
     
       `Twitter.Following( *TwitterHandle* )`
     
       输入用双引号括住的 Twitter 用户名或等效值。 例如，直接在公式表达式中输入 `"satyanadella"` 或 `"powerapps"`。
   * 添加一个名为“Tweep”的文本输入控件，并将其 Default 属性设置为 `Tweep.Text`。 在 Tweep 文本框中，键入 Twitter 用户名，如 `satyanadella`（不加引号和 @ 符号）。
     
       在库控件中，将 Items 属性设置为以下公式：  
     
       `Twitter.Following(Tweep.Text, {maxResults:5})`
     
       库控件自动显示你正在关注的其他用户名。
     
     选择库后，右侧窗格显示该库的选项。
2. 在“Body1”列表中选择“Description”，在“Heading1” 列表中选择“UserName”，在“Subtitle1” 列表中选择“FullName”。
   
    库现在显示所选属性的值。

### <a name="show-information-about-a-user"></a>显示有关用户的信息
添加一个标签，然后将“[Text](../controls/properties-core.md)”属性设置为以下公式之一：  

* `twitter.User( *TwitterHandle* ).Description`
* `twitter.User( *TwitterHandle* ).FullName`
* `twitter.User( *TwitterHandle* ).Location`
* `twitter.User( *TwitterHandle* ).UserName`
* `twitter.User( *TwitterHandle* ).FollowersCount`
* `twitter.User( *TwitterHandle* ).FriendsCount`
* `twitter.User( *TwitterHandle* ).Id`
* `twitter.User( *TwitterHandle* ).StatusesCount`

输入用双引号括住的 Twitter 用户名或等效值。 例如，直接在公式表达式中输入 `"satyanadella"` 或 `"powerapps"`。

或者，可以使用输入文本控件键入 Twitter 用户名，如本主题中所述。

### <a name="search-tweets"></a>搜索推文
1. 添加**带有文本**的库，将其 **[Items](../controls/properties-core.md)** 属性设置为下列公式：  
   
    `Twitter.SearchTweet( *SearchTerm* ).TweetText`
   
    输入用双引号括住的 *SearchTerm* 或引用等效值。 例如，直接在公式中输入 `"PowerApps"` 或 `"microsoft"`。
   
    或者，可以使用**输入文本**控件指定搜索项，如本主题中所述。
   
    > [!TIP]
> 使用 maxResults 可显示前五个结果：  
   
    `Twitter.SearchTweet(SearchTerm.Text, {maxResults:5}).TweetText`
2. 将库的 **Items** 属性设置为 `Twitter.SearchTweet(SearchTerm.Text, {maxResults:5})`。
   
    选择库后，右侧窗格显示该库的选项。
3. 在第一个列表中选择“TweetText”，第二个列表中选择“TweetedBy”，然后在第三个列表中选择“CreatedAt”。
   
    库现在显示所选属性的值。

### <a name="send-a-tweet"></a>发送推文
1. 添加一个文本输入控件，然后将其重命名为“MyTweet”。
2. 添加按钮，然后将其 **[OnSelect](../controls/properties-core.md)** 属性设置为以下公式：  
    `Twitter.Tweet({tweetText: MyTweet.Text})`
3. 按 F5，或选择“预览”按钮 (![](./media/connection-twitter/preview.png))。 在“MyTweet”中输入一些文本，然后选择按钮来推送你输入的文本。
4. 按 Esc 返回默认工作区。

## <a name="view-the-available-functions"></a>查看可用函数
此连接包括以下函数：

| 函数名称 | 说明 |
| --- | --- |
| [UserTimeline](connection-twitter.md#usertimeline) |检索指定用户发布的最新推文的集合 |
| [HomeTimeline](connection-twitter.md#hometimeline) |检索我和我的关注者发布的最新推文和转发的推文 |
| [SearchTweet](connection-twitter.md#searchtweet) |检索与指定查询匹配的相关推文的集合 |
| [Followers](connection-twitter.md#followers) |检索关注指定用户的用户 |
| [MyFollowers](connection-twitter.md#myfollowers) |检索关注我的用户 |
| [Following](connection-twitter.md#following) |检索指定用户正在关注的用户 |
| [MyFollowing](connection-twitter.md#myfollowing) |检索我正在关注的用户 |
| [User](connection-twitter.md#user) |检索指定用户的详细信息（例如：用户名、说明、关注者数量等。） |
| [Tweet](connection-twitter.md#tweet) |推文 |
| [OnNewTweet](connection-twitter.md#onnewtweet) |发布与搜索查询匹配的新推文时触发工作流 |

### <a name="usertimeline"></a>UserTimeline
获取用户时间线：检索指定用户发布的最新推文的集合

#### <a name="input-properties"></a>输入属性
| 名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| userName |字符串 |是 |Twitter 用户名 |
| maxResults |整数 |否 |要检索的推文的最大数量，例如 {maxResults:5} |

#### <a name="output-properties"></a>输出属性
| 属性名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| TweetText |字符串 |是 | |
| TweetId |字符串 |否 | |
| CreatedAt |字符串 |否 | |
| RetweetCount |整数 |是 | |
| TweetedBy |字符串 |是 | |
| MediaUrls |数组 |否 | |

### <a name="hometimeline"></a>HomeTimeline
获取主页时间线：检索我和我的关注者发布的最新推文和转发的推文

#### <a name="input-properties"></a>输入属性
| 名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| maxResults |整数 |否 |要检索的推文的最大数量，例如 {maxResults:5} |

#### <a name="output-properties"></a>输出属性
| 属性名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| TweetText |字符串 |是 | |
| TweetId |字符串 |否 | |
| CreatedAt |字符串 |否 | |
| RetweetCount |整数 |是 | |
| TweetedBy |字符串 |是 | |
| MediaUrls |数组 |否 | |

### <a name="searchtweet"></a>SearchTweet
搜索推文：检索与指定查询匹配的相关推文的集合

#### <a name="input-properties"></a>输入属性
| 名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| searchQuery |字符串 |是 |查询文本（可以使用 Twitter 支持的任何查询运算符：http://www.twitter.com/search)） |
| maxResults |整数 |否 |要检索的推文的最大数量，例如 {maxResults:5} |

#### <a name="output-properties"></a>输出属性
| 属性名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| TweetText |字符串 |是 | |
| TweetId |字符串 |否 | |
| CreatedAt |字符串 |否 | |
| RetweetCount |整数 |是 | |
| TweetedBy |字符串 |是 | |
| MediaUrls |数组 |否 | |

### <a name="followers"></a>关注者
获取关注者：检索关注指定用户的用户

#### <a name="input-properties"></a>输入属性
| 名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| userName |字符串 |是 |用户的 Twitter 用户名 |
| maxResults |整数 |否 |要检索的用户的最大数量，例如 {maxResults:5} |

#### <a name="output-properties"></a>输出属性
| 属性名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| 全名 |字符串 |是 | |
| 位置 |字符串 |是 | |
| ID |整数 |否 | |
| UserName |字符串 |是 | |
| FollowersCount |整数 |否 | |
| 说明 |字符串 |是 | |
| StatusesCount |整数 |否 | |
| FriendsCount |整数 |否 | |

### <a name="myfollowers"></a>MyFollowers
获取我的关注者：检索关注我的用户

#### <a name="input-properties"></a>输入属性
| 名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| maxResults |整数 |否 |要检索的用户的最大数量，例如 {maxResults:5} |

#### <a name="output-properties"></a>输出属性
| 属性名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| 全名 |字符串 |是 | |
| 位置 |字符串 |是 | |
| ID |整数 |否 | |
| UserName |字符串 |是 | |
| FollowersCount |整数 |否 | |
| 说明 |字符串 |是 | |
| StatusesCount |整数 |否 | |
| FriendsCount |整数 |否 | |

### <a name="following"></a>关注
获取关注的人：检索指定用户正在关注的用户

#### <a name="input-properties"></a>输入属性
| 名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| userName |字符串 |是 |用户的 Twitter 用户名 |
| maxResults |整数 |否 |要检索的用户的最大数量，例如 {maxResults:5} |

#### <a name="output-properties"></a>输出属性
| 属性名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| 全名 |字符串 |是 | |
| 位置 |字符串 |是 | |
| ID |整数 |否 | |
| UserName |字符串 |是 | |
| FollowersCount |整数 |否 | |
| 说明 |字符串 |是 | |
| StatusesCount |整数 |否 | |
| FriendsCount |整数 |否 | |

### <a name="myfollowing"></a>MyFollowing
获取我关注的人：检索我正在关注的用户

#### <a name="input-properties"></a>输入属性
| 名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| maxResults |整数 |否 |要检索的用户的最大数量，例如 {maxResults:5} |

#### <a name="output-properties"></a>输出属性
| 属性名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| 全名 |字符串 |是 | |
| 位置 |字符串 |是 | |
| ID |整数 |否 | |
| UserName |字符串 |是 | |
| FollowersCount |整数 |否 | |
| 说明 |字符串 |是 | |
| StatusesCount |整数 |否 | |
| FriendsCount |整数 |否 | |

### <a name="user"></a>用户
获取用户：检索指定用户的详细信息（例如：用户名、说明、关注者数量等。）

#### <a name="input-properties"></a>输入属性
| 名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| userName |字符串 |是 |用户的 Twitter 用户名 |

#### <a name="output-properties"></a>输出属性
| 属性名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| 全名 |字符串 |是 | |
| 位置 |字符串 |是 | |
| ID |整数 |否 | |
| UserName |字符串 |是 | |
| FollowersCount |整数 |否 | |
| 说明 |字符串 |是 | |
| StatusesCount |整数 |否 | |
| FriendsCount |整数 |否 | |

### <a name="tweet"></a>推文
发布新推文：推文

#### <a name="input-properties"></a>输入属性
| 名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| TweetText |字符串 |否 |要发布的文本，例如 {tweetText:"hello"} |
| body |字符串 |否 |要发布的媒体 |

#### <a name="output-properties"></a>输出属性
| 属性名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| TweetId |字符串 |是 | |

### <a name="onnewtweet"></a>OnNewTweet
显示新推文时：发布与搜索查询匹配的新推文时触发工作流

#### <a name="input-properties"></a>输入属性
| 名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| searchQuery |字符串 |是 |查询文本（可以使用 Twitter 支持的任何查询运算符：http://www.twitter.com/search)） |

#### <a name="output-properties"></a>输出属性
| 属性名称 | 数据类型 | 需要 | 说明 |
| --- | --- | --- | --- |
| 值 |数组 |否 | |

## <a name="helpful-links"></a>有用链接
查看所有[可用连接](../connections-list.md)。  
了解如何向你的应用[添加连接](../add-manage-connections.md)。

