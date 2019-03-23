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
ms.openlocfilehash: 77268aa63ed49d10f825850909d31ec4feace063
ms.sourcegitcommit: 5b2b70c3fc7bcba5647d505a79276bbaad31c610
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2019
ms.locfileid: "58357589"
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

2. 从 **Accounts** 实体[生成应用](../data-platform-create-app.md)。

3. 在左边缘附近的屏幕和控件列表中，向下滚动到显示出 EditScreen1，并选择其下方的 EditForm1。

    ![在左侧导航栏中，选择 EditScreen1 上的 EditForm1](media/function-choices/select-editform.png)

4. 在右窗格的“属性”选项卡上，选择“Accounts”。

    ![选择“Accounts”以打开“数据”窗格。](media/function-choices/open-data-pane.png)

5. 在“数据”窗格中，向下滚动到字段列表。

    ![选择“Accounts”以打开“数据”窗格。](media/function-choices/field-list.png)

6. 找到“Primary Contact”复选框，如果已取消选中，则选中它。

7. （可选）将“Primary Contact”字段从字段列表底部拖动到顶部。

8. 在“Primary Contact”的卡片中，选择“组合框”控件。

    该控件的 Items 属性设置为两个公式之一，具体取决于高级设置中“使用列显示名称”复选框的状态。

   - 如果选中了该复选框，则该属性设置为以下公式：<br>**Choices( Accounts.'Primary Contact' )**
   - 如果取消选中了该复选框，则该属性设置为以下公式：<br>**Choices( Accounts.primarycontactid )**

     ![包含窗体控件的画布屏幕。 选择了 Primary Contact 卡片中的组合框控件，显示了包含公式 Choices( Accounts.'Primary Contact' ) 的 Items 属性](media/function-choices/accounts-primary-contact.png)

9. 在“开始”选项卡上，选择“新建屏幕”，然后选择“Blank”。

10. 在“插入”选项卡上，选择“数据表”。

11. 将数据表控件的 Items 属性设置为以下公式之一：

     - 如果选中了高级设置中的“使用列显示名称”复选框，请使用以下公式：<br>**Choices( Accounts.'Primary Contact' )**
     - 否则，请使用以下公式：<br>**Choices( Accounts.primarycontactid )**

12. 打开“数据”窗格，然后选择 firstname、lastname 或要显示的任何其他字段的复选框。

     ![包含数据表控件的画布屏幕。 Items 属性设置为公式 Choices( Accounts.'Primary Contact' )，表显示 Contacts 实体中第一组记录的 firstname 和 lastname 列](media/function-choices/full-accounts-pc.png)
