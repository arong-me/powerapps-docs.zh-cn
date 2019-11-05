---
title: 容器控件：参考 |Microsoft Docs
description: 有关容器控件的信息（包括属性和示例）
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 9/20/2019
ms.author: emcoope
ms.reviewer: tapanm-msft
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8456e82cfd2680fcbb722c8b4b2b5b32ef73dbde
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540275"
---
# <a name="container-control-in-powerapps-experimental"></a>PowerApps 中的容器控件（实验性）
提供创建层次结构的功能。

> [!IMPORTANT]
> 这是一项实验性功能。 实验性功能可能随时从根本上更改或彻底消失。
> 有关详细信息，请参阅[了解 PowerApps 中的实验性和预览功能](https://docs.microsoft.com/powerapps/maker/canvas-apps/working-with-experimental-preview)。

## <a name="description"></a>描述
 容器可以保存一组控件并具有自己的属性。 

你可以开始插入一个空容器，然后通过将控件添加到它来对其进行自定义、调整大小、移动、隐藏它，以及进行其他更改。 你还可以从多个控件开始，选择它们，然后通过树视图中的上下文菜单或右键单击画布，将它们添加到容器中。 

## <a name="properties"></a>属性
[BorderColor](properties-color-border.md) – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

[Width](properties-size-location.md) – 控件左边缘和右边缘之间的距离。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[X](properties-size-location.md)** - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。 

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。 


## <a name="known-limitations"></a>已知的限制

容器不能用于画布组件或窗体内。 

## <a name="frequently-asked-questions"></a>常见问题

**容器和组之间的区别是什么？**
创作组是一种轻型概念，用于在控件中移动和批量编辑组中控件的类似属性。 创作组不影响应用程序的布局。 

之前在实验中交付的容器控件，作为重命名为增强组的创作组的替代项。 已将其重命名为容器控件，因为轻型创作组和具有其他属性的 strutured 容器控件存在值。 

