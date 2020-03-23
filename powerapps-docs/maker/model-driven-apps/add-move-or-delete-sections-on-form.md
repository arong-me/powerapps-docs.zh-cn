---
title: 使用窗体设计器添加、配置、移动或删除分区 | MicrosoftDocs
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
author: Aneesmsft
ms.author: matp
manager: kvivek
tags:
- Power Apps maker portal impact
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2731520659633c305e19e02b67670bb12796dc50
ms.sourcegitcommit: ed583eb94720a9645bfd79776311792a958077b8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/01/2020
ms.locfileid: "3094010"
---
# <a name="add-configure-move-or-delete-sections-on-a-form"></a>添加、配置、移动或删除窗体中的分区 
使用窗体设计器添加、配置、移动或删除分区。 

## <a name="add-sections-to-a-form"></a>向窗体中添加分区
要将分区添加到窗体中，请使用**组件**窗格。 

> [!div class="mx-imgBorder"] 
> ![](media/FormDesignerComponentsLayout.png "Layout components")

  > [!NOTE]
  >   分区只能在主窗体和快速视图窗体中添加。 详细信息：[窗体类型](types-forms.md)

### <a name="add-sections-to-a-form-using-drag-and-drop"></a>使用拖放将分区添加到窗体
> [!NOTE]
> 在使用拖放添加或移动分区时，请了解，窗体预览可以响应，并可以堆叠式地呈现多个选项卡。 要确保分区在正确的选项卡栏中添加或移动，将它放下或粘贴，使其锚定到已位于该选项卡栏的另一个分区。
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在命令栏中，选择**添加组件**，或在左侧窗格中选择**组件**。 
3. 在**组件**窗格中，选择分区组件并将其拖动到窗体预览。 当您在窗体预览上拖动分区时，您将看到可以添加分区的置放目标。 
4. 在所需位置放下分区。 请注意以下事项： 
    - 分区可以放在任何现有分区的前面或后面。
    - 分区也可以放在选项卡内的空区域。在这种情况下，分区将被添加到可用空间中，以便让分区在选项卡栏之间平均分布。
    - 在拖动分区时将鼠标指针悬停在选项卡标题上将更改当前选择的选项卡，让您可以将分区添加到其他选项卡。   
5. 如果要添加多个分区，请重复上述步骤 3-4。
6. 在命令栏中，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

### <a name="add-sections-to-a-form-using-selection"></a>使用选择将分区添加到窗体 
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择另一个现有分区或选项卡。请注意以下事项：
    - 当您选择现有分区时，将把新分区添加到现有分区后面。 
    - 如果选择选项卡，将把新分区添加到可用空间中，以便让分区在选项卡栏之间平均分布。 
3. 在命令栏中，选择**添加组件**，或在左侧窗格中选择**组件**。  
4. 在**组件**窗格中，选择分区组件将其添加到窗体。 或者选择所需分区组件旁边的 **...**，然后选择**添加到所选选项卡**。 
5. 如果要添加多个分区，请重复上述步骤 2-4。
6. 在命令栏中，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

## <a name="configure-sections-on-a-form"></a>配置窗体上的分区
当您使用窗体设计器创建或编辑窗体时，以下属性可用于配置分区。

|面积图   |姓名  |说明  |
|---------|---------|---------|
|**显示选项** | **节标签**    | 可本地化的节标签，向用户显示。 <br /><br />该属性是必需的。      |
|**显示选项** | **名称** | 节的唯一名称，在脚本中引用节时使用该名称。 该名称只能包含字母数字字符和下划线。 <br /><br />该属性是必需的。 |
|**显示选项** | **隐藏标签** |  选择后，节标签将隐藏。 |
|**显示选项** | **锁定节** | 锁定此节以防止它被删除。 |
|**显示选项** | **隐藏节** | 选择后，分区默认隐藏，可以使用代码显示。 |
|**显示选项** | **在电话上隐藏** |  可隐藏分区以在手机屏幕上显示此窗体的浓缩版。 |
|**格式设置** |  **列** |  分区最多可指定四栏。 |

