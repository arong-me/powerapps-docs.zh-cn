---
title: 自定义画布应用中的卡片 |Microsoft Docs
description: 在画布应用中更改在卡片上显示的默认控件详细信息或编辑窗体
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/18/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5bcf1515f72bdce0872f91c64b5ac4fe5028ee2c
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985924"
---
# <a name="customize-a-card-in-a-canvas-app"></a>自定义画布应用中的卡片

举例来说，通过更改卡控件执行基本的自定义（无需解锁卡）。 例如，通过解锁卡及添加默认情况下该卡无法使用的控件来执行高级自定义。

有关概述，请参阅 [了解数据卡](working-with-cards.md)。

## <a name="prerequisites"></a>先决条件

- 了解如何 [添加和配置控件](add-configure-controls.md)。
- 您可以仅查看本主题中的常规概念，也可以在您首先完成这些主题中的过程后逐步执行以下操作：

    1. [生成应用](data-platform-create-app.md)。
    1. [自定义库](customize-layout-sharepoint.md)。
    1. [自定义窗体](customize-forms-sharepoint.md)。

## <a name="customize-a-locked-card"></a>自定义锁定的卡

在此过程中，您将使用 **[滑块] （控件/控制滑块**控件）替换 **[文本输入](controls/control-text-input.md)** 控件，而无需解锁卡。

1. 在生成并自定义的应用程序中，在左侧导航栏中选择 " **EditForm1** "，然后选择右侧窗格的 "**属性**" 选项卡上的 "**编辑字段**"。

1. 在字段列表中，选择 "**雇员数**" 的下箭头，然后打开 "**控件类型**" 下的列表。

    > [!div class="mx-imgBorder"]
    > 用于数字卡片 @ no__t 的选项的 @no__t 0Drop 列表

1. 选择 "**编辑滑块**"。

    屏幕将体现所做的更改。

    > [!div class="mx-imgBorder"]
    > ![EditForm1 与 slider control @ no__t-1

## <a name="unlock-and-customize-a-card"></a>解锁和自定义卡

在此过程中，将解锁卡，并更新刚添加的**滑块**控件的**Max**属性。

1. 在**EditForm1**中，选择 "**员工**" 卡的 "**滑块**" 控件。

    > [!div class="mx-imgBorder"]
    > ![Select 滑块 @ no__t-1

1. 在右侧窗格的 "**高级**" 选项卡上，选择锁定图标来解锁卡。

    > [!div class="mx-imgBorder"]
    > @no__t 0Unlock 卡片式 @ no__t-1

1. 将**滑块**控件的**Max**属性设置为10000。

    > [!div class="mx-imgBorder"]
    > "高级" 选项卡上的 "0Max" 属性 @ no__t-1 @no__t

    **滑块**控件显示的值越精确。

    > [!div class="mx-imgBorder"]
    > ![Slider 范围：0-10000 @ no__t-0

## <a name="next-steps"></a>后续步骤

现已基本了解如何生成应用并自定义库、窗体和卡片，可以[从头开始构建自己的应用](data-platform-create-app-scratch.md)。