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
ms.openlocfilehash: 25daee9c8dabdbfd39cc1995c6d1e3b28e307da3
ms.sourcegitcommit: 4d858e628c89d245317d6192801d136f3591ea52
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76832616"
---
# <a name="using-relevance-search-to-search-for-records"></a>使用关联性搜索来搜索记录

## <a name="what-is-relevance-search"></a>什么是相关性搜索？

相关性搜索跨多个实体、按相关性排序的单个列表提供快速、全面的结果。 它使用 Common Data Service 的外部专用搜索服务（由 [!INCLUDE[pn_Windows_Azure](../includes/pn-windows-azure.md)]提供支持）以提高搜索性能。 
  
相关性搜索提供了以下增强功能和优点：  
  
- 通过外部索引和 [!INCLUDE[pn_azure_shortest](../includes/pn-azure-shortest.md)] 搜索技术提高性能。  
  
- 与 "快速查找" 相比，查找在实体中任何字段的搜索项中的任何词的匹配项。 

- 匹配可以包括**流**、**流式处理**或**流式**处理等变形词。  
  
- 返回按相关性排序的单个列表中所有可搜索实体的结果，因此匹配越好，结果中显示的位置就越高。 如果搜索词中的更多单词彼此接近，则匹配项的相关性会更高。 找到搜索词的文本量越小，相关性越高。 例如，如果您在公司名称和地址中查找搜索词，则它可能比在大文章中找到的相同词的匹配项可能更好。   
  
- 突出显示结果列表中的匹配项。 如果搜索词与记录中的字词匹配，术语将在搜索结果中显示为粗体和斜体文本。 

    > [!NOTE]
    > - 搜索时，将忽略某些在语言中非常常用的词语 **（如或** **），** 因为它们不能帮助唯一地标识记录。 由于在搜索时它们会被忽略，因此结果中也不会突出显示这些词。
    > - 突出显示的术语通常作为字段的完整值的一部分返回，因为只突出显示匹配的字词。  

- 你将在存储在 Common Data Service 中的文档中找到文本的搜索结果，其中包括备注、电子邮件附件或约会中的文本。 搜索支持以下文件格式： PDF、Microsoft Office 文档、HTML、XML、ZIP、.EML、纯文本和 JSON。  
  
- 您可以搜索与您共享的记录以及您拥有的记录。  
  
  > [!NOTE]
  >  不支持分层的安全模型。  即使您在 Common Data Service 中看到一行，因为您可以通过分层安全性来访问它，否则不会在相关性搜索中看到结果。  
  
- 还可以搜索选项集和查找。 例如，假设你想要查找名称中包含**药品**的零售商店帐户。 当你搜索**制药零售**时，你会发现结果，因为它是一个可搜索的选项集。

  > [!NOTE]
  > - 相关性搜索基于文本，并且只能在类型为 "单行文本"、"多行文本"、"选项集" 或 "查找" 的字段中搜索。 它不支持在数字或日期数据类型的字段中进行搜索。 
  
