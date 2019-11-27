---
title: 对记录使用查找字段 |MicrosoftDocs
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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2019
ms.locfileid: "74177849"
---
#  <a name="use-the-lookup-field-on-a-record"></a>对记录使用查阅字段

查找可帮助您从相关实体中选择记录。 选择相关实体并输入搜索条件（如姓名或电子邮件地址）时，查找将自动开始解析部分文本，并显示所有匹配的记录。 如果键入搜索条件的完整文本后未显示任何记录，则显示一条消息，指出没有记录。

例如，可以搜索名称**Adrian Dumitrascu**。 键入**ad**时，可能会自动填充和显示可能的匹配记录。

  > [!div class="mx-imgBorder"]
  > ![自动填充匹配记录](media/automatically-populate-matching-records.png "自动填充匹配记录")
  
>[!NOTE] 
>管理员可以定义查找用于解析部分搜索文本的条件。

此外，还可以通过选择 "**新建**" 按钮创建新的记录。 您必须具有足够的权限才能查看 "**新建**" 按钮和创建记录。 选择查找字段时，会显示五个最近使用的记录以及五个收藏记录。 显示哪些记录取决于您的视图历史记录和您已固定的收藏夹。 

例如，如果历史记录中只有三个记录，则 "查找" 将显示这三个记录以及七个常用记录。 如果尚未固定任何收藏夹，则只会显示最近查看的记录。

## <a name="types-of-lookups"></a>查找类型

查找分为以下几个类别： 

- **简单查找：** 从单个实体的字段中选择单个记录。 

- **Attributetype.partylist 类型的字段：** 用于在查找中从多个实体选择多个记录。 使用 attributetype.partylist 字段可以选择多个记录。 这允许您通过多次执行新的搜索来添加每条记录。 每次选择一条记录时，都可以为另一个记录执行新的搜索。
  
- **相关类型字段：** 用于在查找中从多个实体选择单个记录。 

## <a name="search-in-a-lookup-field"></a>在查找字段中搜索 
若要搜索查找，请选择文本框并键入搜索条件。 如果为查找启用了 "最近的记录"，则在您选择文本框时将显示您最近的记录。

  > [!div class="mx-imgBorder"]
  > ![浏览查找字段](media/MRU.png "浏览查找字段")  
  
>[!NOTE]   
> 查找搜索的默认搜索结果为，以开头。 这意味着，结果包括以特定词开头的记录。 例如，如果要搜索**Alpine 滑雪房子**，请在搜索框中键入**alp** ;如果键入**ski**，则记录将不会显示在搜索结果中。
>
> 对于通配符搜索，请使用星号：例如，键入 * ski 或 * ski。

## <a name="browse-in-a-lookup-field"></a>在查找字段中浏览
若要浏览查找，请选择查找图标（放大镜）。 下拉列表中会显示项的完整列表。

  > [!div class="mx-imgBorder"]
  > ![搜索查找字段](media/MRU_1.png "搜索查找字段")  
 
## <a name="most-recently-used-record-type-images"></a>最近使用的记录类型图像
最近使用的记录列表显示了有助于区分不同记录类型的图像。

>[!NOTE] 
>不按搜索词或所选视图筛选最新记录。

  > [!div class="mx-imgBorder"]
  > ![查找字段显示图像](media/Lookup_03-MRU_Entity_Images_56[1].png "查找字段显示图像")  
  
## <a name="record-type-selection-list"></a>记录类型选择列表  
如果结果跨越多个记录类型，您可以查看其中有多少条记录，并从列表中选择它们。

  > [!div class="mx-imgBorder"]
  > ![查看多少条记录](media/Lookup_04-MultipleEntityTypes[1].gif "查看多少条记录")  
  
## <a name="create-a-new-record-if-you-dont-find-an-existing-record"></a>如果找不到现有记录，则创建一个新记录

如果未找到记录，请在查找区域中选择 "**新建**" 以创建新记录。


### <a name="replace-an-existing-record-from-a-lookup-field"></a>替换查找字段中的现有记录

使用简单的和 "相关类型" 查找时，可以替换现有记录。 搜索记录。 然后选择记录，并将其替换为新记录。

### <a name="change-a-view-in-a-lookup-field"></a>更改查找字段中的视图 

通过选择 "**更改视图**"，您可以确定：
 - 希望如何查看**联系人**、**联系人查找视图**或**活动联系人**等记录。
 - 要在记录中查看的内容，如姓名、电子邮件或电话号码。 例如，如果你只想查看你关注的联系人，请选择 "**更改视图**" \>**正在追随的联系人**。 将只显示你关注的联系人，如此处所示。 

    ![更改视图联系人类型](media/change-view.png "更改视图联系人类型")

>[!IMPORTANT] 
>如果管理员未将选项配置为显示在视图中，则不会显示 "**更改视图**" 选项。

### <a name="choose-from-multiple-records"></a>从多个记录中选择

如果查找的字段中的记录数多于可用显示区域容纳的数量，则显示区域将折叠，也就是说，显示区域的记录将显示在未显示的记录数旁边。 若要查看所有记录，请选择该数字。 下面的图像显示折叠和非折叠字段之间的差异。

**折叠**

![已折叠的多查找显示区域](media/collapsed-multi-lookup-display-area.png "已折叠的多查找显示区域")


**非折叠：**

![非折叠多查找显示区域](media/non-collapsed-multi-lookup-display-area.png "非折叠多查找显示区域")
