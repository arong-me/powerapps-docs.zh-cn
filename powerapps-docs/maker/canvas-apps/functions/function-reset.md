---
title: Reset 函数 | Microsoft 文档
description: Power Apps 中 Reset 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 07/06/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 20109be5e9c77af75409973a32fe46c353d57282
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730315"
---
# <a name="reset-function-in-power-apps"></a>Power Apps 中的 Reset 函数
将控件重置为默认值，放弃任何用户更改。  

## <a name="description"></a>描述
**Reset** 函数将控件重置为其 **Default** 属性值。  将放弃任何用户更改。

不能从[**库**](../controls/control-gallery.md)或[**编辑表单**](../controls/control-form-detail.md)控件外部重置这些控件内部的控件。  可以在同一个库或表单中的控件上，通过公式重置控件。  也可以使用 [**ResetForm**](function-form.md) 函数重置表单中的所有控件。 

使用 **Reset** 函数可用于替换切换输入控件的 **Reset** 属性，并且通常首选此方法。  需要从多个公式同时重置许多控件时，**Reset** 属性可能是更好的选择。  可以使用 **Reset = Button.Pressed** 公式通过[**按钮**](../controls/control-button.md)控件，或通过变量（使用 **Reset = MyVar** 并使用 **Button.OnSelect = Set( MyVar, true ); Set( MyVar, false )** 公式切换 **MyVar**），完成切换 **Reset** 属性。    

输入控件的 **Default** 属性更改时，输入控件也将重置。

**Reset** 没有返回值，只可以在[行为公式](../working-with-formulas-in-depth.md)中使用它。

## <a name="syntax"></a>语法
**Reset**( *Control* )

* *Control* – 必需。 要重置的控件。

## <a name="example"></a>示例
1. 在屏幕上插入“文本输入”控件。  默认情况下，其名称为 **TextInput1**，且其 **Default** 属性将设置为 **"Text input"** 。
2. 在文本框中键入新值。  
3. 在屏幕上插入“按钮”控件。
4. 将该按钮的 **OnSelect** 属性设置为 **Reset( TextInput1 )** 。
5. 选择此按钮。  即使选择在控件的末尾进行创作，也可以执行此操作。
6. 文本框的内容将返回到 **Default** 属性的值。

