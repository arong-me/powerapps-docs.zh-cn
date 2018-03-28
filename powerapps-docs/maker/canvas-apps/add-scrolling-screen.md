---
title: 添加滚动屏幕 | Microsoft 文档
description: 创建用户可以滚动浏览更多类型内容的屏幕（与一次性显示全部内容的屏幕相比）。
services: ''
suite: powerapps
documentationcenter: na
author: lonu
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/25/2016
ms.author: lonu
ms.openlocfilehash: d4022716ec83d9b981d3ac2b9e123689452a115a
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="add-a-scrolling-screen-in-powerapps"></a>在 PowerApps 中添加滚动屏幕
创建用户可以滚动浏览不同项的屏幕。 例如，不妨创建一个用柱形图和折线图显示数据的应用。 通过添加滚动屏幕，可以添加多个控件，以便用户可以滚动浏览这些控件。

在一个分区中添加多个控件时，这些控件会在这一分区中保持相对位置不变，无论是手机应用，还是平板电脑应用。 请注意，屏幕尺寸和方向可能会决定各分区的排列方式。  

[!INCLUDE [app-customization-requirements](../../includes/app-customization-requirements.md)]

## <a name="create-a-scrolling-screen"></a>创建滚动屏幕
1. 在“开始”选项卡上，单击或点击“新屏幕””：
   
    ![用于在应用中添加屏幕的选项][1]
2. 在“开始”选项卡上，依次单击或点击“布局”和用于添加无限滚动画布的选项：  
   
    ![用于添加无限滚动画布的选项][2]
   
    此时，画布已添加：  
   
    ![默认显示的包含无限滚动画布的屏幕][3]

## <a name="add-elements"></a>添加元素
现在，让我们在画布上添加一些控件，了解一下滚动屏幕的工作原理。

1. 在已添加的画布上，单击或点击“从‘插入’选项卡添加项”。
   
    ![][4]
2. 在“插入”选项卡上，依次单击或点击“图表”和“柱形图”。
   
    ![用于添加柱形图的选项][5]
   
    此时，柱形图在屏幕上的第一张卡中显示：  
   
    ![默认柱形图][7]
3. 在“插入”选项卡上，依次单击或点击“文本”和“笔输入”：  
   
    ![用于添加笔控件的选项][8]
4. 将笔控件移到图表下方，然后重设笔控件大小，以覆盖卡的底部：  
   
    ![移动笔控件并重设大小][9]

## <a name="add-a-section"></a>添加分区
现在，让我们来添加另一张卡，并在此卡中添加其他控件。

1. 单击或点击屏幕底部附近的“添加分区”：  
   
    ![用于添加分区的选项][10]
   
    此时，一张新卡已添加到屏幕中：  
   
    ![新卡位于默认分区下方][11]
2. 保持选择此卡不变，转到“插入”选项卡，然后依次单击或点击“图表”和“折线图”。
   
    新图表太大了，无法在屏幕上与其他控件一起显示：  
   
    ![折线图已添加到新卡底部][12]
3. 按 F5（或者单击或点击右上角附近的播放图标）即可打开预览模式。
   
    ![打开预览模式](./media/add-scrolling-screen/open-preview.png)
4. 向下滚动浏览新添加的折线图。  
   
    ![预览中显示折线图][13]

[1]: ./media/add-scrolling-screen/add-screen.png
[2]: ./media/add-scrolling-screen/add-canvas.png
[3]: ./media/add-scrolling-screen/default-canvas.png
[4]: ./media/add-scrolling-screen/insert-visual.png
[5]: ./media/add-scrolling-screen/add-chart.png
[7]: ./media/add-scrolling-screen/default-chart.png
[8]: ./media/add-scrolling-screen/add-pen.png
[9]: ./media/add-scrolling-screen/move-resize-pen.png
[10]: ./media/add-scrolling-screen/add-section.png
[11]: ./media/add-scrolling-screen/new-card.png
[12]: ./media/add-scrolling-screen/add-line-chart.png
[13]: ./media/add-scrolling-screen/line-chart-preview.png