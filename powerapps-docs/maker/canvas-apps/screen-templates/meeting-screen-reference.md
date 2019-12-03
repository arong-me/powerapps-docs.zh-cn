---
title: 画布应用的会议屏幕模板参考 |Microsoft Docs
description: 了解适用于画布应用的会议屏幕模板在 Power Apps 中的工作原理的详细信息
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/03/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 66cf9ae4cc16ba8004775ba86db3f5497fb99937
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733116"
---
# <a name="reference-information-about-the-meeting-screen-template-for-canvas-apps"></a>有关 canvas 应用的会议屏幕模板的参考信息

对于 "Power Apps 中的画布应用"，了解会议屏蔽模板中的每个重要控件如何为屏幕的整体默认功能提供帮助。 这一深入探讨介绍了如何通过其他属性来确定控件如何响应用户输入。 有关此屏幕默认功能的详细讨论，请参阅[会议屏幕概述](meeting-screen-overview.md)。

本主题重点介绍一些重要的控件，并说明这些控件的各种属性（例如**Items**和**OnSelect**）的设置表达式或公式：

* [邀请选项卡（LblInviteTab）](#invite-tab)
* ["计划" 选项卡（LblScheduleTab）](#schedule-tab)
* [文本搜索框](#text-search-box)
* [添加图标（AddIcon）](#add-icon)
* [人员浏览库](#people-browse-gallery)（+ 子控件）
* [会议人员库](#meeting-people-gallery)（+ 子控件）
* [会议日期选取器（MeetingDateSelect）](#meeting-date-picker)
* ["会议持续时间" 下拉（MeetingDurationSelect）](#meeting-duration-drop-down)
* [查找会议时间库](#find-meeting-times-gallery)（+ 子控件）
* [会议室浏览库](#room-browse-gallery)（+ 子控件）
* [Back v 形（RoomsBackNav）](#back-chevron) （如果租户不包含会议室列表，可能不可见）
* [发送图标](#send-icon)

## <a name="prerequisite"></a>先决条件

熟悉如何[在 Power Apps 中创建应用](../data-platform-create-app-scratch.md)时添加和配置屏幕和其他控件。

## <a name="invite-tab"></a>邀请选项卡

   ![LblInviteTab 控件](media/meeting-screen/meeting-invite-text.png)

* 属性：**颜色**<br>
    值： `If( _showDetails, LblRecipientCount.Color, RectQuickActionBar.Fill )`

    **_showDetails**是一种用于确定**LblInviteTab**控件或**LblScheduleTab**控件是否处于选中状态的变量。 如果 **_showDetails**的值为**true**，则选择**LblScheduleTab** ;如果该值为**false**，则选择**LblInviteTab** 。 这意味着，如果 **_showDetails**的值为**true** （*未*选中此选项卡），则选项卡颜色将与**LblRecipientCount**的颜色匹配。 否则，它将匹配**RectQuickActionBar**的填充值。

* 属性： **OnSelect**<br> 
    值： `Set( _showDetails, false )`

    将 **_showDetails**变量设置为**false**，这意味着 "邀请" 选项卡的内容可见，并隐藏 "**计划**" 选项卡的内容。

## <a name="schedule-tab"></a>计划选项卡

   ![LblInviteTab 控件](media/meeting-screen/meeting-schedule-text.png)

* 属性：**颜色**<br>
    值： `If( !_showDetails, LblRecipientCount.Color, RectQuickActionBar.Fill )`

    **_showDetails**是一种用于确定**LblInviteTab**控件或**LblScheduleTab**控件是否处于选中状态的变量。 如果为 true，则选择**LblScheduleTab** ;如果为 false，则**LblInviteTab**为。 这意味着，如果 **_showDetails**为 true （选中此选项卡），则*选项卡颜色*将与**RectQuickActionBar**的 "填充" 值匹配。 否则，它与**LblRecipientCount**的颜色值匹配。

* 属性： **OnSelect**<br>
    值： `Set( _showDetails, true )`

    将 **_showDetails**变量设置为**true**，这意味着 "计划" 选项卡的内容可见，"邀请" 选项卡的内容处于隐藏状态。

## <a name="text-search-box"></a>文本搜索框

   ![TextSearchBox 控件](media/meeting-screen/meeting-search-box.png)

<!--Include description of text search box control?-->

屏幕中的其他几个控件依赖于这一控件：

* 如果用户开始键入任何文本，则**PeopleBrowseGallery**变得可见。
* 如果用户键入有效的电子邮件地址，则**AddIcon**会变得可见。
* 当用户在**PeopleBrowseGallery**中选择人员时，将重置搜索内容。

## <a name="add-icon"></a>“添加”图标

   ![AddIcon 控件](media/email-screen/email-add-icon.png)

此控件允许用户将其组织内不存在的人员添加到要撰写的会议的与会者列表。

* 属性：**可见**<br>
    值：三个逻辑检查都必须计算结果为**true** ，控件才能显示：

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```

  逐行，此代码块指出**AddIcon**控件仅在以下情况下才可见：

  * **TextSearchBox**包含文本。
  * **TextSearchBox**中的文本是有效的电子邮件地址。
  * **TextSearchBox**中的文本在**MyPeople**集合中尚不存在。

* 属性： **OnSelect**<br> 
    值：用于将用户添加到与会者列表的**收集**语句，另一个语句用于刷新可用的会议时间和多个变量切换：

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

  如果选择此控件，则会将有效的电子邮件地址（只有在将有效电子邮件地址键入到**TextSearchBox**中时才可见）添加到**MyPeople**集合（此集合是与会者列表），然后使用新用户条目刷新可用的会议时间。

  在较低的级别，此代码块：
  1. 将电子邮件地址收集到**MyPeople**集合，将电子邮件地址收集到**DisplayName**、 **UserPrincipalName**和**Mail**字段。
  1. 重置**TextSearchBox**控件的内容。
  1. 将 **_showMeetingTimes**变量设置为**false**。 此变量控制**FindMeetingTimesGallery**的可见性，这将显示所选与会者要满足的打开时间。
  1. 将 **_loadMeetingTimes**上下文变量设置为**true**。 此变量设置加载状态，该状态将切换加载状态控件（如 **_LblTimesEmptyState** ）的可见性，以指示用户正在加载其数据。
  1. 将 **_selectedMeetingTime**设置为**空白（）** 。 **_selectedMeetingTime**是**FindMeetingTimesGallery**控件中选定的记录。 这会在此处遮蔽，因为添加其他与会者可能意味着 **_selectedMeetingTime**的前一定义不能用于该与会者。
  1. 将 **_selectedRoom**设置为**空白（）** 。 **_selectedRoom**是**RoomBrowseGallery**中所选的会议室记录。 房间可用性由 **_selectedMeetingTime**的值确定。 此值被遮蔽后， **_selectedRoom**值不再有效，因此必须将其遮蔽。
  1. 将 **_roomListSelected**设置为**false**。 该行可能不适用于所有人。 在 Office 中，可以按不同的 "房间列表" 对房间进行分组。 如果你有房间列表，此屏幕会对此进行设置，使你可以在从该列表中选择一个房间之前先选择一个房间列表。 **_RoomListSelected**的值决定了某个用户（在仅包含会议室列表的租户中）是否将查看房间列表或会议室列表集内的会议室。 此参数设置为**false**以强制用户重新选择新的聊天室列表。
  1. 使用[Office365. FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times)操作来确定和收集与会者的可用会议时间。 此操作通过：
      * 每个所选用户在*RequiredAttendees*参数中的**UserPrincipalName** 。
      * **MeetingDurationSelect**。在*MeetingDuration*参数中选择了分钟。
      * 在*Start*参数中 MeetingDateSelect + 8 小时。 添加了8小时，因为默认情况下，日历控件的完整日期/时间为所选日期的 12:00 AM。 可能需要在正常工作时间内检索可用性。 正常工作开始时间为 8:00 AM。
      * **MeetingDateSelect**。*结束*参数 SelectedDate + 17 小时。 添加17小时，因为 12:00 AM + 17 = 5:00 PM。 正常工作结束时间为 5:00 PM。
      * *15*到*MaxCandidates*参数。 这意味着操作仅返回选定日期前15个可用的时间。 这种做法很有意义，因为在8小时的工作日内只有 16 30 分钟的区块，而30分钟的会议是此屏幕中的最小值。
      * *1* *MinimumAttendeePercentage*参数。 实质上，除非没有可用的与会者，否则将检索会议时间。
      * *IsOrganizerOptional*参数的**值为 false** 。 应用用户不是此会议的可选与会者。
      * "工作" 到*ActivityDomain*参数。 这意味着检索到的时间只是在正常工作时间段内的时间。
  1. **ClearCollect**函数还添加了两个列： "StartTime" 和 "EndTime"。 这简化了返回的数据。 
  包含可用开始和结束时间的字段为**MeetingTimeSlot**字段。 此字段是包含开始和结束记录的记录，这些记录本身包含其各自建议的**日期时间**和**时区**值。 将 "StartTime" 和 "EndTime" 列添加到**MeetingTimes**集合，而不是尝试检索记录的这一嵌套，这会使这些**开始 > 日期时间**和**结束时间 > 日期时间**值添加到集合的图面上。
  1. 这些函数全部完成后， **_loadingMeetingTimes**变量将设置为**false**，删除加载状态，并将 **_showMeetingTimes**设置为**true**，显示**FindMeetingTimesGallery**。

## <a name="people-browse-gallery"></a>人员浏览库

   ![PeopleBrowseGallery 控件](media/meeting-screen/meeting-browse-gall.png)

* 属性：**项**<br>
    负值 
    ```powerapps-dot
    If( !IsBlank( Trim( TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( { searchTerm: Trim(TextSearchBox.Text), top: 15 } )
    )
    ```

此库中的项由[Office365. SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser)操作的搜索结果填充。 操作使用 `Trim(**TextSearchBox**)` 中的文本作为其搜索词，并基于该搜索返回前15个结果。
  
由于在空格上搜索的用户无效， **TextSearchBox**已包装在**Trim**函数中。 `Office365Users.SearchUser` 操作包装在 `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` 函数中，因为在用户搜索之前检索搜索结果是一项性能浪费。

### <a name="people-browse-gallery-title"></a>用户浏览库标题

   ![PeopleBrowseGallery 标题控件](media/meeting-screen/meeting-browse-gall-title.png)

* 属性：**文本**<br>
    值： `ThisItem.DisplayName`

    显示用户在其 Office 365 配置文件中的显示名称。

* 属性： **OnSelect**<br>
    值：用于将用户添加到与会者列表的**收集**语句，另一个语句用于刷新可用的会议时间和多个变量切换：

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

    从较高层次来看，选择此控件即可将人员添加到**MyPeople**集合（"与会者列表" 的应用存储），并基于新用户添加刷新可用的会议时间。

    选择此控件非常类似于选择**AddIcon**控件;唯一的区别在于 `Set(_selectedUser, ThisItem)` 语句和操作的执行顺序。 同样，这一讨论并不深入。 有关更完整的说明，请阅读[AddIcon 控件](#add-icon)部分。

    选择此控件将重置**TextSearchBox**。 然后，如果所选内容不在**MyPeople**集合中，则控件：
    1. 将 **_loadMeetingTimes**状态设置为**true** ，将 **_showMeetingTimes**状态设置为**false**，将 **_SelectedMeetingTime**和 **_selectedRoom**变量留空，并刷新**MeetingTimes**集合，并将新添加到**MyPeople**集合。 
    1. 将 **_loadMeetingTimes**状态设置为**false**，并将 **_showMeetingTimes**设置为**true**。 如果选定内容已在**MyPeople**集合中，则它仅重置**TextSearchBox**的内容。

## <a name="meeting-people-gallery"></a>会议人员库

   ![MeetingPeopleGallery 控件](media/meeting-screen/meeting-people-gall.png)

* 属性：**项**<br>
    值： `MyPeople`

    **MyPeople**集合是通过选择 " **PeopleBrowseGallery" 标题**控件进行初始化或添加的人员的集合。

* 属性：**高度**<br>
    值：允许库增长到最大高度为350的逻辑：

    ```powerapps-dot
    Min( 
        76 * RoundUp( CountRows( MeetingPeopleGallery.AllItems ) / 2, 0 ),
        350
    )
    ```

  
   此库的高度将调整为库中的项目数，最大高度为350。 公式采用76作为**MeetingPeopleGallery**的单个行的高度，然后将其与行数相乘。 **WrapCount**属性设置为2，因此 `RoundUp(CountRows(MeetingPeopleGallery.AllItems) / 2, 0)`真正的行数。

* 属性： **ShowScrollbar**<br>
    值： `MeetingPeopleGallery.Height >= 350`

    当达到库的最大高度（350）时，滚动条可见。

### <a name="meeting-people-gallery-title"></a>会议人员画廊标题

   ![MeetingPeopleGallery 标题控件](media/meeting-screen/meeting-people-gall-title.png)

* 属性： **OnSelect**<br>
    
    值： `Set(_selectedUser, ThisItem)`
    
    将 **_selectedUser**变量设置为在**MeetingPeopleGallery**中选定的项。

### <a name="meeting-people-gallery-iconremove"></a>会议人员库 iconRemove

   ![MeetingPeopleGallery iconRemove 控件](media/meeting-screen/meeting-people-gall-delete.png)

* 属性： **OnSelect**<br>
    值：用于从与会者列表中删除用户的**remove**语句、用于刷新可用会议时间的**收集**语句和多个变量切换：

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

  从较高层次来看，选择此控件将从与会者列表中删除该用户，并根据删除此人的情况刷新可用会议时间。

  在上述代码的第一行之后，选择该控件与选择**AddIcon**控件几乎完全相同。 因此，此讨论并不深入。 有关更完整的说明，请阅读[AddIcon 控件部分](#add-icon)。

  在代码的第一行中，从**MyPeople**集合中删除所选的项。 然后，该代码：
  1. 重置**TextSearchBox**，并从**MyPeople**集合中删除所选内容。 
  1. 将 **_loadMeetingTimes**状态设置为**true** ，将 **_showMeetingTimes**状态设置为**false**，将 **_SelectedMeetingTime**和 **_selectedRoom**变量留空，并刷新**MeetingTimes**集合，并将新添加到**MyPeople**集合。 
  1. 将 **_loadMeetingTimes**状态设置为**false**，并将 **_showMeetingTimes**设置为**true**。

## <a name="meeting-date-picker"></a>会议日期选取器

   ![MeetingDateSelect 控件](media/meeting-screen/meeting-datepicker.png)

* 属性： **DisplayMode**<br>
    值： `If( IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit )`

    在至少有一个与会者添加到**MyPeople**集合之前，不能选择会议日期。

* 属性： **OnChange**<br>
    值： `Select( MeetingDateSelect )`

    更改所选日期会触发此控件的**OnSelect**属性中的代码运行。

* 属性： **OnSelect**<br>
    值：用于刷新可用会议时间和多个变量切换的**收集**语句：
  
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

  在高级别中，选择此控件可刷新可用的会议时间。 它非常有用，因为如果用户更改日期，则可用的会议时间需要更新，以反映该日期的与会者可用性。

  除了初始**收集**语句以外，这与**AddIcon**控件的**OnSelect**功能相同。 因此，此讨论并不深入。 有关更完整的说明，请阅读[AddIcon 控件](#add-icon)部分。

  选择此控件将重置**TextSearchBox**。 然后： 
  1. 将 **_loadMeetingTimes**状态设置为**true** ，将 **_showMeetingTimes**状态设置为**false**，为 **_selectedMeetingTime**和 **_selectedRoom**变量提供空白，并通过新的日期选择刷新**MeetingTimes**集合。 
  1. 将 **_loadMeetingTimes**状态设置为**false**，并将 **_showMeetingTimes**设置为**true**。

## <a name="meeting-duration-drop-down"></a>"会议持续时间" 下拉

   ![MeetingDateSelect 控件](media/meeting-screen/meeting-timepicker.png)

* 属性： **DisplayMode**<br>
    值： `If( IsEmpty(MyPeople), DisplayMode.Disabled, DisplayMode.Edit )`

    在至少有一个与会者添加到**MyPeople**集合之前，无法选择会议的持续时间。

* 属性： **OnChange**<br>
    值： `Select(MeetingDateSelect1)`

    更改所选持续时间会触发**MeetingDateSelect**控件的**OnSelect**属性中的代码运行。

## <a name="find-meeting-times-gallery"></a>查找会议时间库

   ![FindMeetingTimesGallery 控件](media/meeting-screen/meeting-time-gall.png)

* 属性：**项**<br>
    值： `MeetingTimes`

    [Office365. FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times)操作检索到的潜在会议时间的集合。

* 属性：**可见**<br>
    值： `_showMeetingTimes && _showDetails && !IsEmpty( MyPeople )`

    仅当 **_showMeetingTimes**设置为**true**，用户已选择**LblScheduleTab**控件，且至少有一个与会者添加到会议时，库才可见。

### <a name="find-meeting-times-gallery-title"></a>查找会议时间库标题

   ![FindMeetingTimesGallery 标题控件](media/meeting-screen/meeting-time-gall-title.png)

* 属性：**文本**<br>
    值：要在用户的本地时间内显示的开始时间的转换：

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

  **StartTime**的检索值采用 UTC 格式。 若要[将 UTC 转换为本地时间](../functions/function-dateadd-datediff.md#converting-from-utc)，请应用**DateAdd**函数。
  [Text 函数](../functions/function-text.md#datetime)使用日期/时间作为其第一个参数，并根据其第二个参数对其进行格式设置。 向其传递**ThisItem**的本地时间转换，并将其显示为**DateTimeFormat. ShortTime**。

* 属性： **OnSelect**<br>
    值：收集会议室的若干个**收集**语句及其建议的可用性，以及多个可变切换：

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

  从较高层次来看，此代码块会根据所选的会议日期/时间为没有会议室列表的用户收集可用房间。 否则，它只检索会议室列表。

  在较低的级别，此代码块：
  1. 将 **_selectedMeetingTime**设置为所选的项。 这用于查找在该时间段内可用的会议室。
  1. 将加载状态变量 **_loadingRooms**设置为**true**，并在上打开加载状态。
  1. 如果**RoomsLists**集合为空，它将检索用户的 tenant's 会议室列表，并将其存储在**RoomsLists**集合中。
  1. 如果用户没有会议室列表或一个房间列表：
      1. **NoRoomLists**变量设置为**true**，此变量用于确定**RoomBrowseGallery**控件中显示的项。
      1. `Office365.GetRooms()` 操作用于检索其租户中的前100个聊天室。 它们存储在**AllRooms**集合中。
      1. **_AllRoomsConcat**变量设置为**AllRooms**集合中房间的前20个电子邮件地址的分号分隔的字符串。 这是因为， [Office365](https://docs.microsoft.com/connectors/office365/#find-meeting-times)被限制为在单个操作中搜索20个 person 对象的可用时间。
      1. **RoomTimeSuggestions**集合使用[Office365](https://docs.microsoft.com/connectors/office365/#find-meeting-times)根据 **_selectedMeetingTime**变量中的时间值检索**AllRooms**集合中前20个房间的可用性。 请注意，`& "Z"` 用于正确设置**日期时间**值的格式。
      1. 创建**AvailableRooms**集合。 这只是与会者可用性的**RoomTimeSuggestions**集合，其中添加了另外两个列： "Address" 和 "Name"。 "Address" 是房间的电子邮件地址，"Name" 是房间的名称。
      1. 然后，创建**AvailableRoomsOptimal**集合。 这只是删除了 "可用性" 和 "与会者" 列的**AvailableRooms**集合。 这样做与**AvailableRoomsOptimal**和**AllRooms**的架构匹配。 这使您可以在**RoomBrowseGallery**的**Items**属性中使用这两个集合。
      1. **_roomListSelected**设置为**false**。
  1. 当所有其他操作完成后，加载状态 " **_loadingRooms**" 设置为 " **false** "。

## <a name="room-browse-gallery"></a>会议室浏览库

   ![RoomBrowseGallery 控件](media/meeting-screen/meeting-rooms-gall.png)

* 属性：**项**<br>
    值：逻辑上设置为相同架构的两个内部集合，具体取决于用户是否已选择会议室列表或其租户中包含会议室列表：

    ```powerapps-dot
    Search(
        If( _roomListSelected || _noRoomLists, AvailableRoomsOptimal, RoomsLists ),
        Trim(TextMeetingLocation1.Text), 
        "Name", 
        "Address"
    )
    ```

  如果 **_roomListSelected**或 **_noRoomLists**为**true**，此库将显示**AvailableRoomsOptimal**集合。 否则，它将显示**RoomsLists**集合。 这可以实现，因为这些集合的架构是相同的。

* 属性：**可见**<br>
    值： ```_showDetails && !IsBlank( _selectedMeetingTime ) && !_loadingRooms```

    只有这三个前述语句的计算结果为**true**时，库才可见。

### <a name="roombrowsegallery-title"></a>RoomBrowseGallery 标题

   ![RoomBrowseGallery 标题控件](media/meeting-screen/meeting-rooms-gall-title.png)

* 属性： **OnSelect**<br>
    值：一组逻辑绑定的**收集**和**set**语句，这些语句可能会或可能不会触发，具体取决于用户是否在查看房间列表或会议室：

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

  选择此控件时所发生的操作取决于用户当前是在查看一组房间列表还是一组聊天室。 如果它是前一种类型，则选择此控件可从 "所选聊天室" 列表中检索所选时间可用的会议室。 如果是后者，则选择此控件会将 **_selectedRoom**变量设置为所选的项。 前面的语句与[**FindMeetingTimesGallery 标题**](#find-meeting-times-gallery)的**Select**语句非常类似。

  在较低的级别上，上一个代码块：
  1. 通过将 **_loadingRooms**设置为**true**，打开房间的加载状态。
  1. 检查是否已选择会议室列表，以及租户是否有房间列表。 如果是这样：
      1. 将 **_roomListSelected**设置为**true** ，并将 **_selectedRoomList**设置为所选的项。
      1. **_AllRoomsConcat**变量设置为**AllRooms**集合中房间的前20个电子邮件地址的分号分隔的字符串。 这是因为， [Office365 FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times)操作仅限于在单个操作中搜索20个 person 对象的可用时间。
      1. **RoomTimeSuggestions**集合使用[Office365 FindMeetingTimes](https://docs.microsoft.com/connectors/office365/#find-meeting-times)操作，根据 **_selectedMeetingTime**变量中的时间值检索**AllRooms**集合中前20个房间的可用性。 请注意，`& "Z"` 用于正确设置**日期时间**值的格式。
      1. 创建**AvailableRooms**集合。 这只是与会者可用性的**RoomTimeSuggestions**集合，其中添加了另外两个列： "Address" 和 "Name"。 "Address" 是房间的电子邮件地址，"Name" 是房间的名称。
      1. 然后，创建**AvailableRoomsOptimal**集合。 这只是删除了 "可用性" 和 "与会者" 列的**AvailableRooms**集合。 这样做与**AvailableRoomsOptimal**和**AllRooms**的架构匹配。 这允许在**RoomBrowseGallery**的**Items**属性中使用这两个集合。
      1. **_roomListSelected**设置为**false**。
  1. 当所有其他操作完成后，加载状态 " **_loadingRooms**" 设置为 " **false** "。

## <a name="back-chevron"></a>后退 v 形

   ![RoomsBackNav 控件](media/meeting-screen/meeting-back.png)

* 属性：**可见**<br>
    值： `_roomListSelected && _showDetails`

    仅当选择了房间列表并且选择了 "**计划**" 选项卡时，此控件才可见。

* 属性： **OnSelect**<br>
    值： `Set( _roomListSelected, false )`

    将 **_roomListSelected**设置为**false**时，它会将**RoomBrowseGallery**控件更改为显示**RoomsLists**集合中的项。

## <a name="send-icon"></a>发送图标

   ![IconSendItem 控件](media/meeting-screen/meeting-send-icon.png)

* 属性： **DisplayMode**<br>
    值：在图标变为可编辑之前强制用户输入某些会议详细信息的逻辑。
    
    ```powerapps-dot
    If( Len( Trim( TextMeetingSubject1.Text ) ) > 0
        && !IsEmpty( MyPeople ) && !IsBlank( _selectedMeetingTime ),
        DisplayMode.Edit, DisplayMode.Disabled
    )
    ```
  此图标仅在以下情况下是可选的：会议主题已填写，至少有一个与会者参加会议，并已选择了会议时间。 否则，它会被禁用。

* 属性： **OnSelect**<br>

    值：用于将会议邀请发送到所选与会者并清除所有输入字段的代码：

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
  1. 使用 "Calendar" 的**DisplayName**将 **_MyCalendarName**设置为[CalendarGetTables （）](https://docs.microsoft.com/connectors/office365/#get-calendars)操作中的日历。
  1. 使用[Office365. V2CalendarPostItem](https://docs.microsoft.com/connectors/office365/#create-event--v2-)操作，从用户使用的各种选择中的所有输入值计划会议。
  1. 重置在创建会议时使用的所有输入字段和变量。

> [!NOTE]
> 根据你所在的区域，所需日历的显示名称可能不是 "Calendar"。 转到 Outlook 查看日历的标题，并在应用中进行适当的更改。

## <a name="next-steps"></a>后续步骤

* [了解有关此屏幕的详细信息](./meeting-screen-overview.md)
* [详细了解 Power Apps 中的 Office 365 Outlook connector](../connections/connection-office365-outlook.md)
* [详细了解 Power Apps 中的 Office 365 用户连接器](../connections/connection-office365-users.md)
