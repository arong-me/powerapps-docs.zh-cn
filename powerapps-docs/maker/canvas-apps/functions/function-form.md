---
title: EditForm、NewForm、SubmitForm、ResetForm 和 ViewForm 函数 | Microsoft 文档
description: PowerApps 中 EditForm、NewForm、SubmitForm、ResetForm 和 ViewForm 函数的引用信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/06/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 930439325b60b60fefed18b66c22d9d4f97f55b7
ms.sourcegitcommit: 4db9c763455d141a7e1dd569a50c86bd9e50ebf0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2019
ms.locfileid: "57802092"
---
# <a name="editform-newform-submitform-resetform-and-viewform-functions-in-powerapps"></a>PowerApps 中的 EditForm、NewForm、SubmitForm、ResetForm 和 ViewForm 函数
查看、编辑或创建一个项，保存内容，以及在[编辑表单](../controls/control-form-detail.md)控件中重置控件。

## <a name="overview"></a>概述
这些函数将更改“编辑表单”控件的状态。  表单控件可以采用以下模式之一：

| 模式 | 描述 |
| --- | --- |
| FormMode.Edit |表单使用现有记录填充，用户可以修改字段的值。  完成后，用户可以将更改保存到记录中。 |
| FormMode.New |表单使用默认值填充，用户可以修改字段的值。  完成后，用户可以将记录添加到数据源。 |
| FormMode.View |表单使用现有记录填充，但用户无法修改字段的值。 |

## <a name="description"></a>说明
这些函数通常从 **[按钮](../controls/control-button.md)** 或 **[图像](../controls/control-image.md)** 控件的 **[OnSelect](../controls/properties-core.md)** 公式中调用，以便用户可以保存编辑、放弃编辑或创建记录。 可通过[将控件和这些函数结合使用](../working-with-forms.md)来创建完整的解决方案。

这些函数不返回任何值。

### <a name="submitform"></a>SubmitForm
在按钮控件的 **[OnSelect](../controls/properties-core.md)** 属性中使用 **SubmitForm** 函数可将窗体控件中的任何更改保存到数据源。

提交任何更改之前，针对被标记为必需或其值有一个或多个约束的字段，此函数会检查验证问题。 此行为与 **[Validate](function-validate.md)** 函数类似。

**SubmitForm** 还会检查窗体的 **[Valid](../controls/control-form-detail.md)** 属性，这包括窗体控件所包含的 **[卡片](../controls/control-card.md)** 控件的所有 **[Valid](../controls/control-card.md)** 属性。 如果出现问题，数据将不会提交，并且窗体控件的 **[Error](../controls/control-form-detail.md)** 和 **[ErrorKind](../controls/control-form-detail.md)** 属性会进行相应的设置。

如果通过验证，**SubmitForm** 会将更改提交到数据源。

* 若成功提交，将运行窗体的 **[OnSuccess](../controls/control-form-detail.md)** 行为，并清除 **[Error](../controls/control-form-detail.md)** 和 **[ErrorKind](../controls/control-form-detail.md)** 属性。  如果窗体之前处于 **FormMode.New** 模式下，则窗体将返回 **FormMode.Edit** 模式。
* 若提交失败，将运行窗体的 **[OnFailure](../controls/control-form-detail.md)** 行为，并且 **[Error](../controls/control-form-detail.md)** 和 **[ErrorKind](../controls/control-form-detail.md)** 属性会进行相应设置。  窗体的模式保持不变。  

### <a name="editform"></a>EditForm
**EditForm** 函数将窗体控件的模式更改为 **FormMode.Edit**。 在此模式下，将使用窗体控件的 **[Item](../controls/control-form-detail.md)** 属性的内容来填充窗体。  如果在窗体处于此模式下时运行 **SubmitForm** 函数，则将更改（而非创建）记录。  **FormMode.Edit** 是窗体控件的默认模式。

### <a name="newform"></a>NewForm
**NewForm** 函数将窗体控件的模式更改为 **FormMode.New**。 在此模式下，窗体控件的 **[Item](../controls/control-form-detail.md)** 属性的内容会被忽略，而使用窗体的 **[DataSource](../controls/control-form-detail.md)** 属性的默认值来填充窗体。 如果在窗体处于此模式下时运行 **SubmitForm** 函数，则将创建（而非更改）记录。

