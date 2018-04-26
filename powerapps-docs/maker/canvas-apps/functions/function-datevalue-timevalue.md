---
title: DateValue、TimeValue 和 DateTimeValue 函数 | Microsoft 文档
description: PowerApps 中 DateValue、TimeValue 和 DateTimeValue 函数的参考信息（包括语法和示例）
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
ms.openlocfilehash: 396a2d5325b7b72f3637dba1edddeead49594167
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="datevalue-timevalue-and-datetimevalue-functions-in-powerapps"></a>PowerApps 中的 DateValue、TimeValue 和 DateTimeValue 函数
将字符串类型的日期和/或时间转换为日期/时间值。

## <a name="description"></a>说明
**DateValue** 函数可用于将日期字符串（例如“10/01/2014”）转换为日期/时间值。

**TimeValue** 函数可用于将时间字符串（例如“12:15 PM”）转换为日期/时间值。

**DateTimeValue** 函数可用于将日期和时间字符串（例如“January 10, 2013 12:13 AM”）转换为日期/时间值。

**DateValue** 函数会忽略日期字符串中的任何时间信息，而 **TimeValue** 函数则会忽略时间字符串中的任何日期信息。

默认情况下使用当前用户的语言环境，但你可以替代此设置以确保正确解释字符串。 例如，“10/1/1920”在“英语语言环境”中解释为 10 月 1 日，而在“法语语言环境”中则解释为 1 月 10 日。<sup></sup><sup></sup>

日期必须采用以下格式之一︰

* MM/DD/YYYY
* DD/MM/YYYY
* DD Mon YYYY
* Month DD, YYYY

请参阅 **[Date](function-date-time.md)** 和 **[Time](function-date-time.md)** 函数以从年、月、日、时、分、秒的数字部分进行转换。

有关详细信息，请参阅[处理日期和时间](../show-text-dates-times.md)。

要转换数字，请参阅 **[Value](function-value.md)** 函数。

## <a name="syntax"></a>语法
**DateValue**( *String* [, *Language* ])<br>**DateTimeValue**( *String* [, *Language* ])<br>**TimeValue**( *String* [, *Language* ])

* *String* - 必需。  包含日期、时间或日期和时间值组合的文本字符串。
* *Language* - 可选。  语言字符串，例如可通过 **[Language](function-language.md)** 函数返回语言的前两个字符。  如果未提供，则使用当前用户客户端的语言。  

## <a name="examples"></a>示例
### <a name="datevalue"></a>DateValue
如果在“Startdate”文本输入控件中键入了“10/11/2014”，然后将标签的“[Text](../controls/properties-core.md)”属性设置为以下函数：

* **Text(DateValue(Startdate.Text), DateTimeFormat.LongDate)**
  
    如果你的计算机区域设置为 **en**，这个标签就会显示 **Saturday, October 11, 2014**。
  
    > [!NOTE]
> 可以将多个选项（LongDateTime 除外）与 DateTimeFormat 参数结合使用。 要显示这些选项的列表，请在函数框中输入该参数，然后输入一个感叹号。
* **Text(DateValue(Startdate.Text, "fr"), DateTimeFormat.LongDate)**
  
    这个标签会显示 **Monday, November 10, 2014**。

如果对 **October 20, 2014** 执行上述操作：

* **DateDiff(DateValue(Startdate.Text), Today())**
  
    如果你的计算机的语言设置为 **en**，这个标签会显示 **9**，表示 10 月 11 日到 10 月 20 日之间间隔的天数。 **[DateDiff](function-dateadd-datediff.md)** 函数还可以显示月份、季度或年份之间的差值。

### <a name="datetimevalue"></a>DateTimeValue
如果在“Start”文本输入控件中键入了“10/11/2014 1:50:24.765 PM”，然后将标签的“[Text](../controls/properties-core.md)”属性设置为以下函数：

* **Text(DateTimeValue(Start.Text), DateTimeFormat.LongDateTime)**
  
    如果你的计算机的区域设置为“en”，这个标签会显示 **Saturday, October 11, 2014 1:50:24 PM**。
  
    > [!NOTE]
> 可以将多个选项（LongDateTime 除外）与 DateTimeFormat 参数结合使用。 要显示这些选项的列表，请在函数框中输入该参数，然后输入一个感叹号。
* **Text(DateTimeValue(Start.Text, "fr"), DateTimeFormat.LongDateTime)**
  
    这个标签会显示 **Monday, November 10, 2014 1:50:24 PM**。
* **Text(DateTimeValue(Start.Text), "dddd, mmmm dd, yyyy hh:mm:ss.fff AM/PM")**
  
    如果你的计算机的区域设置为 **en**，这个标签会显示 **Saturday, October 11, 2014 01:50:24:765 PM**。
  
    还有一种方法是指定 **hh:mm:ss.f** 或 **hh:mm:ss.ff** 以将时间取整为秒的最接近 10 倍或 100 倍值。

### <a name="timevalue"></a>TimeValue
将文本输入控件命名为“FinishedAt”，然后将标签的“[Text](../controls/properties-core.md)”属性设置为以下函数：

**If(TimeValue(FinishedAt.Text)<TimeValue("5:00:00.000 PM"), "You made it!", "Too late!")**

* 如果在 **FinishedAt** 控件中输入 **4:59:59.999 PM**，这个标签会显示“You made it!”
* 如果在 **FinishedAt** 控件中键入 **5:00:00.000 PM**，这个标签会显示“Too late!”

