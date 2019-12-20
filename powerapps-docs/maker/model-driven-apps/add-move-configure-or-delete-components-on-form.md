---
title: 添加、配置、移动或删除窗体中的组件 | MicrosoftDocs
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
ms.openlocfilehash: c77eeb17dfce8d98b7c573993e3096124c8a9bb6
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2863820"
---
# <a name="add-configure-move-or-delete-components-on-a-form"></a>添加、配置、移动或删除窗体中的组件  
通过使用窗体设计器，开发者可以轻松添加和配置热门组件，例如[子网格](form-designer-add-configure-subgrid.md)、[快速视图](form-designer-add-configure-quickview.md)、弧形旋钮、线性滑块等。

## <a name="add-components-to-a-form"></a>向窗体添加组件
要将组件添加到窗体中，请使用**组件**窗格。 **组件**窗格还允许您搜索以快速找到组件。  

> [!div class="mx-imgBorder"] 
> ![](media/FormDesignerComponentsPane.PNG "Components pane")

### <a name="add-components-to-a-form-using-drag-and-drop"></a>使用拖放将组件添加到窗体
> [!NOTE]
> 在使用拖放添加或移动组件时，请了解，窗体预览可以响应，并可以堆叠式地呈现多个分区栏。 要确保添加或移动的组件在正确的分区栏中，将它放下或粘贴，使其锚定到已位于该分区栏的另一个字段或组件。
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在命令栏上，选择**添加组件**，或在左窗格中选择**组件**以查看可用组件的列表。 您还可以将鼠标悬停在列表中的某个组件上，以查看该组件的预览图像、说明和其他详细信息。
3. 在**组件**窗格中，搜索或滚动以找到要添加的组件，然后选择它。
4. 将组件拖放到窗体预览上。 当您在窗体预览上拖动组件时，您将看到可以添加组件的置放目标。 

   请注意以下事项： 
    - 组件可以放在任何现有组件或字段的前面或后面。
    - 组件也可以放在分区内的空区域。 在这种情况下，组件将被添加到可用空间中，以便让字段和组件在分区栏之间平均分布。
    - 在拖动组件时将鼠标指针悬停在选项卡标题上将更改当前选择的选项卡，让您可以将组件添加到其他选项卡。
    - 在大多数情况下，放下组件时，您会看到一个对话框，用于配置组件的属性。 确保已配置组件的所有必需属性。 
5. 在用于配置组件属性的对话框中，在**组件显示位置**下，默认会选择 **Web**、**移动设备**和**平板电脑版**选项，以确保在 Web、移动应用和平板电脑应用上显示窗体时使用该组件。 根据您的要求，您可以清除其中一些选项以限制组件的使用。 选择**完成**。
6. 重复上述步骤 3-5，添加更多组件。
7. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

### <a name="add-components-for-a-field-on-the-form"></a>为窗体上的字段添加组件
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择一个现有字段。
3. 在属性窗格中，在**组件**区域下，选择 **+ 组件**。
4. **添加组件**对话框将显示可用于当前字段类型的组件列表。 您可以将鼠标悬停在列表中的某个组件上，以查看该组件的预览图像、说明和其他详细信息。
5. 在**添加组件**对话框中，搜索或滚动以找到要添加的组件，然后选择它。
   在大多数情况下，会显示一个对话框，以便您可以配置组件的属性。 确保已配置组件的所有必需属性。
6. 在用于配置组件属性的对话框中，在**组件显示位置**下，默认会选择 **Web**、**移动设备**和**平板电脑版**选项，以确保在 Web、移动应用和平板电脑应用上显示窗体时使用该组件。 根据您的要求，您可以清除其中一些选项以限制组件的使用。 选择**完成**。
7. 如果要向同一字段或其他字段添加更多组件，请重复上述步骤 2-6。
8. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。

