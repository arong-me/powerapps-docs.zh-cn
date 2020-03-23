---
title: 解决方案层 | MicrosoftDocs
description: 了解如何使用解决方案层
keywords: ''
ms.date: 02/05/2020
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
ms.openlocfilehash: 10ab6feca7843d64d20938561d44748fc6756768
ms.sourcegitcommit: dc379bede57da58b5787eda5437eb94b662e21ed
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2020
ms.locfileid: "3028327"
---
# <a name="solution-layers"></a>解决方案层

托管和非托管解决方案位于 Common Data Service 环境中的不同层上。 在 Common Data Service 中，有两个不同的层：  
- 非托管层。 所有导入的非托管解决方案和非托管自定义项都存在于此层。 非托管层是一个单层。  
- 托管层。 所有导入的托管解决方案和系统解决方案都存在于此层。 如果安装了多个托管解决方案，则安装的第一个托管解决方案在后安装的托管解决方案下面。 也就是说，安装的第二个解决方案可以自定义之前安装的那个解决方案。 当两托管解决方案的定义有冲突时，一般规则是“后来者赢”。 如果卸载托管解决方案，则其下方的托管解决方案后生效。 如果卸载所有托管解决方案，则应用系统解决方案中定义的默认行为。 系统层是托管层的基础。 系统层包含系统解决方案，其包括所有标准实体和组件。 系统解决方案定义您能或不能使用托管属性自定义的内容。 托管解决方案的发布商具有相同的能力，可以限制您对他们在其解决方案中添加的解决方案组件的自定义能力。 您可以自定义没有阻止您自定义它们的托管属性的任何解决方案组件。 详细信息：[在 Common Data Service 元数据中设置托管属性](set-managed-properties-metadata.md) 

![解决方案层](media/solution-layers.png)

## <a name="solution-merge-behavior"></a>解决方案合并行为
准备要分发的托管解决方案时，请记住环境可能已安装了多个解决方案，或者将来可能要安装其他解决方案。 构造遵循最佳实践的解决方案，以便您的解决方案不会干扰其他解决方案。

Common Data Service 用于合并自定义项的进程强调维护解决方案的功能。 尽管已竭尽全力保持外观，但是自定义项之间的不兼容性可能需要计算的解决方案更改某些外观细节来维护自定义项的功能。 详细信息：[了解如何合并托管解决方案](../../developer/common-data-service/understand-managed-solutions-merged.md)

## <a name="view-the-solution-layers-for-a-component"></a>查看组件的解决方案层
此解决方案层功能允许您查看由于一段时间内的解决方案更改发生的所有组件更改。 在解决方案层中，您可以向下钻取来查看组件的已更改和未更改的特定的属性详细信息。 您可以从**组件**列表或从解决方案资源管理器中的**依赖项详细信息**对话框访问解决方案层。 

此解决方案层功能： 
-   允许您查看解决方案更改组件的顺序。 
-   允许您查看特定解决方案中组件的所有属性（包括对组件进行的更改）。 
-   通过显示解决方案更改引入的组件的更改详细信息，可以用于解决依赖项或解决方案层问题。

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
