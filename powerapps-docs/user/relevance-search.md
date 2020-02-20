---
title: 相关性搜索 |MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 1/28/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3a78e555c8818144b41935715ab9f983c7d9714b
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "76918795"
---
# <a name="using-relevance-search-to-search-for-records"></a>使用关联性搜索来搜索记录

## <a name="what-is-relevance-search"></a>什么是相关性搜索？

相关性搜索可在单个列表中提供跨多个实体的快速且全面的结果（按相关性排序）。 它使用 Common Data Service 的外部专用搜索服务（由 [!INCLUDE[pn_Windows_Azure](../includes/pn-windows-azure.md)] 提供支持）以提高搜索性能。
  
相关性搜索提供了以下增强功能和优势：  
<!--note from editor: Edits to these list items are suggested, so they can be parallel throughout this section.-->  
- 使用外部索引和 [!INCLUDE[pn_azure_shortest](../includes/pn-azure-shortest.md)] 搜索技术来提高性能。  
  
- 在实体的任何字段中，查找搜索词中任何字词的匹配项，而在快速查找中，必须在一个字段中找到搜索词中的所有字词。 

- 查找包括屈折词（stream、streaming 或 streamed）的匹配项    。  
  
- 在单个列表中返回按相关性排序的所有可搜索实体的结果，因此匹配度越高，结果在列表中的显示位置就越靠前。 搜索词中彼此接近的字词越多，匹配项的相关性就越高。 在其中找到搜索词的文本量越少，相关性就越高。 例如，如果要在公司名称和地址中查找搜索词，则与在长篇文章中查找相同的字词相比，前者的匹配度可能更好。
  
- 在结果列表中突出显示匹配项。 如果某搜索词与记录中的某个词匹配，则该词在搜索结果中显示为粗体和斜体。 

    > [!NOTE]
    > - 在搜索过程中，会忽略某些在某种语言中常用的字词（例如 the 或 a），因为它们不能帮助唯一标识记录   。 由于在搜索过程中忽略了这些词，结果中也不会突出显示这些字词。
    > - 突出显示的词通常作为某字段的完整值的一部分返回，因为仅突出显示匹配的词。  

- 包含存储在 Common Data Service 中的文档的文本搜索结果，包括备注中的文本、电子邮件附件或约会。 支持搜索以下文件格式：PDF、Microsoft Office 文档、HTML、XML、ZIP、EML、纯文本和 JSON。  
  
- 使你能够搜索与你分享的记录以及你自己的记录。  
  
  > [!NOTE]
  >  不支持分层的安全模型。 即使由于你已通过分层安全性访问过 Common Data Service 中的一行，而看到了该行，在相关性搜索中你也看不到此结果。  
  
- 让你也能够搜索选项集和查找。 例如，假设你想查找名称中包含“药品”的零售商店帐户  。 搜索“药品零售”时，你会找到这条结果，因为存在一个“行业”字段的匹配项，这是可搜索的选项集  。

  > [!NOTE]
  > - 相关性搜索基于文本，可以只对“单行文本”、“多行文本”、“选项集”或“查找”类型的字段进行搜索。 它不支持在“数字”或“日期数据”类型字段中进行搜索。
  
- 支持在搜索词中使用语句来获取所需的结果。 例如，键入“car silver 2-door”可在搜索结果中包括搜索词中任何字词的匹配项  。 键入“car+silver+2-door”可仅查找包含全部三个词的匹配项  。 键入“car&#124;silver&#124;2-door”可获取包含“car”、“silver”、“2-door”或全部三个词的结果     。 如需详细了解可在搜索查询中使用的语法，请参阅 [Azure 认知搜索中的简单查询语法](https://docs.microsoft.com/rest/api/searchservice/simple-query-syntax-in-azure-search)<!--note from editor: The "More information:" pattern is good when there aren't any additional modifiers, which you have here. -->
  
  > [!NOTE]
  > 相关性搜索配置为要求与查询中的任何（并非所有）条件匹配，这可能会产生与预期不同的结果。 在查询包含布尔运算符时更应如此。<!--note from editor: Via style guide, it's always capital "Boolean," and it's "might" instead of "may.-->

## <a name="enable-relevance-search"></a>启用相关性搜索

默认情况下禁用相关性搜索。 管理员需要为组织启用该功能，以便组织中的所有用户都可使用它。 启用相关性搜索之后，你可能需要等待一个小时或更长时间（具体取决于组织大小），然后才能开始查看应用的相关性搜索结果。 对索引数据进行的较小更改可能最长需要 15 分钟才会显示在系统中。

## <a name="switch-between-relevance-search-and-categorized-search"></a>在相关性搜索与分类搜索之间切换

如果组织已启用这两个搜索选项（相关性搜索和分类搜索），则可在这两者之间切换。

1. 要在搜索类型之间切换，请在导航栏上选择“搜索”  。

2. 在左侧，选择下拉菜单以在“相关性搜索”或“分类搜索”之间切换   。

   > [!div class="mx-imgBorder"]
   > ![在相关性搜索和分类搜索之间切换](media/switch-global-search.png "在相关性搜索与分类搜索之间切换") 
    
## <a name="set-a-default-search-experience"></a>设置默认搜索体验

如果组织已启用这两个搜索选项，则可在个人设置中选择默认搜索体验。

1. 在页面右上角选择“设置”，然后选择“个性化设置”   。  
  
   > [!div class="mx-imgBorder"]
   > ![个性化设置](media/personalization-settings.png "个性化设置")  

2. 在“常规”选项卡上的“选择默认搜索体验”部分，针对“默认搜索体验”选择默认体验    。 

   > [!div class="mx-imgBorder"]
   > ![选择默认搜索体验](media/default-search-experience.png "选择默认搜索体验")  

