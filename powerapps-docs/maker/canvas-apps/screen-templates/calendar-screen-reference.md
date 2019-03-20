---
title: 画布应用的日历屏幕模板引用 |Microsoft Docs
description: 了解 PowerApps 中的画布应用的日历屏幕模板工作原理详细的信息。
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/31/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: abf88db2bfb97a6541ee638ba8be5af27c20bc5f
ms.sourcegitcommit: 5e15a1033a68289781f8092fb65c57432501f911
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54459565"
---
# <a name="reference-information-about-the-calendar-screen-template-for-canvas-apps"></a>有关画布应用的日历屏幕模板的参考信息

对于在 PowerApps 中的画布应用，了解日历屏幕模板中的每个重要控件如何影响屏幕的整体默认功能。 此深入探讨了行为公式以及其他属性，用于确定控件如何响应用户输入的值。 此屏幕的默认功能的综合讨论，请参阅[日历屏幕概述](calendar-screen-overview.md)。

本主题重点介绍一些重要的控件，并介绍的各种属性的表达式或公式 (如**项**并**OnSelect**) 这些控件的设置：

- [日历下拉列表 (dropdownCalendarSelection)](#calendar-drop-down)
- [日历图标 (iconCalendar)](#calendar-icon)
- [上一步月 v 形图标 (iconPrevMonth)](#previous-month-chevron)
- [下个月 v 形图标 (iconNextMonth)](#next-month-chevron)
- [日历库 (MonthDayGallery) （+ 子控件）](#calendar-gallery)
- [事件库 (CalendarEventsGallery)](#events-gallery)

## <a name="prerequisite"></a>先决条件

如何添加和配置屏幕和其他控件为您熟悉[在 PowerApps 中创建应用](../data-platform-create-app-scratch.md)。

## <a name="calendar-drop-down"></a>日历下拉列表

![dropdownCalendarSelection 控件](media/calendar-screen/calendar-dropdown.png)

- 属性：**项**<br>
    值： `Office365.CalendarGetTables().value`

    此值是检索应用程序用户的 Outlook 日历连接器操作。 您可以看到[值](https://docs.microsoft.com/connectors/office365/#entitylistresponse[table])，此操作用于检索。

- 属性：**OnChange**<br>值： `Select(dropdownCalendarSelection)`

    当用户选择一个选项在列表中，在该控件的函数**OnSelect**属性运行。

- 属性：**OnSelect**<br>
    值：**如果**函数，在下面的代码块中出现，以及几个其他的函数后，显示在代码块中。

   公式将会运行只在首次打开应用后，用户，操作选项选择下拉列表中的此部分：

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

    前面的代码中定义以下变量：
    
  - **\_userDomain**:应用用户的公司域，具体体现在用户的电子邮件地址。
  - **\_dateSelected**:今天的日期 （默认）。 日历库突出显示此日期和事件库将显示该日期的计划的事件。
  - **\_firstDayOfMonth**:当前月份的第一天。 因为`(Today + (1 - Today)) = Today - Today + 1 = 1`，则此**DateAdd**函数始终返回月份的第一天。
  - **\_firstDayInView**:日历库可以显示第一天。 此值不相同的月份的第一天，除非在星期日开始月份。 为了防止显示上一个月份的值一整周 **\_firstDayInView**是`_firstDayOfMonth - Weekday(_firstDayOfMonth) + 1`。
  - **\_lastDayOfMonth**:当前月份，等同于下个月，减去一天的第一天的最后一天。

   之后的函数**如果**函数运行时用户 （而不仅仅是第一次用户打开应用程序） 日历下拉列表中选择一个选项：

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

    前面的代码中定义这些变量和一个集合：

    - **\_calendarVisible**:设置为**false** ，以便加载新选择时，不会显示日历。
    - **\_showLoading**:设置为 **，则返回 true** ，以便加载新选择时，将显示加载指示器。
    - **\_myCalendar**:设置的当前值为**日历下拉**控件，以便检索从正确的日历事件。
    - **\_minDate**:设置为相同的值 **\_firstDayInView**。 此变量确定哪些事件已从 Outlook 检索并缓存在应用程序。
    - **\_maxDate**:设置为在日历中的最后一个可查看天。 该公式是`_firstDayInView + 40`。 日历显示最多为 41 天，因此 **\_maxDate**变量始终反映最后一可查看天，并确定哪些事件已从 Outlook 检索并缓存在应用程序。
    - **MyCalendarEvents**:从所选日历中，范围从设置到用户的事件的集合 **\_minDate**到 **\_maxDate**。
    - **\_showLoading**:设置为**false**; **\_calendarVisible**设置为**true**加载其他所有内容之后。

## <a name="calendar-icon"></a>日历图标

![iconCalendar 控件](media/calendar-screen/calendar-today-icon.png)

- 属性：**OnSelect**<br>
    值：四个**设置**重置为今天的日期的日历库的函数：

    ```powerapps-dot
    Set( _dateSelected, Today() );
    Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days) );
    Set( _firstDayInView, DateAdd(_firstDayOfMonth, -(Weekday( _firstDayOfMonth ) - 2 + 1), Days));
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) )
    ```

    前面的代码将重置所需的显示正确的日历视图的所有日期变量：

    - **\_dateSelected**重置为今天。
    - **\_firstDayOfMonth**重置为今天的月的第一天。
    - **\_firstDayInView**重置为选中今天的月的第一天可查看。
    - **\_lastDayOfMonth**重置为今天的月份的最后一天。

    [**日历下拉**](#calendar-drop-down)本主题的部分说明了更多详细信息中的这些变量。

## <a name="previous-month-chevron"></a>上一步月 v 形图标

![iconPrevMonth 控件](media/calendar-screen/calendar-back.png)

- 属性：**OnSelect**<br>值：四个**设置**函数和一个**如果**日历库中显示上一个月份的函数：

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
    > 定义 **\_firstDayOfMonth**，  **\_firstDayInView**，以及 **\_lastDayOfMonth**几乎相同在中[日历下拉](#calendar-drop-down)本主题的部分。

    每当用户选择上一个月份 v 形展开按钮时，运行前面的代码的前三行。 该代码设置显示正确的日历视图所需的变量。 仅当用户以前未选择在所选日历这个月，将运行的剩余代码。

    如果出现这种情况，  **\_minDate**是在上一个月份显示时显示的第一天。 用户选择图标，然后 **\_minDate**的最小可能值为当前月份的 23。 (如果 on a 星期六，3 月 1 日降 **\_firstDayInView**年 3 月是 2 月 23 日。)这意味着，如果用户尚未选择了，本月 **\_minDate**大于新 **\_firstDayOfMonth**，以及**如果**函数返回 **，则返回 true**。 更新代码运行，并且集合和变量：

    - **MyCalendarEvents**与所选日历中检索事件[Office365.GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-)操作。 日期范围为从 **\_firstDayInView**日期并 **\_minDate** -1。 因为**MyCalendarEvents**已包含在事件 **\_minDate**日期，从这一天中此新的日期范围的最大值中减去 1。

    - **\_minDate**设置为当前 **\_firstDayInView**由于这是为其检索事件的第一个日期。 如果用户返回到此日期的上一个月份的 v 形图标，选择**如果**函数将返回**false**; 代码不会运行，因为此视图的事件已缓存在**MyCalendarEvents**。

## <a name="next-month-chevron"></a>下个月 v 形图标

![iconNextMonth 控件](media/calendar-screen/calendar-forward.png)

- 属性：**OnSelect**<br>
    值：四个**设置**函数和一个**如果**显示下个月日历库中的函数：

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
    > 定义 **\_firstDayOfMonth**，  **\_firstDayInView**，以及 **\_lastDayOfMonth**几乎相同在中[日历下拉](#calendar-dropdown)本主题的部分。

    前面的代码的前三个行，其运行时用户选择的下个月 v 形图标，设置显示正确的日历视图所需的变量。 仅当用户以前未选择在所选日历这个月，将运行的剩余代码。

    在这种情况下，  **\_maxDate**是在上一个月份显示时显示的最后一天。 用户选择下一个月的 v 形图标，然后 **\_maxDate**下个月 13 的最大可能值。 (2 月 1 日不再处于时，在非-闰年星期日，  **\_maxDate**是年 3 月 13 日，即 **\_firstDayInView** + 40 天。)这意味着，如果用户尚未选择了，本月 **\_maxDate**大于新 **\_lastDayOfMonth**，以及**如果**函数返回 **，则返回 true**。 更新代码运行，并且集合和变量：

    - **MyCalendarEvents**与所选日历中检索事件[Office365.GetEventsCalendarViewV2](https://docs.microsoft.com/connectors/office365/#get-calendar-view-of-events--v2-)操作。 日期范围为从 **\_maxDate** + 1 day 和 **\_firstDayInView** + 40 天。 因为**MyCalendarEvents**已包含在事件 **\_minDate**日期，1 添加到该日期在此新的日期范围内的最小值。 **\_firstDayInView** + 40 为的公式 **\_maxDate**，因此范围中的第二个日期是新 **\_maxDate**。

    - **\_maxDate**设置为 **\_firstDayInView** + 40 天由于这是最后一天的事件已检索到。 如果用户返回到此日期的下个月的 v 形图标，选择**如果**函数将返回**false**; 代码不会运行，因为此视图的事件已缓存在**MyCalendarEvents**。

## <a name="calendar-gallery"></a>日历库

![MonthDayGallery 控件](media/calendar-screen/calendar-month-gall.png)

- 属性：**项**<br>
    值： `[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,
    20,21,22,23,24,25,26,27,28,29,30,31,32,33,34,35,36,37,38,39,40,41]`
  
  0 到 41 的一套用于日历库中的项因为在最坏的情况的方案中，将具有日历视图以显示 42 全天。 每月的第一个发生在星期六，每月的最后一个星期日发生时，将发生这种情况。 在这种情况下，该日历显示出六天的上个月的第一个月的所在行中，从下个月包含的该月最后一个行中的六天。 这是 42 唯一值，其中 30 个所选月。

- 属性：**WrapCount**<br>
    值： `7`

  此值反映了七个星期。

### <a name="title-control-in-the-calendar-gallery"></a>日历库中的标题控件

![MonthDayGallery 标题控件](media/calendar-screen/calendar-month-text.png)

- 属性：**文本**<br>
    值： `Day( DateAdd( _firstDayInView, ThisItem.Value, Days ) )`

    请记住，  **\_firstDayInView**定义为 (**\_firstDayOfMonth** -其 weekday 的值) + 1。 这让你知道 **\_firstDayInView**始终表示星期日，和 **\_firstDayOfMonth**中的第一行始终是**MonthDayGallery**。 由于这两个事实 **\_firstDayInView**始终位于的第一个单元格**MonthDayGallery**。 **ThisItem.Value**是该单元中的数字**MonthDayGallery**项属性。 因此，采用 **\_firstDayInView**作为起点，每个单元格显示的增量 **\_firstDayInView** + 其各自的单元格的值。

- 属性：**填充**<br>
    值：一个**如果**函数：

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

  中的说明所述**文本**属性，`DateAdd(_firstDayInView, ThisItem.Value)`表示一天中可见的单元格。 考虑到这，前面的代码中执行这些比较：
  1. 如果单元格的值是今天的日期，等效于此单元格 **\_dateSelected**，不提供填充值。
  1. 如果该单元格的值为今天的日期，但不是等效于 **\_dateSelected**，提供**ColorFade**填充。
  1. 最后一次比较不是以明文。 它是单元格中的实际文本值与单元格项 （上显示的数字） 和物料编号的值之间的比较。<br>

      若要更好地理解这一点，请考虑 2018 年 9 月，每月开始 on a 星期六和星期日结束。 在这种情况下，日历是显示在第一行中，通过第 31 年 8 月和日的 9 月 26 日和`Abs(Title.Text - ThisItem.Value) = 26`直到 9 月 1 日。 然后`Abs(Title.Text - ThisItem.Value) = 5`。 它将保持 5 之前的日历，后者将显示 30 年 9 月和 10 月 1 日至 6 日中的最后一行。 在于`Abs(Title.Text - ThisItem.Value)`仍将 5 年 9 月 30 日，但会在 35 年 10 月日期。<br>

      这是模式：显示从上一个月份，天`Abs(Title.Text - ThisItem.Value)`将始终等于`Title.Text`上显示的第一天的值。 显示在下个月，天`Abs(Title.Text - ThisItem.Value)`将始终等于**MonthDayGallery**项 （在此情况下，10 月 1 日） 减 1 的该月的第一个单元格的值。 并且最重要的是，对于显示在当前所选月中的天`Abs(Title.Text - ThisItem.Value)`也始终等于的值减 1 的该月的第一项并不会超过 5，如前面的示例所示。 因此它是完全有效，编写公式作为`Abs(Title.Text - ThisItem.Value) > 5`。

      此语句检查日期值是否为当前所选月之外。 如果是，**填充**是部分不透明的灰色。

    > [!NOTE]
    > 可以自行检查此最后一次比较的有效性，通过插入**标签**控制到库，并设置其**文本**属性设置为此值：<br>`Abs(Title.Text - ThisItem.Value)`.

- 属性：**Visible**<br>
    值：

    ```powerapps-dot
    !(
        DateAdd( _firstDayInView, ThisItem.Value, Days ) - 
            Weekday( DateAdd( _firstDayInView, ThisItem.Value,Days ) ) + 1 
        > _lastDayOfMonth
    )
    ```

    前面的语句会检查该单元格是否位于当前所选月份中的任何天发生的位置的行。 请回顾一下 weekday 的值为日期值的任何一天中减去，始终添加 1 返回的行中的第一项驻留在的那一天。 使此语句将检查后可查看月的最后一天是否行中的第一天。 如果是，它会出现因为整行包含以下月份中的天。

- 属性：**OnSelect**<br>
    值：一个**设置**设置的函数 **\_dateSelected**变量到所选单元格的日期：

    ```powerapps-dot
    Set( _dateSelected, DateAdd( _firstDayInView, ThisItem.Value, Days ) )
    ```

### <a name="circle-control-in-the-calendar-gallery"></a>日历库中的圆形控件

![MonthDayGallery 圆形控件](media/calendar-screen/calendar-month-event.png)

- 属性：**Visible**<br>
    值：一个公式来确定是否为所选日期计划任何事件，以及是否**Subcircle**并**标题**控件是否可见：

    ```powerapps-dot
    CountRows(
        Filter( MyCalendarEvents, 
            DateValue( Text( Start ) ) = DateAdd( _firstDayInView, ThisItem.Value, Days )
        )
    ) > 0 && !Subcircle.Visible && Title.Visible
    ```

    **圆圈**控件是否可见如果**启动**任何事件相当于该单元格的日期字段如果**Title**控件是否可见，并且如果**Subcircle**控件不可见。 换而言之，此控件，则可以看到至少一个事件发生在此日期，这一天未选中。 如果选择它，则该天的事件将显示在**CalendarEventsGallery**控件。

### <a name="subcircle-control-in-the-calendar-gallery"></a>Subcircle 日历库中的控件

![MonthDayGallery Subcircle 控件](media/calendar-screen/calendar-month-selected.png)

- 属性：**Visible**<br>
    值：

    ```powerapps-dot
    DateAdd( _firstDayInView, ThisItem.Value ) = _dateSelected && Title.Visible
    ```

  **Subcircle**时，控件是否可见 **\_dateSelected**等效于该单元格的日期和**标题**控件是否可见。 换而言之，此控件显示当前所选的日期单元格时。

## <a name="events-gallery"></a>事件库

![CalendarEventsGallery 控件](media/calendar-screen/calendar-events-gall.png)

- 属性：**项**<br>
    值：一个公式来排序和筛选器事件库：

    ```powerapps-dot
    SortByColumns(
        Filter( MyCalendarEvents,
            Text( Start, DateTimeFormat.ShortDate ) = Text( _dateSelected, DateTimeFormat.ShortDate )
        ),
        "Start"
    )
    ```

   **MyCalendarEvents**集合包含之间的所有事件 **\_minDate**并 **\_maxDate**。 为了显示仅选定的日期的事件，筛选器应用上**MyCalendarEvents**来显示事件具有开始日期等于**\ _dateSelected**。 项然后按其开始日期，以将其放在连续顺序排序。

## <a name="next-steps"></a>后续步骤

- [了解有关此屏幕的详细信息](./calendar-screen-overview.md)
- [了解有关 PowerApps 中的 Office 365 Outlook 连接器的详细信息](../connections/connection-office365-outlook.md)
- [了解有关 PowerApps 中的 Office 365 用户连接器的详细信息](../connections/connection-office365-users.md)
