---
title: PowerApps 门户中的全局搜索 |MicrosoftDocs
description: 了解如何在门户中使用全局搜索。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: da142a452e903b890b1b395262771228e245140c
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551614"
---
# <a name="search"></a>Search

在 PowerApps 门户中，可以使用门户的 "全局搜索" 功能跨多个实体搜索记录。 你还可以使用实体列表搜索功能在实体列表的记录中搜索。 

门户中的实体列表搜索功能使用后端中的 FetchXML 搜索在实体列表中定义的列，然后显示结果。 

全局搜索使用基于 Lucene.Net 的外部搜索索引，并且用于一次在多个实体和字段中进行搜索。

## <a name="global-search"></a>全局搜索

通过对门户进行全局搜索，可以在多个实体之间搜索记录。 它还允许跨多个列进行搜索，并配置实体中可搜索的列。

全局搜索的优点包括：
- 查找实体中任何字段的搜索项中的任何词的匹配项。 匹配可以包括流、流式处理或流式处理等变形词。
- 返回按相关性排序的单个列表中所有可搜索实体的结果，基于与匹配的单词数量或其在文本中的邻近性等因素排序。
- 突出显示搜索结果中的匹配项。
- 提供可用于进一步筛选搜索结果的方面选项。

在全局搜索中，匹配越好，结果中显示的位置就越高。 如果搜索词中的更多单词彼此接近，则匹配项的相关性会更高。 找到搜索词的文本量越小，相关性越高。 例如，如果您在公司名称和地址中查找搜索词，则它可能比在大文章中找到的相同词的匹配项可能更好。 由于结果是在单个列表中返回的，因此，您可以看到一条单独显示的记录，其中突出显示了 "匹配的工作"。 

以下各节详细介绍了如何在 PowerApps 门户中使用全局搜索，并介绍了各种可用的配置选项。

## <a name="entities-searchable-in-portal-global-search"></a>门户全局搜索中可搜索的实体

如果已安装了相应的解决方案包并已将搜索添加到门户，则可以在门户网站中搜索以下实体。 已编制索引的列将包含在搜索视图中找到的列，可以对其进行自定义。  列表中的每个实体都有其默认的属性集，如下所示：
- 知识文章
    - 知识库文章的说明和附件也是可搜索的。 详细信息：[在文件附件内容中搜索](search-file-attachment.md)
    - 只有发布项目时，项目才可搜索，而仅限内部字段设置为 false。
- 博客 
- 博客文章 
- 博客文章注释 
- 讨论 
- 论坛帖子 
- 论坛线索 
- 核心 
- 创意注释 
- 创意论坛 
- Web 文件 
    - Web 文件的附件内容也是可搜索的。 详细信息：[在文件附件内容中搜索](search-file-attachment.md)
- 网页 
- 事件 

> [!NOTE]
> 除了此处列出的实体外，不能在门户中为全局搜索启用其他实体。

## <a name="fields-searchable-in-global-search"></a>全局搜索中可搜索的字段

所有实体的 Search/IndexQueryName 网站设置定义的视图中的所有可用字段在全局搜索中编制索引，并且可搜索。 

Search/IndexQueryName 的默认值为 "门户搜索"。

如果视图不能用于任何实体，则不会为其编制索引，并且结果不会显示在全局搜索中。

> [!NOTE]
> 如果更改 Search/IndexQueryName 站点设置的值，则需要使用 "[重建完全搜索索引](#rebuild-full-search-index)" 部分中定义的步骤来触发生成的手动重新索引。

## <a name="related-site-settings"></a>相关站点设置

以下站点设置与全局搜索相关：

