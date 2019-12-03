---
title: 在画布应用中添加屏幕并在不同屏幕间切换 | Microsoft Docs
description: 向画布应用添加屏幕，使用 "下一步" 和 "后退" 箭头在 Power Apps 中的屏幕之间切换
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 02/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cbe6173c94f001874b126a5b8ecb1bdf9ad21b70
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74724483"
---
# <a name="add-a-screen-to-a-canvas-app-and-navigate-between-screens"></a>在画布应用中添加屏幕并切换屏幕

创建包含多个屏幕的画布应用，然后为用户提供屏幕切换方式。

## <a name="add-and-rename-a-screen"></a>添加并重命名屏幕

1. 在 "**主页**" 选项卡上，选择 "**新屏幕**"，然后选择要添加的屏幕类型。

    ![“开始”选项卡上的“添加屏幕”选项](./media/add-screen-context-variables/add-screen.png)

2. 在右侧窗格中，选择屏幕的名称（在 "**属性**" 选项卡的上方），然后键入**Source**。

    ![重命名默认屏幕](./media/add-screen-context-variables/name-source-screen.png)

3. 添加另一个屏幕，然后将其命名为“Target”。

    ![左侧导航栏中有两个屏幕](./media/add-screen-context-variables/two-screens-in-nav.png)

## <a name="reorder-screens"></a>重新排序屏幕

在左侧导航栏中，将鼠标悬停在要上移或下移的屏幕上，选择显示的省略号按钮，然后选择 "**上移**" 或 **"下移"。**

![重新排序屏幕](./media/add-screen-context-variables/reorder-screen.png)

> [!NOTE]
> 打开应用后，控件分层列表顶部的屏幕通常会首先出现。 但可以通过将 **[OnStart](controls/control-screen.md)** 属性设置为包含 **[导航](functions/function-navigate.md)** 函数的公式来指定其他屏幕。

## <a name="add-navigation"></a>添加导航

1. 选择**源**屏幕后，打开 "**插入**" 选项卡，选择 "**图标**"，然后选择 "**下一步" 箭头**。  

    ![“插入”选项卡上的形状选项](./media/add-screen-context-variables/add-next-arrow.png)

2. （可选）将此箭头移到屏幕右下角。

3. 在仍选中箭头的情况下，选择 "**操作**" 选项卡，然后选择 "**导航**"。

    此箭头的 **[“OnSelect”](controls/properties-core.md)** 属性会自动设为 **“Navigate”** 函数。

    ![“OnSelect”属性自动设为“Navigate”函数](./media/add-screen-context-variables/onselect-default.png)

    当用户选择箭头时，**目标**屏幕将淡入。

4. 在“Target”屏幕上，添加“后退箭头” ，然后将其 **[“OnSelect”](controls/properties-core.md)** 属性设为以下公式：

    `Navigate(Source, ScreenTransition.Fade)`

5. 按下 Alt 键时，通过选择每个屏幕上的箭头在屏幕之间切换。

## <a name="more-information"></a>详细信息

[屏幕控制参考](controls/control-screen.md)