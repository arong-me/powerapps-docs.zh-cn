---
title: 日历屏幕模板 |Microsoft Docs
description: 了解画布应用的日历屏幕模板的工作原理，修改屏幕上，和扩展其作为应用程序的一部分
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/28/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 745b4232a43a06c46866e83ca2452f8a55afeddf
ms.sourcegitcommit: 5e15a1033a68289781f8092fb65c57432501f911
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54459496"
---
# <a name="overview-of-the-calendar-screen-template-for-canvas-apps"></a>画布应用的日历屏幕模板的概述

在画布应用中，添加一个显示用户从其 Office 365 Outlook 帐户即将发生的事件的日历屏幕。 用户可以从日历和滚动浏览该天的事件的列表中选择一个日期。 您可以更改的详细信息显示在列表中，添加第二个屏幕，其中显示有关每个事件的更多详细信息、 显示的每个事件的与会者列表和进行其他自定义。

您还可以添加其他基于模板的屏幕，如显示不同的数据从 Office 365[电子邮件](email-screen-overview.md)，[人](people-screen-overview.md)在组织中，并[可用性](meeting-screen-overview.md)的人员用户可能想要邀请参加会议。

本概述介绍了：
> [!div class="checklist"]
> * 如何使用默认日历屏幕。
> * 如何对其进行修改。
> * 如何将其集成到应用。

此屏幕的默认功能的更深入了解，请参阅[日历屏幕引用](calendar-screen-reference.md)。

## <a name="prerequisite"></a>先决条件

如何添加和配置屏幕和其他控件为您熟悉[在 PowerApps 中创建应用](../data-platform-create-app-scratch.md)。

## <a name="default-functionality"></a>默认功能

若要从模板添加日历屏幕：

