---
title: 日历-屏幕模板 |Microsoft Docs
description: 了解 canvas 应用的日历屏幕模板的工作原理，修改屏幕，并将其作为应用的一部分进行扩展
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/28/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 945a4fd3c017363a8c43171c8e891e0c32c84a0f
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675224"
---
# <a name="overview-of-the-calendar-screen-template-for-canvas-apps"></a>用于画布应用的日历屏幕模板概述

在画布应用中，添加一个日历屏幕，其中显示来自其 Office 365 Outlook 帐户的即将到来的事件的用户。 用户可以从日历中选择日期并滚动当天事件的列表。 您可以更改列表中显示的详细信息，添加第二个屏幕，显示每个事件的详细信息，显示每个事件的与会者列表，并进行其他自定义。

你还可以添加其他基于模板的屏幕，这些屏幕显示 Office 365 中的不同数据，如[电子邮件](email-screen-overview.md)、组织中的[人员](people-screen-overview.md)，以及用户可能想要邀请参加会议的人员的[可用性](meeting-screen-overview.md)。

本概述介绍了以下内容：
> [!div class="checklist"]
> * 如何使用默认日历屏幕。
> * 如何修改它。
> * 如何将其集成到应用中。

若要深入了解此屏幕的默认功能，请参阅[日历屏幕参考](calendar-screen-reference.md)。

## <a name="prerequisite"></a>先决条件

熟悉如何[在 PowerApps 中创建应用](../data-platform-create-app-scratch.md)时添加和配置屏幕和其他控件。

## <a name="default-functionality"></a>默认功能

从模板添加日历屏幕：

