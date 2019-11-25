---
title: 查看解决方案的历史记录 | MicrosoftDocs
description: 了解如何查看解决方案的历史记录
keywords: ''
ms.date: 05/19/2019
ms.service: powerapps
ms.custom: ''
ms.topic: article
ms.assetid: ''
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: ''
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 67239062f30efb80fb8ee416614c1088e20c4075
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702179"
---
# <a name="view-the-history-of-a-solution"></a>查看解决方案的历史记录
您可以从模型驱动应用的**解决方案**区域查看有关解决方案操作的详细信息。 操作可以是解决方案导入、导出或删除。 解决方案历史记录显示解决方案版本、解决方案发布商、操作类型、操作开始和结束时间、操作状态等信息。

> [!div class="mx-imgBorder"] 
> ![](media/solutions-history-custom-view.png "Solutions history custom view")

## <a name="view-solution-history"></a>查看解决方案历史
1. 选择**设置**，然后选择**解决方案历史记录**。

     > [!div class="mx-imgBorder"] 
     > ![](media/solution-history-sitemap.png "Solution History area")

     > [!NOTE]
     > 要从 PowerApps 统一接口模型驱动应用进入**设置**区域，选择应用工具栏中的**设置** ![设置](../model-driven-apps/media/powerapps-gear.png)，然后选择**高级设置**。 

2. 默认情况下，**自定义解决方案历史记录**视图显示。 以下视图在**解决方案历史记录**区域提供。 
- **所有解决方案历史记录**。 显示内部系统和自定义解决方案的解决方案历史记录。 
- **自定义解决方案历史记录**。 仅显示自定义解决方案的解决方案历史记录。 
- **内部解决方案历史记录**。 仅显示内部系统解决方案的解决方案历史记录。 

每个解决方案历史记录都是只读的，并包括以下属性： 
- **开始时间**。 操作开始的时间。 
- **结束时间**：操作结束的时间。 
- **解决方案版本**。 解决方案的版本。 
- **发布商名称**。 与操作关联的发布商的名称。 详细信息：[更改解决方案发布商前缀](change-solution-publisher-prefix.md)  
- **操作**。 操作，如导入、导出或删除。 详细信息：[导入、更新和导出解决方案](import-update-export-solutions.md)
- **子操作**：指示操作的类型，如新解决方案导入或更新为现有解决方案。 
- **状态**。 操作的当前状态，如**已完成**或**未完成**。 
- **结果**。 操作的结果，如**成功**或**失败**。 
- **错误代码**：操作返回的错误代码。 错误代码 0 表示操作已成功完成。 

### <a name="view-solution-operation-error-details"></a>查看解决方案操作错误详细信息 
当解决方案操作包含失败时，您可以选择它来显示包含其他错误详细信息的页面。 

> [!div class="mx-imgBorder"] 
> ![](media/solution-history-with-failure.png "Solution history with operation error")

详细信息页面包含包括可帮助诊断操作失败根本原因的**异常消息**的信息。 某些错误（包括解决方案依赖项错误）也可能包含**解决方案层**链接来方便您诊断问题。 如果您需要与 Microsoft 客户支持联系，**活动 ID** 可能非常有用。 

> [!div class="mx-imgBorder"] 
> ![](media/solution-history-error-details.png "Solution operation error details")

### <a name="see-also"></a>另请参阅
[查看解决方案层](solution-layers.md)  <br />
[解决方案概述](solutions-overview.md) 


