---
title: 在 PowerApps 中优化模型驱动应用窗体的性能 | Microsoft Docs
description: 了解如何避免导致窗体加载缓慢的窗体设计
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: 59cfa5e6-638a-437f-a462-fddfd26fb07d
caps.latest.revision: 8
ms.author: matp
manager: kvivek
ms.openlocfilehash: c9dd764fe565b59e68411dabf453207c4e01a320
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667779"
---
# <a name="optimize-model-driven-app-form-performance"></a>优化模型驱动应用窗体的性能

窗体加载缓慢会降低工作效率和用户采用率。 请遵循本文中的建议，最大限度地提高窗体的加载速度。 其中，许多建议是关于开发人员如何为组织实现窗体脚本的。 请务必与为窗体创建窗体脚本的开发人员讨论这些建议。  
  
<a name="BKMK_FormDesign"></a>   
## <a name="form-design"></a>窗体设计  
 考虑用户与窗体的交互以及必须在其中显示的数据量。  
  
 **保持最少字段数**  
 窗体中字段越多，为查看每条记录而需要通过 Internet 或 Intranet 传输的数据就越多。  
  
<a name="BKMK_FormScripts"></a>   
## <a name="form-scripts"></a>窗体脚本  
 使用窗体脚本进行自定义时，请确保开发人员了解这些策略以提高性能。  
  
 **避免包含不必要的 JavaScript Web 资源库**  
 添加到窗体的脚本越多，下载脚本所需的时间就越长。 通常第一次加载脚本后它会缓存在浏览器中，而第一次查看窗体时的性能往往会给人留下深刻印象。  
  
 **避免在 Onload 事件中加载所有脚本**  
 如果代码仅支持字段的 `OnChange` 事件或 `OnSave` 事件，请确保使用事件处理程序为这些事件（除 `OnLoad` 事件）设置脚本库。 这样即可延迟加载这些库，从而在加载窗体时提高性能。  
  
 **使用折叠选项卡延迟加载 Web 资源**  
 当 Web 资源或 IFRAME 包含在折叠选项卡内的部分中时，如果选项卡已折叠，则不会加载它们。 展开选项卡时将加载它们。 选项卡状态更改时，发生 `TabStateChange` 事件。 要求支持折叠选项卡中 Web 资源或 IFRAME 的任何代码均可为 TabStateChange 事件使用事件处理程序，并减少在 `OnLoad` 事件中可能必须使用的代码。  
  
 **设置默认可见性选项**  
 避免在隐藏窗体元素的 `OnLoad` 事件中使用窗体脚本。 而将可能隐藏的窗体元素的默认可见性选项设置为加载窗体时默认不可见。 然后，使用 `OnLoad` 事件中的脚本来显示要显示的窗体元素。  
  
<a name="BKMK_CommandBar"></a>   
## <a name="command-bar-or-ribbon"></a>命令栏或功能区  
 编辑命令栏或功能区时，请记住这些建议。  
  
 **保持最少控件数**  
 在命令栏或窗体的功能区中，评估必须显示的控件并隐藏任何不需要的控件。 显示的每个控件都会增加需下载到浏览器的资源。  
  
## <a name="next-steps"></a>后续步骤  
 [创建并设计窗体](create-design-forms.md)    
    
 
