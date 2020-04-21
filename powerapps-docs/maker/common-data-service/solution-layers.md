---
title: 解决方案层 | MicrosoftDocs
description: 了解如何使用解决方案层
keywords: ''
ms.date: 03/13/2020
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
ms.openlocfilehash: 9c9e95e477e2ccb0bce9eac2256221486412f584
ms.sourcegitcommit: 6fce86edacd9bfe49f8114a2a69bc18302cd01f9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "3260672"
---
# <a name="solution-layers"></a>解决方案层

托管和非托管解决方案位于 Common Data Service 环境中的不同级别上。 在 Common Data Service 中，有两个不同的层级：  
- 非托管层。 所有导入的非托管解决方案和非托管自定义项都存在于此层。 非托管层是一个单层。  
- 托管层。 所有导入的托管解决方案和系统解决方案都存在于此级别。 如果安装了多个托管解决方案，则安装的最后一个托管解决方案在之前安装的托管解决方案上面。 也就是说，安装的第二个解决方案可以自定义之前安装的那个解决方案。 当两个托管解决方案的定义相互冲突时，运行时行为要么是“后来者赢”，要么是实现合并逻辑。  如果卸载托管解决方案，则其下方的托管解决方案后生效。 如果卸载所有托管解决方案，则应用系统解决方案中定义的默认行为。 系统层是托管层级的基础。 系统层包含平台运行所需的实体和组件。 

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
5. 选择 **LocalizedLabels** 选项卡可显示在解决方案层中有标签字段的组件的信息。 将按照 **languageid** 列中所示显示基本语言和任何导入的翻译文本。 如果不存在任何标签，将不显示该选项卡。  
   > [!div class="mx-imgBorder"] 
   > ![解决方案层本地化标签](media/localized-labels.png "解决方案层本地化标签")

    选择标签查看其完全分层。

### <a name="see-also"></a>另请参阅
[翻译模型驱动应用程序的可本地化文本](../model-driven-apps/translate-localizable-text.md) <br />
[解决方案概述](solutions-overview.md)
