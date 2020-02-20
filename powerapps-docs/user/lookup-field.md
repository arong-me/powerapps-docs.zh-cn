---
title: 对记录使用查阅字段 |MicrosoftDocs
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/06/2019
ms.author: mkaur
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 4ef67695603f3badeba92f46c6da90e21715c98b
ms.sourcegitcommit: 01fefd7a06bf5d6509acd0bb54ea6479208cbbc8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2019
ms.locfileid: "74177849"
---
#  <a name="use-the-lookup-field-on-a-record"></a>对记录使用查阅字段

查阅可帮助你从相关实体中选择记录。 当你选择相关实体并输入搜索条件（如姓名或电子邮件地址）时，查阅会自动开始解析部分文本并显示所有匹配记录。 如果键入搜索条件的完整文本后未显示任何记录，则显示一条表明无记录的消息。

例如，你可以搜索姓名“Adrian Dumitrascu”  。 当你键入“ad”后，系统将自动填充和显示可能的匹配记录  。

  > [!div class="mx-imgBorder"]
  > ![自动填充匹配记录](media/automatically-populate-matching-records.png "自动填充匹配记录")
  
>[!NOTE] 
>管理员可以定义查阅用于解析部分搜索文本的条件。

此外，还可以选择“新建”按钮来创建新记录  。 你必须具有足够的权限才能查看“新建”按钮并创建一条记录  。 选择查阅字段时，会显示五个最近使用的记录以及五个收藏记录。 显示的记录取决于查看历史记录和已固定的收藏。 

例如，如果历史记录中只有三条记录，则查阅将显示这三条记录以及七条收藏记录。 如果尚未固定任何收藏记录，则只会显示最近查看的记录。

## <a name="types-of-lookups"></a>查阅类型

查阅可划分为以下几个类别： 

- **简单查阅：** 从单个实体的字段中选择单个记录。 

- **PartyList 类型字段：** 用于在查找中从多个实体选择多个记录。 使用 partylist 类型字段选择多个记录。 由此可多次执行新的搜索来添加每条记录。 每次选择一条记录时，都可以为另一条记录执行新的搜索。
  
- **相关类型字段：** 用于在查阅中从多个实体选择单条记录。 

## <a name="search-in-a-lookup-field"></a>在查阅字段中搜索 
若要搜索查阅，请选择文本框并键入搜索条件。 如果为查阅启用了最近记录，则在选择文本框时将显示最近的记录。

  > [!div class="mx-imgBorder"]
  > ![浏览查阅字段](media/MRU.png "浏览查阅字段")  
  
>[!NOTE]   
> 查阅搜索的默认搜索结果为“开头”。 这意味着，结果包括以特定词开头的记录。 例如，如果要搜索“Alpine Ski House”，请在搜索框中键入“alp”；如果键入“ski”，则该记录不会显示在搜索结果中    。
>
> 若要进行通配符搜索，请使用星号：例如，键入 *ski 或 *ski。

## <a name="browse-in-a-lookup-field"></a>在查阅字段中浏览
若要浏览查阅，请选择查阅图标（放大镜）。 下拉列表中会显示项的完整列表。

  > [!div class="mx-imgBorder"]
  > ![搜索查阅字段](media/MRU_1.png "搜索查阅字段")  
 
## <a name="most-recently-used-record-type-images"></a>最近使用的记录类型图像
最近使用的记录列表显示了有助于区分不同记录类型的图像。

>[!NOTE] 
>不按搜索词或所选视图筛选最近使用的记录。

  > [!div class="mx-imgBorder"]
  > ![查阅字段显示图像](media/Lookup_03-MRU_Entity_Images_56[1].png "查阅字段显示图像")  
  
## <a name="record-type-selection-list"></a>记录类型选择列表  
如果结果跨越多个记录类型，你可以查看其中有多少种记录类型，并从列表中进行选择。

  > [!div class="mx-imgBorder"]
  > ![查看有多少条记录](media/Lookup_04-MultipleEntityTypes[1].gif "查看有多少条记录")  
  
## <a name="create-a-new-record-if-you-dont-find-an-existing-record"></a>如果找不到现有记录，请创建新记录

如果找不到记录，请在查阅区域中选择“新建”以创建新记录  。


### <a name="replace-an-existing-record-from-a-lookup-field"></a>替换查阅字段中的现有记录

使用简单和相关类型查阅时，可以替换现有记录。 搜索记录。 然后选择记录，再将其替换为新记录。

### <a name="change-a-view-in-a-lookup-field"></a>在查阅字段中更改视图 

选择“更改视图”可确定  ：
 - 如何查看记录，如“关注的联系人”、“联系人查阅视图”或“活动联系人”    。
 - 要在记录中查看的内容，如姓名、电子邮件或电话号码。 例如，如果只想查看你关注的联系人，请选择“更改视图”\>“关注的联系人”   。 将只显示你关注的联系人，如此处所示。 

    ![更改视图联系人类型](media/change-view.png "更改视图联系人类型")

>[!IMPORTANT] 
>如果你的管理员尚未将“更改视图”选项配置为在视图中显示，则该选项将不可见  。

### <a name="choose-from-multiple-records"></a>从多条记录中选择

如果查阅字段中的记录数多于可用显示区域中容纳的数量，则显示区域将折叠，也就是说，将显示区域可显示的记录，并在其旁边显示未显示的记录数。 若要查看所有记录，请选择该数字。 下面的图像显示了已折叠和未折叠字段的差异。

**已折叠：**

![已折叠的多查阅显示区域](media/collapsed-multi-lookup-display-area.png "已折叠的多查阅显示区域")


**未折叠：**

![未折叠的多查阅显示区域](media/non-collapsed-multi-lookup-display-area.png "未折叠的多查阅显示区域")
