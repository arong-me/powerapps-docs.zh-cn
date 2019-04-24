---
title: 画布应用的会议屏幕模板引用 |Microsoft Docs
description: 了解 PowerApps 中的画布应用的会议屏幕模板工作原理详细的信息
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a7559f84b43d3c0372dea71d49c35461ba9d4e57
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61539378"
---
# <a name="reference-information-about-the-meeting-screen-template-for-canvas-apps"></a>有关画布应用的会议屏幕模板的参考信息

对于在 PowerApps 中的画布应用，了解会议屏幕模板中的每个重要控件如何影响屏幕的整体默认功能。 此深入探讨了行为公式以及其他属性，用于确定控件如何响应用户输入的值。 此屏幕的默认功能的综合讨论，请参阅[会议屏幕概述](meeting-screen-overview.md)。

本主题重点介绍一些重要的控件，并介绍的各种属性的表达式或公式 (如**项**并**OnSelect**) 这些控件的设置：

* [邀请选项卡 (LblInviteTab)](#invite-tab)
* [计划选项卡 (LblScheduleTab)](#schedule-tab)
* [文本搜索框](#text-search-box)
* [添加图标 (AddIcon)](#add-icon)
* [用户浏览库](#people-browse-gallery)（+ 子控件）
* [会议的人员库](#meeting-people-gallery)（+ 子控件）
* [会议日期选取器 (MeetingDateSelect)](#meeting-date-picker)
* [会议持续时间下拉列表 (MeetingDurationSelect)](#meeting-duration-drop-down)
* [查找会议时间库](#find-meeting-times-gallery)（+ 子控件）
* [聊天室浏览库](#room-browse-gallery)（+ 子控件）
* [后 v 形图标 (RoomsBackNav)](#back-chevron) （可能不会显示如果租户没有聊天室列表）
* [发送图标](#send-icon)

## <a name="prerequisite"></a>先决条件

如何添加和配置屏幕和其他控件为您熟悉[在 PowerApps 中创建应用](../data-platform-create-app-scratch.md)。

## <a name="invite-tab"></a>邀请选项卡

   ![LblInviteTab 控件](media/meeting-screen/meeting-invite-text.png)

* 属性：颜色<br>
    值： `If( _showDetails, LblRecipientCount.Color, RectQuickActionBar.Fill )`

    **_showDetails**是用于确定变量是否**LblInviteTab**控件或**LblScheduleTab**控件处于选中状态。 如果的值 **_showDetails**是**true**， **LblScheduleTab**处于选中状态，如果值为**false**， **LblInviteTab**处于选中状态。 这意味着，如果的值 **_showDetails**是**true** (此选项卡*不*选)，选项卡颜色匹配的**LblRecipientCount**. 否则，它还与填充值相匹配**RectQuickActionBar**。

* 属性：**OnSelect**<br> 
    值： `Set( _showDetails, false )`

    集 **_showDetails**变量**false**，这意味着邀请选项卡的内容是可见的和的内容**计划**隐藏选项卡。

## <a name="schedule-tab"></a>计划选项卡

   ![LblInviteTab 控件](media/meeting-screen/meeting-schedule-text.png)

* 属性：颜色<br>
    值： `If( !_showDetails, LblRecipientCount.Color, RectQuickActionBar.Fill )`

    **_showDetails**是用于确定变量是否**LblInviteTab**控件或**LblScheduleTab**控件处于选中状态。 如果为 true， **LblScheduleTab**处于选中状态，如果为 false， **LblInviteTab**是。 这意味着，如果 **_showDetails**为 true (此选项卡*是*选)，选项卡颜色匹配的填充值**RectQuickActionBar**。 否则，它匹配的颜色值**LblRecipientCount**。

* 属性：**OnSelect**<br>
    值： `Set( _showDetails, true )`

    集 **_showDetails**变量**true**，这意味着计划选项卡的内容是可见的并且邀请选项卡的内容隐藏状态。

## <a name="text-search-box"></a>文本搜索框

   ![TextSearchBox 控件](media/meeting-screen/meeting-search-box.png)

<!--Include description of text search box control?-->

在屏幕中的多个其他控件具有此依赖关系：

* 如果用户开始输入任何文本**PeopleBrowseGallery**将变得可见。
* 如果用户键入一个有效的电子邮件地址， **AddIcon**将变得可见。
* 如果用户选择内的某个人**PeopleBrowseGallery**搜索内容会重置。

## <a name="add-icon"></a>“添加”图标

   ![AddIcon 控件](media/email-screen/email-add-icon.png)

此控件允许用户添加到正在撰写会议的与会者列表其组织内不存在的人员。

* 属性：**Visible**<br>
    值：三个逻辑会检查所有必须计算结果为 **，则返回 true**控件可见：

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```

  行的行，此代码块指出**AddIcon**控件是否可见仅当：

  * **TextSearchBox**包含文本。
  * 中的文本**TextSearchBox**是有效的电子邮件地址。
  * 中的文本**TextSearchBox**中不存在**MyPeople**集合。

* 属性：**OnSelect**<br> 
    值：一个**收集**语句将用户添加到非指定与会者列表中，另一个用来刷新可用的会议时间和几个变量切换：

    ```powerapps-dot
    Collect( MyPeople,
        { 
            DisplayName: TextSearchBox.Text, 
            UserPrincipalName: TextSearchBox.Text, 
            Mail: TextSearchBox.Text
        }
    );
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    { 
                        RequiredAttendees: Concat(MyPeople, UserPrincipalName & ";")
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ),
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage:1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  选择此控件将添加有效的电子邮件地址 (仅在有效的电子邮件地址中键入时可见**TextSearchBox**) 到**MyPeople**集合 （此集合是与会者列表），然后刷新与新的用户条目的可会面时间。

  在较低的级别，此代码块：
  1. 收集到的电子邮件地址**MyPeople**集合，收集到的电子邮件地址**DisplayName**， **UserPrincipalName**，和**邮件**字段。
  1. 将重置的内容**TextSearchBox**控件。
  1. 集 **_showMeetingTimes**变量**false**。 此变量控制的可见性**FindMeetingTimesGallery**，它显示打开以满足所选的与会者的时间。
  1. 集 **_loadMeetingTimes**到上下文变量**true**。 此变量设置切换加载类的状态控件的可见性的加载状态 **_LblTimesEmptyState**以指示用户正在加载其数据。
  1. 集 **_selectedMeetingTime**到**blank （)**。 **_selectedMeetingTime**是从所选的记录**FindMeetingTimesGallery**控件。 它此处留空，因为另一个非指定与会者添加可能意味着，以前的定义 **_selectedMeetingTime**是无法用于该非指定与会者。
  1. 集 **_selectedRoom**到**blank （)**。 **_selectedRoom**就是所选的空间中**RoomBrowseGallery**。 空间可用性确定的值从 **_selectedMeetingTime**。 用此值留空， **_selectedRoom**值不再有效，因此它必须留空。
  1. 集 **_roomListSelected**到**false**。 这行可能不是适用于每个人。 在 Office 中您可以在聊天室按分组不同"会议室列表"。 如果有房间列表，此屏幕中占了，这样，您首先选择房间列表选择从该列表中的房间之前。 值 **_roomListSelected**确定是否 （在仅房间列表与租户） 的用户将查看聊天室房间列表或组的空间列表中。 设置为**false**来强制用户重新选择新的房间列表。
  1. 使用[Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times)操作来确定并收集与会者的可会面时间。 此操作将传递：
      * **UserPrincipalName**的每个所选用户*RequiredAttendees*参数。
      * **MeetingDurationSelect**。到 Selected.Minutes *MeetingDuration*参数。
      * MeetingDateSelect.SelectedDate + 8 小时数加到*启动*参数。 因为默认情况下，完整日期/时间的日历控件是在选定日期的凌晨 12:00，添加八个小时。 你可能想要在正常工作时间内检索可用性。 正常工作的开始时间是上午 8:00。
      * **MeetingDateSelect**。SelectedDate + 17 小时数加到*最终*参数。 由于添加 17 小时上午 12:00 + 17 = 下午 5:00。 正常的工作结束时间是下午 5:00。
      * *15*成*MaxCandidates*参数。 这意味着该操作将返回只返回前 15 可用的所选日期时间。 这是有意义，因为在 8 小时工作日中有仅十六个 30 分钟区块和 30 分钟会议是一个可在此屏幕中设置的最小。
      * *1*成*MinimumAttendeePercentage*参数。 从根本上讲，除非没有其他与会者都不可用，会议时间检索。
      * **false**成*IsOrganizerOptional*参数。 应用程序用户不是此会议与会者。
      * "工作"到*ActivityDomain*参数。 这意味着检索到的时间是只有那些正常工作时间内时间。
  1. **ClearCollect**函数还将添加两个列："StartTime"和"EndTime"。 这简化了返回的数据。 
  包含可用的开始和结束时间的字段是**MeetingTimeSlot**字段。 此字段是记录包含开始和结束的记录，本身包含**DateTime**并**时区**其各自的建议的值。 而不尝试检索的记录这种嵌套时，将添加到的"StartTime"和"结束时间"列**MeetingTimes**集合将那些**开始 > DateTime**和**结束 >DateTime**值到集合中的图面。
  1. 这些函数具有全部完成后， **_loadingMeetingTimes**变量设置为**false**，删除加载状态，并且 **_showMeetingTimes**设置为 **，则返回 true**，显示**FindMeetingTimesGallery**。

## <a name="people-browse-gallery"></a>用户浏览库

   ![PeopleBrowseGallery 控件](media/meeting-screen/meeting-browse-gall.png)

* 属性：**项**<br>
    值： 
    ```powerapps-dot
    If( !IsBlank( Trim( TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( { searchTerm: Trim(TextSearchBox.Text), top: 15 } )
    )
    ```

此库的项填充从搜索结果的[Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser)操作。 该操作采用文本`Trim(**TextSearchBox**)`作为搜索字词，并返回前 15 个结果基于该搜索。
  
**TextSearchBox**包装在**剪裁**函数，因为空间上的用户搜索无效。 `Office365Users.SearchUser`操作包装在`If(!IsBlank(Trim(TextSearchBox.Text)) ... )`函数，因为用户具有搜索之前检索搜索结果则性能会浪费。

### <a name="people-browse-gallery-title"></a>用户浏览库标题

   ![PeopleBrowseGallery 标题控件](media/meeting-screen/meeting-browse-gall-title.png)

* 属性：**文本**<br>
    值： `ThisItem.DisplayName`

    显示从其 Office 365 配置文件的用户的显示名称。

* 属性：**OnSelect**<br>
    值：一个**收集**语句将用户添加到非指定与会者列表中，另一个用来刷新可用的会议时间和几个变量切换：

    ```powerapps-dot
    Concurrent(
        Reset( TextSearchBox ),
        Set( _selectedUser, ThisItem ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem ); 
            Concurrent(
                Set( _showMeetingTimes, false ),
                UpdateContext( { _loadMeetingTimes: true } ),
                Set( _selectedMeetingTime, Blank() ),
                Set( _selectedRoom, Blank() ),
                Set( _roomListSelected, false ),
                ClearCollect( MeetingTimes, 
                    AddColumns(
                        'Office365'.FindMeetingTimes(
                            {
                                RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ),
                                MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                                Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ),
                                End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                                MaxCandidates: 15, 
                                MinimumAttendeePercentage: 1, 
                                IsOrganizerOptional: false, 
                                ActivityDomain: "Work"
                            }
                        ).MeetingTimeSuggestions,
                        "StartTime", MeetingTimeSlot.Start.DateTime, 
                        "EndTime", MeetingTimeSlot.End.DateTime
                    )
                )
            );
            UpdateContext( { _loadingMeetingTimes: false } );
            Set( _showMeetingTimes, true )
        )
    )
    ```

    在高级别中，选择此控件将添加到 person **MyPeople**集合 （非指定与会者列表的应用程序的存储，） 和刷新的可会面时间基于添加新用户。

    选择此控件是非常类似于选择**AddIcon**控制; 的唯一区别在于`Set(_selectedUser, ThisItem)`语句和操作的执行顺序。 在这种情况下，这一讨论将无法做到。 有关更完整说明，通读[AddIcon 控件](#add-icon)部分。

    选择此控件重置**TextSearchBox**。 然后，如果所选内容不在**MyPeople**集合，该控件：
    1. 集 **_loadMeetingTimes**状态变为**true**并 **_showMeetingTimes**状态变为**false**，空白 **_selectedMeetingTime**并 **_selectedRoom**变量和刷新**MeetingTimes**集合的新增功能与**MyPeople**集合。 
    1. 设置 **_loadMeetingTimes**状态变为**false**，并设置 **_showMeetingTimes**到**true**。 如果所选内容已处于**MyPeople**集合，它将重置的内容**TextSearchBox**。

## <a name="meeting-people-gallery"></a>会议的人员库

   ![MeetingPeopleGallery 控件](media/meeting-screen/meeting-people-gall.png)

* 属性：**项**<br>
    值： `MyPeople`

    **MyPeople**集合是初始化或通过选择添加到用户的集合**PeopleBrowseGallery 标题**控件。

* 属性：**Height**<br>
    值：若要允许库增长到 350 的最大高度的逻辑：

    ```powerapps-dot
    Min( 
        76 * RoundUp( CountRows( MeetingPeopleGallery.AllItems ) / 2, 0 ),
        350
    )
    ```

  
   此库的高度调整为在库中，为 350 的最大高度的项的数目。 该公式将作为单个行的高度 76 **MeetingPeopleGallery**，然后将其乘以的行数。 **WrapCount**属性设置为 2，因此，则返回 true 的行数是`RoundUp(CountRows(MeetingPeopleGallery.AllItems) / 2, 0)`。

* 属性：**ShowScrollbar**<br>
    值： `MeetingPeopleGallery.Height >= 350`

    当 (350) 达到库的最大高度，则会显示滚动条。

### <a name="meeting-people-gallery-title"></a>会议的人员库标题

   ![MeetingPeopleGallery 标题控件](media/meeting-screen/meeting-people-gall-title.png)

* 属性：**OnSelect**<br>
    
    值： `Set(_selectedUser, ThisItem)`
    
    集 **_selectedUser**变量中的选定项**MeetingPeopleGallery**。

### <a name="meeting-people-gallery-iconremove"></a>会议的人员库 iconRemove

   ![MeetingPeopleGallery iconRemove 控件](media/meeting-screen/meeting-people-gall-delete.png)

* 属性：**OnSelect**<br>
    值：一个**删除**语句以从非指定与会者列表中，删除用户**收集**语句以刷新可用的会议时间和几个变量切换：

    ```powerapps-dot
    Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) );
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    {
                        RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ), 
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ), 
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage: 1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  在高级别中，选择此控件从非指定与会者列表中删除该人员并刷新基于此人删除的可会面时间。

  在前面的代码中的第一行后, 选择此控件是选择几乎完全相同**AddIcon**控件。 在这种情况下，这一讨论将不可做到。 有关更完整说明，通读[AddIcon 控制部分](#add-icon)。

  在第一行代码，所选的项已从**MyPeople**集合。 然后代码：
  1. 重置**TextSearchBox**，然后从选择中删除**MyPeople**集合。 
  1. 集 **_loadMeetingTimes**状态变为**true**并 **_showMeetingTimes**状态变为**false**，空白 **_selectedMeetingTime**并 **_selectedRoom**变量和刷新**MeetingTimes**集合的新增功能与**MyPeople**集合。 
  1. 设置 **_loadMeetingTimes**状态变为**false**，并设置 **_showMeetingTimes**到**true**。

## <a name="meeting-date-picker"></a>会议日期选取器

   ![MeetingDateSelect 控件](media/meeting-screen/meeting-datepicker.png)

* 属性：**DisplayMode**<br>
    值： `If( IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit )`

    不能选会议的日期，直到至少一个非指定与会者已添加到**MyPeople**集合。

* 属性：**OnChange**<br>
    值： `Select( MeetingDateSelect )`

    更改所选的日期中的代码将触发**OnSelect**要运行此控件的属性。

* 属性：**OnSelect**<br>
    值：一个**收集**语句以刷新可用的会议时间和几个变量切换：
  
    ```powerapps-dot
    Concurrent(
        Reset( TextSearchBox ),
        Set( _showMeetingTimes, false ),
        UpdateContext( { _loadingMeetingTimes: true } ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false ),
        ClearCollect( MeetingTimes, 
            AddColumns(
                'Office365'.FindMeetingTimes(
                    {
                        RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ), 
                        MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: Text( DateAdd( MeetingDateSelect.SelectedDate, 8, Hours ), UTC ), 
                        End: Text( DateAdd( MeetingDateSelect.SelectedDate, 17, Hours ), UTC ),
                        MaxCandidates: 15, 
                        MinimumAttendeePercentage: 1, 
                        IsOrganizerOptional: false, 
                        ActivityDomain: "Work"
                    }
                ).MeetingTimeSuggestions,
                "StartTime", MeetingTimeSlot.Start.DateTime, 
                "EndTime", MeetingTimeSlot.End.DateTime
            )
        )
    );
    UpdateContext( { _loadingMeetingTimes: false } );
    Set( _showMeetingTimes, true )
    ```

  在高级别中，选择此控件刷新的可会面时间。 它非常有用，因为如果用户更改日期，需要更新以反映对这一天的与会者的可用性的可会面时间。

  除了初始**收集**语句，这等同于**OnSelect**的功能**AddIcon**控件。 在这种情况下，这一讨论将不可做到。 有关更完整说明，通读[AddIcon 控件](#add-icon)部分。

  选择此控件重置**TextSearchBox**。 然后它： 
  1. 集 **_loadMeetingTimes**状态变为**true**并 **_showMeetingTimes**状态变为**false**，空白 **_selectedMeetingTime**并 **_selectedRoom**变量和刷新**MeetingTimes**使用新的日期选择的集合。 
  1. 设置 **_loadMeetingTimes**状态变为**false**，并设置 **_showMeetingTimes**到**true**。

## <a name="meeting-duration-drop-down"></a>会议持续时间下拉列表

   ![MeetingDateSelect 控件](media/meeting-screen/meeting-timepicker.png)

* 属性：**DisplayMode**<br>
    值： `If( IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit )`

    不能选会议的持续时间，直到至少一个非指定与会者已添加到**MyPeople**集合。

* 属性：**OnChange**<br>
    值： `Select(MeetingDateSelect1)`

    更改所选时段内将触发中的代码**OnSelect**的属性**MeetingDateSelect**控件运行。

## <a name="find-meeting-times-gallery"></a>查找会议时间库

   ![FindMeetingTimesGallery 控件](media/meeting-screen/meeting-time-gall.png)

* 属性：**项**<br>
    值： `MeetingTimes`

    从潜在的会议时间的集合中检索[Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times)操作。

* 属性：**Visible**<br>
    值： `_showMeetingTimes && _showDetails && !IsEmpty( MyPeople )`

    库是可见才 **_showMeetingTimes**设置为**true**，用户所选**LblScheduleTab**控件，并且至少一个非指定与会者添加到会议。

### <a name="find-meeting-times-gallery-title"></a>查找会议时间库标题

   ![FindMeetingTimesGallery 标题控件](media/meeting-screen/meeting-time-gall-title.png)

* 属性：**文本**<br>
    值：若要显示在用户的本地时间的开始时间的转换：

    ```powerapps-dot
    Text(
        DateAdd(
            DateTimeValue( ThisItem.StartTime ),
            - TimeZoneOffset(), 
            Minutes
        ),
        DateTimeFormat.ShortTime
    )
    ```

  检索到的值的**StartTime**采用 UTC 格式。 向[从 UTC 转换为本地时间](../functions/function-dateadd-datediff.md#converting-from-utc)，则**DateAdd**应用函数。
  [文本函数](../functions/function-text.md#datetime)将日期/时间作为其第一个参数，并基于其第二个参数的格式。 传递给它的本地时间转换**ThisItem.StartTime**，并将其作为显示**DateTimeFormat.ShortTime**。

* 属性：**OnSelect**<br>
    值：多个**收集**语句，以收集会议房间和其建议的可用性，以及多个变量切换：

    ```powerapps-dot
    Set( _selectedMeetingTime, ThisItem );
    UpdateContext( { _loadingRooms: true } );
    If( IsEmpty( RoomsLists ),
        ClearCollect( RoomsLists, 'Office365'.GetRoomLists().value) );
    If( CountRows( RoomsLists ) <= 1,
        Set( _noRoomLists, true );
        ClearCollect( AllRooms, 'Office365'.GetRooms().value );
        Set( _allRoomsConcat, Concat( FirstN( AllRooms, 20 ), Address & ";" ) );
        ClearCollect( RoomTimeSuggestions, 
            'Office365'.FindMeetingTimes(
                {
                    RequiredAttendees: _allRoomsConcat, 
                    MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                    Start: _selectedMeetingTime.StartTime & "Z", 
                    End: _selectedMeetingTime.EndTime & "Z", 
                    MinimumAttendeePercentage: "1",
                    IsOrganizerOptional: "false", 
                    ActivityDomain: "Unrestricted"
                }
            ).MeetingTimeSuggestions
        );
        ClearCollect( AvailableRooms, 
            AddColumns(
                AddColumns(
                    Filter( 
                        First( RoomTimeSuggestions ).AttendeeAvailability,
                        Availability="Free"
                    ), 
                    "Address", Attendee.EmailAddress.Address
                ), 
                "Name", LookUp( AllRooms, Address = Attendee.EmailAddress.Address ).Name 
            )
        );
        ClearCollect( AvailableRoomsOptimal, 
            DropColumns(
                DropColumns( AvailableRooms, "Availability" ), 
                "Attendee" 
            )
        ),
        Set( _roomListSelected, false) 
    );
    UpdateContext( {_loadingRooms: false} )
    ```

  在高级别中，此代码块不具有权限的用户收集可用聊天室房间列表中，根据会议的所选日期/时间。 否则，它就只检索聊天室列表。

  在较低的级别，此代码块：
  1. 集 **_selectedMeetingTime**到选定的项。 这用于查找哪些聊天室可在该时间段。
  1. 设置在加载状态变量 **_loadingRooms**到**true**，开启加载状态。
  1. 如果**RoomsLists**集合为空，它检索用户的租户的房间列表并将它们存储在**RoomsLists**集合。
  1. 如果用户没有房间列表或一个房间列表：
      1. **NoRoomLists**变量设置为**true**，并使用此变量来确定在显示的项**RoomBrowseGallery**控件。
      1. `Office365.GetRooms()`操作用于检索在其租户中的前 100 个教室。 它们存储在**AllRooms**集合。
      1. **_AllRoomsConcat**变量设置为以分号分隔的聊天室中的第一个 20 电子邮件地址字符串**AllRooms**集合。 这是因为[Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times)限制为 20 个人员对象在单个操作中的可用时间，搜索。
      1. **RoomTimeSuggestions**集合使用[Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times)若要检索的前 20 个房间可用性**AllRooms**基于的集合从时间值 **_selectedMeetingTime**变量。 请注意，`& "Z"`用于正确进行格式化**DateTime**值。
      1. **AvailableRooms**创建集合。 这是只需**RoomTimeSuggestions**集合包含两个其他列添加到其中的非指定与会者可用性："地址"和"Name"。 "地址"是此聊天室的电子邮件地址和"Name"是聊天室的名称。
      1. 然后，将**AvailableRoomsOptimal**创建集合。 而这仅仅是**AvailableRooms**与"可用性"和"与会者"列的集合中删除。 执行此操作的架构匹配**AvailableRoomsOptimal**并**AllRooms**。 这允许您使用这两个集合中的**项**的属性**RoomBrowseGallery**。
      1. **_roomListSelected**设置为**false**。
  1. 加载状态 **_loadingRooms**，设置为**false**完成其他所有内容后执行。

## <a name="room-browse-gallery"></a>聊天室浏览库

   ![RoomBrowseGallery 控件](media/meeting-screen/meeting-rooms-gall.png)

* 属性：**项**<br>
    值：以逻辑方式将设置为两个完全相同的架构，具体取决于用户选择文件室中还是在其租户中具有房间列表的内部集合：

    ```powerapps-dot
    Search(
        If( _roomListSelected || _noRoomLists, AvailableRoomsOptimal, RoomsLists ),
        Trim(TextMeetingLocation1.Text), 
        "Name", 
        "Address"
    )
    ```

  此库显示**AvailableRoomsOptimal**集合如果 **_roomListSelected**或 **_noRoomLists**是**true**。 否则，将显示**RoomsLists**集合。 这可以因为这些集合的架构相同。

* 属性：**Visible**<br>
    值： ```_showDetails && !IsBlank( _selectedMeetingTime ) && !_loadingRooms```

    库是仅在前面的三个语句的计算结果为时可见 **，则返回 true**。

### <a name="roombrowsegallery-title"></a>RoomBrowseGallery 标题

   ![RoomBrowseGallery 标题控件](media/meeting-screen/meeting-rooms-gall-title.png)

* 属性：**OnSelect**<br>
    值：一组逻辑上绑定**收集**并**设置**语句，它们可能会或可能不会触发，具体取决于用户是否查看房间列表或聊天室：

    ```powerapps-dot
    UpdateContext( { _loadingRooms: true } );
    If( !_roomListSelected && !noRoomLists,
        Set( _roomListSelected, true );
        Set( _selectedRoomList, ThisItem.Name );
        ClearCollect( AllRooms, 'Office365'.GetRoomsInRoomList( ThisItem.Address ).value );
        Set( _allRoomsConcat, Concat( FirstN( AllRooms, 20 ), Address & ";" ) );
        ClearCollect( RoomTimeSuggestions, 
            'Office365'.FindMeetingTimes(
                {
                    RequiredAttendees: _allRoomsConcat, 
                    MeetingDuration: MeetingDurationSelect.Selected.Minutes,
                        Start: _selectedMeetingTime.StartTime & "Z", 
                    End: _selectedMeetingTime.EndTime & "Z", 
                    MinimumAttendeePercentage: "1",
                    IsOrganizerOptional: "false", 
                    ActivityDomain: "Unrestricted"
                }
            ).MeetingTimeSuggestions
        );
        ClearCollect( AvailableRooms, 
            AddColumns(
                AddColumns(
                    Filter(
                        First( RoomTimeSuggestions ).AttendeeAvailability, 
                        Availability = "Free"
                    ),
                    "Address", Attendee.EmailAddress.Address 
                ), 
                "Name", LookUp( AllRooms, Address = Attendee.EmailAddress.Address ).Name
            )
        );
        ClearCollect( AvailableRoomsOptimal, 
            DropColumns(
                DropColumns( AvailableRooms, "Availability" )
            ), 
            "Attendee" )
        ),
        Set( _selectedRoom, ThisItem )
    );
    UpdateContext( {_loadingRooms: false} )
    ```

  选择此控件，可能发生的操作取决于是否用户一组房间列表或聊天室一组当前正在查看。 如果是前者，然后选择此控件检索聊天室从所选的空间列表的所选时间上可用的。 如果是后者，选择此控件设置 **_selectedRoom**变量到选定的项。 前面的语句是非常类似于**选择**语句[ **FindMeetingTimesGallery 标题**](#find-meeting-times-gallery)。

  在较低的级别，前面的代码块：
  1. 通过设置开启聊天室的加载状态 **_loadingRooms**到**true**。
  1. 检查列表，以查看是否房间列表已被选中，并且租户有空间。 如果是这样：
      1. 设置 **_roomListSelected**到**true**并设置 **_selectedRoomList**到选定的项。
      1. **_AllRoomsConcat**变量设置为以分号分隔的聊天室中的第一个 20 电子邮件地址字符串**AllRooms**集合。 这是因为[Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times)操作仅限于在单个操作中的 20 个人员对象的可用时间，搜索。
      1. **RoomTimeSuggestions**集合使用[Office365.FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times)操作以检索前 20 个工作室中的可用性**AllRooms**集合中，基于时间的值从 **_selectedMeetingTime**变量。 请注意，`& "Z"`用于正确进行格式化**DateTime**值。
      1. **AvailableRooms**创建集合。 这是只需**RoomTimeSuggestions**集合包含两个其他列添加到其中的非指定与会者可用性："地址"和"Name"。 "地址"是此聊天室的电子邮件地址和"Name"是聊天室的名称。
      1. 然后，将**AvailableRoomsOptimal**创建集合。 而这仅仅是**AvailableRooms**与"可用性"和"与会者"列的集合中删除。 执行此操作的架构匹配**AvailableRoomsOptimal**并**AllRooms**。 这允许您使用这两个集合中的**项**的属性**RoomBrowseGallery**。
      1. **_roomListSelected**设置为**false**。
  1. 加载状态 **_loadingRooms**，设置为**false**完成其他所有内容后执行。

## <a name="back-chevron"></a>后 v 形展开按钮

   ![RoomsBackNav 控件](media/meeting-screen/meeting-back.png)

* 属性：**Visible**<br>
    值： `_roomListSelected && _showDetails`

    此控件是否可见的仅当选择这两个房间列表和**计划**选择选项卡。

* 属性：**OnSelect**<br>
    值： `Set( _roomListSelected, false )`

    当 **_roomListSelected**设置为**false**，它会更改**RoomBrowseGallery**控件来显示项从**RoomsLists**集合。

## <a name="send-icon"></a>发送图标

   ![IconSendItem 控件](media/meeting-screen/meeting-send-icon.png)

* 属性：**DisplayMode**<br>
    值：若要强制用户在之前的图标将变为可编辑输入某些会议详细信息的逻辑。
    
    ```powerapps-dot
    If( Len( Trim( TextMeetingSubject1.Text ) ) > 0
        && !IsEmpty( MyPeople ) && !IsBlank( _selectedMeetingTime ),
        DisplayMode.Edit, DisplayMode.Disabled
    )
    ```
  图标才可选择填写会议主题，则至少一个会议，与会者，已选择的会议时间。 否则，它处于禁用状态。

* 属性：**OnSelect**<br>

    值：若要向所选与会者发送会议邀请并清除所有输入的字段的代码：

    ```powerapps-dot
    Set( _myCalendarName, LookUp( 'Office365'.CalendarGetTables().value, DisplayName = "Calendar" ).Name );
    Set( _myScheduledMeeting, 
        'Office365'.V2CalendarPostItem( _myCalendarName,
            TextMeetingSubject1.Text, 
            Text(DateAdd(DateTimeValue( _selectedMeetingTime.StartTime), -TimeZoneOffset(), Minutes) ),
            Text(DateAdd(DateTimeValue( _selectedMeetingTime.EndTime), -TimeZoneOffset(), Minutes) ),
            {
                RequiredAttendees: Concat( MyPeople, UserPrincipalName & ";" ) & _selectedRoom.Address, 
                Body: TextMeetingMessage1.Text, 
                Location: _selectedRoom.Name, 
                Importance: "Normal", 
                ShowAs: "Busy", 
                ResponseRequested: true
            }
        )
    );
    Concurrent(
        Reset( TextMeetingLocation1 ),
        Reset( TextMeetingSubject1 ),
        Reset( TextMeetingMessage1 ),
        Clear( MyPeople ),
        Set( _selectedMeetingTime, Blank() ),
        Set( _selectedRoomList, Blank() ),
        Set( _selectedRoom, Blank() ),
        Set( _roomListSelected, false )
    )
    ```
  
  在较低的级别，此代码块：
  1. 集 **_myCalendarName**到中的日历[Office365.CalendarGetTables()](https://docs.microsoft.com/connectors/office365/#get-calendars)操作**DisplayName**的"日历"。
  1. 计划与输入的所有会议中的值的各种选择整个屏幕使用内容中进行用户[Office365.V2CalendarPostItem](https://docs.microsoft.com/connectors/office365/#create-event--v2-)操作。
  1. 重置所有输入的字段和变量在创建会议时使用。

> [!NOTE]
> 根据你所在的地区，所需的日历可能不具有的显示名称为"日历"。 转到 Outlook，若要查看你的日历的标题是什么，并在应用中进行相应更改。

## <a name="next-steps"></a>后续步骤

* [了解有关此屏幕的详细信息](./meeting-screen-overview.md)
* [了解有关 PowerApps 中的 Office 365 Outlook 连接器的详细信息](../connections/connection-office365-outlook.md)
* [了解有关 PowerApps 中的 Office 365 用户连接器的详细信息](../connections/connection-office365-users.md)
