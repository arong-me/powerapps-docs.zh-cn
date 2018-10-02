---
title: PowerApps 中模型驱动应用程序窗体的选项卡属性 | MicrosoftDocs
description: 了解主窗体的选项卡属性
Keywords: Tab properties; Dynamics 365; Main forms
author: matp
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - powerapps
ms.author: Mattp123
manager: kvivek
ms.date: 06/07/2018
ms.service: crm-online
ms.topic: article
ms.assetid: e0790865-c5a4-4e86-bce2-584af2b8ed93
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="tab-properties-for-model-driven-app-forms-overview"></a>模型驱动应用程序窗体的选项卡属性概述

 在窗体的主体中，选项卡提供水平分隔。 选项卡有一个可显示的标签。 如果显示了标签，则可通过选择标签来展开或折叠选项卡，以显示或隐藏其内容。  
  
 选项卡最多包含三栏，每栏的宽度可设置为总宽度的百分比。 创建新选项卡时，每个栏会预填充一个分区。  

您可以从 PowerApps 站点访问**选项卡属性**。 
1.  在 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 站点，选择**模型驱动**（导航窗格的右下方）。  

     ![模型驱动设计模式](media/model-driven-switch.png)

2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。  

3.  在窗体列表中，打开**主**类型的窗体。 然后在窗体区域的选项卡之一内双击以查看选项卡属性。

    ![选项卡属性](media/tab-properties.png)
  
 下表显示了可为窗体中的选项卡设置的属性：
  
|Tab|属性|说明|  
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
  
## <a name="next-steps"></a>后续步骤

[使用“主”窗体及其组件](use-main-form-and-components.md)
