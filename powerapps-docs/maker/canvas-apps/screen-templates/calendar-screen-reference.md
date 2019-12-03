---
title: 画布应用的日历屏幕模板参考 |Microsoft Docs
description: 了解有关 canvas 应用的日历屏幕模板在 PowerApps 中的工作方式的详细信息。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/31/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a586f705780ef370c63dc35e0d63658a437b549e
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675369"
---
# <a name="reference-information-about-the-calendar-screen-template-for-canvas-apps"></a>有关 canvas 应用的日历屏幕模板的参考信息

对于 Power Apps 中的画布应用，请了解日历屏幕模板中的每个重大控件如何为屏幕的整体默认功能提供帮助。 这一深入探讨介绍了如何通过其他属性来确定控件如何响应用户输入。 有关此屏幕默认功能的详细讨论，请参阅[日历屏幕概述](calendar-screen-overview.md)。

本主题重点介绍一些重要的控件，并说明这些控件的各种属性（例如**Items**和**OnSelect**）的设置表达式或公式：

- [日历下拉（dropdownCalendarSelection）](#calendar-drop-down)
- [日历图标（iconCalendar）](#calendar-icon)
- [上月 v 形（iconPrevMonth）](#previous-month-chevron)
- [下个月 v 形（iconNextMonth）](#next-month-chevron)
- [日历库（MonthDayGallery）（+ 子控件）](#calendar-gallery)
- [事件库（CalendarEventsGallery）](#events-gallery)

## <a name="prerequisite"></a>先决条件

熟悉如何[在 PowerApps 中创建应用](../data-platform-create-app-scratch.md)时添加和配置屏幕和其他控件。

## <a name="calendar-drop-down"></a>日历下拉

![dropdownCalendarSelection 控件](media/calendar-screen/calendar-dropdown.png)

- 属性：**项**<br>
    值： `Office365.CalendarGetTables().value`

    此值是一个连接器操作，用于检索应用用户的 Outlook 日历。 你可以看到此操作检索的[值](https://docs.microsoft.com/connectors/office365/#entitylistresponse[table])。

- 属性： **OnChange**<br>值： `Select(dropdownCalendarSelection)`

    当用户在列表中选择一个选项时，该控件的**OnSelect**属性中的函数将运行。

- 属性： **OnSelect**<br>
    值：一个**If**函数（出现在下面的代码块中）和几个附加函数（之后出现在代码块中）。

   此部分公式仅在打开应用后首次在下拉列表中选择选项时才运行：

    ```powerapps-dot
    If( IsBlank( _userDomain ),
        UpdateContext( {_showLoading: true} );
        Set( _userDomain, Right( User().Email, Len( User().Email ) - Find( "@", User().Email ) ) );
        Set( _dateSelected, Today() );
        Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days ) );  
        Set( _firstDayInView, DateAdd( _firstDayOfMonth, -(Weekday(_firstDayOfMonth) - 1), Days ) );
        Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) )  
    );
    ```

    前面的代码定义了以下变量：
    
  - **\_userDomain**：应用用户的公司域，如用户的电子邮件地址中所示。
  - **\_dateSelected**：当天的日期（默认值）。 日历库将突出显示此日期，事件库将显示计划用于该日期的事件。
  - **\_firstDayOfMonth**：当月的第一天。 由于 `(Today + (1 - Today)) = Today - Today + 1 = 1`，此**DateAdd**函数始终返回每月的第一天。
  - **\_firstDayInView**：日历库可以显示的第一天。 此值不同于月的第一天，除非月份从星期日开始。 若要防止上个月显示整周，请 `_firstDayOfMonth - Weekday(_firstDayOfMonth) + 1` **\_firstDayInView**的值。
  - **\_lastDayOfMonth**：当月的最后一天，即与下个月的第一天，减一天。

   每当用户在 "日历" 下拉列表中选择一个选项时（不只是用户首次打开该应用程序时），将运行**If**函数之后的函数：

    ```powerapps-dot
    Set( _calendarVisible, false );
    UpdateContext( {_showLoading: true} );
    Set( _myCalendar, dropdownCalendarSelection2.Selected );
    Set( _minDate, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days )
    );
    Set(_maxDate, 
        DateAdd(
            DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days ), 
            40, 
            Days
        )
    );
    ClearCollect( MyCalendarEvents, 
        'Office365'.GetEventsCalendarViewV2( _myCalendar.Name, 
            Text( _minDate, UTC ), 
            Text( _maxDate, UTC )
        ).value
    );
    UpdateContext( {_showLoading: false} );
    Set( _calendarVisible, true )
    ```

    前面的代码定义这些变量和一个集合：

    - **\_calendarVisible**：设置为**false** ，以便在加载新的所选内容时不显示日历。
    - **\_showLoading**：设置为**true** ，以便在加载新选择时显示加载指示器。
    - **\_myCalendar**：设置为 "**日历" 下拉**控件的当前值，以便检索正确日历中的事件。
    - **\_minDate**：设置为与 **\_firstDayInView**相同的值。 此变量确定已从 Outlook 检索并在应用中缓存的事件。
    - **\_maxDate**：设置为日历中的最后一个可查看日期。 该公式是 `_firstDayInView + 40`的。 日历最多可显示41天，因此 **\_maxDate**变量始终反映最后一个可见日期，并确定哪些事件已经从 Outlook 检索并在应用中缓存。
    - **MyCalendarEvents**：设置为所选日历中用户事件的集合，范围从 **\_MinDate**到 **\_maxDate**。
    - **\_showLoading**：设置为**false**;加载其他所有内容后， **\_calendarVisible**设置为**true** 。

## <a name="calendar-icon"></a>日历图标

![iconCalendar 控件](media/calendar-screen/calendar-today-icon.png)

- 属性： **OnSelect**<br>
    值：四个用于将日历库重置为当前日期的**设置**函数：

    ```powerapps-dot
    Set( _dateSelected, Today() );
    Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days) );
    Set( _firstDayInView, DateAdd(_firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days));
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) )
    ```

    前面的代码将重置显示正确日历视图所需的所有日期变量：

    - **\_dateSelected**重置为 "今日"。
    - **\_firstDayOfMonth**重置为当天月份的第一天。
    - **\_firstDayInView**将重置为选中 "当前月" 后的第一天。
    - **\_lastDayOfMonth**重置为当天月份的最后一天。

    本主题中的 "[**日历" 下拉**](#calendar-drop-down)部分更详细地说明了这些变量。

## <a name="previous-month-chevron"></a>上月 v 形

![iconPrevMonth 控件](media/calendar-screen/calendar-back.png)

- 属性： **OnSelect**<br>值：四个**集**函数和一个**If**函数，用于显示日历库中的上月：

    ```powerapps-dot
    Set( _firstDayOfMonth, DateAdd( _firstDayOfMonth, -1, Months ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days )
    );
    Set( _lastDayOfMonth, DateAdd(DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    If( _minDate > _firstDayOfMonth,
        Collect( MyCalendarEvents,
            'Office365'.GetEventsCalendarViewV2( _myCalendar.Name,
                Text( _firstDayInView, UTC ), 
                Text( DateAdd( _minDate, -1, Days ), UTC )
            ).value
        );
        Set( _minDate, _firstDayInView )
    )
    ```

    > [!NOTE]
    > **\_firstDayOfMonth**、 **\_FirstDayInView**和 **\_lastDayOfMonth**的定义与本主题的 "[日历" 下拉](#calendar-drop-down)部分中的定义几乎相同。

    只要用户选择上个月的 v 形 v 形 v 形 v 形 v 形，就会运行上述代码的前三行。 此代码设置显示适当日历视图所需的变量。 仅当用户之前未对选定日历选择本月时，其余代码才运行。

    如果是这种情况， **\_minDate**是上个月显示时显示的第一天。 在用户选择图标之前， **\_minDate**具有当前月份的23日的最小可能值。 （如果3月1日落在周六，则3月23日 **\_firstDayInView** 。）这意味着，如果用户尚未选择本月， **\_minDate**大于新 **\_firstDayOfMonth**， **if**函数返回**true**。 代码将运行，并更新集合和变量：

    - **MyCalendarEvents**从所选日历中检索带有[GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-)操作的事件。 日期范围介于 **\_firstDayInView** date 和 **\_minDate** -1 之间。 由于**MyCalendarEvents**已在 **\_minDate**日期包含事件，因此，在此日期范围内的最大值从该日期减去1。

    - **\_minDate**设置为当前 **\_firstDayInView** ，因为这是检索事件的第一个日期。 如果用户通过选择前个月 v 形返回到此日期，则**if**函数返回**false**;此视图的事件已在**MyCalendarEvents**中缓存，因此代码不会运行。

## <a name="next-month-chevron"></a>下个月 v 形

![iconNextMonth 控件](media/calendar-screen/calendar-forward.png)

- 属性： **OnSelect**<br>
    值：四个**集**函数和一个**If**函数，用于显示日历库中的下个月：

    ```powerapps-dot
    Set( _firstDayOfMonth, DateAdd( _firstDayOfMonth, 1, Months ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days ) );
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    If( _maxDate < _lastDayOfMonth,
        Collect( MyCalendarEvents, 
            'Office365'.GetEventsCalendarViewV2( _myCalendar.Name, 
                Text( DateAdd( _maxDate, 1, Days ), UTC ), 
                DateAdd( _firstDayInView, 40, Days )
            ).value
        );
        Set( _maxDate, DateAdd( _firstDayInView, 40, Days) )    
    )
    ```

    > [!NOTE]
    > **\_firstDayOfMonth**、 **\_FirstDayInView**和 **\_lastDayOfMonth**的定义与本主题的 "[日历" 下拉](#calendar-drop-down)部分中的定义几乎相同。

    上述代码的前三行（当用户选择下个月的 v 形 v 形 v 形 v 形 v 形 v 形 v）时，请设置显示正确日历视图所需的变量。 仅当用户之前未对选定日历选择本月时，其余代码才运行。

    在这种情况下， **\_maxDate**是上个月显示时显示的最后一天。 在用户选择下个月的 v 形 v 形前， **\_maxDate**的最大可能值为下个月的第13个。 （当2月1日落在星期日的非闰年时， **\_maxDate**为3月13日 **\_firstDayInView** + 40 天。）这意味着，如果用户尚未选择本月， **\_maxDate**大于新 **\_lastDayOfMonth**， **if**函数返回**true**。 代码将运行，并更新集合和变量：

    - **MyCalendarEvents**从所选日历中检索带有[GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-)操作的事件。 日期范围介于 **\_maxDate** + 1 天和 **\_firstDayInView** + 40 天之间。 由于**MyCalendarEvents**已在 **\_minDate**日期包含事件，因此，在此日期范围内的最小值为1时添加了1。 **\_firstDayInView** + 40 是 **\_maxDate**的公式，因此该范围中的第二个日期只是新的 **\_maxDate**。

    - **\_maxDate**设置为 **\_firstDayInView** + 40 天，因为这是检索事件的最后一天。 如果用户通过选择下个月 v 形返回到此日期，则**if**函数返回**false**;此视图的事件已在**MyCalendarEvents**中缓存，因此代码不会运行。

## <a name="calendar-gallery"></a>日历库

![MonthDayGallery 控件](media/calendar-screen/calendar-month-gall.png)

- 属性：**项**<br>
    值： `[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,
    20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41]`
  
  将0到41的集合用于日历库中的项，因为在最糟糕的情况下，"日历" 视图将必须显示42整天。 当月份第一月份出现在星期六，而最后一个月的最后一星期日出现时，就会发生这种情况。 在这种情况下，日历将显示上个月中第一个月的第几天，从下个月的第六天开始显示六天。 这是42的唯一值，其中30表示所选月份。

- 属性： **WrapCount**<br>
    值： `7`

  此值反映七天。

### <a name="title-control-in-the-calendar-gallery"></a>日历库中的标题控件

![MonthDayGallery 标题控件](media/calendar-screen/calendar-month-text.png)

- 属性：**文本**<br>
    值： `Day( DateAdd( _firstDayInView, ThisItem.Value, Days ) )`

    请记住， **\_firstDayInView**定义为（ **\_firstDayOfMonth** -其 weekday 值） + 1。 这表明 **\_firstDayInView**始终是星期日， **\_FirstDayOfMonth**始终在**MonthDayGallery**的第一行中。 由于这两个事实， **\_firstDayInView**始终位于**MonthDayGallery**的第一个单元格中。 **ThisItem**是**MonthDayGallery**项属性中该单元的数字。 因此，将 **\_firstDayInView**作为起点，每个单元显示 **\_firstDayInView** + 其各自单元值的增量。

- 属性：**填充**<br>
    值：一个**If**函数：

    ```powerapps-dot
    If( DateAdd( _firstDayInView, ThisItem.Value ) = Today() && 
                DateAdd( _firstDayInView, ThisItem.Value ) = _dateSelected, 
            RGBA( 0, 0, 0, 0 ),
        DateAdd( _firstDayInView, ThisItem.Value) = Today(), 
            ColorFade( Subcircle.Fill, 0.67 ),
        Abs( Title.Text - ThisItem.Value) > 10,
            RGBA( 200, 200, 200, 0.3 ),
        RGBA( 0, 0, 0, 0 )
    )
    ```

  如 "**文本**" 属性的 "说明" 中所述，`DateAdd(_firstDayInView, ThisItem.Value)` 表示可见单元格中的日。 考虑到这一点，前面的代码将执行以下比较：
  1. 如果单元格的值是今天的日期，并且此单元格等效于 **\_dateSelected**，请不要提供填充值。
  1. 如果单元格的值是今天的日期，但不等于 **\_dateSelected**，请提供**ColorFade**填充。
  1. 最后一个比较不是如此清晰。 这是单元中的实际文本值与单元项的值（显示的数字和项号）之间的比较。<br>

      为了更好地理解这一点，请考虑九月2018年9月，在星期六开始，到星期日结束。 在这种情况下，日历将显示8月26日至第9月1日，第一行中的第1天，`Abs(Title.Text - ThisItem.Value) = 26` 到9月1日。 然后 `Abs(Title.Text - ThisItem.Value) = 5`。 它将保持为5，直到日历中的最后一行，其中显示第30年9月30日到6月1日。 在该 `Abs(Title.Text - ThisItem.Value)` 中，将在9月30日仍为5，但对于10月的日期将为35。<br>

      这是模式：对于上个月显示的日，`Abs(Title.Text - ThisItem.Value)` 将始终等于显示第一天的 `Title.Text` 值。 对于下个月显示的日，`Abs(Title.Text - ThisItem.Value)` 将始终等于该月的第一个单元的**MonthDayGallery**项值（在本例中为10月1日）减1。 而且，最重要的是，对于当前选定月份中显示的天数，`Abs(Title.Text - ThisItem.Value)` 还将始终等于该月第一项的值减1，并且永远不会超过5，如前面的示例所示。 因此，将公式编写为 `Abs(Title.Text - ThisItem.Value) > 5`是非常有效的。

      此语句检查日期值是否在当前选定的月份之外。 如果是，则**填充**是部分不透明的灰色。

    > [!NOTE]
    > 您可以通过在库中插入**标签**控件并将其**Text**属性设置为以下值，来检查上一次比较的有效性：<br>`Abs(Title.Text - ThisItem.Value)`。

- 属性：**可见**<br>
    负值

    ```powerapps-dot
    !(
        DateAdd( _firstDayInView, ThisItem.Value, Days ) - 
            Weekday( DateAdd( _firstDayInView, ThisItem.Value,Days ) ) + 1 
        > _lastDayOfMonth
    )
    ```

    前面的语句检查单元格是否在当前选定月份的任何日期的行中。 请记住，从日期值中减去任何日期的 weekday 值并添加1将始终返回该日所在行中的第一项。 因此，此语句检查行中的第一天是否晚于可查看月份的最后一天。 如果是，则不会出现此情况，因为整行包含下个月的几天。

- 属性： **OnSelect**<br>
    值：将 **\_dateSelected**变量设置为所选单元格的日期的**集**函数：

    ```powerapps-dot
    Set( _dateSelected, DateAdd( _firstDayInView, ThisItem.Value, Days ) )
    ```

### <a name="circle-control-in-the-calendar-gallery"></a>日历库中的 Circle 控件

![MonthDayGallery Circle 控件](media/calendar-screen/calendar-month-event.png)

- 属性：**可见**<br>
    值：确定是否为所选日期计划了任何事件以及**Subcircle**和**Title**控件是否可见的公式：

    ```powerapps-dot
    CountRows(
        Filter( MyCalendarEvents, 
            DateValue( Text( Start ) ) = DateAdd( _firstDayInView, ThisItem.Value, Days )
        )
    ) > 0 && !Subcircle.Visible && Title.Visible
    ```

    如果任何事件的 "**开始**" 字段等效于该单元格的日期（如果**标题**控件可见），并且**Subcircle**控件不可见，则该**圆圈**控件可见。 换言之，此控件在此天至少发生一次事件时可见，而当天未选中。 如果选择此选项，则该日期的事件将显示在**CalendarEventsGallery**控件中。

### <a name="subcircle-control-in-the-calendar-gallery"></a>日历库中的 Subcircle 控件

![MonthDayGallery Subcircle 控件](media/calendar-screen/calendar-month-selected.png)

- 属性：**可见**<br>
    负值

    ```powerapps-dot
    DateAdd( _firstDayInView, ThisItem.Value ) = _dateSelected && Title.Visible
    ```

  当 **\_dateSelected**等效于单元格的日期，并且**标题**控件可见时， **Subcircle**控件可见。 换言之，当单元格为当前选定的日期时，将显示此控件。

## <a name="events-gallery"></a>事件库

![CalendarEventsGallery 控件](media/calendar-screen/calendar-events-gall.png)

- 属性：**项**<br>
    值：对事件库进行排序和筛选的公式：

    ```powerapps-dot
    SortByColumns(
        Filter( MyCalendarEvents,
            Text( Start, DateTimeFormat.ShortDate ) = Text( _dateSelected, DateTimeFormat.ShortDate )
        ),
        "Start"
    )
    ```

   **MyCalendarEvents**集合包含 **\_MinDate**和 **\_maxDate**之间的所有事件。 为了只显示所选日期的事件，将对**MyCalendarEvents**应用筛选器，以显示开始日期等效于 **\ _dateSelected**的事件。 然后按其开始日期对项进行排序，以按顺序进行排序。

## <a name="next-steps"></a>后续步骤

- [了解有关此屏幕的详细信息](./calendar-screen-overview.md)
- [详细了解 PowerApps 中的 Office 365 Outlook connector](../connections/connection-office365-outlook.md)
- [详细了解 PowerApps 中的 Office 365 用户连接器](../connections/connection-office365-users.md)