## <a name="start-a-search"></a>启动搜索 
 
1.  在顶部导航栏中，选择“搜索”  。  

    > [!div class="mx-imgBorder"]
    > ![“全局搜索”按钮](media/global-search-button.png "全局搜索") 
  
2.  在搜索框中输入搜索词，然后选择“搜索”  。

    > [!div class="mx-imgBorder"]
    > ![相关性搜索框](media/relevance-search-box.png "相关性搜索框")   

## <a name="filter-records-with-facets"></a>使用 facet 筛选记录

使用 Common Data Service，现在可以通过使用 facet 和筛选器来优化搜索结果。 通过 facet 和筛选器，可以深入了解和探索当前搜索的结果，而无需重复优化搜索词。

可在最左侧窗格中找到 facet。 执行搜索后，以下全局 facet 可立即用于四个常见字段：  
  
-   记录类型  
  
-   所有者  
  
-   创建时间  
  
-   修改时间  
  
### <a name="record-type-facets"></a>记录类型 facet

要将搜索结果范围缩小到特定实体，请在“记录类型”部分下选择该实体  。  
 
  > [!div class="mx-imgBorder"]
  > ![用于缩小搜索结果范围的记录类型 facet](media/relevance-search-record-type-facet.png "用于缩小搜索结果范围的记录类型 facet")  
  
对特定记录类型进行筛选时，可以在搜索结果中包括与所选记录相关的活动和备注。 为此，请选中“相关备注和活动”复选框  。 活动和备注将显示在顶层结果中。
 
  > [!div class="mx-imgBorder"]
  > ![在搜索结果中包括与记录类型相关的备注和活动](media/relevance-search-record-type-facet-related-notes-activities.png "在搜索结果中包括与记录类型相关的备注和活动")  
  
在电子邮件附件或约会实体中找到的搜索结果显示在其父记录（电子邮件或附件）下的搜索结果中。  
  
按记录类型进行优化时，facet 范围将切换到所选实体，并且显示最多四个特定于该实体的 facet。 例如，如果选择“帐户”实体，则除全局 facet 外，还会显示“主要联系人” facet  。  
  
在“设置个人选项”对话框中，还可以从系统管理员或客户提供的 facet 中选择其他 facet  。 用户设置将替代默认设置。 [!INCLUDE[proc_more_information](../includes/proc-more-information.md)] [配置 facet 和筛选器以进行搜索](#BKMK_ConfigureFacets)  
  
### <a name="text-based-facets"></a>基于文本的 facet

所有查找、选项集和记录类型都是基于文本的 facet。 例如，基于文本的 facet 所有者包含字段值及其相应计数的列表。  
 
  > [!div class="mx-imgBorder"]
  > ![相关性搜索中基于文本的 facet](media/relevance-search-text-based-facets.png "相关性搜索中基于文本的 facet")  
  
这些 facet 中的筛选器按计数降序排序。 默认情况下，显示前四个 facet 值。 如果有四个以上的 facet 值，将看到“显示更多”链接，可选择该链接以展开列表并查看最多 15 个 facet 值  。 选择每个值以筛选搜索结果，以仅显示字段包含所选值的记录。 例如，如果选择“Jim Glynn”，搜索结果将显示所有者为 Jim Glynn 的所有记录  。 选择查找或选项集 facet 值时，会对搜索结果进行筛选，以仅包含具有指定值的记录。  
  
### <a name="date-and-time-facets"></a>日期和时间 facet

与其他 facet 一样，可以使用日期和时间 facet 来筛选和查看特定时间内的搜索结果。 要选择值的范围，请拖动滑块或选择其中一个垂直列。  
 
  > [!div class="mx-imgBorder"]
  > ![相关性搜索的日期和时间 facet](media/relevance-search-date-time-facets.png "相关性搜索的日期和时间 facet")  

<a name="BKMK_ConfigureFacets"></a>

## <a name="configure-facets-and-filters"></a>配置 facet 和筛选器
  
> [!NOTE]
>  系统定制员可以为所有实体设置默认体验，但是你可以配置自己的 facet 和筛选器。  
  
1. 在右上角选择“设置”，然后选择“个性化设置”   。  
  
   > [!div class="mx-imgBorder"]
   > ![个性化设置](media/personalization-settings.png "个性化设置")
  
2. 在“常规”选项卡上的“选择默认搜索体验”部分中，针对“Facet 和筛选器”字段选择“配置”     。  

   > [!div class="mx-imgBorder"]
   > ![配置 facet 和筛选器](media/configure-facets-filters.png "配置 facet 和筛选器")  
  
3. 在“配置 facet 和筛选器”对话框中，为实体指定你想看到的 facet  。 系统管理员或定制员可以为所有实体设置默认体验，但你可以在此处设置自己的体验。  
  
   - 在“选择实体”下拉列表中，选择要为其配置 facet 的实体  。 此下拉列表仅包含为相关性搜索启用的实体。  
  
   - 对于所选实体，请选择最多四个 facet 字段。 默认情况下，在列表中为所选实体选择“快速查找”视图中的前四个“facet-able”字段  。 任何时候都可以只选择四个字段作为 facet。  
  
   一次可以更新多个实体。 如果选择“确定”，将保存已配置的所有实体的更改  。 要恢复之前配置的实体的默认行为，请选择“默认”  。  
  
   > [!NOTE]
   > - 如果系统定制员删除某字段或使其不再可搜索，并且你已保存该字段的 facet，则它将不再作为 facet 显示。  
   >   -   你将只能看到默认解决方案中存在且系统定制员已配置为可搜索的字段。  
