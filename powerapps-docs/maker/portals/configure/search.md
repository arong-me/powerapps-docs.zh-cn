---
title: Power Apps 门户中的全局搜索 | MicrosoftDocs
description: 了解全局搜索如何在门户中工作。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/30/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 9b2a2333c3e8422470521a7af135ea2c7d7040f2
ms.sourcegitcommit: 4349eefb1fd788f5e27d91319bc878ee9aba7a75
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2020
ms.locfileid: "3012614"
---
# <a name="search"></a>Search

在 Power Apps 门户中，可通过使用门户的全局搜索功能在多个实体中搜索记录。 您也可以使用实体列表搜索功能在实体列表记录中搜索。 

门户中的实体列表搜索功能在后端使用 FetchXML 搜索在实体列表中定义的列，然后显示结果。 

全局搜索使用外部搜索索引，其基于 Lucene.Net，用于在多个实体和字段中立即搜索。

## <a name="global-search"></a>全局搜索

门户的全局搜索允许跨多个实体搜索记录。 还可以让您跨多个列搜索，并配置实体的哪些列是可搜索的。

全局搜索的好处在于它能够：
- 可以在实体中任何字段内找到搜索词中任何单词的匹配项。 匹配项可以包含单词变体，如 stream、streaming 或 streamed。
- 返回结果来自所有可搜索实体，为根据匹配的字数或单词在文本中彼此的亲缘关系之类因素，按相关性排序的一个列表。
- 在搜索结果中突出显示匹配项。
- 提供可用于进一步筛选搜索结果的分面选项。

在全局搜索中，匹配程度越高，在结果中显示的位置越高。 在接近的彼此亲缘关系中找到的搜索词中的单词越多，匹配项的相关性越高。 找到搜索单词的文本量越小，相关性越高。 例如，如果在公司名和地址中找到了搜索词，则比在大型文章中找到的彼此距离遥远的相同单词的匹配情况更好。 由于结果通过单个列表返回，您可能会看到记录逐一混合显示，并突出显示匹配的工作。 

以下部分详细介绍全局搜索在 Power Apps 门户中的搜索方式，并介绍各个可用配置选项。

## <a name="entities-searchable-in-portal-global-search"></a>在门户全局搜索中可搜索的实体

以下实体可在门户网站内搜索，前提是已安装相应的解决方案包，并且已将搜索添加到门户。 编入索引的列将包含在“搜索”视图中找到的列，其可以自定义。  列表中的每个实体都有其默认的按此处列出的方式编入索引的属性集：
- 知识文章
    - 知识文章的注释和附件也是可搜索的。 更多信息：[在文件附件内容中搜索](search-file-attachment.md)
    - 仅当文章已发布且“仅限内部”字段设置为 false 时文章才可以搜索。
- 博客 
- 博客文章 
- 博客发布注释 
- 论坛 
- 论坛帖子 
- 论坛执行绪 
- 观点 
- 创意评论 
- 观点论坛 
- Web 文件 
    - Web 文件的附件内容也是可搜索的。 更多信息：[在文件附件内容中搜索](search-file-attachment.md)
- 网页 
- 事件 

> [!NOTE]
> 除了此处列出的实体外，不能在门户中为全局搜索启用其他实体。

## <a name="fields-searchable-in-global-search"></a>全局搜索中可搜索的字段

任何实体的 Search/IndexQueryName 站点设置定义的视图中的所有可用字段都在全局搜索中编入索引并且可搜索。 

Search/IndexQueryName 的默认值为“门户搜索”。

如果视图不可用于任何实体，它将不编入索引，并且结果不会显示在全局搜索中。

