---
title: 窗体设计器中的可用属性 | MicrosoftDocs
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: 7a30c6b59b5426cea7fc265112ac24ebe8efd36d
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2868103"
---
# <a name="properties-available-in-the-form-designer"></a>窗体设计器中的可用属性

位于模型驱动窗体设计器的右侧窗格，属性窗格让您可以快速查看和更新从预览或树视图选择的任何元素的属性。 

> [!div class="mx-imgBorder"] 
> ![](media/form-designer-property-pane.png "Form designer property pane")

## <a name="form-properties"></a>窗体属性

|名称  |说明  |
|---------|---------|
|**标题**     | 输入一个对用户有意义的名称。 此名称将向使用窗体的用户显示。 如果他们可以使用为实体配置的多个窗体，则将使用此名称区分可用窗体。 <br /> 该属性是必需的。        |
|**说明**     |  输入描述，说明此窗体与其他主窗体的不同之处。 此描述仅在解决方案资源管理器中某个实体的窗体列表中显示。        |
|**最大宽度**     | 设置最大宽度（像素）可限制窗体的宽度。 默认值为 1900。 <br /> 该属性是必需的。       |
|**显示图像**      | 显示实体的**主要图像**（如果已经设置）。 此设置允许在此窗体的标题中显示图像字段。 <br /> 有关实体选项的详细信息，请参阅启用或禁用实体选项。         |


## <a name="tab-properties"></a>选项卡属性

|面积图   |姓名  |说明  |
|---------|---------|---------|
|**显示选项**      | **选项卡标签**      | 可本地化的选项卡标签，向用户显示。 <br /> 该属性是必需的。         |
| **显示选项**      |  **名称**     |  选项卡的唯一名称，在脚本中引用选项卡时使用该名称。 该名称只能包含字母数字字符和下划线。 <br />该属性是必需的。      |
| **显示选项**      |  **默认情况下展开此选项卡**      |  可以使用窗体脚本或者由选择标签的用户来切换选项卡的展开或折叠状态。 选择选项卡的默认状态。       |
| **显示选项**      | **隐藏选项卡**     | 选择后，选项卡默认隐藏，可以使用代码显示。       |
| **显示选项**      | **在电话上隐藏**     |  对于电话屏幕上的此窗体的浓缩版，选项卡可以隐藏。     |
| **格式设置**   | **布局**     |  选项卡最多可以有三栏。 使用这些选项可以设置选项卡的数量，以及它们应填充的总宽度百分比。      |


## <a name="section-properties"></a>分区属性

|面积图   |姓名  |说明  |
|---------|---------|---------|
|**显示选项**      | **节标签**    | 可本地化的节标签，向用户显示。 <br /> 该属性是必需的。      |
|**显示选项**      | **名称**    | 节的唯一名称，在脚本中引用节时使用该名称。 该名称只能包含字母数字字符和下划线。 <br /> 该属性是必需的。        |
|**显示选项**      | **隐藏标签**   |  选择后，节标签将隐藏。  |
|**显示选项**      | **锁定节**    | 锁定此节以防止它被删除。      |
|**显示选项**      | **隐藏节**     | 选择后，节默认隐藏，可以使用代码显示。      |
|**显示选项**      | **在电话上隐藏**     |  对于电话屏幕上的此窗体的浓缩版，节可以隐藏。     |
|**格式设置**     |  **列**    |  分区中最多可指定四栏。      |

## <a name="field-properties"></a>字段属性

|面积图  |姓名  |说明  |
|---------|---------|---------|
|**显示选项**     | **字段标签**    | 默认情况下，标签与字段的显示名称匹配。 通过在此处输入其他标签，可以覆盖窗体的该名称。       |
|**显示选项**     |  **字段名称**    | 字段的名称。 来自实体上的字段属性，为只读字段。     |
|**显示选项**     | **隐藏标签**     | 选择后，字段标签将隐藏。      |
|**显示选项**     | **只读字段**    | 选择后，字段值不可编辑。      |
|**显示选项**     |  **锁定字段**   |  锁定此字段以防止它被删除。     |
|**显示选项**     |  **隐藏字段**     | 选择后，字段默认隐藏，可以使用代码显示。      |
|**显示选项**     |  **在电话上隐藏**    | 对于电话屏幕上的此窗体的浓缩版，字段可以隐藏。         |
|**格式设置**     | **字段宽度**      |  当包含字段的分区有多栏时，可以将字段设置为最多占据分区具有的栏数。       |

## <a name="see-also"></a>另请参阅
[模型驱动的窗体设计器概述](form-designer-overview.md)  
[使用窗体设计器创建、编辑或配置窗体](create-and-edit-forms.md)  
[添加、配置、移动或删除窗体中的字段](add-move-or-delete-fields-on-form.md)  
[添加、配置、移动或删除窗体中的组件](add-move-configure-or-delete-components-on-form.md)  
[添加、配置、移动或删除窗体中的分区](add-move-or-delete-sections-on-form.md)  
[添加、配置、移动或删除窗体中的选项卡](add-move-or-delete-tabs-on-form.md)  
[在窗体设计器中配置页眉属性](form-designer-header-properties.md)  
[在窗体中添加和配置子网格组件](form-designer-add-configure-subgrid.md)  
[在窗体中添加和配置快速视图组件](form-designer-add-configure-quickview.md)  
[在窗体设计器中使用树视图](using-tree-view-on-form.md)  
[创建和编辑字段](../common-data-service/create-edit-field-portal.md)  
