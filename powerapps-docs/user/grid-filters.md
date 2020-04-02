---
title: 在网格上筛选数据 | MicrosoftDocs
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 03/31/2020
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 54ddcf717b26859e71ed1339caa533fa9c6bcbb8
ms.sourcegitcommit: f5d15c973b2a129a0cc29a74cf8eaf6b24fbf36d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/01/2020
ms.locfileid: "80516666"
---
# <a name="use-grid-filters"></a>使用网格筛选器 

已改善统一接口中的网格，增加了可在屏幕上看到的数据量。 现在，可对一个列使用多个不同的筛选选项；列中的数据类型决定了可用的筛选器选项。 例如，“联系人”网格中的“全名”列具有与“活动”网格中“活动类型”列不同的筛选器选项     。


   > [!div class="mx-imgBorder"]
   > ![网格筛选](media/filter-options.png "网格筛选")
   

## <a name="grid-and-filter-navigation"></a>网格和筛选器导航

筛选网格中的数据时，如果你离开再返回到页面，主网格页会记住筛选器、排列顺序和页面状态。 通过快速查找、列筛选、页码等筛选数据时，页面也会记住最终状态。 

   > [!div class="mx-imgBorder"]
   > ![返回页面时，页面会以相同的状态打开](media/grid-remember-state-on-back-navigate.gif "返回页面时，页面会以相同的状态打开")

页面跳转栏使用第一个已排序的字段。 如果没有对排列顺序进行更改，跳转栏将使用主字段。

   > [!div class="mx-imgBorder"]
   > ![在跳转栏上选择筛选器](media/jumpbar-filter-on-sorted-column.gif "在跳转栏上选择筛选器")
  
选择层次结构图标时，可导航到层次结构视图。

   > [!div class="mx-imgBorder"]
   > ![层次结构图标](media/grid-row-hierarchy-icon.png "层次结构图标")

还可在新的选项卡或窗口中打开主字段和查阅字段。

   > [!div class="mx-imgBorder"]
   > ![在新窗口中打开](media/newtab.png "在新窗口中打开")
  
  
## <a name="lookup-field-column"></a>查阅字段列

对查阅列进行筛选时，可以从记录列表中选择筛选依据，而不能手动键入数据。 例如，在“主要联系人”查阅列中，可以从记录列表中选择联系人姓名作为筛选依据  。

   > [!div class="mx-imgBorder"]
   > ![查阅筛选](media/lookup-filter.png "查阅筛选")

## <a name="date-filter"></a>日期筛选器

可靠的“日期”筛选器包含多个不同的值供选择，如“日期”按准确的日期进行搜索，或“后 X 个会计年度”或“在会计期”按年份或季度搜索     。

   > [!div class="mx-imgBorder"]
   > ![日期筛选](media/date-filter.png "日期筛选")

## <a name="filter-the-list-of-activities"></a>筛选活动列表

可以筛选活动列表，仅查看你感兴趣的活动。 例如，可使用活动类型筛选器进一步限制视图中看到的活动。 借助活动类型筛选器，可根据类型（如电子邮件、任务、通话等）筛选活动。


   > [!div class="mx-imgBorder"]
   > ![活动筛选器](media/activity_filter.png "活动筛选器")


### <a name="known-issue"></a>已知问题 

如果更改数字、货币、时间或日期的默认显示格式，然后筛选网格中的数据，则筛选器不会显示所选的显示格式。 筛选器会仍以系统默认格式显示，在某些情况下，筛选功能可能会失效。 

若要解决此问题，请将数字、货币、时间和日期设置回默认设置。 

1. 在右上角选择齿轮图标![齿轮图标](media/selection-rule-gear-button.png)，然后选择“个性化设置”  。

2. 在“格式”选项卡上，将数字、货币、时间或日期值更改回默认设置  。

    > [!div class="mx-imgBorder"] 
    > ![格式设置](media/default-format.png "格式设置")
    
我们正在处理此问题，请在稍后返回此页，了解是否有可用的修补程序。

  
## <a name="use-search-on-a-grid"></a>在网格上使用搜索

在网格页上使用“搜索此视图”选项时，系统会在你当前所处的视图中搜索数据  。 在下面的示例中，将对“联系人”网格上进行搜索  。

1. 转到“联系人”网格，然后从视图列表中选择“我的活动联系人”   。

    > [!div class="mx-imgBorder"]
    > ![“我的活动联系人”视图](media/myactive-contacts-view.png "我的活动联系人视图")

2. 选择“搜索此视图”搜索所处视图中的数据  。

    > [!div class="mx-imgBorder"]
    > ![搜索视图](media/search-view.png "搜索此视图")

系统将在“我的活动联系人”视图中搜索数据，并使用在当前视图中使用的同一组列显示搜索结果  。

   > [!div class="mx-imgBorder"]
   > ![搜索视图](media/search-view2.png "搜索此视图命令中的搜索结果")


## <a name="use-the-quick-find-search-experience"></a>使用快速查找搜索体验

需要管理员权限，才能切换回旧版快速查找搜索体验，使用实体的快速查找视图定义来执行搜索。

1. 选择右上角的齿轮图标![齿轮图标](media/selection-rule-gear-button.png)，然后选择“高级设置”  。

2. 请转到“设置” > 管理” > “系统设置”    。

3. 在“常规”选项卡上的“设置快速查找”下，为“使用实体的快速查找视图在网格和子网格上进行搜索”选择“是”     。



