---
title: 在 PowerApps 中设置仪表板包括的模型驱动应用图表或列表的属性 | MicrosoftDocs
description: 了解如何设置仪表板包括的图表或列表的属性
ms.custom: ''
ms.date: 06/06/2018
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: 50fb2ab0-5c1a-4a5e-8ebc-5603fecc4da0
caps.latest.revision: 26
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b284b42c162c44d59fc7af22905be08748d9c766
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711155"
---
# <a name="set-properties-for-a-model-driven-app-chart-or-list-included-in-a-dashboard"></a>设置仪表板包括的模型驱动应用程序图表或列表的属性

若要从仪表板设计器编辑图表或列表组件，选择所需图标或列表，然后在仪表板设计器工具栏上选择“编辑组件”。   
  > [!div class="mx-imgBorder"] 
  > ![仪表板设计器图表编辑组件](media/dashboard-chart-select.png)

此时将打开**设置属性**对话框。

  > [!div class="mx-imgBorder"] 
  > ![图表设置属性](media/set-properties-chart.png)  
 
可以设置从**设置属性**对话框设置以下图表属性：  
  
- **名称**. 图表的唯一名称。 系统会建议一个值，但是，您可以改变该值。  
  
- **标签**。 显示在图表顶部的标签。  
  
- **在仪表板上显示标签**。 选择或清除此复选框可以查看或隐藏图表标签。  
  
- **实体**。 选择实体（记录类型）基于的图表。 此设置将确定默认视图和默认图表属性的可用值。  
  
- **默认视图**。 选择将用于检索图表数据的视图。  
  
- **默认图表**。 选择首次打开仪表板时要显示的默认图表。 为实体属性设置的值决定提供的值。 此属性与显示图表选择属性同时使用。 如果**显示图表选择**选项打开，用户可以更改图表的类型，但是在下次打开仪表板时，图表将还原为默认图表。  
  
- **仅显示图表**。 如果希望显示该图表，请选中此复选框。 如果您要显示图表及其关联的数据，请清除此复选框。  
  
- **显示图表选择**。 选择该复选框时使用户能在使用仪表板时更改图表类型（列、条形图、饼图等）。 如果用户更改图表类型，设置将不会保存。 当仪表板关闭时，图表类型还原为默认图表设置。  
  
可以设置从**设置属性**对话框设置以下列表属性：  
  
- **名称**. 列表的唯一名称。 系统会建议一个值，但是，您可以改变该值。  
  
- **标签**。 显示在列表顶部的标签。  
  
- **在仪表板上显示标签**。 选择或清除此复选框可以查看或隐藏列表标签。  
  
- **实体**。 选择实体（记录类型）基于的列表。 此设置将确定默认视图属性的可用值。  
  
- **默认视图**。 选择用于检索列表中的数据的视图。 用户可以更改视图，但是下次打开仪表板时，列表会还原为默认视图。  
  
- **显示搜索框**。 如果希望在列表顶部显示搜索框，请选中此复选框。 如果已包含搜索框，您或其他用户可以在运行时搜索列表查找记录。  
  
- **显示索引**。 如果希望在列表底部显示 A 到 Z 筛选器，请选中此复选框。 当 A 到 Z 筛选器显示时，您或其他用户可以选择相应字母就可以跳转到以该字母开头的记录。  
  
- **视图选择器**。 可从以下值中选择：  
  
    - **禁用**。 不想显示视图选择器。 您或其他用户将无法在运行时更改视图。  
  
    - **显示所有视图**。 提供与在实体属性中设置的值相关的完整视图列表。  
  
    - **显示选定视图**。 选择此设置可以限制在运行时可用的视图列表。 要选择要显示的特定视图，按住 Ctrl 键并点按或者选择要包括的每个视图。  
 
## <a name="next-steps"></a>后续步骤  
 [创建或自定义仪表板](create-edit-dashboards.md)
