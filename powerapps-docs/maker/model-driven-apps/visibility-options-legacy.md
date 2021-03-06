---
title: 使用 Power Apps 显示或隐藏模型驱动应用程序窗体元素 | MicrosoftDocs
description: 了解如何从元素（如选项卡、区段或字段）中显示或隐藏
ms.custom: ''
ms.date: 06/11/2018
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
ms.assetid: 7b9e8dc2-229c-455f-ae18-49e8d879ff71
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 54a2aeed489cf3e3621bcf21f5f6e0f12b15deff
ms.sourcegitcommit: 2d21c2c65875f97dff6d5843611d4221a4282f22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/05/2020
ms.locfileid: "3027574"
---
# <a name="show-or-hide-model-driven-app-form-elements"></a>显示或隐藏模型驱动应用程序窗体元素

 多种窗体元素类型有默认显示或隐藏的选项。 选项卡、分区、字段、iFrame 和 Web 资源都提供了此选项。 通过使用窗体脚本或业务规则，可以控制这些元素的可见性来创建动态窗体，从而提供适应窗体中条件的用户界面。  
  
> [!NOTE]
>  建议不要通过隐藏窗体来加强安全性。 隐藏元素时，用户可通过多种方式查看窗体中的所有元素和数据。 
  
 与其设计依赖脚本来控制选项可见性的窗体，不如考虑业务流程、对话框或者切换到不同窗体是否可能更适合满足您的要求。 如果使用脚本，请确保可能隐藏的任一元素是否默认为隐藏状态。 仅在您的逻辑需要时才使用脚本显示隐藏元素。 这样，就不会在不支持脚本的显示方式中显示隐藏元素。
 
 > [!NOTE]
> 在统一接口中，对于其中的字段未跨越多列的部分，隐藏该部分中的一个字段将把下面的字段在窗体中向上移动。 如果某个字段在一个部分中跨越两列以上，则隐藏该部分中具有控件的字段不会将下面的字段在窗体中向上移动。 您将在该部分中隐藏的字段所在位置看到更多空白。

## <a name="next-steps"></a>后续步骤

[窗体编辑器界面概述](form-editor-user-interface-legacy.md)
