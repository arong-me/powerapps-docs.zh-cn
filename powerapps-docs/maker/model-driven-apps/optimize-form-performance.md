---
title: 在 PowerApps 中优化模型驱动应用窗体的性能 | MicrosoftDocs
description: 了解如何避免导致窗体加载缓慢的窗体设计
ms.custom: ''
ms.date: 06/27/2018
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
ms.assetid: 59cfa5e6-638a-437f-a462-fddfd26fb07d
caps.latest.revision: 8
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: b777dc346897f87d710edc309b9e9a7eda1b711b
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2711595"
---
# <a name="optimize-model-driven-app-form-performance"></a>优化模型驱动应用程序窗体的性能

加载速度慢的窗体可能会降低工作效率和用户的认可度。 请根据以下建议来充分提高窗体的加载速度。 其中的许多建议涉及开发人员如何实施组织的窗体脚本。 请务必与为窗体创建窗体脚本的开发人员讨论这些建议。  
  
<a name="BKMK_FormDesign"></a>   
## <a name="form-design"></a>窗体设计  
 考虑用户将与窗体进行的交互以及必须在窗体中显示的数据量。  
  
 **将字段数量保持在最低**  
 窗体中的字段越多，查看每个记录时要通过 Internet 或 Intranet 传输的数据也越多。  
  
<a name="BKMK_FormScripts"></a>   
## <a name="form-scripts"></a>窗体脚本  
 如果您有使用窗体脚本的自定义项，请确保开发人员了解这些策略以提高性能。  
  
 **避免包含不必要的 JavaScript Web 资源库**  
 向窗体中添加的脚本越多，用于下载脚本的时间也会越多。 通常，脚本首次下载后会缓存在浏览器中，但首次查看窗体时的性能通常会形成重要的印象。  
  
 **避免在 Onload 事件中加载所有脚本**  
 如果您有仅支持字段的 `OnSave` 事件或 `OnChange` 事件的代码，请确保使用事件处理程序为这些事件（而不是 `OnLoad` 事件）设置脚本库。 这样可以推迟加载这些库，从而提高窗体加载时的性能。  
  
 **使用折叠选项卡来推迟加载 Web 资源**  
 当折叠的选项卡中的分区中包括了 Web 资源或 IFRAME 时，在选项卡折叠的情况下不会加载它们。 它们会在选项卡展开时加载。 当选项卡状态发生变化时，会发生 `TabStateChange` 事件。 支持折叠的选项卡中的 Web 资源或 IFRAME 所需的任何代码都可以使用 **TabStateChange** 事件的事件处理程序，从而减少本来必须在 `OnLoad` 事件中发生的代码。  
  
 **设置默认可见性选项**  
 避免在隐藏窗体元素的 `OnLoad` 事件中使用窗体脚本。 请为可能隐藏的窗体元素设置默认可见性选项，以便在加载窗体时使其默认不可见。 然后，在 `OnLoad` 事件中使用脚本来显示您希望显示的窗体元素。  
  
<a name="BKMK_CommandBar"></a>   
## <a name="command-bar-or-ribbon"></a>命令栏或功能区  
 在编辑命令栏或功能区时，请记住以下建议。  
  
 **将控件数量保持在最低**  
 在窗体的命令栏或功能区内，评估必要的控件，隐藏您不需要的控件。 显示的每个控件会增加需要下载到浏览器的资源。  
  
## <a name="next-steps"></a>后续步骤  
 [创建和设计窗体](create-design-forms.md)    
    
 
