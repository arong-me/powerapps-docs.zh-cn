---
title: 在模型驱动应用中将数据导出到 Excel Online | MicrosoftDocs
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
- D365CE
ms.openlocfilehash: 6cb8fe650db464f41c63af87c3fcb34bb2203cf2
ms.sourcegitcommit: 483c777a1537ccab6a2a2da6a5d1fe4470dd0e7e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544768"
---
# <a name="export-your-data-to-excel-online"></a>将数据导出到 Excel Online 

通过将数据从应用导出到 Excel Online，可以快速对应用中的数据进行临时分析。
  
在 Excel Online 中更改数据时，可以将更新后的信息保存在应用中。 请记住要保留 Excel 单元格的现有格式，以防在导入过程中出现问题。 添加到电子表格中的任何信息（例如图形、图表或颜色）都不会保存。  
  
## <a name="prerequisites"></a>先决条件  
  
- 此功能要求你具有 Office 365 订阅或 SharePoint Online 或 Exchange Online 等联机服务的订阅。
  
- 需要一个 Microsoft 帐户。    
  
## <a name="open-app-data-in-excel-online"></a>在 Excel Online 中打开应用数据  

并非所有记录类型都提供“在 Excel Online 中打开数据”选项。 如果未显示该选项，则该选项不可用于该记录。  
  
> [!NOTE]
> 如果最近两分钟内在 Excel Online 中打开了相同的视图，则应用中更新后的数据将不会立即反映在 Excel Online 中。 超过这一时间段，任何更新后的数据都将显示在 Excel Online 中。
  
要在应用中打开记录列表，请在命令栏上选择“导出到 Excel”菜单，然后选择“在 Excel Online 中打开”。 

> [!div class="mx-imgBorder"] 
> ![导出到 Excel Online] (media/exportexcelonline.png "Export to Excel Online")  

  
## <a name="save-your-data-and-import-it-back-to-the-app"></a>保存数据并将其导入回应用  
  
1. 完成任何更改后，选择“保存”。  
  
   > [!NOTE]
   > - 暂时存储使用 Excel Online 进行临时分析的数据。 任何附加内容（例如图表、计算和列）都不会从 Excel Online 中的临时分析保存回应用。  
   > 
   > - 如果进行大量更改，文件导入可能会失败。 如需对数据进行大量更改并将其导入回应用，建议改为导出 Excel 中的工作表。  
   > 
   > - 根据设计，你不能在 Excel Online 中执行 **“文件”** > **“另存为”** 操作。 如果这样做，你将会收到 **“无法保存工作簿”** 错误消息。   
2. 在“提交导入的数据”对话框中，选择“关闭”。  
  

  

 