### <a name="resetform"></a>ResetForm
**ResetForm** 函数将窗体的内容重置为其初始值，即用户进行任何更改之前的值。 如果窗体处于 **FormMode.New** 模式下，则窗体将重置为 **FormMode.Edit** 模式。 还将运行窗体控件的 **[OnReset](../controls/control-form-detail.md)** 行为。  还可以使用 [Reset](function-reset.md) 函数重置各个控件，但仅可以从表单内进行重置。

### <a name="viewform"></a>ViewForm
ViewForm 函数将表单控件的模式更改为 FormMode.View。 在此模式下，将使用窗体控件的 **[Item](../controls/control-form-detail.md)** 属性的内容来填充窗体。  **SubmitForm**并**ResetForm**函数具有在此模式下时不起作用。

### <a name="displaymode-property"></a>DisplayMode 属性
可通过 Mode 属性读取当前模式。  该模式还可以确定 DisplayMode 属性的值，数据卡和控件可在表单控件中使用该属性。  通常情况下，数据卡的**DisplayMode**属性将设置为**Parent.DisplayMode** （引用表单） 也将控件的**DisplayMode** （引用属性数据卡）： 

| 模式 | DisplayMode | 描述 |
| --- | --- | --- |
| FormMode.Edit |DisplayMode.Edit |数据卡和控件是可编辑的，可以接受对记录的更改。 |
| FormMode.New |DisplayMode.Edit |数据卡和控件是可编辑的，可以接受对新记录的更改。 |
| FormMode.View |DisplayMode.View |数据卡和控件不可出于查看目的进行编辑和优化。 |

## <a name="syntax"></a>语法
**SubmitForm**( *FormName* )

* *FormName* - 必需。 要提交到数据源的窗体控件。

**EditForm**( *FormName* )

* *FormName* - 必需。  要切换到 **FormMode.Edit** 模式的窗体控件。

**NewForm**( *FormName* )

* *FormName* - 必需。 要切换到 **FormMode.New** 模式的窗体控件。

**ResetForm**( *FormName* )

* *FormName* - 必需。 要重置为初始值的窗体控件。 还会将窗体从 **FormMode.New** 模式切换到 **FormMode.Edit** 模式。

ViewForm( FormName )

* *FormName* - 必需。  要切换到 FormMode.View 模式的表单控件。

## <a name="examples"></a>示例
请参阅[了解数据窗体](../working-with-forms.md)获取完整示例。

1. 添加一个按钮控件，将其 **[Text](../controls/properties-core.md)** 属性设置为显示“保存”，并将其 **[OnSelect](../controls/properties-core.md)** 属性设置为以下公式：
   
    **SubmitForm( EditForm )**
2. 将窗体控件的 **[OnFailure](../controls/control-form-detail.md)** 属性设置为空白，将其 **[OnSuccess](../controls/control-form-detail.md)** 属性设置为以下公式：
   
    **Back()**
3. 将“[标签](../controls/control-text-box.md)”控件命名为“ErrorText”，然后将“[Text](../controls/properties-core.md)”属性设置为以下公式：
   
    **EditForm.Error**
   
    用户选择“保存”按钮后，窗体控件中的任何更改都会提交到基础数据源。
   
   * 如果提交成功，则会保存所有更改；或者如果窗体控件处于“新建”模式下，则会创建一条记录。 **ErrorText** 为空白，且上一个屏幕再次出现。
   * 如果提交失败，**ErrorText** 会显示用户友好的错误消息，并且当前屏幕会保持可见，以便用户可以更正问题并重试。
4. 添加一个按钮控件，将其 **[Text](../controls/properties-core.md)** 属性设置为显示“取消”，并将其 **[OnSelect](../controls/properties-core.md)** 属性设置为以下公式：
   
    **ResetForm( EditForm ); Back()**
   
    用户选择“取消”按钮后，窗体控件中的值会被重置为用户对其进行编辑之前的值，上一个屏幕将再次出现，并且如果窗体控件之前处于“新建”模式下，则它将返回“编辑”模式。
5. 添加一个按钮控件，将其 **[Text](../controls/properties-core.md)** 属性设置为显示“新建”，并将其 **[OnSelect](../controls/properties-core.md)** 属性设置为以下公式：
   
    **NewForm( EditForm ); Navigate( EditScreen, None )**
   
    用户选择“新建”按钮后，窗体控件将切换到“新建”模式，窗体控件数据源的默认值将填充该控件，并出现包含该窗体控件的屏幕。 **SubmitForm** 函数运行时，将创建（而非更新）记录。

