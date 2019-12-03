---
title: Text 属性 | Microsoft 文档
description: Text、Tooltip 和 HintText 等属性的参考资料
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/25/2016
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e65bbf31ade0d6eda655d5d307dd8af7ea9b024d
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731875"
---
# <a name="text-properties-in-power-apps"></a>Power Apps 中的文本属性
配置控件上显示的文本、工具提示中显示的文本以及当用户键入数据时作为提示显示的文本，并指定其他文本相关特征。

## <a name="text-appearance"></a>文本外观
**Font**：文本中所显示的字体系列的名称。

* 适用于 **[添加图片](control-add-picture.md)** 、 **[按钮](control-button.md)** 、 **[复选框](control-check-box.md)** 、 **[柱形图](control-column-line-chart.md)** 、 **[日期选取器](control-date-picker.md)** 、 **[下拉](control-drop-down.md)** 列表、 **[导出](control-export-import.md)** 、 **[HTML 文本](control-html-text.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[折线图](control-column-line-chart.md)** 、 **[列表框](control-list-box.md)** 、 **[饼图](control-pie-chart.md)** 、 **[单选按钮](control-radio.md)** 、 **[文本输入](control-text-input.md)** 和 **[计时器](control-timer.md)** 控件。

**FontWeight**：控件中文本的粗细：“粗体”、“半粗体”、“正常”或“细体”。

* 适用于 **[添加图片](control-add-picture.md)** 、 **[按钮](control-button.md)** 、 **[复选框](control-check-box.md)** 、 **[日期选取器](control-date-picker.md)** 、 **[下拉列表](control-drop-down.md)** 、 **[导出](control-export-import.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[列表框](control-list-box.md)** 、 **[单选按钮](control-radio.md)** 、 **[文本输入](control-text-input.md)** 和 **[计时器](control-timer.md)** 控件。

**Italic**：控件中的文本是否为斜体。

* 适用于 **[添加图片](control-add-picture.md)** 、 **[按钮](control-button.md)** 、 **[复选框](control-check-box.md)** 、 **[日期选取器](control-date-picker.md)** 、 **[下拉列表](control-drop-down.md)** 、 **[导出](control-export-import.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[列表框](control-list-box.md)** 、 **[单选按钮](control-radio.md)** 、 **[文本输入](control-text-input.md)** 和 **[计时器](control-timer.md)** 控件。

**Size**：控件上显示的文本的字号。

* 适用于 **[添加图片](control-add-picture.md)** 、 **[按钮](control-button.md)** 、 **[复选框](control-check-box.md)** 、 **[柱形图](control-column-line-chart.md)** 、 **[日期选取器](control-date-picker.md)** 、 **[下拉](control-drop-down.md)** 列表、 **[导出](control-export-import.md)** 、 **[HTML 文本](control-html-text.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[折线图](control-column-line-chart.md)** 、 **[列表框](control-list-box.md)** 、 **[笔输入](control-pen-input.md)** 、 **[饼图](control-pie-chart.md)** 、 **[单选按钮](control-radio.md)** 、 **[文本输入](control-text-input.md)** 和 **[计时器](control-timer.md)** 控件。

**Strikethrough**：贯穿文本的线是否在控件上显示。

* 适用于 **[添加图片](control-add-picture.md)** 、 **[按钮](control-button.md)** 、 **[复选框](control-check-box.md)** 、 **[下拉列表](control-drop-down.md)** 、 **[导出](control-export-import.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[列表框](control-list-box.md)** 、 **[单选按钮](control-radio.md)** 、 **[文本输入](control-text-input.md)** 和 **[计时器](control-timer.md)** 控件。

**Underline**：在文本下方显示的线是否在控件上显示。

* 适用于 **[添加图片](control-add-picture.md)** 、 **[按钮](control-button.md)** 、 **[复选框](control-check-box.md)** 、 **[下拉列表](control-drop-down.md)** 、 **[导出](control-export-import.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[列表框](control-list-box.md)** 、 **[单选按钮](control-radio.md)** 、 **[文本输入](control-text-input.md)** 和 **[计时器](control-timer.md)** 控件。

## <a name="text-placement"></a>文本放置
**Align**：文本相对于其控件的水平居中的位置。

* 适用于 **[添加图片](control-add-picture.md)** 、 **[按钮](control-button.md)** 、 **[导出](control-export-import.md)** 、 **[导入](control-export-import.md)** 、 **[标签](control-text-box.md)** 、 **[单选按钮](control-radio.md)** 、 **[文本输入](control-text-input.md)** 和 **[计时器](control-timer.md)** 控件。

**LineHeight**：诸如文本行之间或列表中项之间的距离。

* 适用于 **[列表框](control-list-box.md)** 、 **[标签](control-text-box.md)** 、 **[单选按钮](control-radio.md)** 和 **[文本输入](control-text-input.md)** 控件。

**VerticalAlign**：控件上的文本相对于该控件垂直居中的位置。

* 适用于 **[添加图片](control-add-picture.md)** 、 **[按钮](control-button.md)** 、 **[复选框](control-check-box.md)** 、 **[导出](control-export-import.md)** 、 **[导入](control-export-import.md)** 和 **[标签](control-text-box.md)** 控件。

