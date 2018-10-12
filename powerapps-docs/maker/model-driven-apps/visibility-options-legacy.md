---
title: 使用 PowerApps 显示或隐藏模型驱动应用窗体元素 | MicrosoftDocs
description: 了解如何显示或隐藏窗体元素，如选项卡、节或字段
ms.custom: ''
ms.date: 06/11/2018
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
ms.assetid: 7b9e8dc2-229c-455f-ae18-49e8d879ff71
caps.latest.revision: 63
ms.author: matp
manager: kvivek
ms.openlocfilehash: 86fafe70ae3bc04eff5e85a4baf3682c32427149
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669490"
---
# <a name="show-or-hide-model-driven-app-form-elements"></a>显示或隐藏模型驱动应用窗体元素

 默认情况下，可以选择显示或隐藏多种类型的窗体元素。 选项卡、节、字段、iFrame 和 Web 资源都提供此选项。 使用窗体脚本或业务规则可以控制这些元素的可见性，以创建动态窗体，提供适应窗体条件的用户界面。  
  
> [!NOTE]
>  不推荐隐藏窗体元素来强制执行安全性。 元素处于隐藏状态时，用户可通过多种方式查看窗体中的所有元素和数据。 
  
 与其设计依赖于脚本来控制选项可见性的窗体，更应该考虑业务流程、对话或切换到不同窗体是否能更好地满足要求。 如果确实要使用脚本，请确保默认情况下可以隐藏的任何元素均处于隐藏状态。 仅在逻辑需要调用它时使用脚本显示。 这样，元素就不会在不支持脚本的演示中显示。  

## <a name="next-steps"></a>后续步骤

[窗体编辑器界面概述](form-editor-user-interface-legacy.md)