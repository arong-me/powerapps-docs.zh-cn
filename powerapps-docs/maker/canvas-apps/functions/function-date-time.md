---
title: Date 和 Time 函数 | Microsoft 文档
description: PowerApps 中 Date 和 Time 函数的引用信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 869c0fcff6e519281e527c832305d74f2e7fd78f
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551229"
---
# <a name="date-and-time-functions-in-powerapps"></a>PowerApps 中的 Date 和 Time 函数
将日期和时间组件转换为日期/时间值。

## <a name="description"></a>描述
**Date** 函数将单个年、月、日的值转换为日期/时间值。  时间部分为午夜。

* 如果“年”介于 0 到 1899（含）之间，则函数将该值加上 1900，以计算年份。  **70** 成为 **1970**。
* 如果“月”小于 1 或大于 12，则结果将从指定年份的第一个月减去或加上该月数。
* 如果“日”大于指定月的天数，函数将从该月的第一天加上该天数，并返回次月对应的日期。  如果“日”小于 1，函数将从指定月份的第一天减去该天数，再加 1。

**Time** 函数将单个小时、分钟和秒的值转换为日期/时间值。  其结果不与日期相关联。

有关如何将字符串转换为值的信息，请参阅 **[DateValue](function-datevalue-timevalue.md)** 、 **[TimeValue](function-datevalue-timevalue.md)** 和 **[DateTimeValue](function-datevalue-timevalue.md)** 函数。  

有关详细信息，请参阅[处理日期和时间](../show-text-dates-times.md)。

## <a name="syntax"></a>语法
**Date**( *Year*, *Month*, *Day* )

* *Year* - 必需。  大于 1899 的数值将被解释为绝对值（1980 被解释为 1980）；介于 0 到 1899 之间的数值将被解释为相对于 1900。 （例如，80 将被解释为 1980。）
* *Month* - 必需。  该数值介于 1 到 12 之间。
* *Day* - 必需。 该数值介于 1 到 31 之间。

**Time**( *Hour*, *Minute*, *Second* )

* *Hour* - 必需。  该数值介于 0（上午 12:00）到 23（下午 11:00）之间。
* *Minute* - 必需。 该数值介于 0 到 59 之间。
* *Second* - 必需。 该数值介于 0 到 59 之间。

## <a name="examples"></a>示例
### <a name="date"></a>Date
如果用户在“HireYear”  文本输入控件中键入“1979”  ，在“HireMonth”  文本输入控件中键入“3”  ，在“HireDay”  文本输入控件中键入“17”  ，那么此函数会返回“3/17/1979”  ：

**Date(Value(HireYear.Text), Value(HireMonth.Text), Value(HireDay.Text))**

### <a name="time"></a>Time
如果用户在“BirthHour”  文本输入控件中键入“14”  ，在“BirthMinute”  文本输入控件中键入“50”  ，在“BirthSecond”  文本输入控件中键入“24”  ，那么此函数会返回“02:50:24 p”  。

**Text(Time(Value(BirthHour.Text), Value(BirthMinute.Text), Value(BirthSecond.Text)), "hh:mm:ss a/p")**

