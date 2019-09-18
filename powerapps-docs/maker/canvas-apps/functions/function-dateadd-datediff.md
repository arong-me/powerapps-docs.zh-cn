---
title: DateAdd、DateDiff 和 TimeZoneOffset 函数 | Microsoft 文档
description: PowerApps 中 DateAdd、DateDiff 和 TimeZoneOffset 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/23/2017
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e2c90566f235093f25e3a8c35bc1700f2a61b348
ms.sourcegitcommit: 5899d37e38ed7111d5a9d9f3561449782702a5e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71037968"
---
# <a name="dateadd-datediff-and-timezoneoffset-functions-in-powerapps"></a>PowerApps 中的 DateAdd、DateDiff 和 TimeZoneOffset 函数
加上或发现日期/时间值的差值，并转换本地时间和 UTC。

## <a name="description"></a>描述
DateAdd 函数用于在日期/时间值中加上时间单位值。 结果是一个新的日期/时间值。 还可以指定负值，从日期/时间值中减去时间单位值。

DateDiff 函数返回两个日期/时间值的差值。 结果是时间单位值。

对于这两个函数，时间单位可以是毫秒、秒、分钟、小时、天、月、季度或年。  默认情况下，这两个函数都以**天**为单位。

TimeZoneOffset 函数返回用户本地时间和 UTC（协调世界时）的时间差（以分钟为单位）。   

可以结合使用 DateAdd 和 TimeZoneOffset，转换用户本地时间和 UTC（协调世界时）。  加上 TimeZoneOffset 会将本地时间转换为 UTC，减去 TimeZoneOffset（即添加负值）会将 UTC 转换为本地时间。

有关详细信息，另请参阅[日期、时间和日期时间数据类型](/data-types#date-time-and-datetime)以及使用[日期和时间](../show-text-dates-times.md)。

## <a name="syntax"></a>语法
**DateAdd**( *DateTime*, *Addition* [, *Units* ] )

* *DateTime* - 必需。 要进行运算的日期/时间值。
* *Addition* - 必需。 要在 DateTime 中加上的数值，以时间单位为单位。
* *单位* - 可选。 要添加的*单位*类型：**毫秒**、**秒**、**分钟**、**小时**、**日**、**月**、**季度**或**年**。  如果未指定则使用**天**。

**DateDiff**( *StartDateTime*, *EndDateTime* [, *Units* ] )

* *StartDateTime* - 必需。 开始日期/时间值。
* *EndDateTime* - 必需。 结束日期/时间值。
* *单位* - 可选。 要添加的*单位*类型：**毫秒**、**秒**、**分钟**、**小时**、**日**、**月**、**季度**或**年**。  如果未指定则使用**天**。

TimeZoneOffset( [ DateTime ] )

* DateTime - 可选。  要为其返回时间差的日期/时间值。  默认情况下，使用当前日期/时间。

## <a name="examples"></a>示例
在下面所有示例中，假定当前日期和时间为“July 15, 2013, 1:02 PM”。

### <a name="simple-dateadd"></a>简单 DateAdd

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Text( DateAdd( Now(), 3 ),<br>"dd-mm-yyyy hh:mm" )** |在当前日期和时间中加上三天（默认时间单位）。 |"18-07-2013 13:02" |
| **Text( DateAdd( Now(), 4, Hours ),<br>"dd-mm-yyyy hh:mm" )** |在当前日期和时间中加上四小时。 |"15-07-2013 17:02" |
| **Text( DateAdd( Today(), 1, Months ),<br>"dd-mm-yyyy hh:mm" )** |在当前日期（无时间）中加上一个月，因为“Today”不返回时间组件。 |"15-08-2013 00:00" |
| **Text( DateAdd( Now(), &#8209;30, Minutes ),<br>"dd-mm-yyyy hh:mm" )** |从当前日期和时间中减去 30 分钟。 |"15-07-2013 12:32" |

### <a name="simple-datediff"></a>简单 DateDiff

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **DateDiff( Now(), DateValue("1/1/2014") )** |返回两个时间单位（默认时间单位为“天”）差值 |170 |
| **DateDiff( Now(), DateValue("1/1/2014"), Months )** |返回两个时间单位（月）差值 |6 |
| **DateDiff( Now(), Today(), Minutes )** |返回当前日期/时间和仅当前日期（没有时间）的差值（以分钟为单位）。  由于“Now”晚于“Today”，因此结果将为负数。 |-782 |

### <a name="converting-to-utc"></a>转换为 UTC
若要转换为 UTC（协调世界时），请为给定时间加上 TimeZoneOffset。  

例如，假设当前日期和时间为“July 15, 2013, 1:02 PM”，使用太平洋夏令时（PDT、UTC-7）。  若要确定当前 UTC，请使用：

* **DateAdd( Now(), TimeZoneOffset(), Minutes )**

由于 TimeZoneOffset 默认为当前时间，因此无需向其传递参数。

若要查看结果，请使用格式为“dd-mm-yyyy hh:mm”的 Text 函数，这将返回“15-07-2013 20:02”。

### <a name="converting-from-utc"></a>从 UTC 转换
若要从 UTC 转换，请为给定时间减去 TimeZoneOffset（通过添加负号）。

例如，假设将 UTC 日期和时间“July 15, 2013, 8:02 PM”存储到名为“StartTime”的变量中。 若要调整用户时区时间，请使用：

* **DateAdd （starttime， &minus;TimeZoneOffset （starttime），分钟）**

请注意，TimeZoneOffset 之前是负号，以减去（而不是加上）时间差。

若要查看结果，请使用格式为“dd-mm-yyyy hh:mm”的 Text 函数，这将返回“15-07-2013 13:02”（如果使用太平洋夏令时）。