1. [登录](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 PowerApps，然后创建应用或在 PowerApps Studio 中打开现有应用程序。

    本主题显示手机应用，但概念同样适用于平板电脑应用。

1. 上**主页**选项卡的功能区中，选择**新屏幕** > **日历**。

    默认情况下，查找类似于以下屏幕：

    ![日历屏幕](media/calendar-screen/calendar-initial.png)

1. 若要显示的数据，请在屏幕顶部附近的下拉列表中选择一个选项。

    ![日历屏幕后加载已完成](./media/calendar-screen/calendar-screen.png)

几个有用的说明：

* 默认情况下，选择今天的日期，您可以轻松返回到它通过在右上角选择日历图标。
* 如果选择一个不同的日期，圆周围和浅色矩形 （蓝色表示如果应用的默认主题） 环绕今天的日期。
* 如果某一特定日期计划至少一个事件，小的彩色的圆圈将显示在日历中的相应日期。
* 如果选择为其计划一个或多个事件的日期，这些事件出现在下日历列表。

## <a name="modify-the-screen"></a>修改屏幕

多种常见的方式，可以修改此屏幕的默认功能：

* [指定日历](calendar-screen-overview.md#specify-the-calendar)。
* [显示有关的事件的不同详细信息](calendar-screen-overview.md#show-different-details-about-an-event)。
* [隐藏非阻止性事件](calendar-screen-overview.md#hide-nonblocking-events)。

如果你想要修改的屏幕进一步，使用[日历屏幕引用](./calendar-screen-reference.md)作为指南。

### <a name="specify-the-calendar"></a>指定的日历

如果您已经知道应查看你的用户的日历，可以通过指定该日历，然后发布该应用程序来简化屏幕。 可以将其删除，此更改将不再需要的日历，下拉列表。

1. 设置**[OnStart](../controls/control-screen.md)** 属性的默认屏幕中为此公式应用：

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
    > 此公式略有编辑默认值为**OnSelect**选择日历的下拉列表的属性。 有关该控件的详细信息，请参阅在其部分[日历屏幕引用](./calendar-screen-reference.md#calendar-drop-down)。

1. 替换`{YourCalendarNameHere}`，包括大括号，与你想要显示的日历的名称 (例如，**日历**)。

    > [!IMPORTANT]
    > 以下步骤假定你已将只有一个日历屏幕添加到应用。 如果你已添加多个控件名称 (如**iconCalendar1**) 将结束使用其他号码，并需要进行相应地调整公式。

1. 设置**Y**的属性**iconCalendar1**控制为以下表达式：

    `RectQuickActionBar1.Height + 20`

1. 设置**Y**的属性**LblMonthSelected1**控制为以下表达式：

    `iconCalendar1.Y + iconCalendar1.Height + 20`

1. 设置**文本**的属性**LblNoEvents1**为此值的控件：

    `"No events scheduled"`

1. 设置**Visible**的属性**LblNoEvents1**为以下公式：

    `CountRows(CalendarEventsGallery1.AllItems) = 0 && _calendarVisible`

1. 删除这些控件：

    - **dropdownCalendarSelection1**
    - **LblEmptyState1**
    - **iconEmptyState1**

1. 如果日历屏幕不是默认屏幕，添加一个按钮，以便可以测试应用程序从默认屏幕导航到日历屏幕。

    例如，在添加一个按钮**Screen1**导航到**Screen2**如果日历屏幕添加到从空白创建的应用。

1. 保存应用程序中，并在浏览器中或在移动设备上测试它。

### <a name="show-different-details-about-an-event"></a>显示有关的事件的不同详细信息

默认情况下，在日历中，库名为**CalendarEventsGallery**，显示的开始时间、 持续时间、 使用者，以及每个事件的位置。 你可以配置库以显示任何字段 （如组织者） 的[Office 365 连接器](https://docs.microsoft.com/connectors/office365/#calendareventclientreceive)支持。

1. 在中**CalendarEventsGallery**，请设置**文本**属性的新的或现有标签到`ThisItem`跟一个句点。

    IntelliSense 会列出可以选择的字段。

1. 选择所需的字段。

    标签显示信息的指定的类型。

### <a name="hide-nonblocking-events"></a>隐藏非阻止性事件

在许多办公室，团队成员将发送会议请求以互相通知，当其将为离开办公室时。 若要避免阻止所有人的计划，在发送请求的人员设置其可用性**免费**。 可以通过更新几个属性来隐藏这些事件从日历和库。

1. 设置**项**的属性**CalendarEventsGallery**为以下公式：

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

    在此公式**筛选器**函数会隐藏这些事件不是所选日期已计划的不仅可用性设置为事件**免费**。

1. 在日历中，设置**Visible**的属性**圆圈**控制为以下公式：

    ```powerapps-dot
    CountRows(
        Filter(
            MyCalendarEvents,
            DateValue( Text(Start) ) = DateAdd( _firstDayInView, ThisItem.Value, Days ),
            ShowAs <> "Free"
        )
    ) > 0 && !Subcircle1.Visible && Title2.Visible
    ```
    此公式包含为前面的公式相同的筛选器。 因此，事件指示器圆圈下一个日期，才会显示它具有一个或多个事件将在所选日期以及可用性不是设置为**免费**。

## <a name="integrate-the-screen-into-an-app"></a>集成到应用的屏幕

日历屏幕是功能强大的控件在自己的权限，但它通常作为更大、 更灵活的应用的一部分执行最佳。 可以将此屏幕中通过多种方式，包括添加这些选项的更大应用到：

* [查看事件详细信息](calendar-screen-overview.md#view-event-details)。
* [显示事件的与会者](calendar-screen-overview.md#show-event-attendees)。

### <a name="view-event-details"></a>查看事件详细信息

如果用户选择中的事件**CalendarEventsGallery**，可以打开另一个屏幕，其中显示有关该事件的详细信息。

> [!NOTE]
> 此过程包含动态内容库中显示事件的详细信息，但可以通过采用其他方法来实现类似的结果。 例如，可以改为使用的一系列标签来获取更好地设计控制。

1. 添加一个空白屏幕，名为**EventDetailsScreen**，，其中包含空白的可变高度库和导航返回日历屏幕的按钮。

1. 在可变高度库中，添加**标签**控件和一个**HTML 文本**控件，并设置**AutoHeight**属性均为**true**.

    > [!NOTE]
    > PowerApps 为 HTML 文本，检索每个事件的消息正文，因此您需要显示在该内容**HTML 文本**控件。

1. 设置**Y**的属性**HTML 文本**控制为以下表达式：

    `Label1.Y + Label1.Height + 20`

1. 根据需要以满足样式需要调整其他属性。

    例如，你可能想要添加下一条分隔线**HTML 文本**控件。

1. 设置**项**属性的可变高度库，为以下公式：

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

    此公式创建库动态设置为的字段值的数据 **_selectedCalendarEvent**，其中每次用户选择中的事件设置**CalendarEventsGallery**控件。 您可以扩展此库包含多个字段通过将多个标签添加到它，但此集提供了很好的起点。

1. 使用中的位置的库项，设置**文本**的属性**标签**控制对`ThisItem.Title`，和**HtmlText**属性**HTML 文本**控制对`ThisItem.Value`。

1. 在**CalendarEventsGallery**，请设置**OnSelect**属性**标题**控制为以下公式：

    ```powerapps-dot
    Set( _selectedCalendarEvent, ThisItem );
    Navigate( EventDetailsScreen, None )
    ```

    > [!Note]
    > 而不是使用 **_selectedCalendarEvent**变量，您可以改为使用**CalendarEventsGallery**。选择。

### <a name="show-event-attendees"></a>显示事件的与会者

`Office365.GetEventsCalendarViewV2`操作可检索各种字段的每个事件，包含一组之间用分号分隔的必选和可选与会者。 在此过程中，将分析每个集的与会者、 确定在组织中的与会者，检索任何谁是 Office 365 配置文件。

1. 如果您的应用程序不包含 Office 365 用户连接器[将其添加](../add-data-connection.md)。

1. 若要检索的会议与会者的 Office 365 配置文件，请设置**OnSelect**的属性**标题**控制**CalendarEventsGallery**为以下公式：

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

此列表讨论了每个**ClearCollect**操作：

- ClearCollect(AttendeeEmailsTemp)
    ```powerapps-dot
    ClearCollect( AttendeeEmailsTemp,
        Filter(
            Split( ThisItem.RequiredAttendees & ThisItem.OptionalAttendees, ";" ), 
            !IsBlank( Result)
        )
    );
    ```

    此公式将连接成单个字符串必选和可选与会者，然后将该字符串拆分为单个地址在每个分号。 该公式，然后筛选出空白值从这组并将其他值添加到名为的集合**AttendeeEmailsTemp**。

- ClearCollect(AttendeeEmails)
    ```powerapps-dot
    ClearCollect( AttendeeEmails,
        AddColumns( AttendeeEmailsTemp, 
            "InOrg",
            Upper( _userDomain ) = Upper( Right( Result, Len(Result) - Find("@", Result) ) )
        )
    );
    ```
    此公式大致确定你的组织中是否为某个出席者。 定义 **_userDomain**是只需运行该应用程序的人员的电子邮件地址中的域 URL。 该行将创建一个额外的 true/false 列，名为**InOrg**，在**AttendeeEmailsTemp**集合。 此列包含 **，则返回 true**如果**userDomain**等效于该特定行中的电子邮件地址的域 URL **AttendeeEmailsTemp**。

    这种方法并不总是准确，但是它变得相当接近。 例如，在组织中的某些与会者可能具有电子邮件地址，如Jane@OnContoso.com，而 **_userDomain**为 Contoso.com。 应用程序用户和 Jane 可能在同一家公司工作，但其电子邮件地址中有细微的变体。 这种情况，你可能想要使用此公式：

    `Upper(_userDomain) in Upper(Right(Result, Len(Result) - Find("@", Result)))`

    但是，此公式与类似的电子邮件地址进行匹配Jane@NotTheContosoCompany.com与 **_userDomain**如 Contoso.com，但这些人不起作用同一公司的。

- ClearCollect(MyPeople)

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
    若要检索 Office 365 配置文件，必须使用[Office365Users.UserProfile](https://docs.microsoft.com/connectors/office365users/#userprofile)或[Office365Users.UserProfileV2](https://docs.microsoft.com/connectors/office365users/#userprofile)操作。 这些操作首先收集用户的组织中的与会者所有 Office 365 配置文件然后 operations 添加几个字段从组织外部的与会者。 因为这两项分离到不同的操作**ForAll**循环并不能保证顺序。 因此， **ForAll**可能会先收集从组织外部的某个出席者。 在此情况下，架构**MyPeople**仅包含**DisplayName**， **Id**， **JobTitle**，和**UserPrincipalName**. 但是，用户配置文件操作检索多比这更丰富的数据。 因此，强制**MyPeople**集合中添加其他配置文件之前的 Office 365 配置文件。

    > [!NOTE]
    > 您可以获得相同的结果仅有一个**ClearCollect**函数：

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

若要完成此练习：

1. 添加一个屏幕，为其包含一个库**项**属性设置为**MyPeople**。

1. 中**OnSelect**属性**标题**控制**CalendarEventsGallery**，将添加**Navigate**函数在屏幕上，您在上一步中创建。

## <a name="next-steps"></a>后续步骤

* [查看此屏幕的参考文档](calendar-screen-reference.md)。
* [了解有关 Office 365 Outlook 连接器的详细信息](../connections/connection-office365-outlook.md)。
* [了解有关 Office 365 用户连接器的详细](../connections/connection-office365-users.md)。
