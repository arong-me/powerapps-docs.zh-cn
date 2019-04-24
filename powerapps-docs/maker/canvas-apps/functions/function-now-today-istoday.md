---
title: Now、Today 和 IsToday 函数 | Microsoft 文档
description: PowerApps 中 Now、Today 和 IsToday 函数的引用信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/09/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 748f76835e9a66281f4723b88ed7249a7a07e091
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61544089"
---
# <a name="now-today-and-istoday-functions-in-powerapps"></a>PowerApps 中的 Now、Today 和 IsToday 函数
返回当前日期和时间，以及测试某个日期/时间值是否为今天。

## <a name="description"></a>描述
**Now** 函数以日期/时间值返回当前日期和时间。

**Today** 函数以日期/时间值返回当前日期。 时间部分为午夜。 **Today** 在今天午夜到明天午夜的一整天中具有相同的值。

**IsToday** 函数测试某个日期/时间值是否介于今天午夜和明天午夜之间。 此函数返回 true 或 false 布尔值。

所有这些函数使用的都是当前用户的本地时间。

有关详细信息，请参阅[处理日期和时间](../show-text-dates-times.md)。

## <a name="volatile-functions"></a>易失函数
Now 和 Today 是易失函数。  每次计算这些函数时会返回不同的值。  

在数据流公式中使用易失函数时，如果对含有该函数的公式进行重新计算，该函数会返回不同的值。  如果公式中没有任何其他更改，在应用执行期间，它会具有相同的值。

例如，如果一个标签控件设为 **Label1.Text = Now()**，则应用处于活动状态时，该控件不会改变。  只有关闭和重新打开应用会得到新值。

如果包含该函数的公式的其他内容发生了任何更改，会导致该函数进行重新计算。  例如，如果将示例更改为包含一个滑块控件，即设为 **Label1.Text = DateAdd( Now(), Slider1.Value, Minutes )**，则每当滑块控件的值发生更改时会检索当前时间，标签的 text 属性会进行重新计算。

如果在[行为公式](../working-with-formulas-in-depth.md)中使用易失函数，则每当计算该公式时，也会计算该函数。  请参阅下文查看示例。

## <a name="syntax"></a>语法
**Now**()

**Today**()

**IsToday**( *DateTime* )

* *DateTime* - 必需。  要测试的日期/时间值。

## <a name="examples"></a>示例
在本部分的示例中，当前时间是 **2015 年 2 月 12 日****凌晨 3:59**，语言是 **en-us**。

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Text( Now(), "mm/dd/yyyy hh:mm:ss" )** |检索当前日期和时间，并将其显示为字符串。 |“02/12/2015 03:59:00” |
| **Text( Today(), "mm/dd/yyyy hh:mm:ss" )** |仅检索当前日期，时间部分为午夜，并将其显示为字符串。 |“02/12/2015 00:00:00” |
| **IsToday( Now() )** |测试当前日期和时间是否介于今天午夜和明天午夜之间。 |**true** |
| **IsToday( Today() )** |测试当前日期是否介于今天午夜和明天午夜之间。 |**true** |
| **Text( DateAdd( Now(), 12 ), "mm/dd/yyyy hh:mm:ss" )** |检索当前日期和时间，在结果基础上加 12 天，并将其显示为字符串。 |“02/24/2015 03:59:00” |
| **Text( DateAdd( Today(), 12 ), "mm/dd/yyyy hh:mm:ss" )** |检索当前日期，在结果基础上加 12 天，并将其显示为字符串。 |“02/24/2015 00:00:00” |
| **IsToday( DateAdd( Now(), 12 ) )** |测试当前日期和时间加 12 天是否介于今天午夜和明天午夜之间。 |**false** |
| **IsToday( DateAdd( Today(), 12 ) )** |测试当前日期加 12 天是否介于今天午夜和明天午夜之间。 |**false** |

#### <a name="display-a-clock-that-updates-in-real-time"></a>显示一个会实时更新的时钟

1. 添加一个[计时器](../controls/control-timer.md)控件，将其“Duration”属性设置为“1000”，并将其“Repeat”属性设置为“true”。

    计时器将运行一秒钟，然后自动重新开始，并持续该模式。 

1. 将该控件的“OnTimerEnd”属性设置为以下公式：

    **Set( CurrentTime, Now() )**

    每当计时器重新开始（在一秒后），此公式会将“CurrentTime”全局变量设置为“Now”函数的当前值。

    ![屏幕包含一个计时器控件，其公式为 OnTimerEnd = Set(CurrentTime, Now())](media/function-now-today-istoday/now-set-currenttime.png)

1. 添加一个[标签](../controls/control-text-box.md)控件，然后将“Text”属性设置为以下公式：

    **Text( CurrentTime, LongTime24 )**

    使用 [Text](function-text.md) 函数来设置所需的日期和时间格式，或将此属性设置为“CurrentTime”以显示小时和分钟值，但不显示秒。

    ![屏幕包含一个标签控件，其“Text”属性设置为 Text( CurrentTime, LongTime24)](media/function-now-today-istoday/now-use-currenttime.png)

1. 按 F5 可预览应用，然后通过单击或点击计时器可启动计时器。

    标签持续显示当前时间（细化到秒）。

    ![四个屏幕显示四个时间值（13: 50:22、13:50:45、13:51:03 和 13:51:25）](media/function-now-today-istoday/now-four-times.png)

1. 将计时器的“AutoStart”属性设置为“true”，其“Visible”属性设置“false”。

    计时器变为不可见，并自动启动。

1. 设置屏幕的 [OnStart](../controls/control-screen.md) 属性，以使“CurrentTime”变量具有一个有效值，如以下示例所示：

    **Set(CurrentTime, Now())**

    标签会在应用启动时立即显示（在计时器运行完 1 秒之前）。
