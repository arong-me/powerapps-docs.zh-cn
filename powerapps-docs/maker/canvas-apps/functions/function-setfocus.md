---
title: SetFocus 函数 |Microsoft Docs
description: PowerApps 中 SetFocus 函数的参考信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/23/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: cdf34c3c4909697b70a105e5145620ab5bd31ea9
ms.sourcegitcommit: 5899d37e38ed7111d5a9d9f3561449782702a5e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71038158"
---
# <a name="setfocus-function-in-powerapps"></a>PowerApps 中的 SetFocus 函数
将输入焦点移到特定控件。 

## <a name="description"></a>描述
**SetFocus**函数为控件提供输入焦点。  然后，该控件会接收用户的击键，使其可以键入文本输入控件，或使用*Enter*键选择一个按钮。  用户还可以使用*Tab*键、触摸、鼠标或其他笔势来移动输入焦点。 *Tab*键行为由[ **TabIndex**属性](../controls/properties-accessibility.md)控制。

使用**SetFocus**函数设置焦点（每个都有以下示例）：
- 新公开的或已启用的输入控件，以指导用户进入下一步和更快速地输入数据。
- 将对窗体进行验证，使其集中并显示有问题的输入控件以快速解决问题。
- 屏幕将显示，以便将第一个输入控件与[**屏幕**](../controls/control-screen.md)的**OnVisible**属性集中在一起。

具有焦点的控件可能会根据[**FocusedBorderColor**](../controls/properties-color-border.md)和[**FocusedBorderThickness**](../controls/properties-color-border.md)属性在视觉上有所不同。

## <a name="limitations"></a>限制

**SetFocus**只能与一起使用：
- [**Button**](../controls/control-button.md)控件
- [**Icon**](../controls/control-shapes-icons.md)控件
- [**图像**](../controls/control-image.md)控件
- “[**标签**](../controls/control-text-box.md)”控件
- [**TextInput**](../controls/control-text-input.md)控件

不能将焦点设置到[**库**](../controls/control-gallery.md)控件、[**编辑窗体**](../controls/control-form-detail.md)控件或[组件](../create-component.md)中的控件。  **SetFocus**可用于 scrollbale 屏幕中的控件。

您只能将焦点设置为与包含**SetFocus**调用的公式位于同一屏幕上的控件。

尝试将焦点设置到其[**DisplayMode**](../controls/properties-core.md)属性设置为 " **Disabled** " 的控件不起作用。  焦点将保留在以前的位置。

在 Apple iOS 上，只有通过直接用户操作启动了**SetFocus** ，才能自动显示软键盘。  例如，从按钮的**OnSelect**属性调用将显示软键盘，而从屏幕的**OnVisible**调用将不会显示。 

只能在[行为公式](../working-with-formulas-in-depth.md)中使用**SetFocus** 。

## <a name="syntax"></a>语法
**SetFocus**（*控制*）

* *Control* – 必需。  用于给输入焦点的控件。

## <a name="examples"></a>示例

### <a name="focus-on-a-newly-exposed-or-enabled-input-control"></a>专注于新公开或启用的输入控件

许多购物车允许客户使用寄送地址作为计费地址，因而不需要输入相同的信息两次。  如果需要不同的帐单地址，则会启用计费地址文本输入框，并向客户提供这些新启用的控件，以便更快地输入数据。  

![选择使用自定义帐单地址的动画，并将焦点移到计费名称输入控件作为结果，关闭与装运地址的自动同步](media/function-setfocus/shipping-billing.gif)

这里有许多可供播放的公式，但移动焦点的公式位于**复选框**控件的**OnUncheck**属性中：

```powerappa-dot
SetFocus( BillingName ) 
```

*Tab*键还可用于从一个字段快速移动到另一个字段。  为了更好地说明，动画中未使用*Tab*键。

若要创建此示例：
1. 创建新的应用。
1. 添加带有文本 "发货地址"、"名称："、"地址："、"计费地址"、"名称：" 和 "Address：" 的[**标签**控件](../controls/control-text-box.md)，并将其放置在动画中。
1. 添加 " [**文本输入**" 控件](../controls/control-text-input.md)并将其重命名为**ShippingName**。
1. 添加 " [**文本输入**" 控件](../controls/control-text-input.md)并将其重命名为**ShippingAddress**。
1. 添加一个[**复选框**控件](../controls/control-check-box.md)，并将其重命名为**SyncAddresses**。
1. 将此控件的 " **Text** " 属性设置为`"Use Shipping address as Billing address"`公式。
1. 添加 " [**文本输入**" 控件](../controls/control-text-input.md)并将其重命名为**BillingName**。
1. 将此控件的**默认**属性设置为公式`ShippingName`。
1. 将此控件的**DisplayMode**属性设置为公式`If( SyncAddresses.Value, DisplayMode.View, DisplayMode.Edit )`。  这会根据复选框控件的状态自动启用或禁用此控件。
1. 添加 " [**文本输入**" 控件](../controls/control-text-input.md)并将其重命名为**BillingAddress**。
1. 将此控件的**默认**属性设置为公式`ShippingAddress`。
1. 将此控件的**DisplayMode**属性设置为公式`If( SyncAddresses.Value, DisplayMode.View, DisplayMode.Edit )`。  这会根据复选框控件的状态自动启用或禁用此控件。
1. 将复选框的 "**默认**属性" 设置为 " `true`公式"。  这将默认计费地址使用与送货地址相同的值。
1. 将复选框的 " **OnCheck** " 属性设置为公式`Reset( BillingName ); Reset( BillingAddress )`。  如果用户选择同步发货和帐单地址，这将清除 "计费地址" 字段中的任何用户输入，以允许每个字段的**默认**属性从相应的 "发货地址" 字段中提取值。
1. 将复选框的 " **OnUncheck** " 属性设置为公式`SetFocus( BillingName )`。  如果用户选择具有不同的帐单地址，则会将焦点移到计费地址中的第一个控件。  由于控件的**DisplayMode**属性的原因，这些控件将处于启用状态。