## <a name="move-sections-on-a-form"></a>在窗体中移动分区
您可以使用拖放或剪切和粘贴操作来移动分区。 

### <a name="move-sections-on-a-form-using-drag-and-drop"></a>使用拖放在窗体中移动分区
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择要拖放的分区内的分区标签或空格。 当您在窗体预览上拖动分区时，您将看到可以向其移动分区的置放目标。 
   请注意以下事项： 
    - 分区可以放在任何现有分区的前面或后面。
    - 分区也可以放在选项卡内的空区域。在这种情况下，分区将被添加到可用空间中，以让分区在选项卡栏之间平均分布。
    - 在拖动分区时将鼠标指针悬停在选项卡标题上将更改当前选择的选项卡，让您可以将分区添加到其他选项卡。   
3. 如果要移动多个分区，请重复上述步骤 2。
5. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

### <a name="move-sections-on-a-form-using-cut-and-paste"></a>使用剪切和粘贴在窗体中移动分区
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择要移动的分区。
3. 在命令栏上，选择**剪切**。
4. 在窗体预览中，选择另一个现有分区或选项卡。如果需要，您还可以切换到其他选项卡。
5. 在命令栏上，选择**粘贴**或选择 V 形，然后选择**在前面粘贴**。      请注意以下事项： 
    - 当您选择**粘贴**时，被移动的分区会粘贴在现有分区后面。 
    - 当您选择**粘贴在前面**时，被移动的分区会粘贴在现有分区前面。
    - 如果选择选项卡，将把移动的分区添加到可用空间中，以让分区在选项卡栏之间平均分布。 **粘贴在前面**操作不适用，因此在此情况下不可用。
6. 如果要移动多个分区，请重复上述步骤 2-5。
7. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

## <a name="delete-sections-on-a-form"></a>在窗体中删除分区
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择要从窗体中删除的分区。 
3. 在命令栏上，选择**删除**。
4. 如果要删除多个分区，请重复上述步骤 2-3。
4. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

    > [!NOTE]
    >   - 分区只能在主窗体和快速视图窗体中删除。 详细信息：[窗体类型](types-forms.md)
    >   - 如果误删了分区，在命令栏上，选择**撤销**将窗体恢复为之前的状态。 
    >   - 不能删除包含必需字段或已锁定字段的分区。 
    >   - 不能删除已锁定部分。 
    >   - 一个选项卡的每个选项卡栏需要至少一个分区。 如果删除选项卡栏中剩余的最后一个分区，新分区将会自动添加。
    >   - 在统一接口中，如果您已选择隐藏某些部分（包括标题和边框），则不会呈现这些部分。  这与旧版 Web 客户端不同，这样设计是为确保窗体在不同的视图端口之间正确呈现（从宽到窄）。

### <a name="see-also"></a>另请参阅
[模型驱动的窗体设计器概述](form-designer-overview.md)  
[使用窗体设计器创建、编辑或配置窗体](create-and-edit-forms.md)  
[添加、配置、移动或删除窗体中的字段](add-move-or-delete-fields-on-form.md)  
[添加、配置、移动或删除窗体中的组件](add-move-configure-or-delete-components-on-form.md)  
[添加、配置、移动或删除窗体中的选项卡](add-move-or-delete-tabs-on-form.md)  
[在窗体设计器中配置页眉属性](form-designer-header-properties.md)  
[在窗体中添加和配置子网格组件](form-designer-add-configure-subgrid.md)  
[在窗体中添加和配置快速视图组件](form-designer-add-configure-quickview.md)  
[在窗体中配置查找组件](form-designer-add-configure-lookup.md)  
[在窗体设计器中使用树视图](using-tree-view-on-form.md)  
[创建和编辑字段](../common-data-service/create-edit-field-portal.md)  
