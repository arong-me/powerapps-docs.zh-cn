---
title: 画布应用的电子邮件屏幕模板引用 |Microsoft Docs
description: 了解 PowerApps 中的画布应用的电子邮件屏幕模板工作原理详细的信息
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
ms.openlocfilehash: 8f77fe1194ace2f8cb5abeb3f9657cc76aab263a
ms.sourcegitcommit: 5e15a1033a68289781f8092fb65c57432501f911
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54459473"
---
# <a name="reference-information-about-the-email-screen-template-for-canvas-apps"></a>有关画布应用的电子邮件屏幕模板的参考信息

对于在 PowerApps 中的画布应用，了解如何在电子邮件屏幕模板中的每个重要控件影响屏幕的整体默认功能。 此深入探讨了行为公式以及其他属性，用于确定控件如何响应用户输入的值。 此屏幕的默认功能的综合讨论，请参阅[电子邮件屏幕概述](email-screen-overview.md)。

本主题重点介绍一些重要的控件，并介绍的各种属性的表达式或公式 (如**项**并**OnSelect**) 这些控件的设置：

* [文本搜索框](#text-search-box)
* [添加图标](#add-icon)
* [用户浏览库](#people-browse-gallery)
* [电子邮件的人员库](#email-people-gallery)（+ 子控件）
* [邮件图标](#mail-icon)

## <a name="prerequisite"></a>先决条件

如何添加和配置屏幕和其他控件为您熟悉[在 PowerApps 中创建应用](../data-platform-create-app-scratch.md)。

## <a name="text-search-box"></a>文本搜索框

   ![TextSearchBox 控件](media/email-screen/email-search-box.png)

在屏幕中的多个其他控件具有依赖关系**文本搜索框**控件：

* 如果用户开始输入任何文本**PeopleBrowseGallery**出现。
* 如果用户键入一个有效的电子邮件地址，out **AddIcon**出现。
* 如果用户选择内的某个人**PeopleBrowseGallery**，重置搜索内容。

## <a name="add-icon"></a>“添加”图标

   ![AddIcon 控件](media/email-screen/email-add-icon.png)

**添加图标**控件允许应用用户添加到正在撰写的电子邮件的收件人列表其组织内不存在的人员。

* 属性：**Visible**<br>
    值：只有当用户在搜索框中键入一个有效的电子邮件地址时，才显示该控件的逻辑：

    ```powerapps-dot
    !IsBlank( TextSearchBox.Text ) &&
        IsMatch( TextSearchBox.Text, Match.Email ) &&
        Not( Trim( TextSearchBox.Text ) in MyPeople.UserPrincipalName )
    ```
  行的行中，前面的代码块指出**添加图标**控件将显示仅当：

    * **TextSearchBox**包含文本。
    * 中的文本**TextSearchBox**是有效的电子邮件地址。
    * 中的文本**TextSearchBox**中不存在**MyPeople**集合。

* 属性：**OnSelect**<br>
    值：选择此项将添加到有效的电子邮件地址**MyPeople**集合。 此集合可作为收件人列表的屏幕：

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
  
  此代码块添加到行**MyPeople**集合，并填充三个字段中的文本**TextSearchBox**。 这三个字段都**DisplayName**， **UserPrincipalName**，并**邮件**。 它将重置的内容**TextSearchBox**。

## <a name="people-browse-gallery"></a>用户浏览库

   ![PeopleBrowseGallery 控件](media/email-screen/email-browse-gall.png)

* 属性：**项**<br>
    值：键入到搜索文本的前 15 个搜索结果**TextSearchBox**控件：
    
    ```powerapps-dot
    If( !IsBlank( Trim(TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser( {searchTerm: Trim( TextSearchBox.Text ), top: 15} )
    )
    ```

  此库的项填充从搜索结果的[Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser)操作。 该操作采用文本`Trim(TextSearchBox)`作为搜索字词，并返回前 15 个结果基于该搜索。
  
  **TextSearchBox**包装在`Trim()`函数，因为空间上的用户搜索无效。 `Office365Users.SearchUser`操作包装在`If(!IsBlank(Trim(TextSearchBox.Text)) ... )`函数，这意味着只有在搜索框中包含用户输入的文本执行操作。 这可以提高性能。 

### <a name="people-browse-gallery-title-control"></a>用户浏览库标题控件

   ![PeopleBrowseGallery 标题控件](media/email-screen/email-browse-gall-title.png)

* 属性：**文本**<br>
    值： `ThisItem.DisplayName`

  显示从其 Office 365 配置文件的用户的显示名称。

* 属性：**OnSelect**<br>
    值：若要将用户添加到应用程序级集合的代码，然后选择用户：

    ```powerapps-dot
    Concurrent(
        Set( _selectedUser, ThisItem ),
        Reset( TextSearchBox ),
        If( Not( ThisItem.UserPrincipalName in MyPeople.UserPrincipalName ), 
            Collect( MyPeople, ThisItem )
        )
    )
    ```
选择此控件同时执行三项操作：

   * 集 **_selectedUser**变量选择的项。
   * 重置中的搜索词**TextSearchBox**。
   * 将添加到所选的项**MyPeople**集合、 为一组收件人的电子邮件屏幕使用的所有所选用户的集合。

## <a name="email-people-gallery"></a>电子邮件的人员库

   ![EmailPeopleGallery 控件](media/email-screen/email-people-gall.png)

* 属性：**项**<br>
    值： `MyPeople`

  这是初始化或通过选择添加到用户的集合**PeopleBrowseGallery 标题**控件。

* 属性：**Height**<br>
    值：若要设置的高度，基于当前库中的项数量的逻辑：

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery.TemplateHeight + EmailPeopleGallery.TemplatePadding * 2) *
            RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0 ),
        304
    )
    ```

  为 304 的最大高度的项数在库中，调整此库的高度。
  
  所需`TemplateHeight + TemplatePadding * 2`作为单个行的总高度**EmailPeopleGallery**，然后将其乘以的行数。 由于`WrapCount = 2`，则返回 true 的行数是`RoundUp(CountRows(EmailPeopleGallery.AllItems) / 2, 0)`。

* 属性：**ShowScrollbar**<br>
    值： `EmailPeopleGallery.Height >= 304`
  
  当库的高度达到 304 时，滚动条可见。

### <a name="email-people-gallery-title-control"></a>电子邮件的人员库标题控件

   ![EmailPeopleGallery 标题控件](media/email-screen/email-people-gall-text.png)

* 属性：**OnSelect**<br>
    值： `Set(_selectedUser, ThisItem)`

  集 **_selectedUser**变量中的选定项**EmailPeopleGallery**。

### <a name="email-people-gallery-iconremove-control"></a>电子邮件的人员库 iconRemove 控件

   ![MonthDayGallery 标题控件](media/email-screen/email-people-gall-delete.png)

* 属性：**OnSelect**<br>
    值： `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

  查找在中记录**MyPeople**集合，其中**UserPrincipalName**匹配**UserPrincipalName**选定的项，并从记录的删除集合。

## <a name="mail-icon"></a>邮件图标

* 属性：**OnSelect**<br>
    值：若要将用户的电子邮件发送的逻辑：

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

  发送一封电子邮件都需要的电子邮件地址之间用分号分隔的字符串。 在前面的代码：
  1. 第一个行代码所**邮件**字段中的所有行从**MyPeople**集合中，将它们连接成单个字符串的电子邮件地址由分号隔开，并设置 **_emailRecipientString**变量为该字符串值。

  1. 然后，它使用[Office365.SendEmail](https://docs.microsoft.com/connectors/office365/#sendemail)操作发送到收件人的电子邮件。
    该操作具有三个必需的参数，**到**，**主题**，并**正文**，和一个可选参数-**重要性**。 在前面的代码，这些是 **_emailRecipientString**， **TextEmailSubject**。文本**TextEmailMessage**。文本，并**正常**分别。
  1. 最后，它将重置**TextEmailSubject**并**TextEmailMessage**控制，并清除**MyPeople**集合。

* 属性：**DisplayMode**<br>
    值：`If( Len( Trim( TextEmailSubject.Text ) ) > 0 && !IsEmpty( MyPeople ), DisplayMode.Edit, DisplayMode.Disabled )` 要发送的电子邮件，电子邮件主题行必须具有文本和接收方 (**MyPeople**) 集合不能为空。

## <a name="next-steps"></a>后续步骤

* [了解有关此屏幕的详细信息](./email-screen-overview.md)
* [了解有关 PowerApps 中的 Office 365 Outlook 连接器的详细信息](../connections/connection-office365-outlook.md)
* [了解有关 PowerApps 中的 Office 365 用户连接器的详细信息](../connections/connection-office365-users.md)