### <a name="focus-on-validation-issues"></a>专注于验证问题

> [!NOTE]
> 尽管此示例显示为 "**编辑窗体**" 控件，但该控件目前尚不支持**SetFocus** 。  相反，此示例使用可滚动屏幕来承载输入控件。

当验证窗体时，如果出现问题，但同时又使用户转到出现问题的字段时，不仅可以显示消息，这会很有用。  如果相关字段滚动到屏幕之外，则可能特别有用。

![验证数据输入窗体并不仅显示消息，还会将输入焦点设置为有问题的输入控件（即使它在屏幕上滚动）的动画。](media/function-setfocus/scrollable-screen.gif)

在此动画中，将重复按 "验证" 按钮，直到正确填写所有字段。  请注意，鼠标指针不会从屏幕顶部向下移动。   而**SetFocus**函数已将输入焦点移到需要注意此公式的控件中：

```powerapps-dot
If( IsBlank( Name ), 
        Notify( "Name requires a value", Error ); SetFocus( Name ),
    IsBlank( Street1 ), 
        Notify( "Street Address 1 requires a value", Error ); SetFocus( Street1 ),
    IsBlank( Street2 ), 
        Notify( "Street Address 2 requires a value", Error ); SetFocus( Street2 ),
    IsBlank( City ), 
        Notify( "City requires a value", Error ); SetFocus( City ),
    IsBlank( County ), 
        Notify( "County requires a value", Error ); SetFocus( County ),
    IsBlank( StateProvince ), 
        Notify( "State or Province requires a value", Error ); SetFocus( StateProvince ),
    IsBlank( PostalCode ), 
        Notify( "Postal Code requires a value", Error ); SetFocus( PostalCode ),
    IsBlank( Phone ), 
        Notify( "Contact Phone requires a value", Error ); SetFocus( Phone ),
    Notify( "Form is Complete", Success )
)
```

若要创建此示例：
1. 创建新的空白手机应用。
1. 在 "**插入**" 菜单中，选择 "**新屏幕**"，然后选择 "可**滚动**"。
1. 在屏幕的中心部分，添加**文本输入**控件，并**将其命名**为**Street1**、 **Street2**、 **City**、**县**、 **StateProvince**、**邮政编码**和**手机**。 在每个控件上方添加**标签**控件以标识字段。  如果分区不够长而无法容纳所有控件，则可能需要调整此部分的大小。
1. 在屏幕顶部的 "可滚动" 部分上方添加复选标记[**图标**控件](../controls/control-shapes-icons.md)。  
1. 将图标控件的 " **OnSelect** " 属性设置为上面`If( IsBlank( ...`给出的公式。

### <a name="focus-when-displaying-a-screen"></a>显示屏幕时的焦点

> [!NOTE]
> 尽管此示例显示为 "**编辑窗体**" 控件，但该控件目前尚不支持 unforutnatley **SetFocus** 。  相反，此示例使用可滚动屏幕来承载输入控件。

类似于公开输入控件，在显示数据输入屏幕时，最好重点关注第一个输入控件以提高数据输入速度。

![显示使用 SetFocus 与不在显示数据输入屏幕时使用的并排比较的动画](media/function-setfocus/visible-setfocus.gif)

在此动画中，左侧的数据输入屏幕未使用**SetFocus**。  当显示 "无输入控件具有焦点" 时，要求用户使用 tab 键、触摸屏、鼠标或使用其他方法将**名称**字段集中在值之前，然后才能在其中键入值。

在右侧，我们的应用程序的 "数据输入" 屏幕的 " **OnVisible** " 属性设置为以下公式：

```powerapps-dot
SetFocus( Name )
```

这会自动将焦点设置到 "**名称**" 字段。  用户可以立即开始在字段之间进行键入和切换，而无需前面的操作。

若要创建此示例：
1. 在上面创建 "关注验证问题" 应用。
1. 在此屏幕上，将 " **OnVisible** " 属性设置`SetFocus( Name )`为公式。
1. 添加第二个屏幕。
1. 添加[**按钮**控件](../controls/control-button.md)。
1. 将此控件的**OnSelect**属性设置为公式`Navigate( Screen1 )`。
1. 从此屏幕预览应用。  按按钮。  将对**OnVisible**公式进行计算，并将 "**名称**" 字段自动置于焦点。
