---
title: 组合框控件：参考 | Microsoft 文档
description: 了解组合框控件（包括属性和示例）
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 09/13/2017
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e6d1b1083fcc7e865fa7c9cfe3f8966e20ed86a5
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61552034"
---
# <a name="combo-box-control-in-powerapps"></a>PowerApps 中的组合框控件
用户可以在其中提供的选项之间进行选择的控件。  支持搜索和多重选择。

## <a name="description"></a>描述
使用组合框控件，可以搜索要选择的项。  由于搜索是在服务器端对 SearchField 属性执行，因此性能不受非常大的数据源影响。  

单选或多重选择模式是通过 SelectMultiple 属性进行配置。

搜索要选择的项时，可以对所有项修改“数据”窗格中的“布局”设置，选择是显示一个数据值、两个数据值，还是一张图片和两个值（“人员”模板）。

## <a name="people-picker"></a>人员选取器
若要将组合框用作人员选取器，请从“数据”窗格的“布局”设置中选择“人员”模板，并配置要显示的如下人员相关数据属性。

## <a name="key-properties"></a>关键属性
**[Items](properties-core.md)** - 提供待选选项的数据源。

**DefaultSelectedItems** – 的初始选定项之前在用户与控件交互。

**SelectedItems** - 用户交互后的选定项列表。

**SelectMultiple** - 用户是能选择一个项，还是能选择多个项。

**IsSearchable** - 用户能否在选择前先搜索项。

**SearchFields** - 用户输入文本时，所搜索的数据源的数据字段。  若要搜索多个字段，可设置 ComboBox1.SearchFields = ["MyFirstColumn", "MySecondColumn"]

## <a name="additional-properties"></a>其他属性
**[AccessibleLabel](properties-accessibility.md)** – 屏幕阅读器标签。

**[BorderColor](properties-color-border.md)** – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**DisplayFields** - 针对搜索返回的每个项显示的字段列表。  通过“属性选项”选项卡中的“数据”窗格进行配置最为简单。

**[DisplayMode](properties-core.md)** – 此控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[FocusedBorderColor](properties-color-border.md)** – 当聚焦到控件时，控件的边框颜色。

**[FocusedBorderThickness](properties-color-border.md)** – 当聚焦到控件时，控件的边框粗细。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**InputTextPlaceholder** - 在用户未选中项时向最终用户显示的说明文字。

**OnChange** - 在用户更改选项时，应用如何响应。

**OnNavigate** - 在用户单击项时，应用如何响应。

**[OnSelect](properties-core.md)** – 用户点击或单击某个控件时应用响应的方式。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

**[X](properties-size-location.md)** – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

**[Y](properties-size-location.md)** – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。

## <a name="example"></a>示例
1. 上**插入**选项卡上，打开**控件**菜单，并选择**组合框**。  

1. 上**属性**选项卡的右侧窗格中，打开**选择数据源**列表 (下一步**项**)，然后添加或选择数据源。

1. 在同一选项卡上，选择**编辑**(下一步**字段**)。

1. 在中**数据**窗格中，打开**主要文本**列表，并选择你想要在中显示的列**组合框**控件。

1. 在按住 Alt 键，选择向下箭头以打开**组合框**控件。

    此控件显示在你指定数据源中的列中的数据。
    
1. （可选）若要显示的第一个记录，默认情况下，设置**DefaultSelectedItems**属性设置为此表达式中，替换*数据源*与数据源的名称：

    `First(DataSource)`

## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="color-contrast"></a>颜色对比度
在以下项之间必须有足够的颜色对比度：
* ChevronFill 和 ChevronBackground
* ChevronHoverFill 和 ChevronHoverBackground
* SelectionColor 和 SelectionFill
* SelectionFill 和 **[Fill](properties-color-border.md)**
* SelectionTagColor 和 SelectionTagFill

这是除[标准颜色对比度](../accessible-apps-color.md)以外的要求。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* **[“AccessibleLabel”](properties-accessibility.md)** 必须存在。

    > [!NOTE]
  > 在触摸屏上，屏幕阅读器用户可以按顺序导航组合框中的内容。 组合框充当一个按钮，在选中时会显示或隐藏其内容。

### <a name="keyboard-support"></a>键盘支持
* **[“TabIndex”](properties-accessibility.md)** 必须为零或更大，以便键盘用户可以导航到它。
* 焦点指示器必须清晰可见。 可以使用 **[“FocusedBorderColor”](properties-color-border.md)** 和 **[“FocusedBorderThickness](properties-color-border.md)**”来实现此目的。

    > [!NOTE]
  > Tab 键可导航到组合框或离开组合框。 箭头键可导航组合框中的内容。 Esc 键在打开时会关闭下拉列表。