1. [登录](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 power apps，然后在 Power apps Studio 中创建应用或打开现有应用。

    本主题演示了一个手机应用，但相同的概念也适用于平板电脑应用。

1. 在功能区的 "**主页**" 选项卡上，选择 "**新屏幕** > **日历**"。

    默认情况下，屏幕的外观如下所示：

    ![日历屏幕](media/calendar-screen/calendar-initial.png)

1. 若要显示数据，请在屏幕顶部附近的下拉列表中选择一个选项。

    ![加载完成后的日历屏幕](./media/calendar-screen/calendar-screen.png)

一些有用的说明：

* 默认情况下，将选择今天的日期，并且可以通过选择右上角的日历图标轻松返回到该日期。
* 如果选择其他日期，则会在其两侧加一个圆圈，并使用浅色矩形（如果应用了默认主题，则为蓝色）环绕当天的日期。
* 如果为某个特定日期计划了至少一个事件，则日历中该日期下将出现一个小的彩色圆圈。
* 如果选择一个或多个事件的计划日期，事件会出现在日历下的列表中。

## <a name="modify-the-screen"></a>修改屏幕

您可以通过几种常见方法修改此屏幕的默认功能：

* [指定日历](calendar-screen-overview.md#specify-the-calendar)。
* [显示事件的不同详细信息](calendar-screen-overview.md#show-different-details-about-an-event)。
* [隐藏非阻止事件](calendar-screen-overview.md#hide-nonblocking-events)。

如果要进一步修改屏幕，请使用[日历屏幕参考](./calendar-screen-reference.md)作为指南。

### <a name="specify-the-calendar"></a>指定日历

如果已知道用户应该查看的日历，则可以通过在发布应用之前指定该日历来简化屏幕。 此更改消除了对日历下拉列表的需求，因此你可以将其删除。

1. 在应用中将默认屏幕的 **[OnStart](../controls/control-screen.md)** 属性设置为以下公式：

    ```powerapps-dot
    Set( _userDomain, Right( User().Email, Len( User().Email ) - Find( "@", User().Email ) ) );
    Set( _dateSelected, Today() );
    Set( _firstDayOfMonth, DateAdd( Today(), 1 - Day( Today() ), Days ) );
    Set( _firstDayInView, 
        DateAdd( _firstDayOfMonth, -( Weekday( _firstDayOfMonth) - 2 + 1 ), Days )
    );
    Set( _lastDayOfMonth, DateAdd( DateAdd( _firstDayOfMonth, 1, Months ), -1, Days ) );
    Set( _calendarVisible, false );
    Set( _myCalendar, 
        LookUp( Office365.CalendarGetTables().value, DisplayName = "{YourCalendarNameHere}" )
    );
    Set( _minDate, 
        DateAdd( _firstDayOfMonth, -( Weekday(_firstDayOfMonth) - 2 + 1 ), Days )
    );
    Set( _maxDate, 
        DateAdd(
            DateAdd( _firstDayOfMonth, -( Weekday(_firstDayOfMonth) - 2 + 1 ), Days ),
            40, 
            Days 
        )
    );
    ClearCollect( MyCalendarEvents, 
        Office365.GetEventsCalendarViewV2( _myCalendar.Name, 
            Text( _minDate, UTC ), 
            Text( _maxDate, UTC ) 
        ).value
    );
    Set( _calendarVisible, true )
    ```

    > [!NOTE]
    > 此公式从用于选择日历的下拉列表的 " **OnSelect** " 属性的默认值进行了略微编辑。 有关该控件的详细信息，请参阅[日历屏幕参考](./calendar-screen-reference.md#calendar-drop-down)中的部分。

1. 将 `{YourCalendarNameHere}`（包括大括号）替换为要显示的日历的名称（例如， **calendar**）。

    > [!IMPORTANT]
    > 以下步骤假定你已将一个日历屏幕添加到应用。 如果您添加了多个控件名称（如**iconCalendar1**），则会以不同数字结束，并且您需要相应地调整公式。

1. 将**iconCalendar1**控件的**Y**属性设置为以下表达式：

    `RectQuickActionBar1.Height + 20`

1. 将**LblMonthSelected1**控件的**Y**属性设置为以下表达式：

    `iconCalendar1.Y + iconCalendar1.Height + 20`

1. 将**LblNoEvents1**控件的**Text**属性设置为以下值：

    `"No events scheduled"`

1. 将**LblNoEvents1**的**Visible**属性设置为以下公式：

    `CountRows(CalendarEventsGallery1.AllItems) = 0 && _calendarVisible`

1. 删除这些控件：

    - **dropdownCalendarSelection1**
    - **LblEmptyState1**
    - **iconEmptyState1**

1. 如果日历屏幕不是默认屏幕，请添加一个按钮，该按钮从默认屏幕导航到 "日历" 屏幕，以便你可以测试应用程序。

    例如，在**Screen1**上添加一个按钮，导航到**Screen2** （如果已将 "日历" 屏幕添加到从空白创建的应用）。

1. 保存该应用，然后在浏览器或移动设备上对其进行测试。

### <a name="show-different-details-about-an-event"></a>显示事件的不同详细信息

默认情况下，日历下名为**CalendarEventsGallery**的库显示开始时间、持续时间、主题和每个事件的位置。 你可以将库配置为显示[Office 365 连接器](https://docs.microsoft.com/connectors/office365/#calendareventclientreceive)支持的任何字段（如管理器）。

1. 在**CalendarEventsGallery**中，将新的或现有标签的 " **Text** " 属性设置为 `ThisItem` 后跟一个句点。

    IntelliSense 列出了可以选择的字段。

1. 选择所需的字段。

    标签显示您指定的信息的类型。

### <a name="hide-nonblocking-events"></a>隐藏非阻止事件

在许多办公室中，当他们离开办公室时，团队成员将发送会议请求以通知对方。 若要避免阻止所有人的计划，发送请求的用户可将其可用性设置为 "**免费**"。 您可以通过更新几个属性，从日历和库中隐藏这些事件。

1. 将**CalendarEventsGallery**的**Items**属性设置为以下公式：

    ```powerapps-dot
    SortByColumns(
        Filter(
            MyCalendarEvents,
            Text( Start, DateTimeFormat.ShortDate ) = 
                Text( _dateSelected, DateTimeFormat.ShortDate ),
            ShowAs <> "Free"
        ),
        "Start"
    )
    ```

    在此公式中，**筛选器**函数不仅隐藏那些计划用于非所选日期的事件，而且还隐藏可用性设置为 "**免费**" 的事件。

1. 在日历中，将**Circle**控件的**Visible**属性设置为以下公式：

    ```powerapps-dot
    CountRows(
        Filter(
            MyCalendarEvents,
            DateValue( Text(Start) ) = DateAdd( _firstDayInView, ThisItem.Value, Days ),
            ShowAs <> "Free"
        )
    ) > 0 && !Subcircle1.Visible && Title2.Visible
    ```
    此公式包含与上一个公式相同的筛选器。 因此，仅当某个日期有一个或多个处于选定日期的事件并且其可用性未设置为 "**免费**" 时，才会在该日期下显示事件指示器圆圈。

## <a name="integrate-the-screen-into-an-app"></a>将屏幕集成到应用中

日历屏幕是一种功能强大的控件绑定，但它通常作为更大、更通用的应用程序的一部分执行。 可以通过多种方式将此屏幕集成到较大的应用程序中，包括添加以下选项：

* [查看事件详细信息](calendar-screen-overview.md#view-event-details)。
* [显示事件参与者](calendar-screen-overview.md#show-event-attendees)。

### <a name="view-event-details"></a>查看事件详细信息

如果用户在**CalendarEventsGallery**中选择事件，可以打开另一个屏幕，其中显示了有关该事件的详细信息。

> [!NOTE]
> 此过程在库中显示包含动态内容的事件详细信息，但您可以通过采用其他方法实现类似的结果。 例如，您可以通过使用一系列标签来获得更多的设计控制。

1. 添加一个名为 " **EventDetailsScreen**" 的空白屏幕，其中包含一个空白的灵活高度库和一个向后定位到日历屏幕的按钮。

1. 在灵活高度库中，添加 "**标签**" 控件和 " **HTML 文本**" 控件，并将 " **AutoHeight** " 属性设置为 " **true**"。

    > [!NOTE]
    > Power Apps 以 HTML 文本形式检索每个事件的消息正文，因此需要在**html 文本**控件中显示该内容。

1. 将**HTML 文本**控件的**Y**属性设置为以下表达式：

    `Label1.Y + Label1.Height + 20`

1. 根据需要调整其他属性，以满足您的风格需求。

    例如，你可能想要在**HTML 文本**控件下面添加分隔行。

1. 将可变高度库的**Items**属性设置为以下公式：

    ```powerapps-dot
    Table(
        { Title: "Subject", Value: _selectedCalendarEvent.Subject },
        { 
            Title: "Time", 
            Value: _selectedCalendarEvent.Start & " - " & _selectedCalendarEvent.End 
        },
        { Title: "Body", Value: _selectedCalendarEvent.Body }
    )
    ```

    此公式将创建一个动态数据库，其设置为 **_selectedCalendarEvent**的字段值，每次用户在**CalendarEventsGallery**控件中选择一个事件时，都会设置此值。 您可以通过向此库添加更多标签来扩展此库以包含更多字段，但这会提供一个很好的起点。

1. 将库项设置为就地后，将 "**标签**" 控件的 " **Text** " 属性设置为 "`ThisItem.Title`"，并将**HTML 文本**控件的 " **HtmlText** " 属性设置为 "`ThisItem.Value`"。

1. 在**CalendarEventsGallery**中，将 "**标题**" 控件的 " **OnSelect** " 属性设置为以下公式：

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    Navigate( EventDetailsScreen, None )
    ```

    > [!Note]
    > 您可以改为使用**CalendarEventsGallery**，而不是使用 **_selectedCalendarEvent**变量。选择.

### <a name="show-event-attendees"></a>显示事件与会者

`Office365.GetEventsCalendarViewV2` 操作将检索每个事件的各种字段，包括一组以分号分隔的必需和可选的与会者。 在此过程中，你将分析每组与会者，确定组织中的哪些与会者，并检索任何用户的 Office 365 配置文件。

1. 如果你的应用不包含 Office 365 用户连接器，请[添加它](../add-data-connection.md)。

1. 若要检索会议与会者的 Office 365 配置文件，请将**CalendarEventsGallery**中**标题**控件的**OnSelect**属性设置为以下公式：

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ),
            !IsBlank( Result )
        )
    );
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len( Result ) - Find( "@", Result ) ) )
        )
    );
    ClearCollect( MyPeople,
        ForAll( AttendeeEmails, If( InOrg, Office365Users.UserProfile( Result ) ) ) 
    );
    Collect( MyPeople,
        ForAll( AttendeeEmails,
            If( !InOrg, 
                { DisplayName: Result, Id: "", JobTitle: "", UserPrincipalName: Result }
            )
        )
    )
    ```

此列表讨论了每个**ClearCollect**操作的作用：

- ClearCollect （AttendeeEmailsTemp）
    ```powerapps-dot
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ), 
            !IsBlank( Result)
        )
    );
    ```

    此公式将必需的和可选的与会者连接到单个字符串中，然后将该字符串拆分为每个分号的各个地址。 然后，该公式从该集筛选出空值，并将其他值添加到名为**AttendeeEmailsTemp**的集合中。

- ClearCollect （AttendeeEmails）
    ```powerapps-dot
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len(Result) - Find("@", Result) ) )
        )
    );
    ```
    此公式大致确定与会者是否在你的组织中。 **_UserDomain**的定义只是在运行应用程序的用户的电子邮件地址中的域 URL。 此行在**AttendeeEmailsTemp**集合中创建一个名为**InOrg**的额外 true/false 列。 如果**userDomain**等效于**AttendeeEmailsTemp**特定行中的电子邮件地址的域 URL，则此列包含**true** 。

    此方法并非总是准确的，但会非常接近。 例如，你所在组织中的某些与会者可能有类似 Jane@OnContoso.com的电子邮件地址，而 **_userDomain**是 Contoso.com。 应用用户和 Jane 可能在同一公司工作，但其电子邮件地址略有不同。 对于这种情况，可能需要使用以下公式：

    `Upper(_userDomain) in Upper(Right(Result, Len(Result) - Find("@", Result)))`

    但是，此公式会将类似于 Jane@NotTheContosoCompany.com 的电子邮件地址与 **_userDomain** （如 Contoso.com）进行匹配，而这些人在同一公司工作不起作用。

- ClearCollect （MyPeople）

    ```powerapps-dot
    ClearCollect( MyPeople,
        ForAll( AttendeeEmails, 
            If( InOrg, 
                Office365Users.UserProfile( Result )
            )
        )
    );
    Collect( MyPeople,
        ForAll( AttendeeEmails,
            If( !InOrg, 
                { 
                    DisplayName: Result, 
                    Id: "", 
                    JobTitle: "", 
                    UserPrincipalName: Result
                }
            )
        )
    );
    ```
    若要检索 Office 365 配置文件，必须使用[Office365Users](https://docs.microsoft.com/connectors/office365users/#userprofile)或[UserProfileV2](https://docs.microsoft.com/connectors/office365users/#userprofile)操作。 这些操作首先收集用户所在组织中的与会者的所有 Office 365 配置文件。然后，操作会为组织外的与会者添加几个字段。 由于**ForAll**循环不保证顺序，因此可将这两个项分成不同的操作。 因此， **ForAll**可能首先从组织外部收集与会者。 在这种情况下， **MyPeople**的架构只包含**DisplayName**、 **Id**、 **JobTitle**和**UserPrincipalName**。 但是，UserProfile 操作检索的数据要多得多。 因此，在其他配置文件之前强制**MyPeople**集合添加 Office 365 配置文件。

    > [!NOTE]
    > 只需要一个**ClearCollect**函数即可获得相同的结果：

    ```powerapps-dot
    ClearCollect( MyPeople, 
        ForAll(
            AddColumns(
                Filter(
                    Split(
                        ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, 
                        ";"
                    ), 
                    !IsBlank( Result )
                ), 
                "InOrg", _userDomain = Right( Result, Len( Result ) - Find( "@", Result ) )
            ), 
            If( InOrg, 
                Office365Users.UserProfile( Result ), 
                { 
                    DisplayName: Result, 
                    Id: "", 
                    JobTitle: "", 
                    UserPrincipalName: Result, 
                    Department: "", 
                    OfficeLocation: "", 
                    TelephoneNumber: ""
                }
            )
        )
    )
    ```

完成本练习：

1. 添加一个屏幕，其中包含将**Items**属性设置为**MyPeople**的库。

1. 在**CalendarEventsGallery**的 "**标题**" 控件的 " **OnSelect** " 属性中，将一个**导航**函数添加到在上一步中创建的屏幕上。

## <a name="next-steps"></a>后续步骤

* [查看此屏幕的参考文档](calendar-screen-reference.md)。
* [了解有关 Office 365 Outlook connector 的详细信息](../connections/connection-office365-outlook.md)。
* [了解有关 Office 365 用户连接器的详细信息](../connections/connection-office365-users.md)。