- 在搜索词中使用语法可获取所需的结果。 例如，键入 "**汽车银 2-门**"，以在搜索结果中包含搜索词中任何字的匹配项。 键入**car + 白银 +2-门**，仅查找包含全部三个词的匹配项。 键入 **"&#124;汽车&#124;银 2-门**" 以获取包含**汽车**、**银色**或**2 门**或全部三个单词的结果。 有关可在搜索查询中使用的语法的详细信息： [Azure 搜索中的简单查询语法](https://docs.microsoft.com/rest/api/searchservice/simple-query-syntax-in-azure-search)
  
  > [!NOTE]
  > 相关性搜索配置为要求与查询中的任何条件（而非所有）匹配，这可能会导致结果与预期结果不同。 当查询中包含布尔运算符时，尤其如此。

## <a name="enable-relevance-search"></a>启用相关性搜索

默认情况下禁用相关性搜索。 您的管理员需要为组织启用它，从而使组织中的所有用户都能使用它。 启用了相关性搜索后，你可能需要等待一小时或更长时间，具体取决于你的组织的规模，在开始查看应用的相关性搜索结果之前。 对于索引数据的较小更改，最长可能需要15分钟才能显示在你的系统中。

## <a name="switch-between-relevance-and-categorized-search"></a>在相关性和已分类搜索之间切换

如果你的组织启用了两个搜索选项（相关性和已分类的搜索），则可以在两者之间切换。

1. 若要在搜索类型之间切换，请在导航栏上选择 "**搜索**" 按钮。

2. 在左侧，选择下拉菜单以在**相关性搜索**或**分类搜索**之间切换。

   > [!div class="mx-imgBorder"]
   > ![在相关性和已分类搜索之间切换](media/switch-global-search.png "在相关性和已分类搜索之间切换") 
    
## <a name="set-a-default-search-experience"></a>设置默认搜索体验

如果你的组织已打开这两个搜索选项，则可以在你的个人设置中选择默认的搜索体验。

1. 在页面的右上角，选择 "**设置**"，然后选择 "**个性化设置**"。  
  
   > [!div class="mx-imgBorder"]
   > ![个性化设置](media/personalization-settings.png "个性化设置")  

2. 在 "**常规**" 选项卡上的 "**选择默认的搜索体验**" 部分中，对于**默认的搜索体验**，选择你的默认体验。 

   > [!div class="mx-imgBorder"]
   > ![选择默认搜索体验](media/default-search-experience.png "选择默认搜索体验")  

## <a name="start-a-search"></a>开始搜索 
 
1.  从顶部导航栏中选择 "**搜索**" 按钮。  

    > [!div class="mx-imgBorder"]
    > ![全局搜索按钮](media/global-search-button.png "全局搜索按钮") 
  
2.  在搜索框中键入搜索词，然后选择 "**搜索**" 按钮。   

    > [!div class="mx-imgBorder"]
    > ![相关性搜索框](media/relevance-search-box.png "相关性搜索框")   

## <a name="filter-records-with-facets"></a>用 facet 筛选记录  
使用 Common Data Service，现在可以通过使用 facet 和筛选器来改进搜索结果。 Facet 和筛选器可让你钻取并浏览当前搜索的结果，而无需重复优化搜索词。 

可在左窗格中使用方面。 执行搜索后，可以立即在四个公共字段中使用以下全局 facet：  
  
-   记录类型  
  
-   Owner  
  
-   创建于  
  
-   修改时间  
  
### <a name="record-type-facets"></a>记录类型方面  
若要将搜索结果缩小到特定实体，请在 "**记录类型**" 部分下选择实体。  
 
  > [!div class="mx-imgBorder"]
  > ![用于缩小搜索结果范围的记录类型方面](media/relevance-search-record-type-facet.png "用于缩小搜索结果范围的记录类型方面")  
  
当你按特定的记录类型进行筛选时，你可以在搜索结果中包括与所选记录相关的活动和说明。 为此，请选中 "**相关说明 & 活动**" 复选框。 活动和说明将显示在顶级结果中。
 
  > [!div class="mx-imgBorder"]
  > ![在搜索结果中包括与一种记录类型相关的注释和活动](media/relevance-search-record-type-facet-related-notes-activities.png "在搜索结果中包括与一种记录类型相关的注释和活动")  
  
电子邮件附件或约会实体中的搜索结果显示在其父记录下的搜索结果中，即电子邮件或约会。  
  
按记录类型进行优化时，facet 范围将切换到所选实体，并且显示最多四个特定于该实体的方面。 例如，如果选择 "帐户" 实体，则除了全局方面外，还会显示主要的 "**联系人**" 方面。  
  
在 "**设置个人选项**" 对话框中，你还可以从你的系统管理员或客户提供给你的用户的其他方面中进行选择。 用户设置将覆盖默认设置。 [!INCLUDE[proc_more_information](../includes/proc-more-information.md)][配置搜索的方面和筛选器](#BKMK_ConfigureFacets)  
  
### <a name="text-based-facets"></a>基于文本的方面  
所有查找、选项集和记录类型都是基于文本的方面。 例如，基于文本的方面所有者包含字段值的列表及其相应的计数。  
 
  > [!div class="mx-imgBorder"]
  > ![相关性搜索中基于文本的方面](media/relevance-search-text-based-facets.png "相关性搜索中基于文本的方面")  
  
这些方面的筛选器按计数以降序排序。 默认情况下，将显示前四个方面的值。 如果有四个以上的方面值，你将看到 "**显示更多**" 链接，你可以选择该链接来展开列表并查看最多15个顶级 facet 值。 选择每个值以筛选搜索结果，以仅显示字段包含所选值的记录。 例如，如果选择 " **Jim Glynn**"，搜索结果将显示所有者为 Jim Glynn 的所有记录。 选择 "查找" 或 "选项集" 方面值时，会将搜索结果筛选为仅包含指定值的记录。  
  
### <a name="date-and-time-facets"></a>日期和时间方面  
与其他方面一样，可以使用日期和时间方面来筛选和查看特定时间的搜索结果。 若要选择某一范围的值，请拖动滑块或选择其中一个垂直列。  
 
  > [!div class="mx-imgBorder"]
  > ![相关性搜索的日期和时间方面](media/relevance-search-date-time-facets.png "相关性搜索的日期和时间方面")  

<a name="BKMK_ConfigureFacets"></a>

## <a name="configure-facets-and-filters"></a>配置 facet 和筛选器    
  
> [!NOTE]
>  系统定制员可以设置所有实体的默认体验，但您可以配置自己的方面和筛选器。  
  
1. 在右上方，选择 "**设置**"，然后选择 "**个性化设置**"。  
  
   > [!div class="mx-imgBorder"]
   > ![个性化设置](media/personalization-settings.png "个性化设置")    
  
2. 在 "**常规**" 选项卡上，在 "**选择默认的搜索体验**" 部分的 " **facet 和筛选器**" 字段中，选择 "**配置**"。  

   > [!div class="mx-imgBorder"]
   > ![配置 Facet 和筛选器](media/configure-facets-filters.png "配置 Facet 和筛选器")  
  
3. 在 "**配置 facet 和筛选器**" 对话框中，指定要为实体查看的方面。 你的系统管理员或定制员可以为所有实体设置默认体验，但你可以在此处设置自己的体验。  
  
   - 在 "**选择实体**" 下拉列表中，选择要为其配置方面的实体。 此下拉列表仅包含为相关性搜索启用的实体。  
  
   - 对于所选实体，请选择最多四个方面字段。 默认情况下，将在列表中选择所选实体的**快速查找**视图中的前四个可查找字段。 在任何时候，只能选择四个字段作为 facet。  
  
   你可以一次更新多个实体。 选择 **"确定**" 后，将保存已配置的所有实体的更改。 要恢复为先前配置的实体的默认行为，请选择 "**默认**"。  
  
   > [!NOTE]
   > - 如果系统定制器删除某字段或使其不再可搜索，并且您已保存该字段的分面，则它将不再显示为分面。  
   >   -   你将只能看到默认解决方案中存在且配置为你的系统定制器可搜索的字段。  
