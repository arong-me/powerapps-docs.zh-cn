---
title: 为 PowerApps 仪表板中包含的模型驱动应用图表或列表设置属性 | MicrosoftDocs
description: 了解如何为仪表板中包含的图表或列表设置属性
ms.custom: ''
ms.date: 06/06/2018
ms.reviewer: ''
ms.service: crm-online
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
ms.openlocfilehash: c88fef0412060516ef448c89f5ddfdc9cad00e20
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669053"
---
# <a name="set-properties-for-a-model-driven-app-chart-or-list-included-in-a-dashboard"></a>为仪表板中包含的模型驱动应用图表或列表设置属性

若要从仪表板设计器编辑图表或列表组件，请选择所需图表或列表，然后选择“仪表板设计器”工具栏上的“编辑组件”。   

  ![仪表板设计器图表编辑组件](media/dashboard-chart-select.png)

此操作会打开“设置属性”对话框。

  ![图表设置属性](media/set-properties-chart.png)  
 
可以从“设置属性”对话框设置以下图表属性：  
  
- 名称。 图表的唯一名称。 系统会建议一个值，但可以更改。  
  
- 标签。 图表顶部显示的标签。  
  
- 在仪表板上显示标签。 选中或清除此复选框可显示或隐藏图表标签。  
  
- 实体。 选择图表所基于的实体（记录类型）。 此设置确定“默认视图”和“默认图表”属性的可用值。  
  
- 默认视图。 选择用于检索图表数据的视图。  
  
- 默认图表。 选择首次打开仪表板时要显示的默认图表。 可用值由为“实体”属性设置的值决定。 此属性与“显示图表选择”属性一起使用。 如果已启用“显示图表选择”选项，则用户可更改图表类型，但在下次打开仪表板时图表会还原为默认图表。  
  
- 仅显示图表。 如果仅希望显示图表，请选中此复选框。 如果希望显示图表及其关联数据，请清除此复选框。  
  
- 显示图表选择。 选中此复选框，可使用户在使用仪表板时能够更改图表类型（柱状图、条形图、饼状图等）。 如果用户更改图表类型，系统不会保存设置。 关闭仪表板时，图表类型会还原为“默认图表”设置。  
  
可以从“设置属性”对话框设置以下列表属性：  
  
- 名称。 列表的唯一名称。 系统会建议一个值，但可以更改。  
  
- 标签。 列表顶部显示的标签。  
  
- 在仪表板上显示标签。 选中或清除此复选框可显示或隐藏列表标签。  
  
- 实体。 选择列表所基于的实体（记录类型）。 此设置确定“默认视图”属性的可用值。  
  
- 默认视图。 选择用于检索列表中数据的视图。 用户可以更改视图，但在下次打开仪表板时列表将还原为默认视图。  
  
- 显示搜索框。 如果希望在列表顶部显示搜索框，请选中此复选框。 如果已包含搜索框，那么你或其他用户可在运行时搜索列表中的记录。  
  
- 显示索引。 如果希望在列表底部显示 A 到 Z 筛选器，请选中此复选框。 显示 A 到 Z 筛选器后，你或其他用户便可选择某个字母，跳转到以该字母开头的记录。  
  
- 视图选择器。 从下列值中选择:  
  
    - 关闭。 不显示视图选择器。 你或其他用户无法在运行时更改视图。  
  
    - 显示所有视图。 提供与实体属性中设置的值关联的视图的完整列表。  
  
    - 显示所选视图。 选择此设置可限制运行时可用视图列表。 若要选择显示特定视图，请按住 Ctrl 键并点击或选择想要包括的每个视图。  
 
## <a name="next-steps"></a>后续步骤  
 [创建或自定义仪表板](create-edit-dashboards.md)
