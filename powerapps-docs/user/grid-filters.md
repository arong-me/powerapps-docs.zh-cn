---
title: 筛选网格中的数据 |MicrosoftDocs
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 02/03/2019
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2cfe55db19b5d8a7aeed86169a188455686cf81b
ms.sourcegitcommit: 68a31e3fa4d1635ccf4cd8bd9da5fba1bfecefa4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051951"
---
# <a name="use-grid-filters"></a>使用网格筛选器 

已改进统一界面中的网格，增加了你可以在屏幕上看到的数据量。 现在，可以从多个不同的筛选选项中选择一个列;列中的数据类型决定了哪些筛选器选项可用。 例如，"**联系人**" 网格中的 "**全名**" 列与 "**活动**" 网格中的 "**活动类型**" 列具有不同的筛选选项。


   > [!div class="mx-imgBorder"]
   > ![网格筛选](media/filter-options.png "网格筛选")
   

## <a name="grid-and-filter-navigation"></a>网格和筛选器导航

筛选网格中的数据时，主网格页会在您离开并返回到页面时记住筛选器、排序顺序和页面状态。 当对快速查找、列筛选、页码等筛选数据时，此操作是相同的。 

   > [!div class="mx-imgBorder"]
   > ![向后导航到页面将在同一状态中打开它](media/grid-remember-state-on-back-navigate.gif "向后导航到页面将在同一状态中打开它")

页面跳转栏使用第一个已排序的字段。 如果没有对排序顺序进行更改，跳转条将使用主字段。

   > [!div class="mx-imgBorder"]
   > ![选择跳转栏中的筛选器](media/jumpbar-filter-on-sorted-column.gif "选择跳转栏中的筛选器")
  
选择层次结构图标时，导航到层次结构视图。

   > [!div class="mx-imgBorder"]
   > ![层次结构图标](media/grid-row-hierarchy-icon.png "“层次结构”图标")

您还可以在新的选项卡或窗口中打开主字段和查找字段。

   > [!div class="mx-imgBorder"]
   > ![在新窗口中打开](media/newtab.png "[在新窗口中打开")
   
   
### <a name="known-issue"></a>已知问题

如果更改数字、货币、时间或日期的默认显示格式，然后筛选网格中的数据，则筛选器将不会显示所选的显示格式。 筛选器仍将以系统默认格式显示，在某些情况下，筛选可能根本不起作用。 

若要解决此问题，请将数字、货币、时间和日期的显示格式设置回默认设置。 

1. 在右上角，选择 "齿轮" 图标 ![齿轮 "图标](media/selection-rule-gear-button.png)，然后选择"**个性化设置**"。

2. 在 "**格式**" 选项卡上，将数字、货币、时间和日期值更改回默认设置。

    > [!div class="mx-imgBorder"] 
    > ![格式设置](media/default-format.png "格式设置")
    
    
  我们正在努力解决此问题，请重新查看可用性。 



## <a name="preview-new-grid-filters-and-search-option"></a>预览：新建网格筛选器和搜索选项

本部分适用于早期访问功能。 你可以提前选择在你的环境中启用这些功能。 这样，你就可以测试这些功能，然后在你的环境中采用它们。 有关如何启用这些功能的信息，请参阅[选择加入 2020 release wave 1 更新](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates)。


   > [!NOTE]
   > 请勿更改时间、数字、货币、时间或日期的默认显示格式，因为这会导致问题。 有关详细信息，请参阅[已知问题](https://docs.microsoft.com/powerapps/user/grid-filters#known-issue)。

### <a name="lookup-field-column"></a>查找字段列

对查找列进行筛选时，可以从要筛选的记录列表中进行选择，而不是在数据中手动键入。 例如，在**主联系人**查找列中，可以从要筛选的记录列表中选择联系人姓名。

   > [!div class="mx-imgBorder"]
   > ![查找筛选](media/lookup-filter.png "查找筛选")

### <a name="date-filter"></a>日期筛选器

稳健**日期**筛选器包含多个不同的值供您选择，**例如，按以按**准确日期搜索，或**在会计期间**内搜索以按**年份或季度**搜索。

   > [!div class="mx-imgBorder"]
   > ![日期筛选](media/date-filter.png "日期筛选")

### <a name="filter-the-list-of-activities"></a>筛选活动列表

你可以筛选活动列表以仅查看你感兴趣的活动。 例如，您可以使用活动类型筛选器进一步限制您在视图中看到的活动。 活动类型筛选器允许您根据类型（如电子邮件、任务、电话呼叫等）筛选活动。


   > [!div class="mx-imgBorder"]
   > ![活动筛选器](media/activity_filter.png "活动筛选器")


#### <a name="known-issue"></a>已知问题

如果更改数字、货币、时间或日期的默认显示格式，然后筛选网格中的数据，则筛选器将不会显示所选的显示格式。 筛选器仍将以系统默认格式显示，在某些情况下，筛选可能根本不起作用。 

若要解决此问题，请将数字、货币、时间和日期的显示格式设置回默认设置。 

1. 在右上角，选择 "齿轮" 图标 ![齿轮 "图标](media/selection-rule-gear-button.png)，然后选择"**个性化设置**"。

2. 在 "**格式**" 选项卡上，将数字、货币、时间和日期值更改回默认设置。

    > [!div class="mx-imgBorder"] 
    > ![格式设置](media/default-format.png "格式设置")
    
    
我们正在努力解决此问题，请重新查看可用性。 
  
### <a name="use-search-on-a-grid"></a>在网格上使用搜索

使用网格页上的 "**搜索此视图**" 选项时，系统会在当前所在的视图中搜索数据。 在下面的示例中，在 "**联系人**" 网格中执行搜索。

1. 中转到 "**联系人**" 网格，然后从视图列表中选择 **"我的活动联系人**"。

    > [!div class="mx-imgBorder"]
    > ![我的活动联系人视图](media/myactive-contacts-view.png "我的活动联系人视图")

2. 选择 "**搜索此视图**" 以在所处的视图中搜索数据。

    > [!div class="mx-imgBorder"]
    > ![搜索视图](media/search-view.png "搜索此视图")

系统将在 "**我的活动联系人**" 视图中搜索数据，并使用在当前视图中使用的同一组列显示搜索结果。

   > [!div class="mx-imgBorder"]
   > ![搜索视图](media/search-view2.png "搜索此视图命令中的搜索结果")


#### <a name="use-the-quick-find-search-experience"></a>使用 "快速查找" 搜索体验

若要切换回旧的 "快速查找" 搜索体验，使用实体的 "快速查找" 视图定义执行搜索，你将需要管理员权限。

1. 在右上角选择齿轮图标 ![齿轮图标](media/selection-rule-gear-button.png)，然后选择 "**高级设置**"。

2. 请 > **管理** > **系统设置**中转到 "**设置**"。

3. 在 "**常规**" 选项卡上的 "**设置快速查找**" 下，选择 **"是"** 以**使用实体的 "快速查找" 视图来搜索网格和子网格**。



