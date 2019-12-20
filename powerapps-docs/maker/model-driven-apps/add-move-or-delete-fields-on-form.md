---
title: 添加、配置、移动或删除窗体中的字段 | MicrosoftDocs
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
ms.openlocfilehash: d711a46676003786363f3496515dbd387024dadb
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2860636"
---
# <a name="add-configure-move-or-delete-fields-on-a-form"></a>添加、配置、移动或删除窗体中的字段  
使用窗体设计器添加、配置、移动或删除字段。

## <a name="add-fields-to-a-form"></a>将字段添加到表单
要将字段添加到窗体中，请使用**字段**窗格。 可通过**字段**窗格搜索和筛选来帮助快速找到字段。 还包括用于仅显示未使用的字段的选项。 

> [!div class="mx-imgBorder"] 
>    ![](media/FormDesignerFieldsPane.png "Fields pane")

### <a name="add-fields-to-a-form-using-drag-and-drop"></a>使用拖放将字段添加到窗体
> [!NOTE]
> 在使用拖放添加或移动字段时，请了解，窗体预览可以响应，并可以堆叠式地呈现多个分区栏。 要确保字段在正确的分区栏中添加或移动，将它放下或粘贴，使其锚定到已位于该分区栏的另一个字段。
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在命令栏中，选择**添加字段**，或在左侧窗格中选择**字段**。  打开窗体设计器时，默认打开**字段**窗格。 
3. 在**字段**窗格中，搜索、筛选或滚动以查找要添加的字段。 如果找不到字段，可能是因为该字段已在窗体上。 清除**显示未使用的字段**显示所有字段，包括已添加到窗体的字段。 
4. 在**字段**窗格中，选择字段并将其拖动到窗体预览。 当您在窗体预览上拖动字段时，您将看到可以添加字段的置放目标。 
5. 在所需位置放下字段。 请注意以下事项： 
    - 字段可以放在任何现有字段或组件的前面或后面。
    - 字段也可以放在分区内的空区域。 在这种情况下，字段将被添加到可用空间中，以便让字段和组件在分区栏之间平均分布。
    - 在拖动字段时将鼠标指针悬停在选项卡标题上将更改当前选择的选项卡，让您可以将字段添加到其他选项卡。   
6. 如果要添加多个字段，请重复上述步骤 3-5。
7. 在命令栏中，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

### <a name="add-fields-to-a-form-using-selection"></a>使用选择将字段添加到窗体 

1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择另一个现有字段或分区。 请注意以下事项：
    - 如果选择现有字段，将把新字段添加到现有字段后面。 
    - 如果选择分区，将把新字段添加到可用空间中，以便让字段在分区栏之间平均分布。 
3. 在命令栏中，选择**添加字段**，或在左侧窗格中选择**字段**。 打开窗体设计器时，默认打开**字段**窗格。 
4. 在**字段**窗格中，搜索、筛选或滚动以查找要添加的字段。 如果找不到字段，可能是因为该字段已在窗体上。 清除**显示未使用的字段**显示所有字段，包括已添加到窗体的字段。 
5. 在**字段**窗格中，选择字段将其添加到窗体。 或者选择所需字段旁边的 **...**，然后选择**添加到所选部分**。 
6. 如果要添加多个字段，请重复上述步骤 2-5。
7. 在命令栏中，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

## <a name="configure-fields-on-a-form"></a>配置窗体上的字段
当您使用窗体设计器创建或编辑窗体时，以下属性可用于配置字段。

## <a name="field-properties"></a>字段属性

|面积图  |姓名  |说明  |
|---------|---------|---------|
|**显示选项** | **字段标签** | 默认情况下，标签与字段的显示名称匹配。 通过在此处输入其他标签，可以覆盖窗体的该名称。 <br /><br />该属性是必需的。 |
|**显示选项** |  **字段名称** | 字段的名称。 来自实体上的字段属性，为只读字段。 |
|**显示选项** | **隐藏标签** | 选择后，字段标签将隐藏。 |
|**显示选项** | **只读字段** | 选择后，字段值不可编辑。 |
|**显示选项** | **锁定字段** |  锁定此字段，使其无法删除。 |
|**显示选项** | **隐藏字段** | 选择后，字段默认隐藏，可以使用代码显示。 |
|**显示选项** | **在电话上隐藏** | 可隐藏字段以在手机屏幕上显示此窗体的浓缩版。 |
|**格式设置** | **字段宽度** |  当包含字段的分区有多栏时，可以将字段设置为最多占据分区具有的栏数。 |

