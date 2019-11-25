---
title: PowerApps 中模型驱动应用的计时器控件 | MicrosoftDocs
description: 了解您如何使用计时器控件
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
ms.assetid: b2b64771-083b-42f9-a3d5-2218f9d8a713
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 31b7f2b55f10e404841517aada26b0b38df7fbbf
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2710803"
---
# <a name="model-driven-app-timer-control-overview"></a>模型驱动应用程序的计时器控件概述

 计时器控件用于实现特定基于时间的里程碑所需记录的窗体。 计时器控件显示用户在可用户记录中完成一个操作所用的时间，或显示完成该操作已经过去了多长时间。 至少，在完成操作中计时器控件需配置为显示成功或失败。 此外，当条件正在接近失败时，可将它们配置为显示警告。  
  
 计时器控件可以添加到所有实体窗体，但是其通常应用于案例实体，特别是当链接到跟踪服务级别协议的字段。 您可以在窗体的主体中添加多个计时器控件。 您不可以将它们添加到页眉或页脚。  
  
 计时器控制**数据源**属性使用实体字段。  
  
-   **失败时间字段**使用日期-时间字段设置时间。  
  
-   三个条件字段使用为实体使用**选项集**、**两个选项**、**状态**或**状态描述**字段之一。  

若要创建计时器控件，在窗体设计器中，选择**插入**选项卡，然后在工具栏上选择**计时器**。 

  > [!div class="mx-imgBorder"] 
  > ![插入计时器控件](media/insert-timer-control.png)

在计时器控件属性页上，输入或选择所需属性，然后选择**确定**。 

  
<a name="BKMK_TimerControlProperties"></a>   

## <a name="timer-control-properties"></a>时间控件属性  
 下表介绍了时间控件的属性。  
  
|组|客户|说明|  
|-----------|----------|-----------------|  
|客户|客户|**必需**。 控件的唯一名称。|  
||标签|**必需**。 显示计时器控件的标签。|  
|数据源|失败时间字段|**必需**。 为实体选择一个日期-时间字段显示何时应会成功完成里程碑。|  
||成功条件|**必需**。 为实体选择字段来估算里程碑的成功率，然后选择指示成功选项。|  
||警告条件|为实体选择字段来评估里程碑的成功是否存在风险，以便应显示警告，然后选择指示应显示警告的选项。|  
||取消条件|为实体选择字段来评估是否应删除里程碑的成绩，然后选择指示里程碑被删除的选项。|  

## <a name="next-steps"></a>后续步骤

[窗体编辑器用户界面概述](form-editor-user-interface-legacy.md)
