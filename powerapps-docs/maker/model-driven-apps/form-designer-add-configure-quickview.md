---
title: 在窗体中添加和配置快速视图组件 | MicrosoftDocs
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
ms.openlocfilehash: 4d0b13a43f595c5b9bae7b9a8146b7ccb2b8308d
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2703851"
---
# <a name="add-and-configure-a-quick-view-component-on-a-form"></a>在窗体中添加和配置快速视图组件  
显示记录详细信息的主窗体可使用快速视图组件显示相关记录（查找）的只读详细信息。 快速视图组件显示的数据由相关实体的快速视图窗格定义。 如果没有相关记录（如查找），将自动隐藏快速视图组件。

## <a name="add-a-quick-view-component"></a>添加快速视图组件
可按照添加其他任何组件的相同方法添加快速视图组件。 详细信息：[在窗体中添加、配置、移动或删除组件](add-move-configure-or-delete-components-on-form.md)

## <a name="configure-a-quick-view-component"></a>配置快速视图组件
使用窗体中的快速视图组件时，可使用窗体设计器配置一些属性。


<!--note from editor: "Drop-down" should be used only as an adjective. In the following table, is it a list? A menu? (It's used three times in line 44.) --> 


|面积图   |姓名  |说明  |
|---------|---------|---------|
|**显示选项** | **标签** | 可本地化的快速视图标签，向用户显示。 <br /><br /> 该属性是必需的。 |
| **显示选项** | **姓名** |  选项卡的唯一名称，在脚本中引用快速视图时使用该名称。 该名称只能包含字母数字字符和下划线。 <br /> <br />该属性是必需的。 |
| **显示选项**  | **隐藏标签** |  选择后，快速视图标签将隐藏。 |
| **显示选项**  | **快速视图窗体** |  向应用程序用户显示的快速视图窗格的列表。 <br /><br />若要配置快速视图窗体列表 <br /><br /> 选择**选择窗体 ...**，然后在**查找**下拉列表中选择要在其中显示快速视图窗体的查找字段。 <br /><br />您将看到可用于为一个或多个实体选择快速视图窗格的下拉列表，具体取决于您在**查找**下拉列表中选择的查找字段。 |

## <a name="see-also"></a>另请参阅
[模型驱动的窗体设计器概述](form-designer-overview.md)  
[使用窗体设计器创建、编辑或配置窗体](create-and-edit-forms.md)  
[添加、配置、移动或删除窗体中的字段](add-move-or-delete-fields-on-form.md)  
[添加、配置、移动或删除窗体中的组件](add-move-configure-or-delete-components-on-form.md)  
[添加、配置、移动或删除窗体中的分区](add-move-or-delete-sections-on-form.md)  
[添加、配置、移动或删除窗体中的选项卡](add-move-or-delete-tabs-on-form.md)  
[在窗体设计器中配置页眉属性](form-designer-header-properties.md)  
[在窗体中添加和配置子网格组件](form-designer-add-configure-subgrid.md)  
[在窗体中配置查找组件](form-designer-add-configure-lookup.md)  
[在窗体设计器中使用树视图](using-tree-view-on-form.md)  
[创建和编辑字段](../common-data-service/create-edit-field-portal.md)  