## <a name="configure-components-on-a-form"></a>在窗体中配置组件
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择一个现有字段。
3. 在属性窗格的**组件**区域下，选择要配置的组件。
4. 您可能会看到一个对话框，用于配置组件的属性。 根据需要更改组件的属性，然后选择**完成**。
5. 重复步骤 2-4，以在同一个或另一个字段上配置更多组件。
6. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。

## <a name="move-components-on-a-form"></a>在窗体中移动组件
您可以通过拖放或剪切和粘贴操作来移动窗体上的组件。 

### <a name="move-components-on-a-form-using-drag-and-drop"></a>使用拖放在窗体中移动组件
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择要移动的组件并拖放它。 当您在窗体预览上拖动组件时，您可以向其移动组件的置放目标将显示。     

   请注意以下事项： 
    - 组件可以放在任何现有组件或字段的前面或后面。
    - 组件也可以放在分区内的空区域。 在这种情况下，组件将被添加到可用空间中，以便让组件和字段在分区栏之间平均分布。
    - 在拖动组件时将鼠标指针悬停在选项卡标题上将更改当前选择的选项卡，让您可以将组件添加到其他选项卡。   
4. 重复上述步骤 2-3，移动更多组件。
5. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

### <a name="move-components-on-a-form-using-cut-and-paste"></a>使用剪切和粘贴在窗体中移动组件
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择要移动的组件。
3. 在命令栏上，选择**剪切**。
4. 在窗体预览中，选择另一个现有组件、字段或分区。 如果需要，可以切换到其他选项卡。
5. 在命令栏上，选择**粘贴**或选择 V 形，然后选择**在前面粘贴**。     

   请注意以下事项：
    - 当您选择**粘贴**时，被移动的组件会粘贴在现有组件或字段后面。 
    - 当您选择**粘贴在前面**时，被移动的组件会粘贴在现有组件或字段前面。
    - 如果选择分区，将把移动的组件添加到可用空间中，以便让组件和字段在分区栏之间平均分布。 **粘贴在前面**操作不适用，因此在此情况下不可用。
6. 如果要移动多个组件，请重复上述步骤 2-5。
7. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

## <a name="delete-components-on-a-form"></a>在窗体中删除组件
1. 打开窗体设计器创建或编辑窗体。 更多信息：[创建窗体](create-and-edit-forms.md#create-a-form)或[编辑窗体](create-and-edit-forms.md#edit-a-form)
2. 在窗体预览中，选择要从窗体中删除的组件，然后在命令栏上选择**删除**。 
3. 如果要删除多个组件，请重复步骤 2。
4. 在命令栏上，选择**保存**保存窗体，或在要保存更改并向用户显示时选择**发布**。 

     > [!NOTE]
     >   -  如果误删了组件，在命令栏上，选择**撤销**将窗体恢复为之前的状态。 
     >   -  您不能删除锁定的组件或正在使用窗体上其他任何地方都没有的必填字段的组件。 

### <a name="see-also"></a>另请参阅
[模型驱动的窗体设计器概述](form-designer-overview.md)  
[使用窗体设计器创建、编辑或配置窗体](create-and-edit-forms.md)  
[添加、配置、移动或删除窗体中的字段](add-move-or-delete-fields-on-form.md)  
[添加、配置、移动或删除窗体中的分区](add-move-or-delete-sections-on-form.md)  
[添加、配置、移动或删除窗体中的选项卡](add-move-or-delete-tabs-on-form.md)  
[在窗体设计器中配置页眉属性](form-designer-header-properties.md)  
[在窗体中添加和配置子网格组件](form-designer-add-configure-subgrid.md)  
[在窗体中添加和配置快速视图组件](form-designer-add-configure-quickview.md)  
[在窗体中配置查找组件](form-designer-add-configure-lookup.md)  
[在窗体设计器中使用树视图](using-tree-view-on-form.md)  
[创建和编辑字段](../common-data-service/create-edit-field-portal.md)  