> [!NOTE]
> 如果更改 Search/IndexQueryName 站点设置的值，您需要使用[重新生成完整的搜索索引](#rebuild-full-search-index)部分中定义的步骤触发手动将生成重新编入索引。

## <a name="related-site-settings"></a>相关站点设置

以下站点设置与全局搜索相关：

| 姓名    | 默认值     | 说明       |
|-----------------------|--------------------|-------------|
| Search/Enabled | True  | 表示搜索是否启用的布尔值。 如果将其值设置为 false，门户中的全局搜索将关闭。<br>如果使用现成的 Web 模板并且关闭此设置，搜索框则不会显示在标题以及搜索页面。 此外，将不返回任何结果，即使点击搜索页的直接 URL。  |
| 搜索/筛选器  | Content:adx_webpage;Events:adx_event,adx_eventschedule;Blogs:adx_blog,adx_blogpost,adx_blogpostcomment;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea,adx_ideacomment;Issues:adx_issueforum,adx_issue,adx_issuecomment;Help Desk:incident | 搜索逻辑名称筛选器选项的集合。 在此处定义值会将下拉筛选器选项添加到全局搜索。 此值应采用名称/值对的形式，名称和值以冒号分隔，对以分号分隔。 例如："Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Blogs:adx_blog,adx_blogpost,adx_blogpostcomment"。  |
| Search/IndexQueryName   | 门户搜索  | 门户搜索查询用于定义支持的编入索引并搜索的实体字段的系统视图的名称。   |
| 搜索/查询  | +(@Query) _title:(@Query) _logicalname:adx_webpage\~0.9^0.2 -_logicalname:adx_webfile\~0.9 adx_partialurl:(@Query) _logicalname:adx_blogpost\~0.9^0.1 -_logicalname:adx_communityforumthread\~0.9   | 此设置将其他权重和筛选器添加到用户在显示在门户中的默认搜索框中输入的查询。 在默认值中，@Query 是用户输入的查询文本。<br>有关如何修改此值的信息，请参阅 [Lucene 查询语法](https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html)。<br>**重要提示**：此权重和筛选仅适用于默认的门户搜索页中的搜索框。 如果使用 liquid 搜索标记创建您自己的搜索页，那么此设置不适用。 |
| Search/Stemmer  | 英语    | 门户搜索的词干分析算法使用的语言。   |
| Search/FacetedView  | 真   | 这支持搜索结果中的分面。 如果设置为 True，分面将在搜索页面上与结果一起显示。  |
| Search/IndexNotesAttachments   | 真    | 指示知识库文章和 Web 文件中注释附件的内容是否应编入索引。 默认情况下，它设置为 False。 更多信息：[在文件附件内容中搜索](search-file-attachment.md)    |
| Search/RecordTypeFacetsEntities  | Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Downloads:annotation,adx_webfile    | 这将确定实体在搜索页如何在记录类型分面中分组。 此设置的格式为 <br>“DisplayNameinRecordTypeFacet1:logicalnameofentity1,logicalnameofentity2; DisplayNameinRecordTypeFacet2:logicalnameofentity3,logicalnameofentity4” <br>记录类型分面中的显示名称将显示在 UI 上。 此分面组将合并配置中定义的实体的结果。   |
| KnowledgeManagement/DisplayNotes | 真   | 指示是否将知识库文章的附件编入索引。 默认情况下，它设置为 False。 |
|||

## <a name="related-content-snippets"></a>相关内容片段

以下内容片段与全局搜索相关：

| 姓名   | 默认值  | 说明   |
|------------------|-----------------|--------------------|
| 标头/搜索/标签| Search| 此内容片段确定在门户标题的搜索框中显示的水印文本。<br>![搜索标签](../media/search-label.png "搜索标签")    |
| 标头/搜索/工具提示| Search  | 此内容片段确定当您悬停在门户标题中的搜索图标上时将显示的工具提示文本。<br>![搜索工具提示](../media/search-tooltip.png "搜索工具提示")  |
| Search/Default/FilterText| 所有   | 此内容片段确定在搜索框旁边的筛选器下拉列表中显示的默认文本。<br>![搜索筛选文本](../media/search-filter-text.png "搜索筛选文本")  |
| 搜索/分面/全部| 所有| 此内容片段确定为在搜索结果页的“记录类型”分面中的“所有记录分面”显示的默认文本。<br>![所有分面](../media/facet-all.png "所有分面") |
| Search/Facet/ClearConstraints   | 全部清除  | 此内容片段确定重置搜索结果页上应用的所有分面的按钮的标签。<br>![重置所有分面](../media/facet-clear-all.png "重置所有分面") |
| Search/Facet/Downloads   | 下载   | 此内容片段确定在“记录类型”分面的批注附件和 Web 文件记录的搜索结果中显示的标签。<br>![下载分面](../media/facet-download.png "下载分面")|
| 搜索/分面/更少    | 显示更少  | 此内容片段确定折叠分面结果的按钮的标签。<br>![显示更少分面](../media/facet-show-less.png "显示更少分面") |
| Search/Facet/ModifiedDate  | 修改日期  | 此内容片段确定为“修改日期”分面显示的标题的标签。<br>![修改日期](../media/facet-modified-date.png "修改日期分面")   |
| 搜索/分面/更多   | 显示更多  | 此内容片段确定展开分面结果的按钮的标签。<br>![显示更多分面](../media/facet-show-more.png "显示更多分面")  |
| 搜索/分面/产品  | 产品 | 此内容片段确定“产品”分面的标签。<br>![“产品”分面](../media/facet-product.png "“产品”分面")  |
| 搜索/分面/评分   | 评级   | 此内容片段确定“评分”分面的标签。<br>![“评分”分面](../media/facet-rating.png "“评分”分面")  |
| Search/Facet/RecordType   | 记录类型 | 此内容片段确定“记录类型”分面的标签。<br>![记录类型分面](../media/facet-record-type.png "记录类型分面")     |
| Search/Facet/SortOrder/AverageUserRating | 平均用户评分 | 此内容片段确定为搜索结果页上排序下拉列表中的“按平均用户评分排序”选项显示的标签。<br>![按平均用户评分排序](../media/sort-avg-user-rating.png "按平均用户评分排序")  |
| Search/Facet/SortOrder/Relevance| 相关性| 此内容片段确定为搜索结果页上排序下拉列表中的“按相关性排序”选项显示的标签。<br>![按相关性排序](../media/sort-relevance.png "按相关性排序")|
| Search/Facet/SortOrder/Views| 视图数量| 此内容片段确定为搜索结果页上排序下拉列表中的“按视图数量排序”选项显示的标签。<br>![按视图数量排序](../media/sort-view-count.png "按视图数量排序")|
|||

## <a name="entity-specific-handling"></a>实体特定处理

- **案例**：默认情况下，仅为**已解决**状态并且**发布到 Web** 字段设置为 **True** 的案例可搜索。 此行为可以通过更新案例实体的门户搜索视图并删除门户搜索视图中的可用筛选器来修改。 不过，在删除此选择时，务必确保“客户服务 – 案例”Web 模板相应地修改，因为此 Web 模板限制所有用户查看可用且不发布到 Web 的案例。 如果 Web 模板未修改，案例会在搜索结果中可见。 但是，如果选择它们，案例详细信息网页将显示，并包含“权限被拒绝”错误。

- **知识库**：仅当处于**已发布**状态并且**内部**字段设置为**否**时知识文章才可以搜索。 不能修改此行为。 知识文章也有在搜索结果中可用的特殊功能，如下所示：

    - **分面**：两个特殊分面只可用于知识文章，并在知识文章记录在搜索结果中提供时显示。

        - **评分分面**：此分面允许您根据知识文章的平均评分筛选搜索结果。

        - **产品分面**：此分面允许您根据与知识文章关联的产品筛选搜索结果。

    - **附件搜索**：此功能允许您在与知识文章关联的附件或注释中搜索。 这允许您在门户上公开的注释或附件的注释描述、标题、附件文件名和附件内容中搜索。 更多信息：[在文件附件内容中搜索](search-file-attachment.md)

## <a name="special-characters-and-syntax-supported-by-search"></a>搜索支持的特殊字符和语法

作为门户全局搜索的一部分，支持使用各种特殊字符和语法来更好地筛选搜索结果。 这些特殊字符和语法广泛分为以下组：

- **搜索词**：用户输入的用于搜索的每个查询被解析为搜索词和运算符。 下面搜索词类型： 

    - **单个搜索词**：单个搜索词是单个字词。 例如，查询{hello world}会被解析为两个单个搜索词“hello”和“world”。 每个单个搜索词单独搜索。 因此，在查询{hello world}中，所有包含搜索词“hello”或“world”的记录将显示在搜索结果中。

    - **短语**：短语是以双引号 (“”) 括起来的一组搜索词。 例如，查询{“hello world”}会被解析为短语“hello world”。 每个短语作为一个整体搜索。 因此，在查询{“hello world”}中，所有包含完整短语“hello world”的记录将显示在搜索结果中，而只有“hello”或“world”的任何记录将不显示。

    每个搜索查询可能包含任何类型的一个或多个搜索词，其组合起来使用布尔运算符创建复杂的查询。

- **搜索词修饰符**

    - **通配符搜索**：有两类通配符可以在搜索查询的单个搜索词中（不在短语查询中）使用：单字符通配符搜索和多字符通配符搜索。

        - **单字符通配符搜索**：若要执行单字符通配符搜索，使用问号 (?) 符号。 单字符通配符搜索查找使用替换的单个字符进行匹配。 例如，若要搜索“text”或“test”，您可以使用搜索查询“te?t”。

        - **多字符通配符搜索**：若要执行多字符通配符搜索，使用星号 (\*) 符号。 多字符通配符搜索查找零个或多个字符。 例如，要搜索 test、tests 或 tester，可以使用搜索查询“test *”。您也可以在查询中间使用多字符通配符搜索。例如，“te*t”。

        > [!NOTE]
        > - 不能使用 * 或 ? 符号作为搜索的第一个字符。
        > - 通配符搜索不能在短语查询中使用。 例如，如果您使用查询“hell* world”，将不会显示包含文本“hello world”的结果。

    - **邻近搜索**：邻近搜索使您能够搜索彼此位于特定距离的字词。 例如，如果需要在 10 个字词内显示的字词“Picture”和“blurry”的结果，可以使用邻近搜索。
    
        若要执行邻近搜索，请在查询末尾使用波浪 (~) 符号。 例如，如果需要在 10 个字词内显示的字词“Picture”和“blurry”的结果，查询将为“Picture blurry”~10。

    - **增强搜索词**：全局搜索根据找到的搜索词提供匹配文档的相关性级别。 若要增强搜索词，请在所搜索的搜索词末尾使用具有增强系数（数字）的插入 (^) 符号。 增强系数越高，搜索词会更相关。

        增强允许您通过增强搜索词来控制文档的相关性。 例如，如果搜索 Smart TV，而您希望搜索词“Smart”更相关，则使用 ^ 符号以及在搜索词旁边加上增强系数来进行增强。 您会键入：Smart^4 TV。 这会使显示的包含搜索词 Smart 的文档更相关。

        您还可以按照示例所示增强短语搜索词：Smart TV^4 New TV。 在此例中，“Smart TV”短语会对比“New TV”进行增强。

        默认情况下，增强系数为 1。 虽然增强系数必须是正值，但可能小于 1（例如，0.2）。

- **布尔运算符**：布尔运算符允许通过逻辑运算符合并搜索词。 全局搜索支持 OR、AND、NOT、"+" 和 "-" 作为布尔运算符。

    > [!NOTE]
    > 布尔运算符必须为大写字母。

    - **OR**：OR 运算符是默认的连接运算符。 这意味着如果两个搜索词之间没有布尔运算符，将使用 OR 运算符。 OR 运算符链接两个搜索词，并在记录中存在任意一个搜索词时查找匹配记录。 这与使用集的并集等效。 符号 || 可以代替字词 OR 使用。 例如，搜索查询“Smart TV”（不包括双引号）将搜索包含字词 Smart 或 TV 的所有记录。 该查询还可以写入为“Smart OR TV”、“Smart || TV”。

    - **AND：** AND 运算符与两个搜索词都存在于单个文档的文本的任意位置的记录匹配。 这与使用集的交集等效。 符号 && 可以代替字词 AND 使用。 例如，搜索查询“Smart AND TV”（不包括双引号）将搜索包含字词 Smart 和 TV 的所有记录。 该查询还可以写入为“Smart && TV”。

    - **NOT**：NOT 运算符不包括在 NOT 后包含搜索词的记录。 这与使用集的差异等效。 符号 ! 可以代替字词 NOT 使用。 例如，搜索查询“Smart NOT TV”（不包括双引号）将搜索包含字词 Smart 但不包含字词 TV 的所有记录。 该查询还可以写入为“Smart ! TV”。

    - **加号 (+) 符号**：加号 (+) 符号也称为所需运算符，需要“+”符号后面的搜索词存在于记录的某处。 例如，搜索查询“Smart + TV”将搜索字词 TV 必须存在，字词 Smart 可能也存在的所有记录。 

    - **减号 (–) 符号**：减号 (–) 符号也称为禁止符号，不包括在“-”符号之后包含搜索词的文档。 例如，搜索查询“Smart - TV”将搜索字词 Smart 存在，字词 TV 禁止存在的所有记录。

- **分组**：门户全局搜索支持使用括号分组子句来建立子查询。 如果要控制查询的布尔逻辑，这可能非常有用。 例如，如果要搜索搜索词“HD”或“Smart”其中一个存在，但字词 TV 始终存在的所有记录，那么查询可以写为“(HD or Smart) AND TV”（不包括双引号）。

## <a name="liquid-search-tag"></a>Liquid 搜索标记

您可以使用 searchindex 标记从 liquid 模板调用门户全局搜索。 详细信息：[searchindex](../liquid/portals-entity-tags.md#searchindex)

> [!IMPORTANT]
> 在使用 searchindex 标记时，分面不会作为结果的一部分返回，也不能用作筛选器。

## <a name="update-search-index"></a>更新搜索索引

Power Apps 门户中的搜索索引更新与缓存无效一样自动发生。 请记住这些重要事项：

- 启用所有搜索的实体必须启用“更改通知”元数据标志，否则不会有更改被通知到门户，搜索索引将不会更新。

- 任何更改者可能最多需要 30 分钟时间反映在门户搜索中。 但是，95% 的更改会在 15 分钟内更新。 如果有附件，根据附件的大小，可能需要更长时间。

- 建议在较短时间范围内执行批量数据迁移或执行记录的批量更新后手动重新生成完整索引。 有关详细信息，请参阅[重新生成完整的搜索索引](#rebuild-full-search-index)。

## <a name="rebuild-full-search-index"></a>重新生成完整的搜索索引

以下情况下均需要重新生成完整的搜索索引：

- 您进行元数据更改以搜索属性，如更改某个查询特定的站点设置或更改实体的搜索视图等。
- 执行批量数据迁移或更新。
- 与您的门户关联的网站记录在 Common Data Service 环境中更改。

您还可以从门户重新生成完整的搜索索引。
1.  以管理员身份登录到门户。
2.  导航到如下 URL：`<portal_path>/_services/about`
3.  选择**重新生成搜索索引**。

> [!IMPORTANT]
> 重新生成完整索引是一项成本高昂的操作，不应在使用高峰时间进行，因为可能让您的门户停机。

## <a name="remove-an-entity-from-global-search"></a>从全局搜索中删除实体

有时，您可能需要将某些实体从门户全局搜索中完全删除，以确保您的客户能够快速获得正确的结果。

在下面的示例中，我们将从门户全局搜索中删除案例实体。

### <a name="step-1-block-case-entity-from-getting-indexed"></a>步骤 1：阻止案例实体被编入索引。

若要阻止案例实体被编入索引，必须将将记录集定义为按门户索引的案例实体的视图重命名（由 Search/IndexQueryName 站点设置定义）。 默认情况下，该视图的名称是“门户搜索”。

1.  转到 https://make.powerapps.com，然后选择“解决方案”。 

    ![解决方案](../media/solutions-page.png)

1. 搜索**默认解决方案**，然后选择“编辑”以打开。

    ![编辑解决方案](../media/edit-solution.png)

1. 搜索并编辑**服务案例**实体以查看其组件。 

1. 选择**视图**选项卡，然后选择**门户搜索**，以便在视图编辑器中将其打开。

1. 在视图编辑器中，根据需要重命名视图。 确保新的名称中不包含*门户搜索*一词。 

1. 保存并发布更改，然后关闭视图编辑器。

1. 按照[重新生成完整的搜索索引](#rebuild-full-search-index)部分所述重新生成完整的索引。

> [!NOTE]
> 在本例中，我们通过直接编辑视图在非托管层进行更改。 您也可以通过托管解决方案进行更改。

### <a name="step-2-remove-case-entity-from-the-ui"></a>步骤 2：从 UI 中删除案例实体

执行步骤 1 中所述的操作后，案例实体将被停止编入索引。 若要从 UI 界面区域删除案例实体，必须修改与门户全局搜索关联的站点设置。 必须修改以下站点设置：

search/filters：这将从搜索页以及站点标题的搜索框的筛选器中删除案例实体。 默认情况下，值为：`Content:adx_webpage,adx_webfile;Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Help Desk:incident;Knowledge:knowledgearticle`

必须从此站点设置的值中删除 `Help Desk:incident;`，以便从 UI 上搜索框旁边的筛选器中删除事件实体。

修改后的值将为：

`Content:adx_webpage,adx_webfile;Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Knowledge:knowledgearticle`

更改此站点设置后，将从搜索页以及标题的筛选器中删除案例实体。

![在页面上搜索](../media/search-on-page.png "在页面上搜索")

![在标题中搜索](../media/search-in-header.png "在标题中搜索")
