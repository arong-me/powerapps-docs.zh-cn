---
title: Accessibility 属性 | Microsoft 文档
description: 有关 TabIndex、Tooltip 等属性的参考信息
services: ''
suite: powerapps
documentationcenter: na
author: fikaradz
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 01/26/2017
ms.author: fikaradz
ms.openlocfilehash: 062267a93ca625513d0280c753eefaaacd743811
ms.sourcegitcommit: 4710a56d308efe67fe60a7688143e61f5e5f2b44
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="accessibility-properties-in-powerapps"></a>PowerApps 中的辅助功能属性
配置有助于残障用户以其他合适方式与控件进行交互的属性。

### <a name="properties"></a>属性
**AccessibleLabel** – 屏幕阅读器标签。 如果“图像”、“图标”和“形状”控件采用空值，将导致这些控件对屏幕阅读器不可见，并被视为修饰。

**TabIndex** – 相对于其他控件的键盘导航顺序。

默认值零根据控件的 XY 坐标指定默认 Tab 键顺序。  如果将值设置为大于零，则会将该控件的 Tab 键顺序移到所有采用默认值的控件的前面。  使用 Tab 键时，TabIndex 值为 2 的控件优先于 TabIndex 值大于等于 3 的控件。

请注意，窗体控件和库控件等容器始终先用 Tab 键访问其所有元素，然后才会访问容器外部的控件。  容器的 Tab 键顺序从具有最小 TabIndex 值的子控件开始。

如果将 TabIndex 设置为 -1，则禁用 tab 键访问控件；如果是“图像”、“图标”和“形状”控件，它们也会成为非交互式元素。
