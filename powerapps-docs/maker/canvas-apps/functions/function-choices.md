---
title: Choices 函数 | Microsoft 文档
description: PowerApps 中 Choices 函数的参考信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/15/2018
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ed555f5de4abc1e29b7d2a637413c440bd882f13
ms.sourcegitcommit: 6b116a4079eb56ebd598d317a12df8856ff3e52a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/30/2019
ms.locfileid: "58671946"
---
# <a name="choices-function-in-powerapps"></a>PowerApps 中的 Choices 函数
返回查找列可能值的表。

## <a name="description"></a>描述
Choices 函数返回查找列可能值的表。  

使用 Choices 函数提供选项列表让用户选择。 此函数通常与[**组合框**](../controls/control-combo-box.md)控件一起用在编辑窗体中。

对于查找，Choices 返回的表与和查找相关联的外部表匹配。 使用 Choices，就无需将外部表添加为另一个数据源。 Choices 会返回外部表的所有列。

由于 Choices 会返回表，因此可使用 [**Filter**](function-filter-lookup.md)[**Sort**](function-sort.md)、[**AddColumns**](function-table-shaping.md) 以及其他所有表操作函数对表进行筛选、排序和定型。 

目前，不能[委派](../delegation-overview.md) Choices。 如果此限制在你的应用中造成问题，请将外部实体添加为数据源，并直接使用它。 

Choices 不要求列名称为字符串且括在双引号中，这一点与 [**ShowColumns**](function-table-shaping.md)、[**Search**](function-filter-lookup.md) 和其他表函数不同。 就像直接引用列一样提供公式。

列引用必须直接连接到数据源。 例如，如果数据源是 Accounts 而查找是 SLA，则列引用是 Accounts.SLA。 引用不能通过函数、变量或控件传递。 深化此示例，如果 Accounts 馈送给 Gallery 控件，则使用公式 Gallery.Selected.SLA 引用所选帐户的 SLA。 但是，此引用通过了一个控件，因此它不能传递给 Columns 函数，即仍必须使用 Accounts.SLA。

在此期间，可以只使用 SharePoint 和 Common Data Service 中使用查找列。

## <a name="syntax"></a>语法
**Choices**( *column-reference* )

* *column-reference* - 必需。  数据源的查找列。 请勿将列名括在双引号中。 引用必须直接指向数据源的列，而不能通过函数或控件传递。

## <a name="examples"></a>示例

#### <a name="choices-for-a-lookup"></a>查找的选项

1. [创建数据库](../../../administrator/create-database.md)通用数据服务，然后选择**包括示例应用和数据**框。

    将会创建多个实体，例如 Accounts。

    **注意**：在 web.powerapps.com 上单数和复数在 PowerApps Studio 中，实体名称。

    ![来自 Commmon Data Service for Apps 中 Account 实体的字段的部分列表，突出显示了“Primary Contact”是查找字段](media/function-choices/entity-account.png)

    Accounts 实体具有 Primary Contact 列，这是对 Contacts 实体的查找。  

    ![来自 Commmon Data Service 中 Contact 实体的字段的部分列表](media/function-choices/entity-contact.png)

    对于每个帐户，不是指定了联系人作为主要联系人，就是主要联系人为*空白*。

1. 从 **Accounts** 实体[生成应用](../data-platform-create-app.md)。

1. 在左边缘附近的屏幕和控件列表中，向下滚动到显示出 EditScreen1，并选择其下方的 EditForm1。

    ![在左侧导航栏中，选择 EditScreen1 上的 EditForm1](media/function-choices/select-editform.png)

1. 上**属性**的右窗格中，选择的选项卡**编辑字段**。

    ![打开数据窗格](media/function-choices/open-data-pane.png)

1. 在中**字段**窗格中，选择**添加字段**。

1. 搜索**主要联系人**字段中，选中其复选框，然后再选择**添加**。

    ![选择“Accounts”以打开“数据”窗格。](media/function-choices/field-list.png)

    **主要联系人**字段显示在窗体的底部。 如果该字段将显示错误，请选择**数据源**上**视图**选项卡上，选择省略号 （...）**帐户**数据源，然后选择**刷新**.

1. （可选）将“Primary Contact”字段从字段列表底部拖动到顶部。

1. 在“Primary Contact”的卡片中，选择“组合框”控件。

    **项**该控件的属性设置为一个公式，用于标识列按其显示名称，如下所示的第一个示例中或其逻辑名称，如第二个示例所示：

   - **Choices( Accounts.'Primary Contact' )**
   - **Choices( Accounts.primarycontactid )**

     ![包含窗体控件的画布屏幕。 选择框控件中的主要联系人卡后，在组合框和项属性的公式的选择 （帐户。 主要联系人） 显示](media/function-choices/accounts-primary-contact.png)

1. 在“开始”选项卡上，选择“新建屏幕”，然后选择“Blank”。

1. 在“插入”选项卡上，选择“数据表”。

1. 设置**项**的属性**数据表**控制为以下公式：

     **Choices( Accounts.'Primary Contact' )**

1. 中间**数据表**控件中，选择的链接，启动**选择的字段...**，然后选择你想要显示的字段对应的复选框 (例如， **firstname**并**lastname**)。

     ![包含数据表控件的画布屏幕。 Items 属性设置为公式 Choices( Accounts.'Primary Contact' )，表显示 Contacts 实体中第一组记录的 firstname 和 lastname 列](media/function-choices/full-accounts-pc.png)