---
title: 在模型驱动 Power Apps 中导出到 Excel 动态工作表 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 11/16/2018
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 99aa4fb38311d51237abba2c56d69e9845ea280f
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733244"
---
# <a name="export-to-an-excel-dynamic-worksheet"></a>导出到 Excel 动态工作表

将应用数据导出到 Office Excel 工作表，以便用户可以获得最新信息。 试想，如果你公司的 CEO 无需在应用中导航，只需在其桌面上打开 Excel 链接，即可获取所需的关键信息，该有多好。 一次最多可以导出 100,000 条记录。    
  
## <a name="export-data-to-an-excel-dynamic-worksheet"></a>将数据导出到 Excel 动态工作表  

只能将某些记录类型的数据导出到 Excel 中的动态工作表。 如果未显示该选项，则该选项不可用于该记录。  
  
1. 在应用中打开记录列表，然后选择“导出到 Excel”右侧的箭头  。 
  
2. 选择“动态工作表”  。  
  
3. 在“选择用于动态 Excel 的列”对话框中，选择列设置，然后选择“导出”   。  
  
4. 选择“保存”并保存 .xlsx 文件  。 记下保存该文件的位置。  
  
   > [!NOTE]
   > 如果以后要编辑数据文件，建议在打开文件之前保存该文件。 否则，可能会收到以下错误消息：由于可用内存或磁盘空间不足，Excel 无法打开或保存更多文档。   
   > 
   > 若要解决这一问题，请执行以下操作：  
   > 
   >    1. 打开 Excel 并转到“文件” > “选项” > “信任中心设置中心设置” > “受保护的视图”      。  
   >    2. 在“受保护的视图”中，取消选中所有三项  。  
   >    3. 选择“确定”   > “确定”  。  
   >     
   >    我们仍强烈建议保存数据文件后将其打开，而不是禁用受保护的视图，这可能会使计算机面临风险。  
  
5. 打开 Excel，然后打开在上一步中保存的 .xlsx 文件。  
  
6. 如果出现安全警告“已禁用外部数据连接”，请选择“启用内容”   。  
  
7. 若要刷新文件中的数据，请在“数据”选项卡上，选择“从 Power Apps 刷新”   。  
  
   > [!NOTE]
   > 如果电话号码以“+”或“-”开头（例如 +1-123-456-7890），刷新动态工作表时，电话号码字段将无法正确显示号码   。   
   >
   > 若要避免此问题，请使用空格或圆括号“()”，例如：+1 123-456-7890 或 +1 (123)-456-7890  。  
  
## <a name="tips"></a>提示  
  
- 如果收件人与你位于同一域中，则可以通过电子邮件发送动态 Excel 文件或将其存储为共享文件。 收件人打开动态文件时，他们可以在应用中看到自己有权查看的数据，也就是说，他们看到的数据可能与你看到的不同。  
  
- 某些系统视图，例如“帐户:最近 3 个月内没有任何市场活动”，只能导出到静态 Excel 工作表中。  
  
- 在 Power Apps 中，货币值作为数字导出到 Excel。 若要在完成导出后将数据格式设置为货币，请参阅标题为“将数字显示为货币”的 Excel 帮助主题。

- 将文件导出到 Excel 后，应用中显示的日期和时间值将仅显示“日期”，但是单元格实际上同时显示了日期和时间。  
  
- 如果要进行更改并将数据文件导入回应用，请记住，受保护的字段、计算字段和复合字段（例如全名）是只读的，无法将其导入到应用中。 可以在 Excel 中编辑这些字段，但是将数据导入回应用时不会更新这些字段。 如果想更新这些字段（例如联系人的姓名），建议使用相应视图导出数据，在 Excel 中对数据进行更新，然后将其重新导入应用以进行更改。  
 

