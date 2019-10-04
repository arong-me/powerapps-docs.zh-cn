---
title: 搜索和查找 Common Data Service 中的选项 |MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/02/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: c7192b98d3f97a4aba57f58c52b02245cb71b155
ms.sourcegitcommit: 7c46e7ce889e2f1c5352ed2e705b0bb8968f2a89
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950878"
---
# <a name="compare-search-and-find-options-in-common-data-service"></a>比较中的搜索和查找选项 Common Data Service

在 Common Data Service 中查找数据有四种方法：

-   相关性搜索  
  
-   全文快速查找（单实体或多实体）  
  
-   快速查找（单实体或多实体）  

-   高级查找

> [!NOTE]
> 多实体快速查找也称为分类搜索。 
  
下表提供了四种可用选项的简短比较。

|性能|[相关性搜索](search-records.md#relevance-search)|[全文快速查找](search-records.md#start-a-search)|[快速查找](search-records.md#start-a-search)|[高级查找](create-edit-or-save-advanced-find-search.md)|  
|-------------------|----------------------|---------------------------|----------------|-------------------|  
|默认情况下是否启用？|不。 管理员必须手动启用它。|不。 管理员必须手动启用它。|是|是|  
|单实体搜索范围|在实体网格中不可用。 您可以通过 "结果" 页面上的实体来筛选搜索结果。|在实体网格中可用。|在实体网格中可用。|在实体网格中可用。|  
|多实体搜索范围|可搜索的实体数量没有最大限制。 **注意：** 虽然您可以搜索的实体数量没有最大限制，但 "记录类型" 筛选器仅显示10个实体的数据。|搜索多达10个实体，按实体分组。|搜索多达10个实体，按实体分组。|多实体搜索不可用。|  
|搜索行为|查找实体中任何字段的搜索项中的任何词的匹配项。|查找与实体中的一个字段的搜索词中的所有单词匹配的匹配项;但是，可以在字段中按任意顺序匹配单词。|在包含 "Like" 子句的 SQL 查询中查找匹配项。 必须在搜索词中使用通配符搜索字符串。 所有匹配项都必须与搜索词完全匹配。|"查询生成器"，您可以在其中定义所选记录类型的搜索条件。 还可用于准备要导出到 Office Excel 的数据，以便对数据进行分析、汇总或聚合，或创建数据透视表以从不同的角度查看数据。|  
|可搜索字段|文本字段，如单行文本、多行文本、查找和选项集。 不支持在数字或日期数据类型的字段中进行搜索。|所有可搜索字段。|所有可搜索字段。|所有可搜索字段。|  
|搜索结果|在单个列表中按其关联顺序返回搜索结果。|对于单实体，返回实体网格中的搜索结果。 对于多实体，返回按类别分组的搜索结果，如 "帐户"、"联系人" 或 "潜在顾客"。|对于单实体，返回实体网格中的搜索结果。 对于多实体，返回按类别分组的搜索结果，如 "帐户"、"联系人" 或 "潜在顾客"。|按照您配置的排序顺序返回所选记录类型的搜索结果。|
|通配符（*）|单词完成支持尾随通配符。|支持前导通配符。 默认添加尾随通配符。|支持前导通配符。 默认添加尾随通配符。|不支持。|  
