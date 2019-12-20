---
title: 使用窗体设计器添加、配置、移动或删除选项卡 | MicrosoftDocs
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
ms.openlocfilehash: 0799fd352a17bb398f3f42444b9312fd90756caa
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2860619"
---
# <a name="add-configure-move-or-delete-tabs-on-a-form"></a>添加、配置、移动或删除窗体中的选项卡  
使用窗体设计器添加、移动或删除选项卡。

## <a name="add-tabs-to-a-form"></a>将选项卡添加到窗体
要将选项卡添加到窗体中，请使用**组件**窗格。  

> [!div class="mx-imgBorder"] 
> ![](media/FormDesignerComponentsLayout.png "Layout components")
   
  > [!NOTE]
  >  选项卡只能在主窗体上添加。 详细信息：[窗体类型](types-forms.md)

### <a name="add-tabs-to-a-form-using-drag-and-drop"></a>使用拖放将选项卡添加到窗体
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在命令栏上，选择**添加组件**，或在左侧窗格中选择**组件**。 
3. 在**组件**窗格中，选择选项卡组件并将其拖放到窗体预览。     当您在窗体预览上拖动选项卡时，您将看到可以添加选项卡的置放目标。请注意以下事项： 
    - 选项卡可以通过将鼠标指针悬停在选项卡标题上放在任何现有选项卡的前面或后面。
    - 选项卡还可以通过悬停在当前选项卡的左边缘或右边缘放在当前选项卡的前面或后面。
4. 如果要添加多个选项卡，请重复上述步骤 3。
5. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

### <a name="add-tabs-to-a-form-using-selection"></a>使用选择将选项卡添加到窗体 
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择另一个现有选项卡或窗体。 请注意以下事项：
    - 如果选择现有选项卡，将把新选项卡添加到现有选项卡后面。 
    - 如果选择窗体，将把新选项卡添加为窗体上的最后一个选项卡。 
3. 在命令栏上，选择**添加组件**，或在左侧窗格中选择**组件**。  
4. 在**组件**窗格中，选择选项卡组件将其添加到窗体。 或者选择所需选项卡组件旁边的 **...**，然后选择**添加到窗体**。 
5. 如果要添加多个选项卡，请重复上述步骤 2-4。
6. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

## <a name="configure-tabs-on-a-form"></a>在窗体上配置选项卡
当您使用窗体设计器创建或编辑窗体时，以下属性可用于配置选项卡。

|面积图   |姓名  |说明  |
|---------|---------|---------|
|**显示选项** | **选项卡标签** | 可本地化的选项卡标签，向用户显示。 <br /><br />该属性是必需的。 |
| **显示选项** |  **名称**  |  选项卡的唯一名称，在脚本中引用选项卡时使用该名称。 该名称只能包含字母数字字符和下划线。 <br /><br />该属性是必需的。 |
| **显示选项** |  **默认情况下展开此选项卡** |  可以使用窗体脚本或者由选择标签的用户来切换选项卡的展开或折叠状态。 选择选项卡的默认状态。 |
| **显示选项** | **隐藏选项卡** | 选择后，选项卡默认隐藏，可以使用代码显示。 |
| **显示选项** | **在电话上隐藏** |  可隐藏选项卡以在手机屏幕上显示此窗体的浓缩版。 |
| **格式设置** | **布局** |  选项卡最多可以有三栏。 使用这些选项可以设置选项卡的数量，以及它们应填充的总宽度百分比。 |

## <a name="move-tabs-on-a-form"></a>在窗体上移动选项卡
您可以使用拖放或剪切和粘贴操作来移动窗体上的选项卡。 

### <a name="move-tabs-on-a-form-using-drag-and-drop"></a>使用拖放在窗体中移动选项卡
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择要移动的选项卡的选项卡标题并对其进行拖放。 当您在窗体预览上拖动选项卡时，您将看到可以移动选项卡的置放目标。请注意以下事项：
    - 选项卡可以通过将鼠标指针悬停在选项卡标题上放在任何现有选项卡的前面或后面。
    - 选项卡还可以通过悬停在当前选项卡的左边缘或右边缘放在当前选项卡的前面或后面。
3. 如果要移动多个选项卡，请重复步骤 2。
4. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

### <a name="move-tabs-on-a-form-using-cut-and-paste"></a>使用剪切和粘贴在窗体中移动选项卡
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择要移动的选项卡。
3. 在命令栏上，选择**剪切**。
4. 在窗体预览中，选择另一个现有选项卡或窗体。
5. 在命令栏上，选择**粘贴**或选择 V 形，然后选择**在前面粘贴**。      请注意以下事项： 
    - 当您选择**粘贴**时，被移动的选项卡会粘贴在现有选项卡后面。 
    - 当您选择**粘贴在前面**时，被移动的选项卡会粘贴在现有选项卡前面。
    - 如果选择窗体，将把移动的选项卡添加为窗体上的最后一个选项卡。 **粘贴在前面**操作不适用，因此在此情况下不可用。
6. 如果要移动多个选项卡，请重复上述步骤 2-5。
7. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

## <a name="delete-tabs-on-a-form"></a>在窗体上删除选项卡
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择要从窗体中删除的选项卡。 
3. 在命令栏上，选择**删除**。
4. 如果要删除多个选项卡，请重复上述步骤 2-3。
4. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

    > [!NOTE]
    >   - 选项卡只能在主窗体上删除。 详细信息：[窗体类型](types-forms.md)
    >   - 如果误删了选项卡，在命令栏上，选择**撤销**将窗体恢复为之前的状态。 
    >   - 不能删除包含具有必需字段或已锁定字段的分区的选项卡。 
    >   - 不能删除具有已锁定部分的选项卡。 
    >   - 一个窗体必须有至少一个选项卡。不能删除窗体上剩余的最后一个选项卡。 

### <a name="see-also"></a>另请参阅
[模型驱动的窗体设计器概述](form-designer-overview.md)  
[使用窗体设计器创建、编辑或配置窗体](create-and-edit-forms.md)  
[添加、配置、移动或删除窗体中的字段](add-move-or-delete-fields-on-form.md)  
[添加、配置、移动或删除窗体中的组件](add-move-configure-or-delete-components-on-form.md)  
[添加、配置、移动或删除窗体中的分区](add-move-or-delete-sections-on-form.md)  
[在窗体设计器中配置页眉属性](form-designer-header-properties.md)  
[在窗体中添加和配置子网格组件](form-designer-add-configure-subgrid.md)  
[在窗体中添加和配置快速视图组件](form-designer-add-configure-quickview.md)  
[在窗体中配置查找组件](form-designer-add-configure-lookup.md)  
[在窗体设计器中使用树视图](using-tree-view-on-form.md)  
[创建和编辑字段](../common-data-service/create-edit-field-portal.md)  
