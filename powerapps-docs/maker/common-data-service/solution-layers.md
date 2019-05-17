---
title: 查看解决方案层 | MicrosoftDocs
description: 了解如何使用解决方案层
keywords: null
ms.date: 04/10/2019
ms.service: powerapps
ms.custom: null
ms.topic: article
applies_to:
  - Dynamics 365 for Customer Engagement (online)
  - Dynamics 365 for Customer Engagement Version 9.x
  - powerapps
ms.assetid: null
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: null
ms.suite: null
ms.tgt_pltfrm: null
caps.latest.revision: null
topic-status: Drafting
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="view-solution-layers"></a>查看解决方案层
解决方案层允许您查看由于一段时间内的解决方案更改发生的所有组件更改。 在解决方案层中，您可以向下钻取来查看组件的已更改和未更改的特定的属性详细信息。 

解决方案层提供以下优势： 
-   允许您查看解决方案更改组件的顺序。 
-   允许您查看特定解决方案中组件的所有属性（包括对组件进行的更改）。 
-   通过显示解决方案更改引入的组件的更改详细信息，可以用于解决依赖项或解决方案层问题。

## <a name="view-the-solution-layers-for-a-component"></a>查看组件的解决方案层
您可以从**组件**列表或从解决方案资源管理器中的**依赖项详细信息**对话框访问解决方案层。 

1. 若要从**组件**列表查看解决方案层，[打开解决方案资源管理器](../model-driven-apps/advanced-navigation.md#solution-explorer)，在**组件**列表中选择组件，如**客户**，然后在工具栏上选择**解决方案层**。 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-toolbar.png "解决方案层按钮")

2. 解决方案层页面显示顶部有最新层的组件（如此处显示的客户实体）的每个层。 若要查看解决方案层的详细信息，请选择它。 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-list.png "解决方案层列表")

3. 在**解决方案层**对话框中，**更改的属性**选项卡仅显示作为特定解决方案层的一部分修改的属性。 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-change-prop.png "解决方案层的更改的属性")

4. 选择**所有属性**选项卡来查看解决方案层的所有属性，包括更改的和未更改的属性。 

   > [!div class="mx-imgBorder"] 
   > ![](media/solution-layers-all-prop.png "解决方案层的所有属性")

## <a name="see-also"></a>另请参阅
[解决方案概述](solutions-overview.md)