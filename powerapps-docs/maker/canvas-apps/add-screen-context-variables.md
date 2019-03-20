---
title: 在画布应用中添加屏幕并在不同屏幕间切换 | Microsoft Docs
description: 在画布应用中添加屏幕，然后在 PowerApps 中使用前进和后退箭头切换屏幕
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
ms.openlocfilehash: b6f83d21b2964dac7c4925d45efdf11a3a1e6b02
ms.sourcegitcommit: 7f67cd28c781a48f6a211ed82c2c861ae3acf1a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2019
ms.locfileid: "57800712"
---
# <a name="add-a-screen-to-a-canvas-app-and-navigate-between-screens"></a>在画布应用中添加屏幕并切换屏幕

创建包含多个屏幕的画布应用，然后为用户提供屏幕切换方式。

## <a name="add-and-rename-a-screen"></a>添加并重命名屏幕

1. 上**主页**选项卡上，选择**新屏幕**，然后选择你想要添加的屏幕的类型。

    ![“开始”选项卡上的“添加屏幕”选项](./media/add-screen-context-variables/add-screen.png)

2. 在右侧窗格中，选择屏幕的名称 (正上方**属性**选项卡)，然后键入**源**。

    ![重命名默认屏幕](./media/add-screen-context-variables/name-source-screen.png)

3. 添加另一个屏幕，然后将其命名为“Target”。

    ![左侧导航栏中有两个屏幕](./media/add-screen-context-variables/two-screens-in-nav.png)

## <a name="reorder-screens"></a>重新排列屏幕

在左侧的导航栏中，悬停在想要上移或向下，选择省略号按钮显示的屏幕，然后选择**上移**或**向下移动**。

![重新排列屏幕](./media/add-screen-context-variables/reorder-screen.png)

> [!NOTE]
> 打开应用时，屏幕顶部的控件的层次结构列表通常会显示第一个。 但您可以通过设置指定不同的屏幕**[OnStart](controls/control-screen.md)** 属性设置为公式，其中包括**[Navigate](functions/function-navigate.md)** 函数。

## <a name="add-navigation"></a>添加导航

1. 与**源**屏幕选择，打开**插入**选项卡上，选择**图标**，然后选择**下一步箭头**。  

    ![“插入”选项卡上的形状选项](./media/add-screen-context-variables/add-next-arrow.png)

2. （可选）将此箭头移到屏幕右下角。

3. 仍处于选中状态的箭头，选择**操作**选项卡，然后选择**Navigate**。

    此箭头的 **[“OnSelect”](controls/properties-core.md)** 属性会自动设为 **“Navigate”** 函数。

    ![“OnSelect”属性自动设为“Navigate”函数](./media/add-screen-context-variables/onselect-default.png)

    当用户选择箭头**目标**屏幕淡入。

4. 在“Target” 屏幕上，添加“后退箭头” ，然后将其 **[“OnSelect”](controls/properties-core.md)** 属性设为以下公式：

    `Navigate(Source, ScreenTransition.Fade)`

5. 按住 Alt 键，同时选择每个屏幕上的箭头屏幕之间切换。

## <a name="more-information"></a>详细信息

[屏幕控件引用](controls/control-screen.md)