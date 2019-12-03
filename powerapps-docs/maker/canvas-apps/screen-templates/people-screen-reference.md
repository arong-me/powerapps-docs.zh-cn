---
title: 人员-屏幕模板参考 |Microsoft Docs
description: 了解有关 canvas 应用的人员屏幕模板在 Power Apps 中的工作原理的详细信息
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 1/2/2019
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e4e67b4905003f8134d8f6868671e74fdece3d6b
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732597"
---
# <a name="reference-information-about-the-people-screen-template-for-canvas-apps"></a>有关 canvas 应用的人员屏幕模板的参考信息

对于 Power Apps 中的画布应用，请了解人员-屏幕模板中的每个重大控件如何为屏幕的整体默认功能提供帮助。 此深入探讨介绍了行为公式以及其他属性的值，这些属性决定控件如何响应用户输入。 有关此屏幕默认功能的详细讨论，请参阅[用户界面概述](people-screen-overview.md)。

本主题重点介绍一些重要的控件，并说明这些控件的各种属性（例如**Items**和**OnSelect**）的设置表达式或公式：

* [文本搜索框](#text-search-box)
* [用户-浏览库](#user-browse-gallery)（+ 子控件）
* [人员添加的库](#people-added-gallery)（+ 子控件）

## <a name="prerequisite"></a>先决条件

熟悉如何[在 Power Apps 中创建应用](../data-platform-create-app-scratch.md)时添加和配置屏幕和其他控件。

## <a name="text-search-box"></a>文本搜索框

![TextSearchBox 控件](media/people-screen/people-search-box.png)

其他一些控件交互或依赖于文本搜索框：

* 如果用户开始键入任何文本，则**UserBrowseGallery**变得可见。
* 当用户在**UserBrowseGallery**中选择用户时，会重置搜索内容。

## <a name="user-browse-gallery"></a>用户-浏览库

![UserBrowseGallery 控件](media/people-screen/people-browse-gall.png)

* 属性：**项**<br>
    值：用户开始键入时查找用户的逻辑：
    
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
    
此库中的项由[Office365. SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser)操作的搜索结果填充。 操作使用 `Trim(TextSearchBox)` 中的文本作为其搜索词，并基于该搜索返回前15个结果。 由于在空格上进行的用户搜索无效， **TextSearchBox**包装在 `Trim()` 函数中。

由于在搜索框包含用户输入的文本时，只需调用该操作，因此 `Office365Users.SearchUser` 操作包装在 `If(!IsBlank(Trim(TextSearchBox.Text)) ... )` 函数中。 这可以提高性能。

### <a name="userbrowsegallery-title-control"></a>UserBrowseGallery 标题控件

![UserBrowseGallery 标题控件](media/people-screen/people-browse-gall-title.png)

* 属性：**文本**<br>值： `ThisItem.DisplayName`

  显示用户在其 Office 365 配置文件中的显示名称。

* 属性： **OnSelect**<br>
    值：要将用户添加到应用程序级集合的代码，然后选择用户：

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

   * 将 **\_selectedUser**变量设置为所选的项。
   * 重置**TextSearchBox**中的搜索词。
   * 将所选项目添加到**MyPeople**集合，该集合是应用用户选择的所有人员的集合。

### <a name="userbrowsegallery-profileimage-control"></a>UserBrowseGallery ProfileImage 控件

![UserBrowseGallery ProfileImage 控件](media/people-screen/people-browse-gall-image.png)

* 属性：**图像**<br>
    值：用于检索用户的个人资料照片的逻辑。

    ```powerapps-dot
    If( !IsBlank( ThisItem.Id ) && 
            'Office365Users'.UserPhotoMetadata( ThisItem.Id ).HasPhoto,
        'Office365Users'.UserPhoto( ThisItem.Id )
    )
    ```

**Image**控件检索用户的图像，并[Office365Users. UserPhoto](https://docs.microsoft.com/connectors/office365users/#get-user-photo--v1-)操作。 但是，在执行此操作之前，它会检查两项内容：
  
   * ID 字段是否为空。 这会阻止**图像**控件在库填充到搜索结果之前尝试检索用户照片。
   * 用户是否有照片（带有[Office365Users. UserPhotoMetadata](https://docs.microsoft.com/connectors/office365users/#get-user-photo-metadata)操作）。 这可以防止 `Office365Users.UserPhoto` 的查找在用户没有配置文件图片时返回异常。

请注意，如果未检索到图像，则**图像**控件为空白，而**iconUser**控件则改为可见。

## <a name="people-added-gallery"></a>人员添加的库

![PeopleAddedGallery 控件](media/people-screen/people-people-gall.png)

* 属性：**项**<br>
    值： `MyPeople`

这是通过选择**UserBrowseGallery 标题**控件进行初始化或添加到的人员的集合。

### <a name="peopleaddedgallery-title-control"></a>PeopleAddedGallery 标题控件

![PeopleAddedGallery 标题控件](media/people-screen/people-people-gall-title.png)

* 属性： **OnSelect**<br>
    值： `Set( _selectedUser, ThisItem )`

将 **_selectedUser**变量设置为在**EmailPeopleGallery**中选定的项。

### <a name="peopleaddedgallery-iconremove-control"></a>PeopleAddedGallery iconRemove 控件

![PeopleAddedGallery iconRemove 控件](media/people-screen/people-people-gall-delete.png)

* 属性： **OnSelect**<br>
    值： `Remove( MyPeople, LookUp( MyPeople, UserPrincipalName = ThisItem.UserPrincipalName ) )`

在**MyPeople**集合中查找记录，其中**UserPrincipalName**与选定项的**userprincipalname**匹配，然后从集合中删除该记录。

## <a name="next-steps"></a>后续步骤

* [了解有关此屏幕的详细信息](./people-screen-overview.md)。
* [了解有关 Office 365 Outlook connector 的详细信息](../connections/connection-office365-outlook.md)。
* [了解有关 Office 365 用户连接器的详细信息](../connections/connection-office365-users.md)。
