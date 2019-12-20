---
title: 在 Power Apps 中创建或编辑模型驱动应用的系统图表 | MicrosoftDocs
description: 了解如何创建或编辑图表
ms.custom: ''
ms.date: 05/23/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Mattp123
ms.assetid: e02d58f7-6b1c-4a51-b801-a4d9f24729c5
caps.latest.revision: 29
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 24c932f34c23c42f938f54ffa4f328f25a714c59
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "2875166"
---
# <a name="create-a-model-driven-app-system-chart"></a>创建模型驱动应用程序的系统图表

在本主题，您可以了解如何创建系统图表。 系统图表是组织负责的图表，这让它们可供具有运行应用程序的数据的读取访问权限的任何人使用。 系统图表不能分配或与特定应用程序用户共享。  
  
1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

    > [!IMPORTANT]
    > “如果**模型驱动**的设计模式不可用，您可能需要[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)。     
  
2. 展开**数据**，选择**实体**，选择所需实体，然后选择**图表**选项卡。  
  
3.  在工具栏上，选择**添加图表**。  
  
4.  指定图表的类型，以及数据在图表中的显示方式。  
  
    -   输入图表名称，如*按客户提供的员工数*。  
  
    -   在**选择字段**下拉列表中： 
        - 在**选择字段**的**系列**轴下拉列表中，选择一个字段，如**员工人数**。  
        - 在**选择字段**的**类别**轴下拉列表中，选择一个字段，如**客户名称**。
  
    -   添加描述以标识图表的用途，如*此列图表按客户名称显示员工数*。 

    > [!div class="mx-imgBorder"] 
    > ![示例图表](media/sample-chart.png)
  
5.  选择**保存并关闭**。  

## <a name="known-issues"></a>已知问题  
在图表设计器中，不支持在某些计算字段上添加订单，这将导致错误。  导致此问题的计算字段正在使用另一个计算字段、相关实体字段或实体上的本地字段。

## <a name="next-steps"></a>后续步骤  
[创建或编辑仪表板](create-edit-dashboards.md)
