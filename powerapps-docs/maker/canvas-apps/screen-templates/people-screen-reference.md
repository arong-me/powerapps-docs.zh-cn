---
title: 人们屏幕模板引用 |Microsoft Docs
description: 了解 PowerApps 中的画布应用的人屏幕模板工作原理详细的信息
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 1/2/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 09b92a1e2bc87ac6f4e2ec651aa67a845e0f07b1
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61540619"
---
# <a name="reference-information-about-the-people-screen-template-for-canvas-apps"></a>有关画布应用的人屏幕模板的参考信息

对于在 PowerApps 中的画布应用，了解人们屏幕模板中的每个重要控件如何影响屏幕的整体默认功能。 此深入探讨了行为公式以及其他属性，用于确定控件如何响应用户输入的值。 此屏幕的默认功能的综合讨论，请参阅[人屏幕概述](people-screen-overview.md)。

本主题重点介绍一些重要的控件，并介绍的各种属性的表达式或公式 (如**项**并**OnSelect**) 这些控件的设置：

* [文本搜索框](#text-search-box)
* [用户浏览库](#user-browse-gallery)（+ 子控件）
* [用户将添加库](#people-added-gallery)（+ 子控件）

## <a name="prerequisite"></a>先决条件

如何添加和配置屏幕和其他控件为您熟悉[在 PowerApps 中创建应用](../data-platform-create-app-scratch.md)。

## <a name="text-search-box"></a>文本搜索框

![TextSearchBox 控件](media/people-screen/people-search-box.png)

几个其他控件进行交互，或在搜索文本框上具有依赖关系：

* 如果用户开始输入任何文本**UserBrowseGallery**将变得可见。
* 如果用户选择内的某个人**UserBrowseGallery**，重置搜索内容。

## <a name="user-browse-gallery"></a>用户浏览库

![UserBrowseGallery 控件](media/people-screen/people-browse-gall.png)

* 属性：**项**<br>
    值：若要查找用户，当用户开始键入时的逻辑：
    
    ```powerapps-dot
    If( !IsBlank( Trim( TextSearchBox.Text ) ), 
        'Office365Users'.SearchUser(
            {
                searchTerm: Trim( TextSearchBox.Text ), 
                top: 15
            }
        )
    )
    ```
    
此库的项填充从搜索结果的[Office365.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser)操作。 该操作采用文本`Trim(TextSearchBox)`作为搜索字词，并返回前 15 个结果基于该搜索。 **TextSearchBox**包装在`Trim()`函数，因为空间上的用户搜索无效。

`Office365Users.SearchUser`操作包装在`If(!IsBlank(Trim(TextSearchBox.Text)) ... )`函数，因为只需在搜索框中包含用户输入的文本时调用该操作。 这可以提高性能。

### <a name="userbrowsegallery-title-control"></a>UserBrowseGallery 标题控件

![UserBrowseGallery 标题控件](media/people-screen/people-browse-gall-title.png)

* 属性：**文本**<br>值： `ThisItem.DisplayName`

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

   * 集 **\_selectedUser**变量选择的项。
   * 重置中的搜索词**TextSearchBox**。
   * 将添加到所选的项**MyPeople**应用用户集合，集合中所有人的选择。

### <a name="userbrowsegallery-profileimage-control"></a>UserBrowseGallery 配置文件映像控件

![UserBrowseGallery 配置文件映像控件](media/people-screen/people-browse-gall-image.png)

* 属性：**图像**<br>
    值：若要检索用户的个人资料照片的逻辑。

    ```powerapps-dot
    If( !IsBlank( ThisItem.Id ) && 
            'Office365Users'.UserPhotoMetadata( ThisItem.Id ).HasPhoto,
        'Office365Users'.UserPhoto( ThisItem.Id )
    )
    ```

**图像**控件中检索用户的映像[Office365Users.UserPhoto](https://docs.microsoft.com/connectors/office365users/#get-user-photo--v1-)操作。 但是之前执行该操作，, 它会检查两件事：
  
   * ID 字段是否为空或不为空。 这可以防止**图像**尝试检索用户照片库填充搜索结果与之前的控件。
   * 用户是否有一张照片 (与[Office365Users.UserPhotoMetadata](https://docs.microsoft.com/connectors/office365users/#get-user-photo-metadata)操作)。 这可以防止`Office365Users.UserPhoto`返回异常，如果用户不具有个人资料图片的查找。

请注意，如果映像不检索，则**图像**控件为空，并**图标**控件改为是否可见。

## <a name="people-added-gallery"></a>用户将添加库

![PeopleAddedGallery 控件](media/people-screen/people-people-gall.png)

* 属性：**项**<br>
    值： `MyPeople`

这是初始化或通过选择添加到用户的集合**UserBrowseGallery 标题**控件。

### <a name="peopleaddedgallery-title-control"></a>PeopleAddedGallery 标题控件

![PeopleAddedGallery 标题控件](media/people-screen/people-people-gall-title.png)

* 属性：**OnSelect**<br>
    值： `Set( _selectedUser, ThisItem )`

集 **_selectedUser**变量中的选定项**EmailPeopleGallery**。

### <a name="peopleaddedgallery-iconremove-control"></a>PeopleAddedGallery iconRemove 控件

![PeopleAddedGallery iconRemove 控件](media/people-screen/people-people-gall-delete.png)

* 属性：**OnSelect**<br>
    值： `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

查找在中记录**MyPeople**集合，其中**UserPrincipalName**匹配**UserPrincipalName**选定的项，然后从记录的删除集合。

## <a name="next-steps"></a>后续步骤

* [了解有关此屏幕的详细信息](./people-screen-overview.md)。
* [了解有关 Office 365 Outlook 连接器的详细信息](../connections/connection-office365-outlook.md)。
* [了解有关 Office 365 用户连接器的详细](../connections/connection-office365-users.md)。
