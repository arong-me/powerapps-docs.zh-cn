---
title: Date 和 Time 函数 | Microsoft 文档
description: PowerApps 中 Date 和 Time 函数的引用信息（包括语法和示例）
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 1d6c2485a8f54e0676cee5443085fb962f144831
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="date-and-time-functions-in-powerapps"></a>PowerApps 中的 Date 和 Time 函数
将日期和时间组件转换为日期/时间值。

## <a name="description"></a>说明
**Date** 函数将单个年、月、日的值转换为日期/时间值。  时间部分为午夜。

* 如果“年”介于 0 到 1899（含）之间，则函数将该值加上 1900，以计算年份。  **70** 成为 **1970**。
* 如果“月”小于 1 或大于 12，则结果将从指定年份的第一个月减去或加上该月数。
* 如果“日”大于指定月的天数，函数将从该月的第一天加上该天数，并返回次月对应的日期。  如果“日”小于 1，函数将从指定月份的第一天减去该天数，再加 1。

**Time** 函数将单个小时、分钟和秒的值转换为日期/时间值。  其结果不与日期相关联。

有关如何将字符串转换为值的信息，请参阅 **[DateValue](function-datevalue-timevalue.md)**、**[TimeValue](function-datevalue-timevalue.md)** 和 **[DateTimeValue](function-datevalue-timevalue.md)** 函数。  

有关详细信息，请参阅[处理日期和时间](../show-text-dates-times.md)。

## <a name="syntax"></a>语法
**日期**（年、月、日）

* 年 - 必需。  大于 1899 的数值将被解释为绝对值（1980 被解释为 1980）；介于 0 到 1899 之间的数值将被解释为相对于 1900。 （例如，80 将被解释为 1980。）
* 月 - 必需。  该数值介于 1 到 12 之间。
* 日 - 必需。 该数值介于 1 到 31 之间。

**时间**（小时、分钟、秒）

* 小时 - 必需。  该数值介于 0（上午 12:00）到 23（下午 11:00）之间。
* 分钟 - 必需。 该数值介于 0 到 59 之间。
* 秒 - 必需。 该数值介于 0 到 59 之间。

## <a name="examples"></a>示例
### <a name="date"></a>Date
如果用户在“HireYear”文本输入控件中键入“1979”，在“HireMonth”文本输入控件中键入“3”，在“HireDay”文本输入控件中键入“17”，那么此函数会返回“3/17/1979”：

**Date(Value(HireYear.Text), Value(HireMonth.Text), Value(HireDay.Text))**

### <a name="time"></a>时间
如果用户在“BirthHour”文本输入控件中键入“14”，在“BirthMinute”文本输入控件中键入“50”，在“BirthSecond”文本输入控件中键入“24”，那么此函数会返回“02:50:24 p”。

**Text(Time(Value(BirthHour.Text), Value(BirthMinute.Text), Value(BirthSecond.Text)), "hh:mm:ss a/p")**

