---
title: DateValue、TimeValue 和 DateTimeValue 函数 | Microsoft 文档
description: Power Apps 中 DateValue、TimeValue 和 DateTimeValue 函数的参考信息、语法和示例
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/16/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fc28b370b36be8d309c292e110d0b927d08c4a11
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "79436738"
---
# <a name="datevalue-timevalue-and-datetimevalue-functions-in-power-apps"></a>Power Apps 中的 DateValue、TimeValue 和 DateTimeValue 函数

将*字符串*中的日期和/或时间转换为*日期/时间*值。

## <a name="description"></a>说明

- **DateValue**函数将*日期字符串*（例如 "10/01/2014"）转换为*日期/时间*值。

- **TimeValue**函数将*时间字符串*（例如 "12:15 PM"）转换为*日期/时间*值。

- **DateTimeValue**函数将*日期和时间字符串*（例如，"1 月10日，2013 12:13 AM"）转换为*日期/时间*值。

**DateValue**函数将忽略日期字符串中的任何时间信息，而**TimeValue**函数将忽略时间字符串中的任何日期信息。

> [!NOTE]
> 默认情况下，DateValue、TimeValue 和 DateTimeValue 函数使用当前用户的设置中的语言。 您可以重写该字符串，以确保正确解释字符串。 例如，"10/1/1920" 将解释为 "*en*" 中的*10 月1日<sup>st</sup>*  ，在 "*fr*" 中解释为 1 *<sup>th</sup>月10日*。

日期必须采用以下格式之一︰

- MM/DD/YYYY
- DD/MM/YYYY
- DD Mon YYYY
- Month DD, YYYY

若要从数字日期、月份和年份组成部分转换，请阅读[日期](function-date-time.md)。 <br>
若要从数字的小时、分钟和秒部分转换，请阅读[Time](function-date-time.md)。

有关详细信息，请阅读：

- 使用[日期和时间](../show-text-dates-times.md)。
- [日期/时间和数据类型](data-types.md#date-time-and-datetime)。

## <a name="syntax"></a>语法

**DateValue**( *String* [, *Language* ])<br>
**DateTimeValue**( *String* [, *Language* ])<br>
**TimeValue**( *String* [, *Language* ])

* *String* - 必需。 包含日期、时间或日期和时间值组合的文本字符串。
* *Language* - 可选。 语言字符串，如[语言函数中](function-language.md)的前两个字符。  如果未提供，则使用当前用户的设置的语言。  

## <a name="examples"></a>示例

### <a name="datevalue"></a>DateValue

如果在名为 "开始" 的文本输入控件**中键入** **10/11/2014** ，然后将标签的 " [text](../controls/properties-core.md) " 属性设置为以下公式：

- 转换用户区域设置中字符串的日期，并将结果显示为长日期。

    ```powerapps-dot
    Text( DateValue( Startdate.Text ), DateTimeFormat.LongDate )
    ```

    设备设置为 " **en** "，则将标签显示为**周六，2014年10月11日**。
  
    > [!NOTE]
    > 与**datetimeformat.longdatetime**相比，你可以将多个选项与**DateTimeFormat**一起使用。 若要显示选项列表，请在编辑栏中键入参数，后跟惊叹号（ **！** ）。

- 转换法语区域设置中的日期，并将结果显示为长日期。 在此示例中，月份和月份的日期以不同于英语的方式解释。

    ```powerapps-dot
    Text( DateValue( Startdate.Text, "fr" ), DateTimeFormat.LongDate )
    ```
  
    设置为**en**区域设置的设备将标签显示为**星期一，11月10日，2014**。

如果键入**的是10月20日，** 则为2014：

- 转换用户区域设置中字符串的日期，并计算两天（天）之间的差异

    ```powerapps-dot
    DateDiff( DateValue( Startdate.Text ), Today() )
    ```
  
    设置为 " **en**区域设置" 的设备将标签显示为**9**，表示10月11日到10月20日之间的天数。 [DateDiff](function-dateadd-datediff.md)函数还可以显示月、季或年的不同之处。

### <a name="datetimevalue"></a>DateTimeValue

如果在名为 " **Start**" 的文本输入控件中键入**10/11/2014 1：50： 24.765 PM** ，然后将标签的 " [text](../controls/properties-core.md) " 属性设置为以下公式：

- 转换当前区域设置中的日期和时间字符串。
 
    ```powerapps-dot
    Text( DateTimeValue( Start.Text ), DateTimeFormat.LongDateTime )
    ```    
    
    设备设置为 " **en** "，则将标签显示为**周六，10月11日，2014 1:50:24 PM**。
  
  > [!NOTE]
  > 与**datetimeformat.longdatetime**相比，你可以将多个选项与**DateTimeFormat**一起使用。 若要显示选项列表，请在编辑栏中键入参数，后跟惊叹号（ **！** ）。

- 转换法语区域设置中的日期和时间字符串。 每月的月份和日期以不同的方式解释。

    ```powerapps-dot
    Text( DateTimeValue( Start.Text, "fr"), DateTimeFormat.LongDateTime )
    ```
  
    设置为**en**区域设置的设备将标签显示为**星期一，11月10日，2014 1:50:24 PM**。

- 同时转换用户区域设置中的日期和时间字符串，并将结果显示为秒的小数部分。

    ```powerapps-dot
    Text( DateTimeValue( Start.Text ), "dddd, mmmm dd, yyyy hh:mm:ss.fff AM/PM" )
    ```
  
    设置为 " **en** " 区域设置的设备会将标签显示为**周六，10月11日，2014 01：50： 24.765 PM**。
  
    作为替代方法，你可以指定**hh： mm： ss. f**或**hh： mm： ss. ff** ，将时间舍入到最接近<sup>的10个第二个或</sup><sup>第100个</sup>。

### <a name="timevalue"></a>TimeValue

将文本输入控件命名为 " **FinishedAt**"，然后将标签的 " [text](../controls/properties-core.md) " 属性设置为以下公式：

```powerapps-dot
If( TimeValue( FinishedAt.Text ) < TimeValue( "5:00:00.000 PM" ), 
    "You made it!", 
    "Too late!"
)
```

- 如果在**FinishedAt**控件中键入**4：59： 59.999 PM** ，则标签会显示 "*你做了！* "
- 如果在**FinishedAt**控件中键入**5：00： 00.000 PM** ，则标签会显示 "*太晚！* "
