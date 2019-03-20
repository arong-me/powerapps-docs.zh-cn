---
title: Calendar 和 Clock 函数 | Microsoft 文档
description: PowerApps 中 Calendar 和 Clock 函数的参考信息（包括语法和示例）
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
ms.openlocfilehash: 25cae936ace1dcd3108f11271e3fe38cb41ae2e7
ms.sourcegitcommit: 55c6af2f767e90c999eea4d29589c1fe19dfc4db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2019
ms.locfileid: "54443726"
---
# <a name="calendar-and-clock-functions-in-powerapps"></a>PowerApps 中的 Calendar 和 Clock 函数
检索有关当前区域设置的日历和时钟信息。

## <a name="description"></a>描述
**Calendar** 和 **Clock** 函数是一组用于检索当前区域设置相关信息的函数。

使用这些函数，可以用当前用户的语言显示日期和时间。  **Calendar** 和 **Clock** 函数返回的单列表可直接与下拉列表控件和列表框控件的 **[Items](../controls/properties-core.md)** 属性结合使用。

| 函数 | 描述 |
| --- | --- |
| **Calendar.MonthsLong()** |包含每月完整名称的单列表，从“January”开始。 |
| **Calendar.MonthsShort()** |包含每月缩写的单列表，从一月的缩写“Jan”开始。 |
| **Calendar.WeekdaysLong()** |包含每个工作日完整名称的单列表，从“星期日”开始。 |
| **Calendar.WeekdaysShort()** |包含每个工作日缩写的单列表，从“星期日”的缩写“周日”开始。 |
| **Clock.AmPm()** |包含长大写“AM”和“PM”标志的单列表。  如果语言使用 24 小时制，则该表为空。 |
| **Clock.AmPmShort()** |包含短大写“A”和“P”标志的单列表。  如果语言使用 24 小时制，则该表为空。 |
| **Clock.IsClock24()** |布尔值，指示此区域设置是否采用 24 小时制。 |

通过 **[Text](function-text.md)** 函数，使用这一相同信息设置日期和时间值的格式。  **[Language](function-language.md)** 函数返回当前的语言和区域代码。

## <a name="syntax"></a>语法
**Calendar.MonthsLong**()

**Calendar.MonthsShort**()

**Calendar.WeekdaysLong**()

**Calendar.WeekdaysShort**()

**Clock.AmPm**()

**Clock.AmPmShort**()

**Clock.IsClock24**()

## <a name="examples"></a>示例
1. 插入下拉列表控件。
2. 将 **[Items](../controls/properties-core.md)** 属性的公式设置为：
   
   * **Calendar.MonthsLong()**
3. 应用的用户现在可以用其自己的语言选择月份。  可以将 **MonthsLong** 替换为 **Calendar** 返回的任何单列表，以创建工作日和时间选择器。

在美国，如果 **[Language](function-language.md)** 返回“en-US”，**Calendar** 函数则返回以下内容：

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Calendar.MonthsLong()** |返回值包含每个月，从"January"开始的完整名称。 |[ "January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December" ] |
| **Calendar.MonthsShort()** |返回值包含每个月，从"January"开始的缩写的名称。 |[ "Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec" ] |
| **Calendar.WeekdaysLong()** |返回值包含每一天，从"星期日"开始的完整名称。 |[ "Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday" ] |
| **Calendar.WeekdaysShort()** |返回值包含每一天，从"星期日"开始的缩写的名称。 |[ "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" ] |
| **Clock.AmPm()** |此语言采用 12 小时制。 返回值包含 AM 和 PM 标志的大写版本。 |[ "AM", "PM" ] |
| **Clock.AmPmShort()** |此语言采用 12 小时制。 返回值包含 AM 和 PM 标志的短大写版本。 |[ "A", "P" ] |
| **Clock.IsClock24()** |此语言采用 12 小时制。 |**false** |

