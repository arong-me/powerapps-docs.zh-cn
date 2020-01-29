---
title: SetProperty 函数 | Microsoft Docs
description: 提供 Power Apps Test Studio 中 SetProperty 函数的参考信息（包括语法）
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/19/2018
ms.author: aheneay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dac65ed25a9e286b056cf3c1408554ca79ea3e11
ms.sourcegitcommit: 6b2961308c41867756ecdd55f55eccbebf70f7f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "76541143"
---
# <a name="setproperty-function-in-power-apps-test-studio"></a>Power Apps Test Studio 的 SetProperty 函数

SetProperty 函数模拟与输入控件的交互，就像用户在控件上输入或设置值一样。 仅当在 Power Apps Test Studio 中编写测试时，此函数才可用。 可以使用 SetProperty 函数设置以下属性。

## <a name="syntax"></a>语法

SetProperty(Control Property, value) 

- Control Property - 必需  。 代表用户进行设置的控件属性。
- *Value* - 必需。 代表用户进行设置的属性值。 

## <a name="examples"></a>示例

| 控制   | 属性  | 示例表达式
| :- | :- | :-
| TextInput | 文本  | ```SetProperty(TextInput1.Text, "Sample text")```
| RichTextEditor    | HtmlText  | ```SetProperty(RichTextEditor1.HtmlText, "<p>Sample text</p>")```
| 切换    | 值 | ```SetProperty(Toggle1.Value, false)```
| 复选框  | 值 | ```SetProperty(Checkbox1.Value, false)```
| 滑块    | 值 | ```SetProperty(Slider1.Value, 10)```
| 评级    | 值 | ```SetProperty(Rating1.Value, 5)```
| DatePicker    | SelectedDate  | ```SetProperty(DatePicker1.SelectedDate, Date(2020,3,10))```
| 单选 | 已选定  | ```SetProperty(Radio1.Selected, "Yes")```
| 单选 | SelectedText | ```SetProperty(Radio1.SelectedText, "Yes")```
| 下拉列表 | 已选定 | ```SetProperty(Dropdown1.Selected, {Value:"Sample value"})```
| 下拉列表 | SelectedText | ```SetProperty(Dropdown1.SelectedText, {Value:"Sample value"})```
| Combobox | 已选定 | ```SetProperty(Dropdown1.Selected, {Value:"Sample value"})```
| Combobox | SelectedItems | ```SetProperty(ComboBox1.SelectedItems, Table({Value:"Sample value"},({Value:"Sample value"}))```
| ListBox | 已选定 | ```SetProperty(Listbox1.Selected, {'Value':"Sample value"})```
| ListBox | SelectedItems | ```SetProperty(Listbox1.SelectedItems, Table({Value:"Sample value"},({Value:"Sample value"}))```

### <a name="see-also"></a>另请参阅

[Test Studio 概述](../test-studio.md) <br>
[使用 Test Studio](../working-with-test-studio.md)