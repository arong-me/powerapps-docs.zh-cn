---
title: 在 PowerApps 中控制对模型驱动应用窗体的访问 | MicrosoftDocs
description: 了解如何控制对主窗体的访问
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
ms.assetid: 15d123e0-b604-45dd-ab34-0b37787a04bb
caps.latest.revision: 33
ms.author: matp
manager: kvivek
tags: ''
ms.openlocfilehash: a895bd9ea0257585f942840924a7044a4dcc23fb
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667914"
---
# <a name="control-access-to-model-driven-app-forms"></a>控制对模型驱动应用窗体的访问

 可通过两种方法控制对主窗体的访问：  
  
- **使主窗体处于非活动状态**  
  
     可将主窗体设置为活动或非活动状态。 此功能主要用于管理 Dynamics 365 Customer Engagement 组织升级时所包含的新窗体，但还可用于阻止用户使用任何主窗体。   
  
- **为主窗体分配安全角色**  
  
     使用此方法可使主窗体供特定组使用。  
  
 组织中的不同人员可能以不同的方式与相同数据进行交互。 管理人员可能需要能够快速扫描记录中的信息，服务人员可能需要可简化数据输入的窗体。 可通过将窗体分配给不同人群组所属的安全角色来满足不同需求。  
  
 有关分步过程，请参阅[将安全角色分配给窗体](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)。  
  
 如果为实体定义了多个主窗体或移动窗体，则可根据用户的安全角色选择其可使用的窗体。 由于每个实体必须可为任何用户显示窗体，因此必须至少将一个窗体指定为“回退”窗体 - 一种对特定用户可见的窗体，这些用户的安全角色未显示分配到任何窗体。  
  
> [!NOTE]
>  不能将“快速创建”和“快速查看”窗体分配给安全角色。  
  
 可在窗体编辑器或窗体网格中将安全角色分配给窗体。 但是，如果实体只有一个窗体，则无法在“分配安全角色”对话框中清除“启用回退”选项。 在这种情况下，即使已为窗体分配了安全角色，与你不具有的安全角色相关联的任何人将仍可查看该窗体，因为该窗体已启用回退。  
  
 为实体创建第二个主窗体或移动窗体后，将可清除其中一个实体的“启用回退”选项。 系统将始终确保至少有一个窗体启用了回退。  
  
 有多个主窗体时，可指定窗体顺序，用于控制允许他人查看的窗体中的哪个窗体将是默认情况下看到的窗体。 如果这些人员可使用多个窗体，则他们将可以更改窗体，并且其所选窗体将是其默认窗体，直到他们选择其他窗体。 此首选项存储在其浏览器中。 使用其他计算机或浏览器时，他们将看到原始默认窗体。  
  
## <a name="strategies-to-manage-the-fallback-form"></a>管理回退窗体的策略  
 管理回退窗体的策略如下：  
  
<a name="BKMK_DoNotUseMultipleForms"></a>   
### <a name="all-users-view-the-same-form"></a>所有用户都查看同一窗体  
 如果不需要一个实体具有多个窗体，则无需回退窗体。  
  
<a name="BKMK_Contingecyform"></a>   
### <a name="create-a-contingency-form"></a>创建应变窗体  
 如果因为想限制人们可能查看或编辑的信息而使用基于角色的窗体，请考虑创建显示最少信息的窗体。 然后，在“分配安全角色”对话框中，选择“仅向所选安全角色显示”，但不要选择“系统管理员”之外的任何角色，然后选择“启用回退”。 这样，除了系统管理员和其安全角色未与特定窗体关联的人员，其他任何人都绝不会看到此窗体。 可在窗体中包含 HTML Web 资源，其中包含有关窗体中可见信息极少的原因的信息，以及关于如何请求添加到与窗体关联的安全角色或如何包含窗体新安全角色的信息的链接。  
  
> [!NOTE]
>  不能在窗体页眉或页脚中包含 Web 资源。  
  
<a name="BKMK_CreateGenericForm"></a>   
## <a name="create-a-generic-form"></a>创建泛型窗体  
 如果使用基于角色的窗体来根据用户角色提供自定义体验，可将最不具针对性的窗体设置为回退窗体，并将其配置为向每个人显示。 然后，为特定安全角色创建自定义窗体，并将这些窗体配置为仅向需要它们的安全角色显示。 请勿对这些窗体启用回退。 最后，在“窗体”列表中，使用“窗体顺序”对话框指定要显示哪些窗体，将它们从最具排他性到最不具排他性进行排序。 回退窗体将位于列表底部。 此策略将使人们看到已为其角色自定义的窗体（作为默认窗体），但他们仍可使用窗体选择器选择最常用的窗体（如果需要）。 无论他们选择何种窗体，该窗体都将成为默认窗体，直到他们选择其他窗体。  
  
<a name="BKMK_UseFormScripting"></a>   
## <a name="use-form-scripting"></a>使用窗体脚本  

 最后，在 Web 应用程序中，开发人员可以（但不推荐）通过使用 Onload 事件窗体中的脚本来使用 [Xrm.Page.ui.formSelector.items 集合](http://go.microsoft.com/fwlink/p/?LinkID=513300)查询可用窗体，以及使用导航方法来将用户定向到特定窗体。 请记住，[导航方法](http://go.microsoft.com/fwlink/p/?LinkID=513301)将导致窗体再次加载（并再次发生 Onload 事件）。 使用导航方法之前，事件处理程序中的逻辑应始终检查某些条件，以避免无限循环或对用于在窗体之间导航的用户选项进行不必要的限制。  
  
 此方法不适用于平板电脑上的 Dynamics 365，因为无法选择多种窗体。  

### <a name="next-steps"></a>后续步骤  

[为窗体分配安全角色](https://docs.microsoft.com/dynamics365/customer-engagement/admin/assign-security-roles-form)
