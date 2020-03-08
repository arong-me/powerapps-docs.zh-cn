---
title: 下拉列表控件：参考 | Microsoft 文档
description: 有关下拉列表控件的信息（包括属性和示例）
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cc9b12f6cf899d0a57e56eda9fe0dd4bc5ba6c2e
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78403843"
---
# <a name="drop-down-control-in-power-apps"></a>Power Apps 中的下拉控件
一个列表，在用户不将其打开的情况下，该表仅显示第一项。

## <a name="description"></a>说明
“下拉列表”控件可以节省屏幕的实际空间，尤其是在列表包含大量选项时。 此控件仅占用一行空间，除非用户选择箭头符号来显示更多选项。  该控件最多显示 500 项。

## <a name="key-properties"></a>关键属性
[Default](properties-core.md) – 用户指定不同值之前控件的初始值。

[Items](properties-core.md) – 包含控件中显示的项的数据源。 如果源具有多列，请将控件的 Value属性设置为要显示的数据列。
  
Value - 要在控件中显示的数据列（例如，如果数据源具有多列）。

**Selected** - 表示选定项的数据记录。

**AllowEmptySelection** –如果未选择任何项，控件是否显示空选择。 应用用户还可以通过选择空白项来清除其选择。

## <a name="additional-properties"></a>其他属性
**[AccessibleLabel](properties-accessibility.md)** – 屏幕阅读器标签。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**ChevronBackground** - 下拉列表中向下箭头的背景色。

**ChevronFill** - 下拉列表中的向下箭头的颜色。

**[Color](properties-color-border.md)** – 控件中文本的颜色。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[DisabledBorderColor](properties-color-border.md)** – 控件的 [DisplayMode](properties-core.md) 属性设置为“Disabled”时，该控件边框的颜色。

**[DisabledColor](properties-color-border.md)** – 控件的 **[DisplayMode](properties-core.md)** 属性设置为 Disabled**Disabled** 时，该控件中的文本颜色。

**[DisabledFill](properties-color-border.md)** – 控件的“DisplayMode” **[Display Mode](properties-core.md)** 属性设置为“Disabled”**Disabled**时，该控件的背景色。

**[Fill](properties-color-border.md)** – 控件的背景色。

**[FocusedBorderColor](properties-color-border.md)** – 当聚焦到控件时，控件的边框颜色。

**[FocusedBorderThickness](properties-color-border.md)** – 当聚焦到控件时，控件的边框粗细。

[Font](properties-text.md) – 文本中所显示的字体系列的名称。

**[FontWeight](properties-text.md)** - 控件中文本的粗细：粗体、半粗体、一般或较细。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[HoverBorderColor](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件边框的颜色。

[HoverColor](properties-color-border.md) – 用户将鼠标指针停留在控件上时，该控件中的文本颜色。

**[HoverFill](properties-color-border.md)** – 用户将鼠标指针停留在控件上时，该控件的背景颜色。

**[Italic](properties-text.md)** – 控件中的文本是否为斜体。

[OnChange](properties-core.md) – 用户更改控件的值（例如，通过调整滑块）时应用的响应方式。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

[PaddingBottom](properties-size-location.md) – 控件中的文本与该控件的下边缘之间的距离。

[PaddingLeft](properties-size-location.md) – 控件中的文本与该控件的左边缘之间的距离。

[PaddingRight](properties-size-location.md) – 控件中的文本与该控件的右边缘之间的距离。

[PaddingTop](properties-size-location.md) – 控件中的文本与该控件的上边缘之间的距离。

**[PressedBorderColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件边框的颜色。

**[PressedColor](properties-color-border.md)** – 用户在点击或单击控件时，该控件中的文本的颜色。

**[PressedFill](properties-color-border.md)** – 用户在点击或单击控件时，该控件的背景色。

[Reset](properties-core.md) – 是否还原控件的默认值。

**SelectedText (Deprecated)** - 表示选定项的字符串值。

[SelectionColor](properties-color-border.md) – 所选项目或列表中项目的文本颜色，或笔控件中选择工具的颜色。

**[SelectionFill](properties-color-border.md)** - 所选项目、列表中项目或笔控件选定区域的背景颜色。

**[Size](properties-text.md)** – 控件上显示的文本的字号。

[Strikethrough](properties-text.md) – 通过文本显示的线是否在控件上显示。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

**[Tooltip](properties-core.md)** – 用户将鼠标悬停在控件上时显示的解释性文本。

[Underline](properties-text.md) – 在文本下方显示的线是否在控件上显示。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="example"></a>示例

### <a name="simple-list"></a>简单列表

1. 添加“下拉列表”控件，然后将其[Items](properties-core.md) 属性设置为该表达式：

    `["Seattle", "Tokyo", "London", "Johannesburg", "Rio de Janeiro"]`

    不知道如何[添加、命名和配置控件](../add-configure-controls.md)？

1. 在按 Alt 键的同时选择控件的向下箭头，以便显示列表中的项目。

### <a name="list-from-a-data-source"></a>来自数据源的列表
此过程中的原则适用于任何[提供表的数据源](../connections-list.md#tables)，但若要完全遵循这些步骤，您必须打开为其创建 Common Data Service 数据库和添加示例数据的环境。

1. [打开空白应用](../data-platform-create-app-scratch.md#open-a-blank-app)，然后[指定 Accounts实体](../data-platform-create-app-scratch.md#specify-an-entity)。

1. 添加“下拉列表”控件，然后将其[Items](properties-core.md) 属性设置为以下公式：

    `Distinct(Accounts, address1_city)`

    此公式显示 Accounts 实体中的所有城市。 如果多个记录具有相同的城市，则[Distinct](../functions/function-distinct.md) 功能会在你的下拉控件中隐藏重复项。

1. （可选）将你的“下拉列表”控件重命名为 Cities，添加垂直“库”控件，并将库的[Items](properties-core.md) 属性设置为这个公式：

    `Filter(Accounts, address1_city = Cities.Selected.Value)`

    此[Filter](../functions/function-filter-lookup.md) 功能仅显示 Accounts 实体中的城市与“城市”控件中所选值匹配的记录。

## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="color-contrast"></a>颜色对比度
在以下项之间必须有足够的颜色对比度：
* ChevronFill 和 ChevronBackground
* ChevronHoverFill 和 ChevronHoverBackground
* SelectionColor 和 SelectionFill
* SelectionFill 和 **[Fill](properties-color-border.md)**

这是除[标准颜色对比度](../accessible-apps-color.md)以外的要求。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* [“AccessibleLabel”](properties-accessibility.md)必须存在。

### <a name="keyboard-support"></a>键盘支持
* **[“TabIndex”](properties-accessibility.md)** 必须为零或更大，以便键盘用户可以导航到它。
* 焦点指示器必须清晰可见。 可以使用 **[“FocusedBorderColor”](properties-color-border.md)** 和 **[“FocusedBorderThickness”](properties-color-border.md)** 来实现此目的。