| 名称    | 默认值     | 描述       |
|-----------------------|--------------------|-------------|
| 搜索/启用 | True  | 指示是否启用搜索的布尔值。 如果将其值设置为 "false"，则会关闭门户中的 "全局搜索"。<br>如果你使用的是现成的 web 模板并关闭此设置，则搜索框将不会显示在标头和 "搜索" 页上。 而且，即使点击搜索页的直接 URL，也不会返回任何结果。  |
| 搜索/筛选器  | 内容： adx_webpage;事件： adx_event、adx_eventschedule;博客： adx_blog、adx_blogpost、adx_blogpostcomment;论坛： adx_communityforum、adx_communityforumthread、adx_communityforumpost; 创意： adx_ideaforum、adx_idea、adx_ideacomment; 问题： adx_issueforum、adx_issue、adx_issuecomment;技术支持：事件 | 搜索逻辑名称筛选器选项的集合。 此处定义值会将下拉筛选器选项添加到全局搜索。 此值应采用名称/值对的形式，名称和值之间用冒号分隔，对用分号分隔。 例如： "论坛： adx_communityforum、adx_communityforumthread、adx_communityforumpost;博客： adx_blog、adx_blogpost、adx_blogpostcomment "。  |
| 搜索/IndexQueryName   | 门户搜索  | 门户搜索查询使用的系统视图的名称，以定义已启用索引和搜索的实体的字段。   |
| 搜索/查询  | \+ （@Query） _title：（@Query） _logicalname： adx_webpage\~0.9 ^ 0.2-_logicalname： adx_webfile\~0.9 adx_partialurl：（@Query） _logicalname： adx_blogpost\~0.9 ^ 0.1-_logicalname： adx_communityforumthread\~0。9   | 此设置向用户在门户中显示的默认搜索框中输入的查询添加额外的权重和筛选器。 在默认值中，@Query 是用户输入的查询文本。<br>有关如何修改此值的信息，请遵循[Lucene 查询语法](https://lucene.apache.org/core/old_versioned_docs/versions/2_9_1/queryparsersyntax.html)。<br>**重要说明**：此权重和筛选仅适用于门户的默认搜索页中的 "搜索" 框。 如果使用液体搜索标记来创建自己的搜索页面，则此设置不适用。 |
| 搜索/词干分析器  | 英语    | 门户搜索的词干算法使用的语言。   |
| 搜索/FacetedView  | True   | 这将启用搜索结果中的方面。 当设置为 True 时，将在 "搜索" 页上显示 facet 和结果。  |
| 搜索/IndexNotesAttachments   | True    | 指示是否应对知识库文章和 web 文件中的 notes 附件内容进行索引。 默认情况下，它设置为 False。 详细信息：[在文件附件内容中搜索](search-file-attachment.md)    |
| 搜索/RecordTypeFacetsEntities  | 博客： adx_blog、adx_blogpost;论坛： adx_communityforum、adx_communityforumthread、adx_communityforumpost; 创意： adx_ideaforum、adx_idea; 下载：批注、adx_webfile    | 这将确定实体在 "搜索" 页上的 "记录类型" 方面的分组方式。 此设置的格式为 <br>"DisplayNameinRecordTypeFacet1:logicalnameofentity1,logicalnameofentity2;DisplayNameinRecordTypeFacet2:logicalnameofentity3,logicalnameofentity4" <br>记录类型方面的显示名称将显示在 UI 上。 此方面组将组合配置中定义的实体的结果。   |
| KnowledgeManagement/DisplayNotes | True   | 指示是否为知识库文章的附件编制索引。 默认情况下，它设置为 False。 |
|||

## <a name="related-content-snippets"></a>相关内容段

以下内容段与全局搜索相关：

| 名称   | 默认值  | 描述   |
|------------------|-----------------|--------------------|
| 标题/搜索/标签| Search| 此内容片段确定了门户标题中的 "搜索" 框中显示的水印文本。<br>![搜索标签](../media/search-label.png "搜索标签")    |
| 标头/搜索/工具提示| Search  | 当你将鼠标悬停在门户标题中的搜索图标上时，此内容段将确定显示的工具提示文本。<br>![搜索工具提示](../media/search-tooltip.png "搜索工具提示")  |
| Search/Default/FilterText| 一切   | 此内容片段确定在 "搜索" 框旁边的 "筛选器" 下拉列表中显示的默认文本。<br>![搜索筛选器文本](../media/search-filter-text.png "搜索筛选器文本")  |
| 搜索/Facet/全部| 一切| 此内容片段确定在 "搜索结果" 页的 "记录类型" 方面显示的 "所有记录方面" 的默认文本。<br>![所有方面](../media/facet-all.png "所有方面") |
| 搜索/Facet/ClearConstraints   | 全部清除  | 此内容片段确定用于重置在 "搜索结果" 页中应用的所有方面的按钮的标签。<br>![重置所有方面](../media/facet-clear-all.png "重置所有方面") |
| 搜索/分面/下载   | 下载   | 此内容片段确定在 "记录类型" 方面的批注附件和 web 文件记录的搜索结果中显示的标签。<br>![下载 facet](../media/facet-download.png "下载 facet")|
| 搜索/方面/更少    | 显示更少  | 此内容片段确定折叠分面结果的按钮的标签。<br>![显示较少方面](../media/facet-show-less.png "显示较少方面") |
| 搜索/Facet/ModifiedDate  | 修改日期  | 此内容片段确定为修改日期方面显示的标头的标签。<br>![修改日期](../media/facet-modified-date.png "修改日期方面")   |
| 搜索/Facet/更多   | 显示更多  | 此内容片段确定用于扩展分面结果的按钮的标签。<br>![显示更多方面](../media/facet-show-more.png "显示更多方面")  |
| 搜索/方面/产品  | 产品 | 此内容片段确定产品方面的标签。<br>![产品方面](../media/facet-product.png "产品方面")  |
| 搜索/Facet/分级   | 评分   | 此内容片段确定评级方面的标签。<br>![分级方面](../media/facet-rating.png "分级方面")  |
| 搜索/Facet/RecordType   | 记录类型 | 此内容片段确定了记录类型方面的标签。<br>![记录类型方面](../media/facet-record-type.png "记录类型方面")     |
| 搜索/Facet/SortOrder/AverageUserRating | 平均用户评分 | 此内容片段确定在 "搜索结果" 页上的 "排序" 下拉列表中为 "按平均用户分级排序" 选项显示的标签。<br>![按平均用户评分排序](../media/sort-avg-user-rating.png "按平均用户评分排序")  |
| 搜索/Facet/SortOrder/相关性| 重要性| 此内容片段确定 "搜索结果" 页上 "排序" 下拉列表中 "排序依据" 选项显示的标签。<br>![按相关性排序](../media/sort-relevance.png "按相关性排序")|
| 搜索/Facet/SortOrder/Views| 查看计数| 此内容片段确定在 "搜索结果" 页上的 "排序" 下拉列表中为 "排序依据视图计数" 选项显示的标签。<br>![按视图计数排序](../media/sort-view-count.png "按视图计数排序")|
|||

## <a name="entity-specific-handling"></a>特定于实体的处理

- **案例**：默认情况下，在 "**发布到 Web** " 字段设置为 " **True**" 的情况下，可搜索的唯一案例处于**已解决**状态。 可以通过更新案例实体的门户搜索视图并删除门户搜索视图中提供的筛选器来修改此行为。 但是，在删除此检查时，务必确保正确修改客户服务-案例 web 模板，因为此 web 模板会限制所有用户查看处于活动状态且未发布到 web 的案例。 如果未修改 web 模板，则事例将显示在搜索结果中。 但是，当你选择它们时，将显示 "案例详细信息" 网页，并显示 "拒绝访问" 错误。

- **知识库**：知识库文章仅在 "**内部**" 字段设置为 "**否**" 的 "**已发布**" 状态时才可搜索。 此行为不能修改。 知识库文章在搜索结果中还提供了一些特殊功能，如下所示：

    - **Facet**：只有知识库文章提供两个特殊方面，并在搜索结果中提供知识库文章记录时显示。

        - **分级方面**：通过此方面，你可以根据知识库文章的平均评级来筛选搜索结果。

        - **产品方面**：通过此方面，你可以根据与知识库文章关联的产品筛选搜索结果。

    - **附件搜索**：此功能可让你在与知识库文章关联的附件或备注内进行搜索。 这样，你便可以在注释说明、标题、附件文件名和门户中公开的注释或附件的附件内容中进行搜索。 详细信息：[在文件附件内容中搜索](search-file-attachment.md)

## <a name="special-characters-and-syntax-supported-by-search"></a>搜索支持的特殊字符和语法

作为门户全局搜索的一部分，支持使用各种特殊字符和语法来更好地筛选搜索结果。 这些特殊字符和语法广泛分为以下几组：

- **术语**：要搜索的用户输入的每个查询都将分析为术语和运算符。 术语的类型如下： 

    - **单一术语**：单一字词为单一字词。 例如，"hello" 和 "world" 这两个词将分析为 "hello" 和 "world"。 将单独搜索每个单个术语。 因此，在查询中，"hello" 或 "world" 这一术语将显示在搜索结果中。

    - **短语**：短语是括在双引号（""）中的一组字词。 例如，"hello world" 查询将分析为短语 "hello world"。 将完全搜索每个短语。 因此，在查询 {"hello world"} 中，包含完整短语 "hello world" 的所有记录都将显示在搜索结果中，并且不会显示仅有 "hello" 或 "world" 的任何记录。

    每个搜索查询可包含任何类型的一个或多个术语，这些术语使用布尔运算符进行组合以创建复杂的查询。

- **字词修饰符**

    - **通配符搜索**：可在单个搜索查询中使用两种类型的通配符（不在短语查询中）：单个字符通配符搜索和多个字符通配符搜索。

        - **单个字符通配符搜索**：若要执行单个字符通配符搜索，请使用问号（？）符号。 单个字符通配符搜索查找与替换单个字符匹配的字词。 例如，若要搜索 "text" 或 "test"，可以使用搜索查询作为 "te？ t"。

        - **多字符通配符搜索**：若要执行多字符通配符搜索，请使用星号（\*）符号。 多个字符通配符搜索查找零个或多个字符。 例如，若要搜索 "测试"、"测试" 或 "测试人员"，可以使用搜索查询 "测试 *"。您还可以在查询的中间使用多个字符通配符搜索。例如，"te*t"。

        > [!NOTE]
        > - 不能使用 * 或？ 符号作为搜索的第一个字符。
        > - 通配符搜索不能用于短语查询。 例如，如果使用 query 作为 "hell * world"，则它不会显示带有 "hello world" 文本的结果。

    - **邻近搜索**：邻近搜索允许搜索特定距离内的单词。 例如，如果想要在每个单词的10个单词内显示 "图片" 和 "模糊" 字样的结果，可以使用邻近搜索。
    
        若要执行邻近搜索，请在查询末尾使用波形符（~）。 例如，如果想要在每个单词的10个单词内显示单词 "Picture" 和 "模糊" 的结果，则查询将是 "图片模糊" ~ 10。

    - **提升术语**：全局搜索根据找到的条款提供匹配文档的关联级别。 若要提高术语，请在要搜索的字词的末尾使用带有提升因子（数字）的插入符号（^）符号。 提升因子越高，术语的相关性就越高。

        通过提高，可以通过提升文档的术语来控制文档的相关性。 例如，如果您正在搜索智能电视，而您希望术语 "智能" 更相关，则使用 "^" 符号以及此项旁边的提升系数来提升此术语。 需要键入： Smart ^ 4 电视。 这会使术语为 "智能" 的文档显得更相关。

        你还可以按以下示例中所示增加短语条款：智能电视 ^ 4 新电视。 在这种情况下，与 "新电视" 相比，"智能电视" 短语会得到提升。

        默认情况下，提升系数为1。 尽管提升因子必须为正，但它可以小于1（例如，0.2）。

- **布尔运算符**：布尔运算符允许术语通过逻辑运算符组合。 全局搜索支持将 OR、AND、NOT、"+" 和 "-" 作为布尔运算符。

    > [!NOTE]
    > 必须用大写形式编写布尔运算符。

    - **或**： or 运算符是默认的结合运算符。 这意味着，如果两个字词之间没有布尔运算符，则使用 OR 运算符。 OR 运算符链接两个字词并查找匹配记录（如果记录中存在这两个条件之一）。 这等效于使用集的联合。 符号 | |可以用来代替词或。 例如，搜索查询 "智能电视" （不包括引号）将搜索其中包含 "智能" 或 "电视" 的所有记录。 此查询还可以编写为 "智能或电视"，"智能 | |TV "。

    - **和：** AND 运算符匹配两个字词均存在于单个文档文本中的任意位置的记录。 这等效于使用集的交集。 符号 & & 可用于代替单词和。 例如，搜索查询 "智能和电视" （不包括引号）将搜索其中带有 "Smart" 和 "TV" 字样的所有记录。 此查询还可以编写为 "智能 & & TV"。

    - **Not**： not 运算符会排除不包含此术语的记录。 这等效于使用集的不同之处。 符号！ 可以用来代替单词。 例如，搜索查询 "智能非电视" （不包括引号）将搜索带有 "智能" 但不包含 "电视" 的所有记录。 此查询还可以编写为 "智能！ TV "。

    - **加号（+）符号**：加号（+）符号（也称为必选运算符）要求在记录中的某处存在 "+" 符号后面的字词。 例如，搜索查询 "智能 + 电视" 将搜索包含单词 "电视" 的所有记录，也可能出现 "智能"。 

    - **减号（–）符号**：减号（-）符号，也称为禁止运算符，排除包含 "-" 符号后面的字词的文档。 例如，搜索查询 "智能电视" 将搜索出现 "Smart" 字样的所有记录，并且不能有 "TV"。

- **分组**：门户全局搜索支持使用括号将子句分组以构成子查询。 如果要控制查询的布尔逻辑，这可能非常有用。 例如，如果要搜索其中某个术语为 "HD" 或 "Smart" 的所有记录，但 "电视" 始终存在，则可以将该查询编写为 "（HD 或 Smart）和 TV" （不包括引号）。

## <a name="liquid-search-tag"></a>液体搜索标记

可以通过使用 searchindex 标记从液体模板调用门户全局搜索。 详细信息： [searchindex](../liquid/portals-entity-tags.md#searchindex)

> [!IMPORTANT]
> 使用 searchindex 标记时，不会将 facet 作为结果的一部分返回，也不能将它们作为筛选器应用。

## <a name="update-search-index"></a>更新搜索索引

PowerApps 门户中的搜索索引更新会自动出现，如缓存失效。 不过，请记住以下重要事项：

- 所有启用搜索的实体都必须启用更改通知元数据标志，否则不会向门户通知更改，搜索索引将不会更新。

- 任何更改最长可能需要30分钟才能在门户搜索中反映出来。 但是，95% 的更改会在15分钟内更新。 如果涉及附件，可能需要更长时间，具体取决于附件的大小。

- 建议在一小段时间内对记录执行批量数据迁移或大容量更新后，手动重新生成完整索引。 有关详细信息，请参阅[Rebuild full search index](#rebuild-full-search-index)。

## <a name="rebuild-full-search-index"></a>重新生成全文搜索索引

每次都需要重新生成完整搜索索引：

- 对搜索属性进行元数据更改，如更改特定于查询的特定站点设置或更改实体的搜索视图等。
- 执行大容量数据迁移或更新。
- 与门户关联的网站记录在 Common Data Service 环境中进行了更改。

还可以从门户重新生成完整的搜索索引。
1.  以管理员身份登录到门户。
2.  导航到 URL，如下所示： `<portal_path>/_services/about`
3.  选择 "**重新生成搜索索引**"。

> [!IMPORTANT]
> 完全索引重新生成是一种非常昂贵的操作，不应在使用高峰时间完成，因为这样可以使门户停止运行。

## <a name="remove-an-entity-from-global-search"></a>从全局搜索中删除实体

有时，你可能需要从门户全局搜索中完全删除某些实体，以确保你的客户能够快速获得正确的结果。

在下面的示例中，我们将从门户全局搜索中删除案例实体。

### <a name="step-1-block-case-entity-from-getting-indexed"></a>步骤1：从获取索引的块案例实体

若要阻止事例实体获得索引，必须重命名事例实体的视图，该实体定义门户要编制索引的记录集（由 Search/IndexQueryName 站点设置定义）。 默认情况下，该视图的名称为 "门户搜索"。

1.  打开[门户管理应用](configure-portal.md)。

2.  从页面顶部的工具栏中选择 "**设置**" 图标，然后选择 "**高级设置**"。

2.  请参阅 "**设置**" > **自**定义 > **自定义系统**。

    ![自定义系统](../media/customize-system.png "自定义系统")

3.  在 "自定义" 对话框中，在左侧导航窗格中转到 "**组件** > **实体**" > **Case** 。 

4.  展开 "**案例**" 实体并选择 "**视图**"。

5.  从列表中选择**门户搜索**视图，并在视图编辑器中将其打开。

    ![Case 视图](../media/case-view.png "Case 视图")

6.  在 "视图编辑器" 中，选择 "**查看属性**"。

    ![视图编辑器](../media/view-editor.png "视图编辑器")

7.  根据需要重命名视图。 确保新名称中不包含 "门户搜索" 术语。

    ![查看属性](../media/view-properties.png "查看属性")

8.  保存更改并关闭视图编辑器。

9.  选择“发布所有自定义项”。

10. 重新生成完整的索引，如 "[重新生成搜索索引](#rebuild-full-search-index)" 一节中所述。

> [!NOTE]
> 在此示例中，我们通过直接编辑视图在非托管层中进行更改。 还可以通过托管解决方案实现此目的。

### <a name="step-2-remove-case-entity-from-the-ui"></a>步骤2：从 UI 中删除案例实体

执行步骤1中所述的操作后，会停止事例实体的索引。 若要从 UI 区域中删除 case 实体，你必须修改与门户全局搜索相关联的站点设置。 必须修改以下站点设置：

搜索/筛选器：此操作将从搜索页面上的筛选器中删除 case 实体，以及站点标题中的搜索框。 默认情况下，该值为： `Content:adx_webpage,adx_webfile;Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Help Desk:incident;Knowledge:knowledgearticle`

您必须从该站点设置的值中删除 `Help Desk:incident;`，以便从用户界面中的 "搜索" 框旁边的筛选器中删除事件实体。

修改后的值将为：

`Content:adx_webpage,adx_webfile;Blogs:adx_blog,adx_blogpost;Forums:adx_communityforum,adx_communityforumthread,adx_communityforumpost;Ideas:adx_ideaforum,adx_idea;Knowledge:knowledgearticle`

更改此站点设置后，将从搜索页面上的筛选器和标头中删除案例实体。

![在页面上搜索](../media/search-on-page.png "在页面上搜索")

![在标头中搜索](../media/search-in-header.png "在标头中搜索")
