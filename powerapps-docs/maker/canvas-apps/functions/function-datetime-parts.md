---
title: Day、Month、Year、Hour、Minute、Second 和 Weekday 函数 | Microsoft 文档
description: PowerApps 中 Day、Month、Year、Hour、Minute、Second 和 Weekday 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 10/25/2016
ms.author: gregli
ms.openlocfilehash: 239fc1638e3424fe30058ed31b18aed94e16d73c
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39015262"
---
# <a name="day-month-year-hour-minute-second-and-weekday-functions-in-powerapps"></a>PowerApps 中的 Day、Month、Year、Hour、Minute、Second 和 Weekday 函数
返回日期/时间值的各个部分。

## <a name="description"></a>描述
**Day** 函数可用于返回日期/时间值的日部分，范围是 1 到 31。

**Month** 函数可用于返回日期/时间值的月部分，范围是 1 到 12。

**Year** 函数可用于返回日期/时间值的年部分，从 1900 开始。

**Hour** 函数可用于返回日期/时间值的小时部分，范围是 0（凌晨12:00）到 23（午夜 11:00 点）。

**Minute** 函数可用于返回日期/时间值的分钟部分，范围是 0 到 59。

**Second** 函数可用于返回日期/时间值的秒部分，范围是 0 到 59。

**Weekday** 函数可用于返回日期/时间值的星期几。  默认情况下，结果范围是 1（星期日）到 7（星期六）。  可以使用 Microsoft Excel 的 Weekday 函数代码或 StartOfWeek 枚举值来指定其他范围：

| Excel 代码 | StartOfWeek 枚举 | 描述 |
| --- | --- | --- |
| **1**, **17** |**StartOfWeek.Sunday** |数字 1（星期日）到 7（星期六）。  默认值。 |
| **2**, **11** |**StartOfWeek.Monday** |数字 1（星期一）到 7（星期日）。 |
| **3** |**StartOfWeek.MondayZero** |数字 0（星期一）到 6（星期日）。 |
| **12** |**StartOfWeek.Tuesday** |数字 1（星期二）到 7（星期一）。 |
| **13** |**StartOfWeek.Wednesday** |数字 1（星期三）到 7（星期二）。 |
| **14** |**StartOfWeek.Thursday** |数字 1（星期四）到 7（星期三）。 |
| **15** |**StartOfWeek.Friday** |数字 1（星期五）到 7（星期四）。 |
| **16** |**StartOfWeek.Saturday** |数字 1（星期六）到 7（星期五）。 |

上述所有函数都返回一个数字。

有关详细信息，请参阅[处理日期和时间](../show-text-dates-times.md)。

## <a name="syntax"></a>语法
**Day**( *DateTime* )<br>**Month**( *DateTime* )<br>**Year**( *DateTime* )<br>**Hour**( *DateTime* )<br>**Minute**( *DateTime* )<br>**Second**( *DateTime* )

* *DateTime* - 必需。  要进行运算的日期/时间值。  

**Weekday**( *DateTime* [, *WeekdayFirst* ] )<br>

* *DateTime* - 必需。  要进行运算的日期/时间值。 
* *WeekdayFirst* - 可选。  Excel 代码指定一周从哪一天开始。  如果未提供，则使用 1（星期日是第一天）。

## <a name="examples"></a>示例
对于下面的示例，当前时间是 **2015 年 4 月 9 日星期四****下午 3:59:37**。

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Year(&nbsp;Now()&nbsp;)** |返回当前时间和日期的年部分。 |2015 |
| **Month(&nbsp;Now()&nbsp;)** |返回当前时间和日期的月部分。 |4 |
| **Day(&nbsp;Now()&nbsp;)** |返回当前时间和日期的日部分。 |9 |
| **Hour(&nbsp;Now()&nbsp;)** |返回当前时间和日期的小时部分。 |15 |
| **Minute(&nbsp;Now()&nbsp;)** |返回当前时间和日期的分钟部分。 |59 |
| **Second(&nbsp;Now()&nbsp;)** |返回当前时间和日期的秒部分。 |37 |
| **Weekday(&nbsp;Now()&nbsp;)** |返回当前时间和日期的星期几部分，使用默认设置（星期日作为一周的第一天）。 |5 |
| **Weekday(&nbsp;Now(),&nbsp;14&nbsp;)** |返回当前时间和日期的星期几部分（使用 Excel 代码指定的星期四作为一周的第一天）。 |1 |
| **Weekday(&nbsp;Now(),&nbsp;StartOfWeek.Wednesday&nbsp;)** |返回当前时间和日期的星期几部分（使用 **StartOfWeek** 枚举指定的星期三作为一周的第一天）。 |2 |

