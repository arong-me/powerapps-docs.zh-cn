---
title: "自定义应用（SharePoint 列表）| Microsoft 文档"
description: "更新应用屏幕、控件和字段"
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
featuredvideoid: KydeusvKndQ
courseduration: 5m
ms.service: powerapps
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/09/2016
ms.author: mblythe
ms.openlocfilehash: 8aa1db7735416a9dc59fc2c726c5b506fd438a03
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="customize-the-app-sharepoint-list"></a>自定义应用（SharePoint 列表）
在此部分的前两个主题中，你生成了基于 SharePoint 列表的应用，并探索了组成应用的三个屏幕。 虽然 PowerApps 生成的应用非常有用，但经常需要在生成应用后进行自定义。 此主题将逐步介绍如何对应用的每个屏幕进行一些基本更改。 还可以自定义应用的更多方面，后续主题将对此进行介绍。 在此期间，可以利用此主题介绍的内容自定义应用。 采用生成的基于列表、Excel 文件或其他源的任何应用，了解如何自定义应用。 这确实是了解应用的各组成部分的最佳方式。

## <a name="browse-screen"></a>浏览屏幕
我们将从浏览屏幕开始。 SharePoint 列表包含每个产品的图像，但图像默认不显示。 让我们来解决此问题。 在右侧窗格的“**布局**”选项卡上，为浏览屏幕选择其他布局。 你会立即看到所选布局，因为 PowerApps 在你执行更改的同时更新应用。

![更改浏览屏幕布局](./media/learning-spo-app-customize/generate-change-layout.png)

设置正确的基本布局后，现在让我们来更改显示字段。 单击或点击第一项中的字段，然后在右侧窗格中更改每一项的显示数据。 这样一来，便可以改进列表中每一项的摘要。

![更改浏览屏幕字段](./media/learning-spo-app-customize/generate-browse-fields.png)

## <a name="details-screen"></a>详细信息屏幕
在详细信息屏幕上，我们要更改字段顺序，并且也要显示图像。 由于此屏幕上的控件不同，因此过程与浏览屏幕略有不同。 单击或点击字段，然后在右侧窗格中将“**标题**”字段拖到顶部。 然后，单击或点击“**图像**”字段，显示此字段。

![更改详细信息屏幕字段](./media/learning-spo-app-customize/generate-detail-fields.png)

## <a name="editcreate-screen"></a>编辑/创建屏幕
最后，在编辑和创建条目的屏幕上，我们要更改字段，以简化文本输入。 依次单击或点击“Overview”字段的下拉列表和“编辑多行文本”控件。

![更改编辑屏幕字段](./media/learning-spo-app-customize/generate-edit-fields.png)

你会发现，只需执行几个基本步骤，就可以改善生成的应用的外观和使用体验。 在本主题中，我们将重点放在了 PowerApps Studio UI 上，其中有许多应用自定义选项。 下一主题将介绍在定义应用行为方面发挥重要作用的公式。  

