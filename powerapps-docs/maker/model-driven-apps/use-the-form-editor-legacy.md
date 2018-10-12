---
title: 更改 PowerApps 中模型驱动应用窗体内的导航 | MicrosoftDocs
description: 了解如何更改窗体内的导航
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
ms.assetid: 4c379202-9f0e-4003-a49c-efff53e7f79f
caps.latest.revision: 63
ms.author: matp
manager: kvivek
ms.openlocfilehash: 5a8156875f669854a4ba4649e50a23e340f3ceff
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667624"
---
# <a name="change-navigation-within-a-model-driven-app-form"></a>更改模型驱动应用窗体内的导航

 窗体内的导航可使应用用户查看相关记录的列表。 每个实体关系都具有控制是否应显示的属性。 详细信息：[主要实体的导航窗格项](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)  
  
 可在窗体编辑器中替代配置为显示的任何实体关系。 还可包含导航链接，以通过窗体导航显示 Web 资源或其他网站。  
  
 有关分步说明，请参阅[为 Common Data Service for Apps 创建和编辑实体关系](../common-data-service/create-edit-entity-relationships.md)  
  
 若要启用编辑导航，必须首先从窗体设计器的“主页”选项卡上的“选择”组中选择“导航”。  
 
 ![导航命令](media/navigation-command.png)
 
 在右侧窗格中，可从“关系资源管理器”中按 1:N（一对多）或 N:N（多对多）关系进行筛选，或查看所有可用关系。 “仅显示未使用的关系”复选框处于禁用状态并已选中。 所以只能添加每个关系一次。  
  
 ![关系资源管理器](media/relationship-explorer.png)

 若要从“关系资源管理器”添加关系，只需双击该关系，它将添加到导航区域中当前所选关系下方。 在导航区域中双击关系，可以在“显示”选项卡上更改标签。在“名称”选项卡上，可看到该关系的相关信息。 使用“编辑”按钮打开实体的定义。  
  
 导航区域中有五个组。 可拖动它们进行重新定位，双击可更改标签，但无法删除它们。 这些组仅在其中存在某些内容时显示。 因此，如果不希望显示组，请不要添加任何内容。  
  
 使用“插入”选项卡的“控制”组中的“导航链接”按钮添加指向 Web 资源或外部 URL 的链接。  
 
 ![导航链接](media/navigation-link.png)
 
<a name="BKMK_NavigationLinkProperties"></a>   
### <a name="navigation-link-properties"></a>导航链接属性  
 导航链接有以下属性：  
  
|属性|描述|  
|--------------|-----------------|  
|名称|**必填项**：要显示为标签的文本。|  
|图标|使用 32x32 像素的 Web 资源。 建议使用透明背景的 PNG 图像。|  
|Web 资源|指定要在窗体的主窗格中显示的 Web 资源。|  
|外部 URL|指定要在窗体的主窗格中显示的页面 URL。|  

<a name="BKMK_PrivacyNotices"></a>   

## <a name="privacy-notices"></a>隐私声明  
 [!INCLUDE[cc_privacy_crm_website_preview_control](../../includes/cc-privacy-crm-website-preview-control.md)]    
  
 [!INCLUDE[cc_privacy_multimedia_control](../../includes/cc-privacy-multimedia-control.md)]  

## <a name="next-steps"></a>后续步骤

[窗体编辑器用户界面概述](form-editor-user-interface-legacy.md)