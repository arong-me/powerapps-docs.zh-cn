---
title: Choices 函数 | Microsoft 文档
description: PowerApps 中 Choices 函数的参考信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/15/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c9b84a8ce89863d94b9f3e4ac390c88e194a2894
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73540195"
---
# <a name="choices-function-in-powerapps"></a>PowerApps 中的 Choices 函数
返回查找列可能值的表。

## <a name="description"></a>描述
Choices 函数返回查找列可能值的表。  

使用 Choices 函数提供选项列表让用户选择。 此函数通常与[**组合框**](../controls/control-combo-box.md)控件一起用在编辑窗体中。

对于查找，Choices 返回的表与和查找相关联的外部表匹配。 使用 Choices，就无需将外部表添加为另一个数据源。 Choices会返回外部表的所有列。

由于 Choices 会返回表，因此可使用 [**Filter**](function-filter-lookup.md)[**Sort**](function-sort.md)、[**AddColumns**](function-table-shaping.md) 以及其他所有表操作函数对表进行筛选、排序和定型。 

目前，不能[委派](../delegation-overview.md) Choices。 如果此限制在你的应用中造成问题，请将外部实体添加为数据源，并直接使用它。 

Choices 不要求列名称为字符串且括在双引号中，这一点与 [**ShowColumns**](function-table-shaping.md)、[**Search**](function-filter-lookup.md) 和其他表函数不同。 就像直接引用列一样提供公式。

列引用必须直接连接到数据源。 例如，如果数据源是 Accounts而查找是 SLA，则列引用是 Accounts.SLA。 引用不能通过函数、变量或控件传递。 深化此示例，如果 Accounts 馈送给 Gallery 控件，则使用公式 Gallery.Selected.SLA 引用所选帐户的 SLA。 但是，此引用通过了一个控件，因此它不能传递给 Columns 函数，即仍必须使用 Accounts.SLA。

此时，只能将查找列与 SharePoint 和 Common Data Service 一起使用。

## <a name="syntax"></a>语法
**Choices**( *column-reference* )

* *column-reference* - 必需。  数据源的查找列。 请勿将列名括在双引号中。 引用必须直接指向数据源的列，而不能通过函数或控件传递。

## <a name="examples"></a>示例

#### <a name="choices-for-a-lookup"></a>查找的选项

1. 在 Common Data Service 中[创建一个数据库](../../../administrator/create-database.md)，然后选择 "**包括示例应用和数据**" 框。

    将会创建多个实体，例如 Accounts。

    **注意**：实体名称在 make.powerapps.com 上是单数的，PowerApps Studio 中的复数。

    ![Common Data Service for Apps 中的 Account 实体的部分字段列表，突出显示 "主要联系人" 是查找字段](media/function-choices/entity-account.png)

    Accounts 实体具有 Primary Contact 列，这是对 Contacts 实体的查找。  

    !["联系人" 实体中的字段的部分列表 Common Data Service](media/function-choices/entity-contact.png)

    对于每个帐户，不是指定了联系人作为主要联系人，就是主要联系人为*空白*。

1. 从 **Accounts** 实体[生成应用](../data-platform-create-app.md)。

1. 在左边缘附近的屏幕和控件列表中，向下滚动到显示出 EditScreen1，并选择其下方的 EditForm1。

    ![在左侧导航栏中，选择 EditScreen1 上的 EditForm1](media/function-choices/select-editform.png)

1. 在右窗格的 "**属性**" 选项卡上，选择 "**编辑字段**"。

    ![打开 "数据" 窗格](media/function-choices/open-data-pane.png)

1. 在 "**字段**" 窗格中，选择 "**添加字段**"。

1. 搜索 "**主要联系人**" 字段，选中其复选框，然后选择 "**添加**"。

    ![选择“Accounts”以打开“数据”窗格。](media/function-choices/field-list.png)

    **主要联系人**字段显示在窗体的底部。 如果该字段显示错误，请在 "**视图**" 选项卡上选择 "**数据源**"，选择 "**帐户**" 数据源的省略号（...），然后选择 "**刷新**"。

1. （可选）将“Primary Contact”字段从字段列表底部拖动到顶部。

1. 在“Primary Contact”的卡片中，选择“组合框”控件。

    该控件的**Items**属性设置为一个公式，该公式按其显示名称（如第一个示例所示）或其逻辑名称标识列，如第二个示例所示：

   - **Choices( Accounts.'Primary Contact' )**
   - **Choices( Accounts.primarycontactid )**

     ![包含窗体控件的画布屏幕。 主联系人卡片内的组合框控件处于选中状态，并且具有公式选择（"主要联系人"）的 "Items" 属性随即出现](media/function-choices/accounts-primary-contact.png)

1. 在“开始”选项卡上，选择“新建屏幕”，然后选择“Blank”。

1. 在“插入”选项卡上，选择“数据表”。

1. 将 **"数据表" 控件的** **Items**属性设置为以下公式：

     **Choices( Accounts.'Primary Contact' )**

1. 在 "**数据表**" 控件的中间，选择开始**选择 "字段 ...** " 的链接，然后选中要显示的一个或多个字段的复选框（例如， **firstname**和**lastname**）。

     ![包含数据表控件的画布屏幕。 Items 属性设置为公式 Choices( Accounts.'Primary Contact' )，表显示 Contacts 实体中第一组记录的 firstname 和 lastname 列](media/function-choices/full-accounts-pc.png)