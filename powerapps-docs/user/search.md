---
title: Common Data Service 中的搜索选项 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 1/27/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 440241571f716fa1931b5c11935c70de5c85e7ee
ms.sourcegitcommit: 5bfd0448f1d5ca3d938e3bd928d1dd3d4042afff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/28/2020
ms.locfileid: "76828583"
---
# <a name="compare-search-options-in-common-data-service"></a>对比 Common Data Service 中的搜索选项

在 Common Data Service 中搜索记录有三种方式：

-   相关性搜索   
  
-   快速查找（单实体或多实体）  

-   高级查找

> [!NOTE]
> 多实体快速查找也称为“分类搜索”。 
  
下表简要对比了这三个选项。

|功能|[相关性搜索](relevance-search.md)|[“快速查找”](quick-find.md)|[高级查找](advanced-find.md)|  
|-------------------|---------------------------|----------------|-------------------|  
|默认情况下是否启用？|否。 管理员必须手动启用它。|是|是|  
|单实体搜索范围|不可在实体网格中使用。 你可以按“结果”页上的实体来筛选搜索结果。|可在实体网格中使用。|可在实体网格中使用。|  
|多实体搜索范围|对可搜索的实体数量没有上限。 **注意：** 尽管对可搜索的实体数量没有上限，但“记录类型”筛选器仅显示 10 个实体的数据。|按实体分组，最多可搜索 10 个实体。|多实体搜索不可用。|  
|搜索行为|在实体的任何字段中，查找搜索词中任何字词的匹配项。|在实体的某一字段中，查找搜索词中所有字词的匹配项；但在字段中可按任意顺序匹配这些字词。|查询生成器，可在其中定义所选记录类型的搜索条件。 还可用于准备要导出到 Office Excel 的数据，以便对数据进行分析、汇总或聚合，或创建数据透视表，从各种角度查看数据。|  
|可搜索的字段|文本字段，如单行文本、多行文本、查找和选项集。 不支持在“数字”或“日期数据类型”字段中进行搜索。|所有可搜索的字段。|所有可搜索的字段。|  
|搜索结果|在单个列表中按其相关性顺序返回搜索结果。|对于单实体，在实体网格中返回搜索结果。 对于多实体，返回按类别（如帐户、联系人或潜在顾客）分组的搜索结果。|按配置的排序顺序以指定的列方式返回所选记录类型的搜索结果。|
|通配符 (*)|字词补全支持的后导通配符。|支持的前导通配符。 默认添加的后导通配符。|不支持。|  
