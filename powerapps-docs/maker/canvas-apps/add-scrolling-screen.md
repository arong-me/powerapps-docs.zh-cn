---
title: 向画布应用添加滚动屏幕 | Microsoft Docs
description: 在 Power Apps 中，创建一个屏幕，用户可以滚动显示更多类型的内容，而不会在画布应用中一次显示该屏幕。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: de0aba95b4bb5c3a308b0b86b739302dc0dc70e3
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74724663"
---
# <a name="add-a-scrolling-screen-to-a-canvas-app-in-power-apps"></a>在 Power Apps 中向画布应用添加滚动屏幕

在画布应用中，创建用户可以滚动浏览不同项的屏幕。 例如，创建一个手机应用，在多个图表中显示数据，当用户滚动屏幕时可浏览这些数据。

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
