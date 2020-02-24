---
title: 使用分面搜索改进门户搜索 | MicrosoftDocs
description: 有关如何启用或禁用分面搜索的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 49985feb494e43350d1e2c8ecb014f405439892a
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980469"
---
# <a name="use-faceted-search-to-improve-portal-search"></a>使用分面搜索改进门户搜索

可使用基于门户内容特征的筛选器搜索门户内容。 客户可通过分面门户搜索实施的筛选器以比传统搜索更快的速度找到所需内容。

## <a name="enable-or-disable-faceted-search"></a>启用或禁用分面搜索

门户中已启用了自带的分面搜索。 若要控制或启用此功能，请按照下列步骤操作：

1. 打开[门户管理应用](configure-portal.md)并转到**门户** &gt; **网站** &gt; **站点设置**。
2. 选择**搜索/分面视图**网站设置。 
3. 将**值**更改为 **True** 以启用分面搜索，或更改为 **False** 以禁用分面搜索。

若要禁用一段分面视图：

1. 打开[门户管理应用](configure-portal.md)并转到**门户** &gt; **Web 面板**。
2. 选择要禁用的视图（即“知识管理 – 评级最高的文章”）
3. 选择页面顶部的**停用**。

## <a name="group-entities-as-part-of-a-record-type-for-faceted-view"></a>为实体分组以作为分面视图的记录类型的一部分

可通过网站设置 **Search/RecordTypeFacetsEntities** 将类似实体组合在一起，以便为用户提供用于筛选搜索结果的逻辑方法。 例如，不为论坛、论坛文章和论坛执行绪提供单独的选项，而是将这些实体在“论坛”记录类型下分组。

转至**门户** &gt; **网站** &gt; **网站设置**，然后打开 **Search/RecordTypeFacetsEntities** 网站设置。 

请注意以单词**论坛:** 开始的不同实体。 这是因为第一个值是充当分组依据的名称。 将根据门户中所用语言翻译此单词。

## <a name="use-faceted-search-to-improve-knowledge-search-results"></a>使用分面搜索改进知识搜索结果

分面搜索为门户在最左侧提供了搜索筛选器，供您在论坛、博客和知识文章之类项之间选择。 为具体搜索类型提供了更多筛选器。 例如，可以按“记录类型”、“修改日期”、“评级”和“产品”筛选文章，以帮助客户找到所需内容。 最右侧也有下拉框，用于根据选择的“相关性”或“查看数量”（特定于知识文章）为结果排序。 下面是带有部分可用筛选器的示例的屏幕截图。

![使用筛选器改进搜索结果](../media/faceted-search-filter.png "使用筛选器改进搜索结果")
