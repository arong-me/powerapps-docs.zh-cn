---
title: 辅助功能属性的画布应用 |Microsoft Docs
description: 有关 TabIndex 和工具提示等属性的参考信息
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/26/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 5fa8b6fecdf690114cbf6a0945f2dfec66b067c3
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61560406"
---
# <a name="accessibility-properties-for-canvas-apps"></a>画布应用的辅助功能属性

配置有助于残障用户以其他合适方式与控件进行交互的属性。

## <a name="properties"></a>属性

**AccessibleLabel** – 屏幕阅读器标签。 如果“图像”、“图标”和“形状”控件采用空值，将导致这些控件对屏幕阅读器不可见，并被视为修饰。

**Live** – 屏幕阅读器应宣布内容的更改方式。 仅适用于**[标签](control-text-box.md)** 控件。

* 如果设置为**关闭**，屏幕读取器不会公布的更改。
* 如果设置为**礼貌**，屏幕读取器完成之前宣布推出时屏幕读取器已谈到出现的任何更改。
* 如果设置为**Assertive**，屏幕阅读器会中断本身地宣布已谈到屏幕读取器时出现的任何更改。

了解如何[宣布活动区域的动态更改](../accessible-apps-live-regions.md)。

**TabIndex** – 相对于其他控件的键盘导航顺序。

默认值零根据控件的 XY 坐标指定默认 Tab 键顺序。  如果将值设置为大于零，则会将该控件的 Tab 键顺序移到所有采用默认值的控件的前面。  使用 Tab 键时，TabIndex 值为 2 的控件优先于 TabIndex 值大于等于 3 的控件。

请注意，窗体控件和库控件等容器始终先用 Tab 键访问其所有元素，然后才会访问容器外部的控件。  容器的 Tab 键顺序从具有最小 TabIndex 值的子控件开始。

如果将 TabIndex 设置为 -1，则禁用 tab 键访问控件；如果是“图像”、“图标”和“形状”控件，它们也会成为非交互式元素。
