---
title: 自定义画布应用中的卡 |Microsoft Docs
description: 显示详细信息上的卡片中的默认控件更改或编辑窗体中的画布应用
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ddc1c677ed95caf10d8cd6e0e7e12e6aaf88a0f5
ms.sourcegitcommit: f4b71ea0996603b3358377a0da21b9e4428a287c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58870899"
---
# <a name="customize-a-card-in-a-canvas-app"></a>自定义卡在画布应用

举例来说，通过更改卡控件执行基本的自定义（无需解锁卡）。 例如，通过解锁卡及添加默认情况下该卡无法使用的控件来执行高级自定义。

有关概述，请参阅 [了解数据卡](working-with-cards.md)。

## <a name="prerequisites"></a>先决条件

- 了解如何 [添加和配置控件](add-configure-controls.md)。
- 你可以查看此主题的基本概念，或如果你先完成这些主题中的过程，可以按照其步骤：

    1. [生成应用](data-platform-create-app.md)。
    1. [自定义库](customize-layout-sharepoint.md)。
    1. [自定义窗体](customize-forms-sharepoint.md)。

## <a name="customize-a-locked-card"></a>自定义锁定的卡

在此过程中，会将为**[文本输入](controls/control-text-input.md)** 与控制 **[滑块] (控件/控件-slider.md**控件，而无需解锁卡。

1. 在生成并自定义的应用，选择**EditForm1**左侧导航栏中，然后选择**编辑字段**上**属性**的右侧窗格的选项卡。

1. 在字段列表中，选择向下的箭头**雇员数目**，然后打开列表下的**控件类型**。

    > [!div class="mx-imgBorder"]
    > ![数量卡片的下拉选项列表](./media/customize-card/card-selector.png)

1. 选择**编辑滑块**。

    屏幕将体现所做的更改。

    > [!div class="mx-imgBorder"]
    > ![带滑块控件的 EditForm1](./media/customize-card/add-slider.png)

## <a name="unlock-and-customize-a-card"></a>解锁和自定义卡

在此过程中，将解锁卡，更新**最大**的属性**滑块**刚添加的控件。

1. 在中**EditForm1**，选择**滑块**控制**雇员数目**卡。

    > [!div class="mx-imgBorder"]
    > ![选择滑块](./media/customize-card/select-slider.png)

1. 上**高级**选项卡的右侧窗格中，选择锁定图标以解锁卡。

    > [!div class="mx-imgBorder"]
    > ![解锁卡](./media/customize-card/lock-icon.png)

1. 设置**最大**的属性**滑块**控件为 10,000。

    > [!div class="mx-imgBorder"]
    > ![高级选项卡上的最大属性](./media/customize-card/max-property.png)

    **滑块**控件显示更精确的值。

    > [!div class="mx-imgBorder"]
    > ![滑块范围：0-10,000](./media/customize-card/final-slider.png)

## <a name="next-steps"></a>后续步骤

现已基本了解如何生成应用并自定义库、窗体和卡片，可以[从头开始构建自己的应用](data-platform-create-app-scratch.md)。