## <a name="move-fields-on-a-form"></a>在窗体中移动字段
您可以使用拖放或剪切和粘贴操作来移动窗体上的字段。 

### <a name="move-fields-on-a-form-using-drag-and-drop"></a>使用拖放在窗体中移动字段
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择要移动的字段并拖放它。 当您在窗体预览上拖动字段时，您将看到可以向其移动字段的置放目标。 
   请注意以下事项：
    - 字段可以放在任何现有字段或组件的前面或后面。
    - 字段也可以放在分区内的空区域。 在这种情况下，字段将被添加到可用空间中，以便让字段和组件在分区栏之间平均分布。
    - 在拖动字段时将鼠标指针悬停在选项卡标题上将更改当前选择的选项卡，让您可以将字段添加到其他选项卡。   
3. 如果要移动多个字段，请重复上述步骤 2。
4. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

### <a name="move-fields-on-a-form-using-cut-and-paste"></a>使用剪切和粘贴在窗体中移动字段
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择要移动的字段。
3. 在命令栏上，选择**剪切**。
4. 在窗体预览中，选择另一个现有字段、组件或分区。 如果需要，还可以切换到其他选项卡。
5. 在命令栏上，选择**粘贴**或选择 V 形，然后选择**在前面粘贴**。      请注意以下事项：
     - 当您选择**粘贴**时，被移动的字段会粘贴在现有字段或组件后面。 
     - 当您选择**粘贴在前面**时，被移动的字段会粘贴在现有字段或组件前面。
     - 如果选择分区，将把移动的字段添加到可用空间中，以便让字段和组件在分区栏之间平均分布。 **粘贴在前面**操作不适用，因此在此情况下不可用。
6. 如果要移动多个字段，请重复上述步骤 2-5。
7. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

## <a name="delete-fields-on-a-form"></a>在窗体中删除字段
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择要从窗体中删除的字段。 
3. 在命令栏上，选择**删除**。 
4. 如果要删除多个字段，请重复步骤 2-3。
5. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

     > [!NOTE]
     >   -  如果误删了字段，在命令栏上，选择**撤销**将窗体恢复为之前的状态。 
     >   -  您不能删除锁定的字段或必填的且在窗体上其他任何地方都没有的字段。 

## <a name="create-a-new-field-on-the-entity-when-editing-a-form"></a>编辑窗体时在实体上创建新字段 
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在命令栏上，选择**添加字段**，或在左侧窗格中选择**字段**。 打开窗体设计器时，默认打开**字段**窗格。 
3. 在**字段**窗格中，选择 **+ 新建字段**。
4. 在**新建字段**对话框中，为字段提供**显示名称**和**名称**。
5. 在**新建字段**对话框中，选择**数据类型**并配置字段的任何其他必需属性。

     > [!NOTE]
     >   -  当您从窗体设计器中创建字段时，某些字段类型不可用。 如果所需的字段类型不可用，则可以按照[使用 Power Apps 门户创建和编辑 Common Data Service 的字段](../common-data-service/create-edit-field-portal.md)中所述的步骤进行操作

6. 选择**完成**在实体上创建新字段。 该字段将显示在**字段**窗格中。
7. 如果您要将新创建的字段添加到窗体，请按照[**将字段添加到窗体**](add-move-or-delete-fields-on-form.md#add-fields-to-a-form)一节中所述的步骤操作。

     > [!NOTE]
     >  在实体上创建字段后，它不仅限于当前窗体，也可以在其他地方使用。

### <a name="see-also"></a>另请参阅
[模型驱动的窗体设计器概述](form-designer-overview.md)  
[使用窗体设计器创建、编辑或配置窗体](create-and-edit-forms.md)  
[添加、配置、移动或删除窗体中的组件](add-move-configure-or-delete-components-on-form.md)  
[添加、配置、移动或删除窗体中的分区](add-move-or-delete-sections-on-form.md)  
[添加、配置、移动或删除窗体中的选项卡](add-move-or-delete-tabs-on-form.md)  
[在窗体设计器中配置页眉属性](form-designer-header-properties.md)  
[在窗体中添加和配置子网格组件](form-designer-add-configure-subgrid.md)  
[在窗体中添加和配置快速视图组件](form-designer-add-configure-quickview.md)  
[在窗体中配置查找组件](form-designer-add-configure-lookup.md)  
[在窗体设计器中使用树视图](using-tree-view-on-form.md)  
[创建和编辑字段](../common-data-service/create-edit-field-portal.md)  
