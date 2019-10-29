---
title: 画布应用中的 AsType 和 IsType 函数 |Microsoft Docs
description: 画布应用中 AsType 和 IsType 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0ecb30a5a452a6ee092ccf9bc9d47f6182ef60ab
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "71993002"
---
# <a name="astype-and-istype-functions-in-canvas-apps"></a>画布应用中的 AsType 和 IsType 函数

检查特定实体类型（**IsType**）的记录引用，并将该引用视为特定类型（**AsType**）。

## <a name="description"></a>描述

阅读[了解记录引用和多态查找](../working-with-references.md)，了解更多详细信息和更多详细信息。

查找字段通常指特定实体中的记录。 由于实体类型已建立良好的关系，因此可以使用简单的点表示法访问查找字段。 例如，**第一个（帐户）。主要联系人 ".""全名"** 从 "**帐户**" 实体遍历到 "**联系人**" 实体中的**主要联系人**记录，并提取 "**全名**" 字段。

Common Data Service 还支持多态查找字段，它们可以引用一组实体中的记录，如这些示例中所示。

| 查找字段 | 可以引用 |
|--------------|--------------|
| **Owner** | **用户**或**团队** |
| **客户** | **帐户**或**联系人** |
| **联系** | **帐户**、**联系人**、**知识库文章**等。 |

<!--note from editor: Change "Knowledge Articles" to "Knowledge Base articles" if that is what is being referenced.   -->

在 "画布-应用公式" 中，您可以使用记录引用来处理多态查找。 由于记录引用可以引用不同的实体，因此，在编写公式时，您不知道哪些字段将可用。 *。字段*表示法不可用。 这些公式必须适应应用在运行时遇到的记录。

**IsType**函数测试记录引用是否引用特定的实体类型。 该函数返回布尔值 TRUE 或 FALSE。

**AsType**函数将记录引用视为特定实体类型，有时称为 "*强制转换*"。 您可以使用结果，就像它是实体的记录一样，并再次使用 *。* 用于访问该记录的所有字段的字段表示法。 如果引用不是特定类型，则会发生错误。

将这些函数一起使用可以先测试记录的实体类型，然后将其视为该类型的记录，以便字段可用：

```powerapps-dot
If( IsType( First( Accounts ).Owner, Users ),
    AsType( First( Accounts ).Owner, Users ).'Full Name',
    AsType( First( Accounts ).Owner, Teams ).'Team Name'
)
```

只有在访问记录引用的字段时，才需要这些函数。 例如，可以在[**筛选器**](function-filter-lookup.md)函数中使用不带**IsType**或**AsType**的记录引用：

```powerapps-dot
Filter( Accounts, Owner = First( Users ) )
```

同样，你可以将记录引用与[**Patch**](function-patch.md)函数结合使用：

```powerapps-dot
Patch( Accounts, First( Accounts ), { Owner: First( Teams ) } )
```  

如果用于记录上下文（如[**库**](../controls/control-gallery.md)中或[**编辑窗体**](../controls/control-form-detail.md)控件中），则可能需要使用[全局歧义消除运算符](operators.md#disambiguation-operator)来引用实体类型。 例如，对于显示其**公司名称**为**客户**查找的联系人列表的库，此公式会有效：

```powerapps-dot
If( IsType( ThisItem.'Company Name', [@Accounts] ),
    AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

对于这两个函数，通过连接到实体的数据源的名称指定类型。 若要运行公式，还必须将数据源添加到应用中要测试或强制转换的任何类型。 例如，如果要将**IsType**和**AsType**与该实体的**所有者**查找和记录一起使用，则必须将**用户**实体添加为数据源。 只能添加实际在应用中使用的数据源;不需要添加查找可以引用的所有实体。

如果记录引用为*空*， **ISTYPE**将返回 FALSE，并且**AsType**将返回*空白*。 *空*记录的所有字段都将为*空*。

## <a name="syntax"></a>语法

**AsType**（ *RecordReference*， *EntityType* ）

- *RecordReference* -必需。 记录引用，通常是可以引用任意多个实体中的记录的查找字段。
- *EntityType* -必需。 要测试的特定实体。

**IsType**（ *RecordReference*， *EntityType* ）

- *RecordReference* -必需。 记录引用，通常是可以引用任意多个实体中的记录的查找字段。
- *EntityType* -必需。 记录应强制转换为的特定实体。

## <a name="example"></a>示例

[了解记录引用和多态查找](../working-with-references.md)包含广泛的示例。

1. 为平板电脑创建空白画布应用。

1. 在 "**视图**" 选项卡上，选择 "**数据源**"，然后添加 "**联系人**" 和 "**帐户**" 实体作为数据源。
    > [!div class="mx-imgBorder"]
    > ![具有两个数据源的空白应用：帐户和联系人](media/function-astype-istype/contacts-add-datasources.png)

1. 插入具有**空白垂直**方向的**库**控件。

    > [!div class="mx-imgBorder"]
    > ![插入具有空白垂直布局的库控件](media/function-astype-istype/contacts-customer-gallery.png)

1. 在屏幕右侧附近的 "**属性**" 选项卡上，将库的**Items**属性设置为 "**联系人**"。

    > [!div class="mx-imgBorder"]
    > ![在 "属性" 窗格中将项目设置为 Contacts](media/function-astype-istype/contacts-customer-datasource.png)

1. 将库的布局设置为 "**标题" 和 "副标题**"。

    > [!div class="mx-imgBorder"]
    > ![在 "属性" 窗格中打开 "布局选取器"](media/function-astype-istype/contacts-customer-layout.png)

    > [!div class="mx-imgBorder"]
    > ![将布局设置为标题和副标题](media/function-astype-istype/contacts-customer-flyout.png)

1. 在 "**数据**" 窗格中，打开 " **Title1** " 列表，然后选择 "**全名**"。

    > [!div class="mx-imgBorder"]
    > ![设置标题值](media/function-astype-istype/contacts-customer-title.png)

1. 选择**Subtitle1**标签控件。

    > [!div class="mx-imgBorder"]
    > ![设置副标题值](media/function-astype-istype/contacts-customer-subtitle.png)

1. 将**Subtitle1**的**Text**属性设置为以下公式：

    ```powerapps-dot
    If( IsBlank( ThisItem.'Company Name' ), "--",
        IsType( ThisItem.'Company Name', [@Accounts] ),
            "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
        "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
    )
    ```

    > [!div class="mx-imgBorder"]
    > 现在，![屏幕显示了在库中混合的帐户和联系人](media/function-astype-istype/contacts-customer-complete.png)

    库中的副标题显示以下值：
    - 如果 **"公司名称"** 为*空*，则为 "--"。
    - "帐户："，然后是 **"帐户" 实体中**的 "**帐户名称**" 字段（如果 "**公司名称**" 字段引用了帐户）。
    - 如果 "**公司名称**" 字段引用某一联系人，则 "联系：" 和 "**联系人**" 实体中的 "**全名**" 字段。

    您的结果可能与本主题中的结果不同，因为它使用修改后的示例数据显示其他类型的结果。
