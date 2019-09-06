---
title: 导出到模型驱动应用中的 Excel 静态工作表 |MicrosoftDocs
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
ms.openlocfilehash: 82d14f70bbdcd9faddc467636db255f0b512830e
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544812"
---
# <a name="export-to-an-excel-static-worksheet"></a>导出到 Excel 静态工作表

如果要向无权访问应用的个人提供有关应用中的数据的信息, 或者你的数据不经常更改, 请考虑将应用数据导出到 Office Excel 静态工作表。

一次最多可以导出100000条记录。 默认情况下, 模型驱动应用最多列出每页50条记录。 选择列表底部的**页**箭头可查看任何其他页。  
  
## <a name="export-data-to-an-excel-static-worksheet"></a>将数据导出到 Excel 静态工作表  
您可以选择将数据导出到所有记录类型中的 Excel 静态工作表。 但是, 在某些情况下, 该格式可能是旧的, 或者数据可能未按您在应用程序中看到的内容进行筛选。  
  
1. 在应用中打开记录列表, 选择 "**导出到 Excel**" 右侧的箭头, 然后选择 "**静态工作表 (仅页面)** "。  
  
2. 默认情况下, 导出的工作表将包含列表中显示的字段, 并使用相同的字段顺序、排序和字段宽度。 若要对高级查找视图中的列进行更改, 请选择 "**编辑列**"。 
  
3. 选择 "**保存**", 然后保存 .xlsx 文件。 记下保存该文件的位置。  
  
   > [!NOTE]
   > 如果以后要编辑数据文件, 建议你在打开文件之前保存该文件。 否则, 你可能会收到以下错误消息:**由于没有足够的可用内存或磁盘空间, Excel 无法打开或保存更多文档。**  
   > 
   > 若要解决此问题, 请执行以下操作:  
   > 
   > 1. 打开 Excel 并中转到**文件** > **选项** > "**信任中心** > **设置** > " "**受保护的视图**"。  
   > 2.  在 "**受保护的视图**" 中, 清除所有三项。  
   > 3.  选择 **"确定** >  **" "确定"** 。  
   > 
   > 我们仍强烈建议您保存并打开数据文件, 而不是禁用受保护的视图, 这可能会使您的计算机面临风险。  


4. 打开 Excel, 然后打开您在上一步中保存的 .xlsx 文件。  
  
   默认情况下, 导出的工作表将包含列表中显示的字段, 并使用相同的字段顺序、排序和字段宽度。  
  
## <a name="tips"></a>提示  
  
- 可以通过电子邮件将静态导出工作表发送给任何人, 或将其存储在共享文件中。 打开该文件的任何人都可以看到该文件中的所有数据。
  
- 不能更改系统视图的列, 例如**所有活动帐户**。 您必须自定义视图 (需要系统管理员或系统定制员安全角色), 或使用高级查找基于当前视图创建自己的视图。  
    
- 在模型驱动应用中, 货币值以数字形式导出到 Excel 中。 之后完成导出后, 请参阅 Excel 帮助主题 "将数字显示为货币", 将数据的格式设置为货币。
  
- 您在应用程序中看到的日期和时间值仅在您将文件导出到 Excel 时显示为日期, 但该单元格实际上同时显示日期和时间。  
  
- 如果要进行更改并将数据文件导入回应用程序, 请记住, 受保护的、计算的和复合字段 (如全名) 是只读的, 无法导入到应用中。 您将能够在 Excel 中编辑这些字段, 但当您将数据导入到应用程序中时, 这些字段将不会更新。 如果要更新这些字段 (如联系人的姓名), 则建议使用该视图导出数据, 并在 Excel 中更新数据, 并将其导入回应用程序进行更改。  
  
