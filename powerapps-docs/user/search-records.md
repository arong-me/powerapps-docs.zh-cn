---
title: 在模型驱动的应用中搜索记录 |MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 35cd4e4f0393f28d6cca5a2bd67497018a12ae26
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2019
ms.locfileid: "61559348"
---
# <a name="search-for-records-in-an-app"></a>在应用中搜索记录

可以通过在模型驱动应用中使用相关性搜索或分类搜索来搜索多个实体中的记录。 相关性搜索跨多个实体、按相关性排序的单个列表提供快速、全面的结果。 分类搜索返回按实体类型 (例如帐户、联系人或潜在顾客) 分组的搜索结果。

通常, 分类搜索是默认的搜索选项。 但是, 如果你的组织启用了相关性搜索, 则它将成为默认搜索体验。   
  
### <a name="normal-quick-find-categorized-search"></a>普通快速查找 (分类搜索) 
  
- **开头为**:结果包括以特定单词开头的记录。 例如, 如果要在搜索框中搜索 "Alpine 滑雪房子", 请在 "搜索" 框中键入**alp** ;如果键入**ski**, 则记录将不会显示。  
  
- **通配符**:例如, * ski 或 * ski\*  
  
### <a name="relevance-search"></a>相关性搜索
  
- **搜索范围**:结果包含的记录包含搜索词中所有单词的字段。  各个单词可以在字符串中的任意位置显示, 并按任何顺序出现。  例如, 如果搜索 "Alpine 滑雪房子", 则可以找到 "我今天离开了 Alpine Meadows 中的滑雪" 的结果, 因为所有搜索词都出现在字符串中的某个位置。  

## <a name="switch-between-relevance-and-categorized-search"></a>在相关性和已分类搜索之间切换

如果你的组织启用了两个搜索选项 (相关性和已分类的搜索), 则可以在两者之间切换。

1. 若要在搜索类型之间切换, 请在导航栏上选择 "**搜索**" 按钮。

2. 在左侧, 选择下拉菜单以在**相关性搜索**或**分类搜索**之间切换。

## <a name="start-a-search"></a>开始搜索  
  
1.  从顶部导航栏中选择 "**搜索**"。  
  
2.  在搜索框中键入搜索词, 然后选择 "**搜索**"。  
  
## <a name="filter-search-results"></a>筛选搜索结果  
  
-   若要按一种记录类型筛选结果, 请在 "搜索" 屏幕上, 从 "**筛选器方式:** " 下拉框中选择一种记录类型。  
  
-   若要搜索所有记录类型, 请在 "**筛选条件:** " 下拉框中选择 "**无**"。  
  
 
