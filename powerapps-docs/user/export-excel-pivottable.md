---
title: 导出到模型驱动 PowerApp 中的 Excel 数据透视表 | MicrosoftDocs
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
ms.openlocfilehash: b14e24e7048e4f91de13f582914ffb621d3c7899
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74725794"
---
# <a name="export-to-an-excel-pivottable"></a>导出到 Excel 数据透视表


可将应用数据导出到 Office Excel 数据透视表，以查看数据的模式和趋势。 Excel 数据透视表是汇总、分析、浏览和展示应用数据的一种好方法。 一次最多可以导出 100,000 条记录。  
  

## <a name="export-data-to-an-excel-pivottable"></a>将数据导出到 Excel 数据透视表  
将数据导出到 Excel 数据透视表的选项并非适用于所有记录类型。 如果未显示该选项，则该选项不可用于该记录。  
  
1. 在应用中打开记录列表，选择“导出到 Excel”右侧的箭头，然后选择“动态数据透视表”   。  
  
2. 在“选择数据透视 Excel 的列”对话框中，选择列设置，然后选择“导出”   。  
  
   默认情况下，“数据透视表字段列表”仅包括“选择数据透视 Excel 的列”列表中显示的字段   。  
  
3. 选择“保存”并保存 .xlsx 文件  。 记下保存该文件的位置。  
  
   > [!NOTE]
   > 如果以后要编辑数据文件，建议在打开文件之前保存该文件。 否则，可能会收到以下错误消息：由于可用内存或磁盘空间不足，Excel 无法打开或保存更多文档  。  
   > 
   > 若要解决这一问题，请执行以下操作：  
   > 
   > 1. 打开 Excel 并转到“文件” > “选项” > “信任中心”    。  
   > 2. 选择“信任中心设置”，然后选择“受保护的视图”   。  
   > 3. 在“受保护的视图”下，清除所有三个项的复选框  。  
   > 4. 选择“确定”   > “确定”  。  
   > 
   > 我们仍强烈建议保存数据文件后将其打开，而不是禁用受保护的视图，这可能会使计算机面临风险。  
  
4. 打开 Excel，然后打开在上一步中保存的 .xlsx 文件。  
  
5. 如果出现安全警告“已禁用外部数据连接”，请选择“启用内容”   。  
  
6. 若要刷新文件中的数据，请在“数据”选项卡上，选择“从 Power Apps 刷新”   。  
  
7. 将字段从“数据透视表字段列表”拖动到数据透视表。 有关详细信息，请参阅 Excel 帮助。  
  
## <a name="tips"></a>提示  
  
- 在 Power Apps 中，货币值作为数字导出到 Excel。 在完成导出后，要将数据格式设置为货币，请参阅 Excel 帮助主题“将数字显示为货币”。
  
- 将文件导出到 Excel 后，应用中显示的日期和时间值将仅显示“日期”，但是单元格实际上同时显示了日期和时间。  
  
- 如果要进行更改并将数据文件导入回应用，请记住，受保护的字段、计算字段和复合字段（例如全名）是只读的，无法将其导入到应用中。 你可以在 Excel 中编辑这些字段，但是将数据导入回应用时，这些字段将不会更新。 如果想更新这些字段（例如联系人的姓名），建议使用相应视图导出数据，在 Excel 中对数据进行更新，然后将其重新导入应用以进行更改。  
  
 
