---
title: PowerApps 中模型驱动的应用计时器控件 | Microsoft Docs
description: 了解如何使用计时器控件
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
ms.assetid: b2b64771-083b-42f9-a3d5-2218f9d8a713
caps.latest.revision: 63
ms.author: matp
manager: kvivek
ms.openlocfilehash: 7df13482e7773abc3e6762f80bd9f6b99c7ba9e6
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667900"
---
# <a name="model-driven-app-timer-control-overview"></a>模型驱动的应用计时器控件概述

 使用带有窗体的计时器控件，且窗体中的记录需要满足特定的基于时间的里程碑。 计时器控件显示在活动记录的解析中完成操作可用的时间，或自完成操作开始过去了多长时间。 计时器控件必须至少配置为显示操作完成成功或失败。 此外，还可将它们配置为在情况接近失败时显示警告。  
  
 可将计时器控件添加到任何实体的窗体中，但它们最常用于案例实体，尤其是在链接到跟踪服务级别协议的字段时。 可在窗体的正文中添加多个计时器控件。 不能将它们添加到页眉或页脚。  
  
 计时器控件“数据源”属性使用实体的字段。  
  
-   “失败时间字段”使用日期-时间字段来设置时间。  
  
-   这三个条件字段使用实体的“选项集”、“两个选项”、“状态”或“状态原因”字段之一。  

要创建计时器控件，在窗体设计器中，选择“插入”选项卡，然后在工具栏上选择“计时器”。 

  ![插入计时器控件](media/insert-timer-control.png)

在“计时器控件”属性页上，输入或选择所需属性，然后选择“确定”。 

  
<a name="BKMK_TimerControlProperties"></a>   

## <a name="timer-control-properties"></a>计时器控件属性  
 下表介绍了计时器控件的属性。  
  
|组|名称|描述|  
|-----------|----------|-----------------|  
|名称|名称|必填。 控件的唯一名称。|  
||标签|必填。 要为计时器控件显示的标签。|  
|数据源|失败时间字段|必填。 选择实体的某个日期-时间字段，以表示应成功完成里程碑的时间。|  
||成功条件|必填。 为实体选择一个字段，以评估里程碑的成功，然后选择指示成功的选项。|  
||警告条件|为实体选择一个字段，以评估里程碑的成功是否存在风险，以便显示警告，然后选择指示应显示警告的选项。|  
||取消条件|为实体选择一个字段，以评估是否应取消里程碑的实现，然后选择指示已取消里程碑的选项。|  

## <a name="next-steps"></a>后续步骤

[窗体编辑器用户界面概述](form-editor-user-interface-legacy.md)