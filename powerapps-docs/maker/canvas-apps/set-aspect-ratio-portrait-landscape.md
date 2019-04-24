---
title: 更改画布应用的屏幕大小和方向 | Microsoft Docs
description: 有关在 PowerApps 中更改画布应用的屏幕大小和方向等设置的分步说明
author: evchaki
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2018
ms.author: evchaki
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c4d9f648a4519ef30887d8d0739d7dc3d940555b
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61536007"
---
# <a name="change-screen-size-and-orientation-of-a-canvas-app-in-powerapps"></a>在 PowerApps 中更改画布应用的屏幕大小和方向
通过更改画布应用的屏幕大小和方向来自定义画布应用。

## <a name="prerequisites"></a>先决条件

创建应用或打开进行编辑，并选择**应用设置**上**文件**菜单。

## <a name="change-screen-size-and-orientation"></a>更改屏幕的大小和方向
1. 在“**应用设置**”下，选择“**屏幕大小和方向**”。

    ![更改应用屏幕大小和方向的选项](./media/set-aspect-ratio-portrait-landscape/size-orientation.png)

1. 在中**方向**列表中，选择**纵向**或**横向**。

1. （仅适用于平板电脑应用）下**纵横比**，执行以下步骤之一：

    - 选择匹配此应用的目标设备的比率。
    - 选择**自定义**以设置你自己的大小，然后指定 50 3840 和 50 2160年之间一个高度之间的宽度。

    ![更改平板电脑应用的纵横比](./media/set-aspect-ratio-portrait-landscape/aspect-tablet.png)
    
1. 下**缩放以适合**，指定**上**或**关闭**。

    此设置上是默认情况下，以便应用屏幕调整大小以适合该设备上的可用空间。 此设置时，应用程序的**宽度**属性匹配其**DesignWidth**，并应用的**高度**匹配其**DesignHeight**。

    如果关闭此设置，应用会调整为它在其正在运行，并且将占用所有可用空间的设备的纵横比。 应用程序不能扩展和结果，屏幕可以显示详细信息。

    当关闭此设置时，**锁定纵横比**自动关闭并禁用。 此外，**宽度**的所有屏幕的属性设置为`Max(App.Width, App.DesignWidth)`，并且其**高度**属性设置为`Max(App.Height, App.DesignHeight)`，以便它们跟踪在其中运行应用程序窗口的尺寸。 进行此更改后，你可以创建响应不同的设备和窗口尺寸的应用。 详细信息：[创建响应式布局](create-responsive-layout.md)

1. 在“**锁定纵横比**”下，指定“**开**”或“**关**”。

    如果打开此设置后，应用将保留的屏幕方向和指定在步骤 2 和 3，无论设备的纵横比。 例如，在 web 浏览器中运行的 phone 应用程序保留手机，而不是填充窗口中的每一侧显示的暗条的比例。

    如果关闭此设置，则应用将调整为在其上它是正在运行 （和扭曲 UI，如有必要） 的设备的纵横比。

1. 在“**锁定方向**”下，指定“**开**”或“**关**”。

    如果锁定应用的方向，应用将保留所指定的方向。 如果应用程序的屏幕是不同的方向中为其设备上运行，该应用不正确地显示，并可能会显示意想不到的效果。 如果解锁应用的方向，它将调整到其运行的设备的屏幕方向。

    此外可以修改应用的方向，从而**启用应用嵌入的用户体验**中**高级设置**。 此功能顶部左侧对齐应用程序时它嵌入，更改将托管画布的背景色为白色。

1. 选择“**应用**”，保存所做的更改。

## <a name="next-step"></a>下一步
在“**文件**”菜单上，选择“**保存**”，重新发布使用新设置的应用。