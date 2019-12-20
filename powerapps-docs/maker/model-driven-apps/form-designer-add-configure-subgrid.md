---
title: 在窗体中添加和配置子网格组件 | MicrosoftDocs
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
ms.openlocfilehash: da158d718754e30a5979b680cd5640c8449a20b2
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2868323"
---
<!-- note from editor: I recommend removing the hyphen from "sub-grid" based on the style guide entry for sub: https://styleguides.azurewebsites.net/Styleguide/Read?id=2700&topicid=28872. I didn't change it here because I don't know how wide an impact that might have. -->


# <a name="add-and-configure-a-sub-grid-component-on-a-form"></a>在窗体中添加和配置子网格组件  
显示记录详细信息的窗体可使用子网格组件以表格格式显示相关或无关记录的列表。 开发者可使用窗体设计器添加和配置子网格组件。

## <a name="add-a-sub-grid-component"></a>添加子网格组件
可按照添加其他任何组件的相同方法添加子网格组件。 详细信息：[在窗体中添加、配置、移动或删除组件](add-move-configure-or-delete-components-on-form.md)

## <a name="configure-a-sub-grid-component"></a>配置子网格组件
使用窗体中的子网格组件时，可使用窗体设计器配置一些属性。


|面积图   |姓名  |说明  |
|---------|---------|---------|
| **显示选项** | **标签** | 可本地化的子网格标签，向用户显示。 <br /><br />该属性是必需的。|
| **显示选项** |  **姓名** |  子网格的唯一名称，在脚本中引用子网格时使用该名称。 该名称只能包含字母数字字符和下划线。 <br /><br />该属性是必需的。 |
| **显示选项** | **在电话上隐藏** |  可隐藏子网格以在手机屏幕上显示此窗体的浓缩版。 |
| **显示选项** | **显示相关记录** |  选择后，子网格仅显示与窗体中显示的当前记录有关的记录。 <br /><br />还将筛选**实体**下拉列表以仅列出与当前实体有关的实体。 |
| **显示选项** | **实体** |  要在子网格中显示其记录的实体。 <br /><br />如果选择**显示相关记录**，将筛选实体列表以仅显示与当前实体有关的实体。 除了实体名称，还将使用括号显示查找字段的名称。 |
| **显示选项** | **默认视图** |  **实体**属性中选择的实体的视图，用于获取记录列表并在子网格中显示。 |
| **显示选项** | **允许用户更改视图** |  选择后，应用程序用户可从**默认视图**切换到**实体**属性中选择的实体的另一个视图。 |
| **显示选项** | **显示所有视图** |  选择后，应用程序用户可从**默认视图**切换到**实体**属性中选择的实体的其他所有视图。 <br /><br />仅当选择了**允许用户更改视图**此属性才可用。 |
| **显示选项** | **所选视图** |  应用程序用户可从**默认视图**切换到的**实体**属性中所选实体视图的列表。 <br /><br />仅当选择了**允许用户更改视图**，但清除**显示所有视图**，此属性才可用。 |

## <a name="see-also"></a>另请参阅
[模型驱动的窗体设计器概述](form-designer-overview.md)  
[使用窗体设计器创建、编辑或配置窗体](create-and-edit-forms.md)  
[添加、配置、移动或删除窗体中的字段](add-move-or-delete-fields-on-form.md)  
[添加、配置、移动或删除窗体中的组件](add-move-configure-or-delete-components-on-form.md)  
[添加、配置、移动或删除窗体中的分区](add-move-or-delete-sections-on-form.md)  
[添加、配置、移动或删除窗体中的选项卡](add-move-or-delete-tabs-on-form.md)  
[在窗体设计器中配置页眉属性](form-designer-header-properties.md)  
[在窗体中添加和配置快速视图组件](form-designer-add-configure-quickview.md)  
[在窗体中配置查找组件](form-designer-add-configure-lookup.md)  
[在窗体设计器中使用树视图](using-tree-view-on-form.md)  
[创建和编辑字段](../common-data-service/create-edit-field-portal.md)  
