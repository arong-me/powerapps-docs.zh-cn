---
title: 使用分面搜索来改善门户搜索 |MicrosoftDocs
description: 有关启用或禁用分面搜索的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 6b605acf1d11ecbc98760810f390f63c9a27a0a6
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552327"
---
# <a name="use-faceted-search-to-improve-portal-search"></a>使用分面搜索来改善门户搜索

可以使用基于内容特征的筛选器搜索门户内容。 多面门户搜索实现的筛选器使客户能够更快地找到所需内容，比传统搜索更快。

## <a name="enable-or-disable-faceted-search"></a>启用或禁用分面搜索

在门户中启用了 "开箱即用" 面搜索。 若要控制或启用它，请执行以下步骤：

1. 打开[门户管理应用](configure-portal.md)，并 &gt;**网站**&gt;**网站设置**"中转到**门户**。
2. 选择**Search/FacetedView**站点设置。 
3. 将**值**更改为**True** **可启用或禁用**分面搜索。

禁用分面视图的单个部分：

1. 打开[门户管理应用](configure-portal.md)，并 &gt; **Web 模板**中转到**门户**。
2. 选择要禁用的视图（即知识管理-排名靠前的文章）
3. 选择页面顶部的 "**停用**"。

## <a name="group-entities-as-part-of-a-record-type-for-faceted-view"></a>将实体分组为分面视图的记录类型的一部分

站点设置**Search/RecordTypeFacetsEntities**允许将相似的实体组合在一起，因此用户可以通过逻辑方式来筛选搜索结果。 例如，对于论坛、论坛文章和论坛线索，这些实体不是单独的选项，而是按论坛记录类型分组。

&gt;**网站**&gt;**网站设置**"中转到**门户**，然后打开"**搜索/RecordTypeFacetsEntities** "网站设置。 

请注意，不同的实体前面是 "**论坛：** "。 这是因为第一个值是将其分组为的名称。 将基于门户中使用的语言来转换此词。

## <a name="use-faceted-search-to-improve-knowledge-search-results"></a>使用分面搜索来改进知识搜索结果

通过多面搜索，门户可在最左侧搜索筛选器，使你能够在论坛、博客和知识库文章等项目之间进行选择。 为特定搜索类型添加了更多筛选器。 例如，可以按记录类型、修改日期、分级和产品筛选知识库文章，以帮助客户找到所需内容。 最右边还有一个下拉框，它根据客户选择的相关性或视图计数（特定于知识库文章）对结果进行排序。 下面是一个屏幕捕获，其中包含一些可用筛选器的示例。

![使用筛选器来改善搜索结果](../media/faceted-search-filter.png "使用筛选器来改善搜索结果")
