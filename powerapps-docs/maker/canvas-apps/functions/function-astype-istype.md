---
title: 中的 AsType 和 IsType 函数画布应用 |Microsoft Docs
description: 参考信息，包括语法和示例，AsType 和 IsType 函数的画布应用
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 999653159f838e840f7f569aa9953633a6a70065
ms.sourcegitcommit: 93096dfa1aadba77159db1e5922f3d5528eecb7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/21/2019
ms.locfileid: "65986329"
---
# <a name="astype-and-istype-functions-in-canvas-apps"></a>中的 AsType 和 IsType 函数画布应用

检查特定实体类型的记录引用 (**IsType**)，并将该引用视为特定类型 (**AsType**)。

## <a name="description"></a>描述

读取[了解记录引用和多态查找](../working-with-references.md)有关的更广泛的介绍和详细信息。

查找字段通常是指特定实体中的记录。 由于实体类型是制定完善，您可以使用简单的点表示法访问查找的字段。 例如，**第一个 （帐户）。主要联系人。完整的名称**从引导**帐户**到实体**主要联系人**记录中**联系人**实体和提取**完整名称**字段。

Common Data Service 还支持多态查找字段，可以引用的记录从一组实体，如以下示例所示。

| 查找字段 | 可以参考 |
|--------------|--------------|
| **Owner** | **用户**或**团队** |
| **客户** | **帐户**或**联系人** |
| **有关** | **帐户**，**联系人**，**知识库文章**，等等。 |

<!--note from editor: Change "Knowledge Articles" to "Knowledge Base articles" if that is what is being referenced.   -->

在画布应用的公式，可以使用记录引用以使用多态查找。 记录引用可引用不同的实体，因为你不知道编写公式时，可以使用哪些字段。 *。字段*表示法不可用。 这些公式必须适应应用程序遇到运行时的记录。

**IsType**函数测试是否记录引用所引用的特定实体类型。 该函数返回布尔值 TRUE 或 FALSE。

**AsType**函数将记录参考特定实体类型，有时称为视为*强制转换*。 您可以使用结果，就好像该实体的记录并再次使用 *。字段*表示法访问的所有该记录的字段。 如果特定类型的引用不，发生错误。

同时使用这些函数来首次测试一条记录的实体类型，然后将其视为该类型的记录，以便这些字段均可用：

```powerapps-dot
If( IsType( First( Accounts ).Owner, Users ),
    AsType( First( Accounts ).Owner, Users ).'Full Name',
    AsType( First( Accounts ).Owner, Teams ).'Team Name'
)
```

仅当要访问的记录引用的字段时，才需要这些函数。 例如，可以使用中的记录引用[**筛选器**](function-filter-lookup.md)有效，无需**IsType**或者**AsType**:

```powerapps-dot
Filter( Accounts, Owner = First( Users ) )
```

同样，可以使用具有记录引用[**修补**](function-patch.md)函数：

```powerapps-dot
Patch( Accounts, First( Accounts ), { Owner: First( Teams ) } )
```  

如果在记录上下文中，使用如内[**库**](../controls/control-gallery.md)或[**编辑窗体**](../controls/control-form-detail.md)控件，您可能需要使用[全局消除歧义运算符](operators.md#disambiguation-operator)要引用的实体类型。 例如，此公式将是一个库，其中显示的联系人列表的有效位置**公司名称**是**客户**查找：

```powerapps-dot
If( IsType( ThisItem.'Company Name', [@Accounts] ),
    AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
    AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
)
```

对于这两个函数指定通过名称连接到该实体的数据源的类型。 若要运行该公式，您必须将数据源添加到适用于你想要测试或强制转换任何类型的应用。 例如，您必须添加**用户**作为数据源，如果你想要使用的实体**IsType**并**AsType**与**所有者**查找和记录从该实体。 可以添加你实际使用应用程序; 中的数据源不需要添加一个查找可以引用的所有实体。

如果记录引用*空白*， **IsType**将返回 FALSE，并**AsType**返回*空白*。 所有字段*空白*将记录*空白*。

## <a name="syntax"></a>语法

**AsType**( *RecordReference*, *EntityType* )

- *RecordReference* -必需。 记录引用，通常可以引用在任意多个实体记录的查找字段。
- *EntityType* -必需。 若要测试特定实体。

**IsType**( *RecordReference*, *EntityType* )

- *RecordReference* -必需。 记录引用，通常可以引用在任意多个实体记录的查找字段。
- *EntityType* -必需。 记录应被强制转换到的特定实体。

## <a name="example"></a>示例

[了解记录引用和多态查找](../working-with-references.md)包含大量示例。

1. 创建适用于平板电脑的空白画布应用。

1. 上**视图**选项卡上，选择**数据源**，然后添加**联系人**并**帐户**作为数据源的实体。
    > [!div class="mx-imgBorder"]
    > ![使用两个数据源的空白应用程序： 客户和联系人](media/function-astype-istype/contacts-add-datasources.png)

1. 插入**库**控件替换**垂直空白库**方向。

    > [!div class="mx-imgBorder"]
    > ![插入具有空白垂直布局的库控件](media/function-astype-istype/contacts-customer-gallery.png)

1. 上**属性**屏幕的右侧附近选项卡上，设置库的**项**属性设置为**联系人**。

    > [!div class="mx-imgBorder"]
    > ![在属性窗格中将项目设为联系人](media/function-astype-istype/contacts-customer-datasource.png)

1. 将库的布局设置为**标题和副标题**。

    > [!div class="mx-imgBorder"]
    > ![从属性窗格打开布局选取器](media/function-astype-istype/contacts-customer-layout.png)

    > [!div class="mx-imgBorder"]
    > ![设置为标题和副标题的布局](media/function-astype-istype/contacts-customer-flyout.png)

1. 在中**数据**窗格中，打开**Title1**列表，并选择**全名**。

    > [!div class="mx-imgBorder"]
    > ![设置标题的值](media/function-astype-istype/contacts-customer-title.png)

1. 选择**Subtitle1**标签控件。

    > [!div class="mx-imgBorder"]
    > ![设置副标题值](media/function-astype-istype/contacts-customer-subtitle.png)

1. 设置**文本**的属性**Subtitle1**为以下公式：

    ```powerapps-dot
    If( IsBlank( ThisItem.'Company Name' ), "--",
        IsType( ThisItem.'Company Name', [@Accounts] ),
            "Account: " & AsType( ThisItem.'Company Name', [@Accounts] ).'Account Name',
        "Contact: " & AsType( ThisItem.'Company Name', [@Contacts] ).'Full Name'
    )
    ```

    > [!div class="mx-imgBorder"]
    > ![屏幕现在是完整显示帐户和联系人混杂在库中](media/function-astype-istype/contacts-customer-complete.png)

    在库中的副标题显示了这些值：
    - "-"如果**的公司名称**是*空白*。
    - "帐户:"，然后**帐户名**字段从**帐户**实体如果**公司名称**字段引用的帐户。
    - "请联系:"，然后**全名**字段从**联系人**实体如果**公司名称**字段指联系人。

    您的结果可能不同于本主题中，因为它使用修改显示的结果的其他类型的示例数据。
