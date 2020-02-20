---
title: 快速查找 | Microsoft Docs
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
ms.openlocfilehash: 42691193a90d56f773de5723c4c27e883b3216ad
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "76918607"
---
# <a name="using-quick-find-to-search-for-records"></a>使用快速查找搜索记录

## <a name="single-entity-quick-find"></a>单实体快速查找

单实体快速查找用于查找只有一种类型的记录。 在视图中可以使用此搜索选项。 

   > [!div class="mx-imgBorder"]
   > ![单实体快速查找](media/single-quick-find-search-box.png "单实体快速查找搜索框") 

## <a name="multiple-entity-quick-find-categorized-search"></a>多实体快速查找（分类搜索）

多实体快速查找也称为“分类搜索”。 

1.  要启动分类搜索，请在顶部导航栏中选择“搜索”  。  

     > [!div class="mx-imgBorder"]
     > ![“全局搜索”按钮](media/global-search-button.png "全局搜索")
  
2.  在搜索框中键入搜索词，然后选择“搜索”  。 分类搜索返回按实体类型（如帐户或联系人）分组的结果。

     > [!div class="mx-imgBorder"]
     > ![分类搜索的结果](media/categorized-search-results.png "分类搜索的结果页面") 

使用分类搜索，可以搜索以特定单词开头或使用通配符的记录。
  
- **开头为**：结果包括以特定单词开头的记录。 例如，如果要搜索“Alpine Ski House”，请在搜索框中键入“alp”；如果键入“ski”，则不会显示记录   。  
  
- **通配符**：例如 *ski 或 *ski\*。 

  > [!NOTE]
  >  在快速查找（单个或多个实体）搜索查询的开头使用通配符可能会降低性能。
  
## <a name="filter-categorized-search-results"></a>筛选分类搜索的结果 
  
-   要按记录类型筛选结果，请从“筛选依据”列表中选择记录类型  。 

    > [!div class="mx-imgBorder"]
    > ![筛选分类搜索的结果](media/filter-categorized-search-results.png "筛选分类搜索的结果")  

  
-   要搜索所有记录类型，请从“筛选依据”列表中选择“无”   。  
