---
title: Now、Today 和 IsToday 函数 | Microsoft 文档
description: PowerApps 中 Now、Today 和 IsToday 函数的引用信息（包括语法和示例）
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 483922d2c96c23d1d2672aed7e284e30d38f298a
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="now-today-and-istoday-functions-in-powerapps"></a>PowerApps 中的 Now、Today 和 IsToday 函数
返回当前日期和时间，以及测试某个日期/时间值是否为今天。

## <a name="description"></a>说明
**Now** 函数以日期/时间值返回当前日期和时间。

**Today** 函数以日期/时间值返回当前日期。 时间部分为午夜。 **Today** 在今天午夜到明天午夜的一整天中具有相同的值。

**IsToday** 函数测试某个日期/时间值是否介于今天午夜和明天午夜之间。 此函数返回 **true** 或 **false** 布尔值。

所有这些函数使用的都是当前用户的本地时间。

有关详细信息，请参阅[处理日期和时间](../show-text-dates-times.md)。

## <a name="syntax"></a>语法
**Now**()

**Today**()

**IsToday**( *DateTime* )

* *DateTime* - 必需。  要测试的日期/时间值。

## <a name="examples"></a>示例
在本部分的示例中，当前时间是 **2015 年 2 月 12 日****凌晨 3:59**，语言是 **en-us**。

| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **Text( Now(), "mm/dd/yyyy hh:mm:ss" )** |检索当前日期和时间，并将其显示为字符串。 |“02/12/2015 03:59:00” |
| **Text( Today(), "mm/dd/yyyy hh:mm:ss" )** |仅检索当前日期，时间部分为午夜，并将其显示为字符串。 |“02/12/2015 00:00:00” |
| **IsToday( Now() )** |测试当前日期和时间是否介于今天午夜和明天午夜之间。 |**true** |
| **IsToday( Today() )** |测试当前日期是否介于今天午夜和明天午夜之间。 |**true** |
| **Text( DateAdd( Now(), 12 ), "mm/dd/yyyy hh:mm:ss" )** |检索当前日期和时间，在结果基础上加 12 天，并将其显示为字符串。 |“02/24/2015 03:59:00” |
| **Text( DateAdd( Today(), 12 ), "mm/dd/yyyy hh:mm:ss" )** |检索当前日期，在结果基础上加 12 天，并将其显示为字符串。 |“02/24/2015 00:00:00” |
| **IsToday( DateAdd( Now(), 12 ) )** |测试当前日期和时间加 12 天是否介于今天午夜和明天午夜之间。 |**false** |
| **IsToday( DateAdd( Today(), 12 ) )** |测试当前日期加 12 天是否介于今天午夜和明天午夜之间。 |**false** |

