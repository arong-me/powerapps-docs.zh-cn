---
title: 导入解决方案 | MicrosoftDocs
description: 了解如何在 Power Apps 中导入解决方案
ms.custom: ''
ms.date: 01/30/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 56363ea3-ea76-4311-9b7a-b71675e446fb
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 504e66801c122810da12810d9b19e5069136f7d6
ms.sourcegitcommit: cb533c30252240dc298594e74e3189d7290a4bd7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/04/2020
ms.locfileid: "3017609"
---
# <a name="import-solutions"></a>导入解决方案 

 可以使用以下步骤手动导入解决方案。 只能导入从受信任源获取的解决方案。 自定义项可能包含可向外部源发送数据的代码。   
  
1.  登录 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后从左侧导航中选择**解决方案**。  
  
2.  在命令栏上选择**导入**。  

    > [!div class="mx-imgBorder"]  
    > ![导入解决方案](media/solution-import.png "导入解决方案") 
  
3.  在**选择解决方案包**页中，选择**浏览**找到包含要导入的解决方案的压缩（.zip 或 .cab）文件。 
  
4.  选择**下一步**。  
  
5.  将显示有关解决方案的信息。 选择**导入**。  
  
6. 在完成导入期间，可能需要等待一会儿。 查看结果，然后选择**关闭**。  
  
 如果导入了需要发布的任何更改，则这些自定义项只有在发布之后才可用。 
  
 如果导入失败，您将看到显示捕获的错误和警告的报告。 选择**下载日志文件**以获取导致导入失败的详细信息。 导入失败的最常见原因是解决方案不包含一些必需的组件。  
  
 下载日志文件时，您将发现一个可以使用 Office Excel 打开以查看内容的 XML 文件。  
  
> [!NOTE]
>  无法编辑活动的传递规则集。 因此，如果您正在向带有同样 ID 规则的环境中导入包括可用路径规则组的解决方案，则导入失败。 详细信息：[为传递案例自动创建规则](https://docs.microsoft.com/dynamics365/customer-engagement/customer-service/create-rules-automatically-route-cases)  
  
<a name="BKMK_UpdateSolutions"></a>   

### <a name="see-also"></a>另请参阅
[更新解决方案](update-solutions.md) <br />
[导出解决方案](export-solutions.md)

