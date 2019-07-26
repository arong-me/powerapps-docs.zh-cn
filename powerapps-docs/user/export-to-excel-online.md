---
title: 在模型驱动的应用中将数据导出到 Excel Online |MicrosoftDocs
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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2019
ms.locfileid: "61544768"
---
# <a name="export-your-data-to-excel-online"></a>将数据导出到 Excel Online 

可以通过将数据从应用导出到 Excel Online 来快速对应用中的数据进行即席分析。
  
当你在 Excel Online 中更改数据时, 可以在应用程序中保存更新后的信息。 请记住保留 Excel 单元格的现有格式, 以防导入过程中出现问题。 任何添加到电子表格中的信息 (如图形、图表或颜色) 都不会保存。  
  
## <a name="prerequisites"></a>先决条件  
  
- 此功能要求你具有 Office 365 订阅或 SharePoint Online 或 Exchange Online 等联机服务的订阅。
  
- 需要 Microsoft 帐户。    
  
## <a name="open-app-data-in-excel-online"></a>在 Excel Online 中打开应用数据  

在 Excel Online 中打开数据的选项在所有记录类型中都不可用。 如果看不到该选项, 则该选项不可用于该记录。  
  
> [!NOTE]
> 如果在 Excel Online 中的过去两分钟内打开了同一个视图, 则在应用中更新后的数据将不会立即反映在 Excel Online 中。 在该时间段后, 所有更新的数据都应显示在 Excel Online 中。
  
若要在应用中打开记录列表, 请在命令栏上选择 "**导出到 excel** " 菜单, 然后选择 "**在 Excel Online 中打开**"。 

> [!div class="mx-imgBorder"] 
> ![导出到 Excel Online](media/exportexcelonline.png "导出到 Excel Online")  

  
## <a name="save-your-data-and-import-it-back-to-the-app"></a>保存数据并将其导入回应用  
  
1. 进行任何更改后, 请选择 "**保存**"。  
  
   > [!NOTE]
   > - 临时存储带 Excel Online 的*实时*分析数据。 任何添加内容 (例如图表、计算和列) 都不会从 Excel Online 中的即席分析保存回应用程序。  
   > 
   > - 如果进行了大量更改, 则文件导入可能会失败。 如果需要对数据进行大量更改, 然后将数据导入回应用程序, 建议改为导出 Excel 中的工作表。  
   > 
   > - 按照设计, 您不能像在 Excel Online 中那样**保存** **文件** > 。 如果执行此操作, 将收到 "**无法保存工作簿**" 错误消息。   
2. 在 "**要导入的数据**" 对话框中, 选择 "**关闭**"。  
  

  

 
