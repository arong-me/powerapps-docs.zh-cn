---
title: DateFormattingInfo | Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e7d43fb-b6b7-4f1d-89e3-0b8157c9d2d9
ms.openlocfilehash: fb6dc5c67cc0ea031ab4e264d282458163ee46a0
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72344821"
---
# <a name="dateformattinginfo"></a>DateFormattingInfo

[!INCLUDE [context-description](includes/dateformattinginfo-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="properties"></a>属性

### <a name="abbreviateddaynames"></a>abbreviatedDayNames

{"Sun"、"周一"、"周二"、"周三"、"Thu"、"星期五"、"Sat"}

**类型**： `string`

### <a name="abbreviatedmonthgenitivenames"></a>abbreviatedMonthGenitiveNames

{"Jan"、"二月"、"Mar"、"Apr"、"可能"、"六月"、"七月"、"8"、"Sep"、"Oct"、"11 月"、"Dec"、""}

**类型**： `string[]`

### <a name="abbreviatedmonthnames"></a>Datetimeformatinfo.abbreviatedmonthnames

{"Jan"、"二月"、"Mar"、"Apr"、"可能"、"六月"、"七月"、"8"、"Sep"、"Oct"、"11 月"、"Dec"、""}

**类型**： `string[]`

### <a name="amdesignator"></a>Datetimeformatinfo.amdesignator

AM

**类型**： `string`

### <a name="calendar"></a>日程表

**类型**： `object`

@No__t_0 对象包含以下属性：

|名称|类型|描述|
|--|--|--|
|`algorithmType`|`number`|1|
|`calendarType`|`number`|1|
|`maxSupportedDateTime`|`Date`|"/Date （253402300799999）/"|
|`minSupportedDateTime`|`Date`|"/Date （-62135568000000）/"|
|`twoDigitYearMax`|`number`|2029|

### <a name="calendarweekrule"></a>calendarWeekRule

**类型**： `number`

### <a name="dateseparator"></a>dateSeparator

"/"

**类型**： `string`

### <a name="daynames"></a>Datetimeformatinfo.daynames

{"星期日"、"星期一"、"星期二"、"星期三"、"星期四"、"星期五"、"星期六"}

**类型**： `string[]`

### <a name="firstdayofweek"></a>firstDayOfWeek

**类型**： `number`

@No__t_0 属性可以设置为以下值之一：

|Value|含义|
|--|--|
|0|星期日|
|1|即|
|2|星期二|
|3|星期三|
|4|日|
|5|星期五|
|6|星期六|

### <a name="fulldatetimepattern"></a>Datetimeformatinfo.fulldatetimepattern

"dddd，MMMM d，yyyy h:mm： ss tt"

**类型**： `string`

### <a name="longdatepattern"></a>Datetimeformatinfo.longdatepattern

dddd，MMMM d，yyyy "

**类型**： `string`

### <a name="longtimepattern"></a>Datetimeformatinfo.longtimepattern

"hh： mm： ss tt"

**类型**： `string`

### <a name="monthdaypattern"></a>Datetimeformatinfo.monthdaypattern

"MMMM dd"

**类型**： `string`

### <a name="monthgenitivenames"></a>monthGenitiveNames

{"1 月"、"二月份"、"三月"、。 "12 月"，""}

**类型**： `string[]`

### <a name="monthnames"></a>monthNames

{"1 月"、"二月份"、"三月"、。 "12 月"，""}

**类型**： `string[]`

### <a name="pmdesignator"></a>Datetimeformatinfo.pmdesignator

下午

**类型**： `string`

### <a name="shortdatepattern"></a>Datetimeformatinfo.shortdatepattern

"M/d/yyyy"

**类型**： `string`

### <a name="shorttimepattern"></a>Datetimeformatinfo.shorttimepattern

"h:mm tt"

**类型**： `string`

### <a name="shortestdaynames"></a>shortestDayNames

{"Su"、"Mo"、"Tu"、"我们"、"Th"、"Fr"、"Sa"}

**类型**： `string[]`

### <a name="sortabledatetimepattern"></a>由 datetimeformatinfo.sortabledatetimepattern

yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-Yyyy'-'mm'-'dd't'hh '： ' MM '： ' ss '

**类型**： `string`

### <a name="timeseparator"></a>timeSeparator

":"

**类型**： `string`

### <a name="universalsortabledatetimepattern"></a>System.globalization.datetimeformatinfo.universalsortabledatetimepattern

"yyyy'-'mm'-'dd't'hh-YYYY'-'MM'-'DD'T'HH-yyyy'-'mm'-'dd HH"： "MM"： "ss'Z" "

**类型**： `string`

### <a name="yearmonthpattern"></a>Datetimeformatinfo.yearmonthpattern

"MMMM yyyy"

**类型**： `string`


### <a name="related-topics"></a>相关主题

[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)