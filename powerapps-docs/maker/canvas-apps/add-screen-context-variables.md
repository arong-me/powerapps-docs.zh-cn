---
title: 添加和切换屏幕 | Microsoft 文档
description: 在应用中添加屏幕，然后在 PowerApps 中使用前进和后退箭头切换屏幕
author: aftowen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 07/10/2017
ms.author: anneta
ms.openlocfilehash: c7a100b6df278812ea93da8c4f5c503a841d4109
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39022001"
---
# <a name="add-a-screen-and-navigate-between-screens"></a>添加和切换屏幕
创建包含多个屏幕的应用，然后为用户提供屏幕切换方式。

## <a name="prerequisites"></a>先决条件
* 了解如何[配置控件](add-configure-controls.md)。
* 创建或打开应用。

## <a name="add-and-rename-a-screen"></a>添加并重命名屏幕
1. 在“开始”选项卡上，单击或点击“新屏幕”。

    ![“开始”选项卡上的“添加屏幕”选项](./media/add-screen-context-variables/add-screen.png)

2. 在右侧窗格中，单击或点击屏幕的名称（“属性”选项卡上方），然后键入新名称“源”。

    ![重命名默认屏幕](./media/add-screen-context-variables/name-source-screen.png)

3. 添加另一个屏幕，然后将其命名为“Target”。

    ![左侧导航栏中有两个屏幕](./media/add-screen-context-variables/two-screens-in-nav.png)

## <a name="add-navigation"></a>添加导航
1. 选择“Source”屏幕后，打开“插入”选项卡，然后依次单击或点击“图标”和“前进箭头”。  

    ![“插入”选项卡上的形状选项](./media/add-screen-context-variables/add-next-arrow.png)

2. （可选）将此箭头移到屏幕右下角。

3. 保持选择此箭头不变，依次单击或点击“操作”选项卡和“导航”。

    此箭头的**[“OnSelect”](controls/properties-core.md)** 属性会自动设为“Navigate”函数。  

    ![“OnSelect”属性自动设为“Navigate”函数](./media/add-screen-context-variables/onselect-default.png)

    当用户单击或点击此箭头时，“Target”屏幕淡入。

4. 在“Target”屏幕上，添加“后退箭头”，然后将其**[“OnSelect”](controls/properties-core.md)** 属性设为以下公式：
   <br>Navigate(Source, ScreenTransition.Fade)

5. 打开预览模式（选择 ![](./media/add-screen-context-variables/preview.png) 或按 F5 键），然后单击或点击所添加的箭头切换屏幕。

6. 按 **Esc** 键返回到默认工作区。
