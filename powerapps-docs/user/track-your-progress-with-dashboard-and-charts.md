---
title: 在模型驱动应用中使用仪表板和图表跟踪进度 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/4/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
- D365CE
ms.openlocfilehash: 70c6f97c2617c9d6084c3aa8a0861793a0c059d5
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74726173"
---
# <a name="track-your-progress-with-dashboards-and-charts"></a>使用仪表板和图表跟踪进度

仪表板收集了一组应用数据并提供见解，以在易于阅读的交互式图表和图形中显示关键性能指标 (KPI) 和其他重要数据。 仪表板可用于所有记录类型。

> [!div class="mx-imgBorder"]
> ![仪表板](media/Dashboard.png "仪表板") 

-  要查看其他仪表板布局，请选择仪表板名称旁的向下箭头，然后选择所需的布局。
-  要选择默认的仪表板，请显示所需的仪表板，然后选择屏幕顶部“设置为默认仪表板”  。

   > [!div class="mx-imgBorder"]
   > ![添加或更改仪表板](media/add_dashboard.png "添加或更改仪表板") 

## <a name="create-a-new-dashboard"></a>创建新的仪表板

1. 要创建新仪表板，请选择“创建 Dynamics 365 仪表板”。  

   > [!div class="mx-imgBorder"]
   > ![添加新仪表板](media/new_dashboard.png "添加新仪表板")
   
2. 选择仪表板布局，并选择“创建”  。  

   > [!div class="mx-imgBorder"]
   > ![创建仪表板](media/create_dashboard.png "创建仪表板")
 
3. 键入仪表板的名称。 
4. 向仪表板的各个区域添加所需内容。 例如，我们来添加一个图表。 

   > [!div class="mx-imgBorder"]
   > ![添加图表](media/add_chart.png "添加图表")
 
 5. 为图表选择“记录类型”  。
 6. 选择将显示图表中的数据的“视图”  。
 7. 选择图表，然后选择“添加”  。
 8. 继续将组件添加到仪表板，完成后，选择“保存”  。 
 
创建的仪表板将显示在可用仪表板的下拉菜单中。

## <a name="use-charts"></a>使用图表 

图表可提供快速视图，用于查看目标的跟踪情况。 它们也是交互式的，因此，可以单击或点击图表中的某个区域以获取详细信息。

-   将鼠标悬停在图表上会显示一个工具提示，可快速提供有关该图表区域的信息。
-   单击图表区域可以查看网格视图，其中包含有关图表中的数据的更多详细信息。
-   要展开图表，请选择“展开图表”  ![展开图表视图](media/expandviewbutton.png "展开图表视图")按钮。
-   要查看图表中的记录或刷新图表，请选择![更多命令](media/MoreButton.png "更多命令")然后选择任一操作：“刷新”或“查看记录”   。
     
     > [!div class="mx-imgBorder"]
     > ![Power Apps 中的图表视图](media/ViewOfCharts.png "Power Apps 中的图表视图")  
       

**更改图表视图**
 
更改图表视图会显示不同的数据细目，如在特定时间段内打开的机会。 通过在“网格”页上选择“视图选择器”，可更改图表视图。

例如，选择“所有机会”，然后选择其他视图，随即将刷新图表和网格。

> [!div class="mx-imgBorder"]
> ![更改 Power Apps 中的图表视图](media/ChangeChartView.png "更改 Power Apps 中的图表视图")

## <a name="known-issues"></a>已知问题  
在图表设计器中，不支持对某些计算字段添加排序依据，并将导致错误。  导致此错误的计算字段将使用其他计算字段、相关实体字段或实体上的本地字段。



