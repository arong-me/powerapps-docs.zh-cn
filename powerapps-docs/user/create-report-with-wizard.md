---
title: 使用报表向导创建报表 | Microsoft Docs
description: 在 Power Apps 中使用报表向导创建报表
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
ms.openlocfilehash: 8c7bde8d3aa5406a7ddcc5ecb2df4c2c7db7051e
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74733256"
---
# <a name="create-a-report-using-the-report-wizard"></a>通过报表向导创建报表


使用报表向导创建包含图表和表的报表，使你可以轻松地分析数据。 

使用报表向导创建的所有报表都是基于 Fetch 的报表。 请注意，使用报表向导生成的所有报表均以横向模式打印。

## <a name="create-a-new-report"></a>创建新报表

1. 从左侧导航窗格中，选择报表区域。  
2. 在命令栏上，选择“新建”  。

    > [!div class="mx-imgBorder"]
    > ![创建新报表](media/newreport.png "创建新报表")
  
3. 系统将显示  “报表: 新建报表”屏幕。 对于“报表类型”，将默认选项保留为“报表向导报表”，然后选择“报表向导”按钮    。 

    > [!div class="mx-imgBorder"]
    > ![报表向导](media/report_wizard.png "“报表向导”屏幕")
  
4. 在下一个屏幕中，保留默认选项，然后选择“下一步”  。
 
    > [!div class="mx-imgBorder"]
    > ![报表向导](media/report_wizard_1.png "“报表向导”屏幕")
   
4. 在“报表属性”屏幕上，输入报表的名称，选择报表中所要包含的记录，然后选择“下一步”   。
 
    > [!div class="mx-imgBorder"]
    > ![“报表属性”屏幕](media/report_wizard_2.png "“报表属性”屏幕")
  
5.  在“选择报表中所要包含的记录”屏幕中，选择筛选器，以确定报表中所要包含的记录  。 例如，如果只想查看最近 60 天内修改的记录的结果，则可以在此屏幕中设置该筛选器。 如果不想对数据进行筛选，则选择“清除”  。

    > [!div class="mx-imgBorder"]
    > ![选择报表中所要包含的记录*](media/report_wizard_3.png "选择报表中所要包含的记录")
  
6. 在“布局字段”屏幕上，选择报表的布局  。 选择“单击此处添加分组”并选择数据的分组方式  。

    > [!div class="mx-imgBorder"]
    > ![布局字段](media/report_wizard_4.png "布局字段")

7. 针对要在报表中进行分组的数据，选择“记录类型”和“列”   。 选择完成后，选择“确定”  。

    > [!div class="mx-imgBorder"]
    > ![“添加分组”屏幕](media/report_wizard_5.png "“添加分组”屏幕")
  
8. 选择“单击此处添加列”，添加与在上一步中选择的记录类型相关的数据列  。  

    > [!div class="mx-imgBorder"]
    > ![“添加分组”屏幕](media/report_wizard_6.png "“添加分组”屏幕")

9. 在“添加列”屏幕上，选择该列所要显示的数据，然后选择“确定”   。 

    > [!div class="mx-imgBorder"]
    > ![“添加列”屏幕](media/report_wizard_7.png "“添加列”屏幕")
  
10. 针对要添加的任何其他列，重复上一步骤。 完成后，在“布局字段”屏幕上，选择“下一步”   。
 
    > [!div class="mx-imgBorder"]
    > ![“添加更多列”屏幕](media/report_wizard_8.png "“添加更多列”屏幕")
  
11. 在“设置报表格式”屏幕上，选择报表的格式设置，然后选择“下一步”   。
 
    > [!div class="mx-imgBorder"]
    > ![设置报表格式](media/report_wizard_9.png "“设置报表格式”屏幕")

12. 查看报表的摘要，选择“下一步”，然后选择“完成”   。 现在可以在系统的报表列表中查看此报表。

    > [!div class="mx-imgBorder"]
    > ![查看报表](media/report_wizard_10.png "查看报表")

### <a name="see-also"></a>另请参阅
[处理报表](work-with-reports.md) 

[添加现有报表](add-existing-report.md)

[编辑报表筛选器](edit-report-filter.md)

[排查报表中不显示数据的问题](troubleshoot-reports.md)


