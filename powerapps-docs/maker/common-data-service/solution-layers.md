---
title: 查看解决方案层 | MicrosoftDocs
description: 了解如何使用解决方案层
keywords: ''
ms.date: 04/18/2019
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
ms.openlocfilehash: a5b507384b3fdf157aa029ad98d4d4203f624d8f
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2702091"
---
<!--note from editor: Best practice is that H1 title and title in metadata are different.    -->

# <a name="view-solution-layers"></a>查看解决方案层
解决方案层允许您查看由于一段时间内的解决方案更改发生的所有组件更改。 在解决方案层中，您可以向下钻取来查看组件的已更改和未更改的特定的属性详细信息。 

解决方案层： 
-   允许您查看解决方案更改组件的顺序。 
-   允许您查看特定解决方案中组件的所有属性（包括对组件进行的更改）。 
-   通过显示解决方案更改引入的组件的更改详细信息，可以用于解决依赖项或解决方案层问题。

## <a name="view-the-solution-layers-for-a-component"></a>查看组件的解决方案层
您可以从**组件**列表或从解决方案资源管理器中的**依赖项详细信息**对话框访问解决方案层。 

<!--note from editor: In step 2 below, does the page display a name at top? If so, use the same capitalization in text. -->

1. 若要查看**组件**列表中的解决方案层，打开[解决方案资源管理器](../model-driven-apps/advanced-navigation.md#solution-explorer)。 在**组件**列表中，选择组件，如**客户**，然后选择工具栏上的**解决方案层**。 

   > [!div class="mx-imgBorder"] 
   > ![解决方案层按钮](media/solution-layers-toolbar.png "解决方案层按钮")

2. 解决方案层页面将显示。 其中显示顶部有最新层的组件（如此处显示的**客户**实体）的每个层。 若要查看解决方案层的详细信息，请选择它。 

   > [!div class="mx-imgBorder"] 
   > ![解决方案层列表](media/solution-layers-list.png "解决方案层列表")

3. 在**解决方案层**对话框中，**更改的属性**选项卡仅显示作为特定解决方案层的一部分修改的属性。 

   > [!div class="mx-imgBorder"] 
   > ![解决方案层的更改的属性](media/solution-layers-change-prop.png "解决方案层的更改的属性")

4. 选择**所有属性**选项卡来查看解决方案层的所有属性，包括更改的和未更改的属性。 

   > [!div class="mx-imgBorder"] 
   > ![解决方案层的所有属性](media/solution-layers-all-prop.png "解决方案层的所有属性")

### <a name="see-also"></a>另请参阅
[解决方案概述](solutions-overview.md)
