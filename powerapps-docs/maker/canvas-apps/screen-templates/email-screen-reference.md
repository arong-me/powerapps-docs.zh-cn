---
title: 画布应用的电子邮件屏幕模板参考 |Microsoft Docs
description: 了解有关 canvas 应用的电子邮件屏幕模板在 PowerApps 中的工作原理的详细信息
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
ms.openlocfilehash: 7663668b77c6f8186ef54c3182230fa843f86577
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71995690"
---
# <a name="reference-information-about-the-email-screen-template-for-canvas-apps"></a>有关 canvas 应用的电子邮件屏幕模板的参考信息

对于 PowerApps 中的画布应用，请了解电子邮件屏幕模板中的每个重要控件如何为屏幕的整体默认功能提供。 这一深入探讨介绍了如何通过其他属性来确定控件如何响应用户输入。 有关此屏幕默认功能的详细讨论，请参阅[电子邮件-屏幕概述](email-screen-overview.md)。

本主题重点介绍一些重要的控件，并说明这些控件的各种属性（例如**Items**和**OnSelect**）的设置表达式或公式：

* [文本搜索框](#text-search-box)
* [添加图标](#add-icon)
* [人员浏览库](#people-browse-gallery)
* [电子邮件人员库](#email-people-gallery)（+ 子控件）
* [邮件图标](#mail-icon)

## <a name="prerequisite"></a>先决条件

熟悉如何[在 PowerApps 中创建应用](../data-platform-create-app-scratch.md)时添加和配置屏幕和其他控件。

## <a name="text-search-box"></a>文本搜索框

   ![TextSearchBox 控件](media/email-screen/email-search-box.png)

屏幕上的多个其他控件在 "**文本搜索框**" 控件上具有依赖关系：

* 如果用户开始键入任意文本，将显示**PeopleBrowseGallery** 。
* 如果用户键入了有效的电子邮件地址，将显示**AddIcon** 。
* 当用户在**PeopleBrowseGallery**中选择用户时，会重置搜索内容。

## <a name="add-icon"></a>“添加”图标

   ![AddIcon 控件](media/email-screen/email-add-icon.png)

"**添加" 图标**控件允许应用程序将其组织内不存在的人员添加到正在撰写的电子邮件的收件人列表。

* 知识产权**亮起**<br>
    负值仅当用户在搜索框中键入有效的电子邮件地址时才显示控件的逻辑：

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```
  就行而言，前面的代码块表明仅在以下情况下，才会显示 "**添加图标**" 控件：

    * **TextSearchBox**包含文本。
    * **TextSearchBox**中的文本是有效的电子邮件地址。
    * **TextSearchBox**中的文本在**MyPeople**集合中尚不存在。

* 知识产权**OnSelect**<br>
    负值选择此将向**MyPeople**集合添加有效的电子邮件地址。 此集合由屏幕用作收件人列表：

    ```powerapps-dot
    Collect( MyPeople,
        { 
            DisplayName: TextSearchBox.Text, 
            UserPrincipalName: TextSearchBox.Text, 
            Mail: TextSearchBox.Text
        }
    );
    Reset( TextSearchBox )
    ```
  
  此代码块将行添加到**MyPeople**集合，并使用**TextSearchBox**中的文本填充三个字段。 这三个字段分别为**DisplayName**、 **UserPrincipalName**和**Mail**。 然后，它会重置**TextSearchBox**的内容。

## <a name="people-browse-gallery"></a>人员浏览库

   ![PeopleBrowseGallery 控件](media/email-screen/email-browse-gall.png)

* 知识产权**项**<br>
    负值键入到**TextSearchBox**控件中的搜索文本的前15个搜索结果：
    
    ```powerapps-dot
    If( !IsBlank( Trim(TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( {searchTerm: Trim( TextSearchBox.Text ), top: 15} )
    )
    ```

  此库中的项由[Office365. SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser)操作的搜索结果填充。 操作采用 `Trim(TextSearchBox)` 作为其搜索词的文本，并基于该搜索返回前15个结果。
  
  **TextSearchBox**封装在 `Trim()` 函数中，因为用户在空格上搜索无效。 @No__t-0 操作封装在一个 @no__t 的函数中，这意味着仅当搜索框包含用户输入的文本时才执行该操作。 这可以提高性能。 

### <a name="people-browse-gallery-title-control"></a>用户浏览库标题控件

   ![PeopleBrowseGallery 标题控件](media/email-screen/email-browse-gall-title.png)

* 知识产权**文本**<br>
    值： `ThisItem.DisplayName`

  显示用户在其 Office 365 配置文件中的显示名称。

* 知识产权**OnSelect**<br>
    负值将用户添加到应用程序级集合的代码，然后选择用户：

    ```powerapps-dot
    Concurrent(
        Set( _selectedUser, ThisItem ),
        Reset( TextSearchBox ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem )
        )
    )
    ```
选择此控件将同时执行三个操作：

   * 将 **_selectedUser**变量设置为所选的项。
   * 重置**TextSearchBox**中的搜索词。
   * 将所选项目添加到**MyPeople**集合，该集合是电子邮件屏幕用作一组收件人的所有选定用户的集合。

## <a name="email-people-gallery"></a>电子邮件人员库

   ![EmailPeopleGallery 控件](media/email-screen/email-people-gall.png)

* 知识产权**项**<br>
    值： `MyPeople`

  这是通过选择**PeopleBrowseGallery 标题**控件进行初始化或添加到的人员的集合。

* 知识产权**高**<br>
    负值用于根据库中当前的项数设置高度的逻辑：

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery.TemplateHeight + EmailPeopleGallery.TemplatePadding * 2) *
            RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0 ),
        304
    )
    ```

  此库的高度将调整为库中的项目数，最大高度为304。
  
  它将 `TemplateHeight + TemplatePadding * 2` 作为**EmailPeopleGallery**的单个行的总高度，然后将其与行数相乘。 由于 `WrapCount = 2`，因此 @no__t 的实际行数为-1。

* 知识产权**ShowScrollbar**<br>
    值： `EmailPeopleGallery.Height >= 304`
  
  当库的高度达到304时，滚动条可见。

### <a name="email-people-gallery-title-control"></a>电子邮件人员库标题控件

   ![EmailPeopleGallery 标题控件](media/email-screen/email-people-gall-text.png)

* 知识产权**OnSelect**<br>
    值： `Set(_selectedUser, ThisItem)`

  将 **_selectedUser**变量设置为在**EmailPeopleGallery**中选定的项。

### <a name="email-people-gallery-iconremove-control"></a>电子邮件人员库 iconRemove 控件

   ![MonthDayGallery 标题控件](media/email-screen/email-people-gall-delete.png)

* 知识产权**OnSelect**<br>
    值： `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

  在**MyPeople**集合中查找记录，其中**UserPrincipalName**与选定项的**userprincipalname**匹配，并从集合中删除该记录。

## <a name="mail-icon"></a>邮件图标

* 知识产权**OnSelect**<br>
    负值用于发送用户电子邮件的逻辑：

    ```powerapps-dot
    Set( _emailRecipientString, Concat( MyPeople, Mail & ";" ) );
    'Office365'.SendEmail( _emailRecipientString, 
        TextEmailSubject.Text,  
        TextEmailMessage.Text, 
        { Importance:"Normal" }
    );
    Reset( TextEmailSubject );
    Reset( TextEmailMessage );
    Clear( MyPeople )
    ```

  发送电子邮件需要用分号分隔的电子邮件地址字符串。 在前面的代码中：
  1. 第一行代码将**MyPeople**集合中的所有行中的**Mail**字段连接到单个字符串（由分号分隔），并将 **_emailRecipientString**变量设置为该字符串负值.

  1. 然后，它使用[Office365. SendEmail](https://docs.microsoft.com/connectors/office365/#sendemail)操作向收件人发送电子邮件。
    操作包含三个必需参数： "**到**"、"**主题**" 和 "**正文**"，以及一个可选参数--**重要性**。 在前面的代码中，这些是 **_emailRecipientString**、 **TextEmailSubject**。Text、 **TextEmailMessage**。Text 和**Normal**。
  1. 最后，它会重置**TextEmailSubject**和**TextEmailMessage**控件，并清除**MyPeople**集合。

* 知识产权**DisplayMode**<br>
    负值`If( Len( Trim( TextEmailSubject.Text ) ) > 0 && !IsEmpty( MyPeople ), DisplayMode.Edit, DisplayMode.Disabled )` 表示发送电子邮件，则电子邮件主题行必须包含文本，收件人（**MyPeople**）集合不得为空。

## <a name="next-steps"></a>后续步骤

* [了解有关此屏幕的详细信息](./email-screen-overview.md)
* [详细了解 PowerApps 中的 Office 365 Outlook connector](../connections/connection-office365-outlook.md)
* [详细了解 PowerApps 中的 Office 365 用户连接器](../connections/connection-office365-users.md)
