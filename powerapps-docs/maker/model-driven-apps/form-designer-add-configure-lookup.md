---
title: 在窗体中配置查找组件 | MicrosoftDocs"
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
  - PowerApps maker portal impact
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="configure-a-lookup-component-on-a-form"></a>在窗体中配置查找组件  
查找字段可用于链接至其他实体中的记录。 如果向窗体添加查找字段，将自动使用查找组件。 开发者可使用窗体设计器配置查找组件。

## <a name="configure-a-lookup-component"></a>配置查找组件
使用窗体中的查找组件时，可使用窗体设计器配置一些属性。


<!--from editor: "Drop-down" should only be an adjective. In the following table, is it a list? A menu? -->


|面积图  |姓名  |说明  |
|---------|---------|---------|
| **显示选项** | **实体** |  查找字段连接到的相关实体。 |
| **显示选项** | **默认视图** |  **实体**属性中选择的实体的视图，可用于获取和显示应用程序用户可在查找下拉列表中选择的记录的列表。 |
| **显示选项** | **允许用户更改视图** |  选择后，应用程序用户可从**默认视图**切换到**实体**属性中选择的实体的另一个视图。 |
| **显示选项** | **显示所有视图** |  选择后，应用程序用户可从**默认视图**切换到**实体**属性中选择的实体的其他所有视图。 <br /><br />仅当选择了**允许用户更改视图**此属性才可用。 |
| **显示选项** | **所选视图** |  应用程序用户可从**默认视图**切换到的**实体**属性中所选实体视图的列表。 <br /><br />仅当选择了**允许用户更改视图**，但未选择**显示所有视图**，此属性才可用。 |

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
