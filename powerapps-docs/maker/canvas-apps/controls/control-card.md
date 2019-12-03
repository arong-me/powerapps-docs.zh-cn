---
title: 卡片控件：参考 | Microsoft 文档
description: 有关卡片控件的信息，包括属性和示例
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 10/25/2016
ms.author: gregli
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7f0d4268700b8c46a15fe74da4a4825395dcfe5b
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74722937"
---
# <a name="card-control-in-power-apps"></a>Power Apps 中的卡片控件
提供 **[显示窗体](control-form-detail.md)** 或 **[编辑窗体](control-form-detail.md)** 控件的单个字段的显示和编辑体验。

## <a name="description"></a>描述
**[显示窗体](control-form-detail.md)** 和 **[编辑窗体](control-form-detail.md)** 控件充当用于显示和查看完整记录的容器。 每个容器可以容纳一组 **卡片** 控件，这些控件显示各个字段或提供更新这些字段的方法。 每种卡片均有一个 **DataField** 属性，此属性指定它所适用的记录字段。  

预定义卡片针对不同的数据类型和用户体验定义。  例如，可能存在使用 **[文本输入](control-text-input.md)** 控件编辑数字字段的卡片，非常适合与键盘结合使用。 而另一种卡片可能支持使用 **[滑块](control-slider.md)** 控件编辑数字。 选择窗体控件后，可以在右侧窗格中基于字段轻松选择卡片。

卡片本身包含控件。 卡片的控件构成了显示和编辑单个字段的体验。 例如，数字卡片可能包含显示字段的显示名称的“[标签](control-text-box.md)”控件，以及提供字段值编辑器的“[文本输入](control-text-input.md)”控件。 卡片可能还包含显示所有验证错误的“[标签](control-text-box.md)”控件，以及使用常见星号指明字段为必填字段的“[标签](control-text-box.md)”控件。

可以通过以下方式自定义预定义卡片的控件：调整大小、移动、隐藏、向其添加控件及进行其他更改。 还可以使用完全空白的卡片（即“自定义卡片”），从头开始向其添加控件。

默认情况下，预定义卡片处于“锁定”状态。 在锁定的卡片中，只能修改卡片的某些属性或卡片内的控件，且无法删除锁定的卡片。 可在“高级”视图的“视图”选项卡中显示卡片锁定并解锁。 如果属性锁定且无法修改，在其名称旁将显示一个锁定图标。 解锁卡片属于高级活动，需谨慎处理，因为卡片将不再自动生成公式，且无法再次锁定卡片。

在窗体的容器内，**ThisItem** 记录可用且包含该记录的所有字段。  例如，卡片的 **[Default](properties-core.md)** 属性通常设置为 **ThisItem**。FieldName。

可以使用**父**引用配置控件以引用卡片的属性。  例如，控件应使用 **Parent.Default** 从数据源读取字段的初始状态。 通过使用**父**引用（而不是直接访问所需信息），可更好地封装卡片，且可以将其更改为不同的字段而不会破坏内部公式。

有关如何自定义、解锁和创建卡片的示例，请参阅[了解数据卡](../working-with-cards.md)。

## <a name="key-properties"></a>关键属性
**DataField** - 此卡片显示和编辑的记录中的字段名称。

* 指定该名称为括在双引号中的单个静态字符串（例如，“Name”），而非公式。
* 通过将卡片的 **DataField** 属性设置为空白，取消绑定卡片。 未绑定卡片将忽略 **Valid** 和 **Update** 属性。

**[Default](properties-core.md)** - 用户更改控件前的初始值。

* 对于卡片中的每个控件，将此属性设置为 **Parent.Default** 以根据数据源引用字段的默认值。 例如，将滑块的 **[Default](properties-core.md)** 属性设置为 **Parent.Default** 以确保用户首先使用该滑块的泛型值。

**DisplayMode** – 值可以是 Edit、View 或 Disabled。 配置卡内控件是允许用户输入 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。  

* 通过配置此属性，可在编辑和查看表单中使用单个卡，该属性默认与表单行为相关联。
* 在 View 模式时，子控件（如[文本输入](control-text-input.md)、[下拉列表](control-drop-down.md)、[日期选取器](control-date-picker.md)）将仅显示文本值，不会呈现任何交互元素或修饰。

**DisplayName** - 数据源中字段的用户友好名称。

* **[DataSourceInfo](../functions/function-datasourceinfo.md)** 函数提供数据源中的元数据。
* 卡片内的控件应使用 **Parent.DisplayName** 来引用字段的名称。

**Error** - 验证失败时，针对该字段显示的用户友好错误消息。

* 调用 **SubmitForm** 时已设置此属性。  
* 该消息根据数据源的元数据和检查卡片的**必需**属性描述验证问题。

**必需** - 无论是否存在卡片，编辑数据源的字段必须包含值。

* **[DataSourceInfo](../functions/function-datasourceinfo.md)** 函数可提供数据源中的必需元数据。
* 卡片内的控件应使用 **Parent.Required** 来确定该卡片的字段是否必需。

**Update** - 回写到字段的数据源的值。

* 使用此属性的公式从卡片的编辑控件中请求值，以回写到数据源。 例如，将卡片的 **Update** 属性设为 **Slider.Value**，使用该卡片中的滑块的值更新数据源。

[Width](properties-size-location.md) – 控件左边缘和右边缘之间的距离。

**[WidthFit](properties-size-location.md)** - 控件是否会自动水平变宽，以填充容器控件（如“[编辑表单](control-form-detail.md)”控件）的所有空白空间。 如果多张数据卡将此属性设置为“true”，那么空白空间会被这些数据卡均分。 有关详细信息，请参阅[了解数据表单布局](../working-with-form-layout.md)。

## <a name="additional-properties"></a>其他属性
[BorderColor](properties-color-border.md) – 控件边框的颜色。

**[BorderStyle](properties-color-border.md)** – 控件边框是“实线”、“虚线”、“点线”还是“无”。

**[BorderThickness](properties-color-border.md)** – 控件边框的粗细。

**[Fill](properties-color-border.md)** – 控件的背景颜色。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**Valid** - **卡片** 或 **[编辑窗体](control-form-detail.md)** 控件是否包含准备好提交到数据源的有效项。

**[Visible](properties-core.md)** – 控件显示还是隐藏。

**[X](properties-size-location.md)** - 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。 对于多列容器中的“[数据卡](control-card.md)”控件，此属性将确定数据卡出现在哪一列。

**[Y](properties-size-location.md)** - 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。 对于多行容器中的“[数据卡](control-card.md)”控件，此属性将确定数据卡出现在哪一行。

## <a name="examples"></a>示例
有关示例，请参阅[了解数据卡](../working-with-cards.md)和[了解数据表单布局](../working-with-form-layout.md)。


## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="color-contrast"></a>颜色对比度
在以下项之间必须有足够的颜色对比度：
* **[Fill](properties-color-border.md)** 和任何子控件。 例如，如果卡片包含 **[标签](control-text-box.md)** ，而标签具有透明填充，则卡片的 **[Fill](properties-color-border.md)** 将有效地成为标签的背景色。 因此，卡片的 **[“Fill”](properties-color-border.md)** 和标签的 **[“Color”](properties-color-border.md)** 之间应具有足够的对比度。

### <a name="screen-reader-support"></a>屏幕阅读器支持
* “DisplayName”必须存在。
