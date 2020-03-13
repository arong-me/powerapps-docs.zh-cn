---
title: 更改画布应用的屏幕大小和方向 | Microsoft Docs
description: 在 Power Apps 中更改设置（例如屏幕大小和画布应用的方向）的分步说明
author: evchaki
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2018
ms.author: evchaki
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b6ec2006266a15b7552d1a83b2d7d67c14560470
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "79211425"
---
# <a name="change-screen-size-and-orientation-of-a-canvas-app-in-power-apps"></a>更改 Power Apps 中画布应用的屏幕大小和方向
通过更改画布应用的屏幕大小和方向来自定义画布应用。

## <a name="prerequisites"></a>先决条件

创建应用或打开一个应用进行编辑，然后在 "**文件**" 菜单上选择 "**应用设置**"。

## <a name="change-screen-size-and-orientation"></a>更改屏幕的大小和方向
1. 在“**应用设置**”下，选择“**屏幕大小和方向**”。

    ![更改应用屏幕大小和方向的选项](./media/set-aspect-ratio-portrait-landscape/size-orientation.png)

1. 在 "**方向**" 列表中，选择 "**纵向**" 或 "**横向**"。

1. （仅限平板电脑应用）在 "**纵横比**" 下，执行以下步骤之一：

    - 选择匹配此应用的目标设备的比率。
    - 选择 "**自定义**" 设置自己的大小，然后指定一个介于 50-3840 和一个 50-2160 之间的高度。

    ![更改平板电脑应用的纵横比](./media/set-aspect-ratio-portrait-landscape/aspect-tablet.png)
    
1. 在 "**缩放到合适大小**" 下，指定 "**开**" 或 "**关**"。

    默认情况下，此设置处于启用状态，以便应用屏幕调整大小以适应设备上的可用空间。 当此设置为 on 时，应用程序的**Width**属性将与其**DesignWidth**匹配，并且应用的**高度**匹配其**DesignHeight**。

    如果关闭此设置，应用程序将调整到运行该设置的设备的纵横比，并占用所有可用空间。 应用不会缩放，因此屏幕可以显示详细信息。

    如果此设置处于关闭状态，则**锁定纵横比**会自动关闭并禁用。 此外，"所有屏幕" 的 " **Width** " 属性设置为 "`Max(App.Width, App.DesignWidth)`"，其 "**高度**" 属性设置为 "`Max(App.Height, App.DesignHeight)` 以便它们跟踪应用运行的窗口的尺寸。 通过此更改，你可以创建响应不同设备和窗口维度的应用。 详细信息：[创建响应式布局](create-responsive-layout.md)

1. 在“**锁定纵横比**”下，指定“**开**”或“**关**”。

    如果此设置为 "启用"，则应用将保留在步骤2和步骤3中指定的屏幕方向和纵横比，而不考虑设备。 例如，在 web 浏览器中运行的手机应用会保留电话的比率，同时在每一边显示一个黑色条形，而不是填充窗口。

    如果此设置处于关闭状态，则应用将调整到运行它的设备的高宽比（如有必要，并扭曲 UI）。

1. 在“**锁定方向**”下，指定“**开**”或“**关**”。

    如果锁定应用的方向，应用将保留指定的方向。 如果应用在屏幕处于不同方向的设备上运行，则应用程序显示不正确，可能会显示不需要的结果。 如果解除应用程序的方向，则会调整到运行该应用程序的设备的屏幕方向。

    还可以通过在**高级设置**中启用 "**启用应用嵌入用户体验**" 来修改应用的方向。 此功能在应用嵌入时靠上左对齐，将宿主画布的背景色更改为白色。

1. 选择“**应用**”，保存所做的更改。

## <a name="next-step"></a>下一步
在“**文件**”菜单上，选择“**保存**”，重新发布使用新设置的应用。