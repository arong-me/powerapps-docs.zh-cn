---
title: 从 PowerApps 外添加报表 |Microsoft Docs
description: 从 PowerApps 外添加报表
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
ms.openlocfilehash: 9f775c5607720adcf233524522accb926d955289
ms.sourcegitcommit: c4328e83f5caa58eab83757180b56ced480af220
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71982657"
---
# <a name="add-a-report-from-outside-powerapps"></a>从 PowerApps 外添加报表

如果已在系统外创建了自定义报表，则可以轻松地将其添加到 PowerApps。

有关如何创建自定义报表的信息，请参阅[报表和分析指南](https://docs.microsoft.com/dynamics365/customer-engagement/analytics/get-started-writing-reports)。

1. 从左侧导航窗格中，选择 "报表" 区域。 
2. 在命令栏上，选择 "**新建**"。
  
   **添加在其他应用程序中创建的文件**  
  
   1. 在 "**源**" 部分的 "**报表类型**" 框中，选择 "**现有文件**"。  
   
     > [!div class="mx-imgBorder"]
     > ![添加现有报表](media/add_existing_report.png "添加现有报表")
  
   2. 在 "**文件位置**" 框中，输入要添加的文件的路径和文件名，或选择 "**浏览**" 找到该文件。 
   
      你可以上传多种其他文件类型（如 excel 文件），但要运行它，就像 SQL Server Reporting Services 报表或报表向导创建的报表一样，该文件必须是。RDL 文件。 有关详细信息，请参阅[使用 SQL Server Data Tools 报表写入环境](https://docs.microsoft.com/dynamics365/customer-engagement/analytics/report-writing-environment-using-sql-server-data-tools)。
  
      -或  
  
   **添加网页链接**  
  
   1.  在 "**源**" 部分的 "**报表类型**" 框中，选择 "**链接到网页**"。  
  
   2.  在 "**网页 url** " 框中，输入网页的 URL。  
  
3. 指定报表的属性。
  
   1.  在 "**详细信息**" 部分中，为报表指定有意义的名称和说明。  
  
   2.  "**父报表**" 文本框显示当前报表的父报表（如果存在）。  
  
   3. **类别**。 选择 "**选择或更改此字段的值"** ![省略号]按钮(media/ellipsis-button.png "省略号")按钮按钮，然后指定要包含在此报表中的类别。  
  
   4. **相关记录类型**。 若要使报表出现在特定记录类型的页面上的 "报表" 列表中，请选择 "**选择或更改此字段的值"** ![省略号]按钮(media/ellipsis-button.png "省略号")按钮，然后选择 "记录类型"。  
  
   5. **显示在中**。 若要指定报表的显示位置，请选择 "**选择或更改此字段的值"** ![省略号]按钮(media/ellipsis-button.png "省略号")按钮，然后选择一个或多个选项。  
  
        如果未选择任何值，则报表对最终用户不可见。  
  
4. 选择 "**保存**" 或 "**保存并关闭**"。  




### <a name="see-also"></a>另请参阅
[使用报表](work-with-reports.md) 

[使用报表向导创建报表](create-report-with-wizard.md)

[编辑报表筛选器](edit-report-filter.md)

[排查报表中的数据不显示问题](troubleshoot-reports.md)
