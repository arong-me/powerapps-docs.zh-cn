---
title: Power Apps 中模型驱动应用窗体的选项卡属性 | MicrosoftDocs
description: 了解主窗体的选项卡属性
Keywords: 选项卡属性; Dynamics 365; 主窗体
author: matp
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: Mattp123
manager: kvivek
ms.date: 03/17/2020
ms.service: powerapps
ms.topic: article
ms.assetid: e0790865-c5a4-4e86-bce2-584af2b8ed93
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 613352e9ec86101b776fce5b0bf18d64b175f363
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "3166518"
---
# <a name="tab-properties-for-model-driven-app-forms-overview"></a>模型驱动应用程序窗体的选项卡属性概述

 在窗体的主体中，选项卡提供水平分隔。 选项卡有一个可显示的标签。 如果显示了标签，则可通过选择标签来展开或折叠选项卡，以显示或隐藏其内容。  
  
 选项卡最多包含三栏，每栏的宽度可设置为总宽度的百分比。 创建新选项卡时，每个栏会预填充一个分区。  

您可以从 Power Apps 站点访问**选项卡属性**。 
1.  登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。  

3.  在窗体列表中，打开**主**类型的窗体。 然后选择窗体上的其中一个选项卡查看选项卡属性。

|属性|说明|  
|--------------|-----------------|  
|**选项卡标签**|**必需**：可本地化的选项卡标签，向用户显示。|  
|**名称**|**必需**：选项卡的唯一名称，在脚本中引用选项卡时使用该名称。 该名称只能包含字母数字字符和下划线。|  
|**默认情况下展开此选项卡**|可以使用窗体脚本或者由选择标签的用户来切换选项卡的展开或折叠状态。 选择选项卡的默认状态。|  
|**隐藏选项卡**|是否显示选项卡是可选的，并可使用脚本来控制。 选择是否让选项卡显示。 详细信息：[可见性选项](visibility-options-legacy.md)|  
|**在电话上隐藏**|选择您是否希望在电话上提供此选项卡。 对于电话屏幕上的此窗体的浓缩版，可以隐藏选项卡。|  
|**格式设置**|选项卡最多可以有三栏。 使用这些选项可以设置选项卡的数量，以及它们应填充的总宽度百分比。|  

  > [!div class="mx-imgBorder"] 
  > ![选项卡属性](media/newform-tab-properties.png "选项卡属性")

## <a name="tab-properties-for-model-driven-app-main-forms-classic"></a>模型驱动应用主窗体的选项卡属性：经典

使用窗体上的选项卡时，可使用经典窗体设计器配置一些属性。 下表显示了可为窗体中的选项卡设置的属性：
  
|选项卡|属性|说明|  
|---------|--------------|-----------------|  
|**显示器**|**名称**|**必需**：选项卡的唯一名称，在脚本中引用选项卡时使用该名称。 该名称只能包含字母数字字符和下划线。|  
||**标签**|**必需**：可本地化的选项卡标签，向用户显示。|  
||**在窗体上显示此选项卡的标签**|如果显示了标签，用户可以选择标签来切换选项卡的展开或折叠状态。 选择是否要显示标签。|  
||**默认情况下展开此选项卡**|可以使用窗体脚本或者由选择标签的用户来切换选项卡的展开或折叠状态。 选择选项卡的默认状态。|  
||**默认情况下可见**|是否显示选项卡是可选的，并可使用脚本来控制。 选择是否让选项卡显示。 详细信息：[可见性选项](visibility-options-legacy.md)|  
||**可用性**|选择您是否希望在电话上提供此选项卡。|  
|**格式设置**|**布局**|选项卡最多可以有三栏。 使用这些选项可以设置选项卡的数量，以及它们应填充的总宽度百分比。|  
|**事件**|**窗体库**|指定将在选项卡 `TabStateChange` 事件处理程序中使用的任何 JavaScript Web 资源。<br /><br />|  
||**事件处理程序**|配置应为选项卡 `TabStateChange` 事件调用的库中的函数。 详细信息：[配置事件处理程序](configure-event-handlers-legacy.md)|  

  > [!div class="mx-imgBorder"] 
  > ![选项卡属性经典](media/tab-properties.png "“经典”中选项卡属性")

## <a name="next-steps"></a>后续步骤

[使用“主”窗体及其组件](use-main-form-and-components.md)
