---
title: 编辑报表的默认筛选器 | Microsoft Docs
description: 编辑报表的默认筛选器
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 06/27/2019
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 53e4f2fc61bb72b4c3fc6fed188b513641c2034d
ms.sourcegitcommit: e9671e018c1ee4b640528915350a367758991b6a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67420205"
---
# <a name="edit-the-default-filter-of-a-report"></a>编辑报表的默认筛选器

如果报表为 SQL Server Reporting Services 报表，启用了预筛选，并且具有默认筛选器，则可以更改默认筛选器以显示所希望在报表中显示的数据。 每当任何用户运行报表时，都会使用此筛选器。

1. 从左侧导航窗格中，选择报表区域
2. 选择报表，然后在 commbar 栏上，选择“编辑默认筛选器”  。

     > [!div class="mx-imgBorder"]
     > ![编辑默认报表筛选器](media/edit_filter.png "Edit default report filter")
  
3. 更改筛选条件。  
  
   条件按可在筛选器中使用的记录类型进行分组，如“帐户”或“联系人”   。  
  
   ### <a name="to-edit-an-existing-row"></a>要编辑现有行
   1. 选择“查询关系运算符”并选择一个运算符，或选择带下划线的值并输入一个新值。  
  
   2. 选择“查询关系运算符”，并选择一个运算符。  
  
   要添加条件行，请执行以下操作：  

   1.  选择“选择”，并指定要筛选的字段  。  

   2.  选择“查询关系运算符”，并选择一个运算符。  

   3.  选择“输入值”，并输入要筛选的值  。 对于某些值，可以选择“选择或更改此字段的值”按钮![](media/ellipsis-button.png "Ellipsis button")打开“选择值”对话框并选择所需值   。  

   ### <a name="to-group-criteria"></a>分组条件
   必须为同一记录类型选择两行或多行。 但是，不能对具有不同记录类型（如“帐户”和“联系人”记录类型）的字段值的行进行分组   。  

   1.  对于每个要进行分组的行，在详细模式下，选择该行的“选项菜单”按钮，然后选择“选择行”   。  

   2.  在“筛选器”工具栏上，选择“组和”或“组或”   。  

   3.  要从组中删除行，请选择该行的“选项菜单”按钮，然后选择“删除”   。  

   4.  要选择组，请选择该组的“选项菜单”按钮，然后选择“选择组”   。  

   5.  要将条件子句添加到组中，请选择该组的“选项菜单”按钮，选择“添加子句”，然后选择字段、查询关系运算符和值   。  

   6.  要取消选择之前选择的组，请选择该组的“选项菜单”按钮，然后选择“取消选择组”   。  

   7.  要对组取消分组，请选择该组的“选项菜单”按钮，然后选择“取消分组”   。  

   8.  要将“组和”组更改为“组或”组，或将“组或”组更改为“组和”组，请选择该组的“选项菜单”按钮，然后选择“更改为或”或“更改为和”        。  

   > [!TIP]
   > - 要清除所有条件并重新开始，请在“筛选器”工具栏上，选择“清除”，然后选择“确认”   。  
   > - 要删除行，请选择该行的“选项菜单”按钮，然后选择“删除”   。  
  
4. 完成后，选择“保存默认筛选器”  。



### <a name="see-also"></a>另请参阅
[处理报表](work-with-reports.md) 

[通过报表向导创建报表](create-report-with-wizard.md)

[添加现有报表](add-existing-report.md)

[排查报表中不显示数据的问题](troubleshoot-reports.md)

