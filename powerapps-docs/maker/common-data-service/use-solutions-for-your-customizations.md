---
title: 通过 Power Apps 使用默认解决方案自定义 | MicrosoftDocs
description: 了解如何自定义默认解决方案
ms.custom: ''
ms.date: 02/20/2020
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
ms.assetid: f993c4ed-1fc3-4e47-bef1-d38695ddb11a
caps.latest.revision: 57
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1525cdb41cb7e809a54b6389472e5be842a87697
ms.sourcegitcommit: d98dd90a7dda11f434a13a7f8976459856d6142b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/29/2020
ms.locfileid: "3093607"
---
# <a name="use-a-solution-to-customize"></a>使用解决方案进行自定义
我们建议您创建一个解决方案来管理您的自定义。 使用自定义解决方案，您可以轻松地找到已自定义的解决方案组件，一致地使用解决方案发布商前缀，并将解决方案导出以分发到其他环境。  

如果不使用自定义解决方案，您将使用非托管层中的默认解决方案。 每个 Common Data Service 环境中都有两个默认解决方案：  
- Common Data Service 默认解决方案。 这是一个基本解决方案，默认供制造者在环境中用来进行自定义。 当您要评估或学习 Power Apps 时，Common Data Service 默认解决方案很有用。  
- 默认解决方案。 这是一个专用解决方案，包含系统中的所有组件。 默认解决方案可用于发现系统中的所有组件和配置。  

## <a name="why-you-shouldnt-use-the-default-solutions-to-manage-customizations"></a>为什么不应该使用默认解决方案来管理自定义
有几个原因使您不应该在两种默认解决方案中创建应用和进行自定义：  
- 默认解决方案包含环境中所有解决方案的所有组件和自定义项。 
- 默认情况下，环境中所有启用的用户都可以在 Common Data Services 默认解决方案中创建应用并自定义组件。 
- 使用哪一个默认解决方案都很难找到或发现您在环境中进行的自定义。 
- 无论使用哪个默认解决方案，在创建组件时都还要使用分配给它的默认发布商。 这可能会导致将错误的发布商前缀应用于某些组件。 
- 默认解决方案无法导出。 因此，您无法将默认解决方案分发给其他环境。 

<!-- Notice that if you have installed or imported other applications or solutions, additional solutions may be available in the solutions list. 

By default,  when you build or customize a model-driven app, you work with the solution called Common Data Services Default Solution. You can open the Common Data Services Default Solution to view and edit the components that are contained in it. To do this, follow these steps.
 
1.  On the left navigation pane select **Solutions**.

2.  In the list of solutions, select **Common Data Services Default Solution**.
  
> [!TIP]
>  If you plan to distribute the applications your make, consider changing the publisher customization prefix. More information: [Solution publisher prefix](change-solution-publisher-prefix.md).  -->
  
<a name="BKMK_PrivacyNotice"></a>   

## <a name="privacy-notices"></a>隐私声明  
 [!INCLUDE[cc_privacy_crm_gcc_solution_import](../../includes/cc-privacy-crm-gcc-solution-import.md)]  
  
 [!INCLUDE[cc_privacy_crm_customizations](../../includes/cc-privacy-crm-customizations.md)]  
  
### <a name="see-also"></a>另请参阅  
[创建解决方案](create-solution.md) <br />
[了解模型驱动的应用程序组件](../model-driven-apps/model-driven-app-components.md)


