---
title: 画布应用的辅助功能属性 |Microsoft Docs
description: 有关 TabIndex 和 Tooltip 等属性的参考信息
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/26/2017
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 056d54fa086a72c0528e51a2eb264692a865f94f
ms.sourcegitcommit: 8e42a5996799d9831f8c5a52b0b051a6088d9ce7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/06/2019
ms.locfileid: "73649634"
---
# <a name="accessibility-properties-for-canvas-apps"></a>画布应用的辅助功能属性

配置有助于残障用户以其他合适方式与控件进行交互的属性。

## <a name="properties"></a>属性

**AccessibleLabel** – 屏幕阅读器标签。 如果“图像”、“图标”和“形状”控件采用空值，将导致这些控件对屏幕阅读器不可见，并被视为修饰。

**Live** –屏幕阅读器应如何公布对内容所做的更改。 仅在 " **[标签](control-text-box.md)** " 控件中可用。

* 当设置为**Off**时，屏幕阅读器不会公告更改。
* 当设置为 "**礼貌**" 时，屏幕阅读器会在通知屏幕阅读器说话时出现的任何更改前完成。
* 设置为 "**主动**" 时，屏幕阅读器会自行中断，以通知屏幕阅读器说话时所发生的任何更改。

了解如何[通过实时区域公告动态更改](../accessible-apps-live-regions.md)。

**TabIndex** –确定控件是否参与键盘导航。

键盘导航是任何应用程序的一个重要方面。  很多键盘比使用触摸或鼠标更高效，并为视觉障碍者启用屏幕阅读器。  导航顺序应：
- 镜像可见内容。
- 只有交互式控件的制表位。
- 依次单击 "Z" 和 "Z" 顺序中的直观顺序，或按 "反 N" 顺序进行。

将通过默认的**TabIndex**值满足上述要求，我们建议您不要更改它们。  默认情况下，大多数用户都能以可视化方式使用，并且它将与屏幕阅读器正常配合使用。  但在某些情况下，您可能需要覆盖默认值。  使用**TabIndex**属性和[**增强组**控件](https://powerapps.microsoft.com/blog/enhanced-group-experimental-control-with-layout-control-and-nesting/)（实验性）来对导航顺序进行调整。  

**TabIndex**属性有两个建议的值：

| TabIndex 值 | 行为 | 默认值 |
|----------------|----------|-------------|
| 0 | 控件参与键盘导航。 | [**按钮**](control-button.md)、[**文本输入**](control-text-input.md)、[**组合框**](control-combo-box.md)以及其他通常交互控件。 |
| &minus;1 | 控件不参与键盘导航。 | [**标签**](control-text-box.md)、[**图像**](control-image.md)、[**图标**](control-shapes-icons.md)和其他通常是非交互式控件。 |

通常，导航顺序从左到右、从上到下、以 "Z" 模式进行。 顺序基于控件的**X**和**Y**属性值。 如果控件在屏幕上动态移动（例如，通过基于计时器或其他控件的**X**或**Y**计算公式），则导航顺序也会动态更改。

使用[**增强组**控件](https://powerapps.microsoft.com/blog/enhanced-group-experimental-control-with-layout-control-and-nesting/)（实验性）来捆绑应在一起导航的控件，或使用 "反 N" 模式创建列。  在下面的示例中，名称字段包含在增强的组控件中，这会导致导航在移动之前继续下一步。  在此示例的底部，不使用任何组控件，导航将继续进行，并在不直观的情况下进行导航，因为控件分组。 

![动画显示增强型组控件，使导航在组内前进，然后移到](media/properties-accessibility/enhanced-group.gif)

同样，在 "[**窗体**](control-form-detail.md)" 和 "[**库**](control-gallery.md)" 控件等容器中，按 tab 将导航到容器中的所有元素，然后继续到容器外的下一个控件。  

导航中不包括**Visible**属性值为*false*或**DisplayMode**属性值为**Disabled**的控件。  

使用浏览器时，从屏幕的最后一个控件导航到浏览器的内置控件，如 URL 地址。  

> [!WARNING]
> 避免**TabIndex**值大于0。 最终控件以 HTML 格式呈现，即使[W3C 已警告](https://www.w3.org/TR/wai-aria-practices/#kbd_general_between)"作者强烈建议不要使用这些值"。 许多 HTML 工具会对大于[0 的值发出警告，因为](../accessibility-checker.md)它报告 "检查屏幕项的顺序"。  这一切都很合理：以这种方式使用**TabIndex**可能会非常困难，而且可以使辅助技术（如屏幕阅读器）不可用。
> 
> 如果存在的**tabindex**大于0，用户将导航到具有增加的**tabindex**值的控件（1，then 2，等等）。 当用户使用正面**TabIndex**值浏览所有控件时，最终将使用**TabIndex** 0 （包括浏览器的内置控件）导航到控件。 如果有多个控件具有相同的**TabIndex**，则其**X**和**Y**位置确定其相对顺序。





