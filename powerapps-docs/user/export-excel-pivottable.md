---
title: 导出到模型驱动的 PowerApp 中的 Excel 数据透视表 |MicrosoftDocs
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
ms.openlocfilehash: 90cf377f10a99dbcece1e5f556cb50e678099744
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544973"
---
# <a name="export-to-an-excel-pivottable"></a>导出到 Excel 数据透视表


你可以将应用程序数据导出到 Office Excel 数据透视表, 以查看数据的模式和趋势。 Excel 数据透视表是汇总、分析、浏览和展示应用程序数据的一种很好的方法。 一次最多可以导出100000条记录。  
  

## <a name="export-data-to-an-excel-pivottable"></a>将数据导出到 Excel 数据透视表  
用于将数据导出到 Excel 数据透视表的选项在所有记录类型中都不可用。 如果看不到该选项, 则该选项不可用于该记录。  
  
1. 在应用中打开记录列表, 选择 "**导出到 Excel**" 右侧的箭头, 然后选择 "**动态数据透视表**"。  
  
2. 在 "**为透视 Excel 选择列**" 对话框中, 选择 "列设置", 然后选择 "**导出**"。  
  
   默认情况下,**数据透视表字段列表**仅包含在 "**为透视 Excel 选择列**" 列表中显示的字段。  
  
3. 选择 "**保存**", 然后保存 .xlsx 文件。 记下保存该文件的位置。  
  
   > [!NOTE]
   > 如果以后要编辑数据文件, 建议你在打开文件之前保存该文件。 否则, 你可能会收到以下错误消息:**由于没有足够的可用内存或磁盘空间, Excel 无法打开或保存更多文档。**  
   > 
   > 若要解决此问题:  
   > 
   > 1. 打开 Excel 并中转到**文件** > **选项** > **信任中心**。  
   > 2. 选择 "**信任中心设置**", 然后选择 "**受保护的视图**"。  
   > 3. 在 "**受保护的视图**" 下, 清除所有三个项目的复选框。  
   > 4. 选择 **"确定** >  **" "确定"** 。  
   > 
   > 我们仍强烈建议您保存并打开数据文件, 而不是禁用受保护的视图, 这可能会使您的计算机面临风险。  
  
4. 打开 Excel, 然后打开您在上一步中保存的 .xlsx 文件。  
  
5. 如果你看到 "安全警告**外部数据连接已禁用**", 请选择 "**启用内容**"。  
  
6. 若要刷新文件中的数据, 请在 "**数据**" 选项卡上选择 "**从 PowerApps 刷新**"。  
  
7. 将字段从 "数据透视表字段列表" 拖至数据透视表。 有关详细信息, 请参阅 Excel 帮助。  
  
## <a name="tips"></a>提示  
  
- 在 PowerApps 中, 货币值以数字形式导出到 Excel 中。 完成导出后, 请参阅 Excel 帮助主题 "将数字显示为货币", 将数据的格式设置为货币。
  
- 您在应用程序中看到的日期和时间值仅在您将文件导出到 Excel 时显示为日期, 但该单元格实际上同时显示日期和时间。  
  
- 如果要进行更改并将数据文件导入回应用程序, 请记住, 受保护的、计算的和复合字段 (如全名) 是只读的, 无法导入到应用中。 你将能够在 Excel 中编辑这些字段, 但当你将数据导入到应用时, 这些字段将不会更新。 如果要更新这些字段 (如联系人的姓名), 建议使用该视图导出数据, 在 Excel 中更新数据, 并将数据导入回应用程序进行更改。  
  
 
