---
title: 在 Power Apps 中更改模型驱动应用窗体内的导航 | MicrosoftDocs
description: 了解如何更改窗体内的导航
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
ms.assetid: 4c379202-9f0e-4003-a49c-efff53e7f79f
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 92d76b056c21ebe583679bc51b73b04dcf812e69
ms.sourcegitcommit: a1b54333338abbb0bc3ca0d7443a5a06b8945228
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/13/2020
ms.locfileid: "3125517"
---
# <a name="change-navigation-within-a-model-driven-app-form"></a>更改模型驱动应用程序窗体内的导航

 通过窗体中的导航，应用用户可以查看相关记录的列表。 每个实体关系都具有控制其是否应显示的属性。 详细信息：[主要实体的导航窗格项](../common-data-service/create-edit-1n-relationships-solution-explorer.md#navigation-pane-item-for-primary-entity)  
  
 可以在窗体编辑器中覆盖配置为要显示的任何实体关系。 您还可以放入导航链接，以便通过窗体导航显示 Web 资源或其他网站。  
  
 有关分步说明，请参阅[创建和编辑 Common Data Service 的实体关系](../common-data-service/create-edit-entity-relationships.md)  
  
 若要编辑导航，必须先在窗体设计器的**主页**选项卡上的**选择** 组中选择**导航**。  
 
> [!div class="mx-imgBorder"] 
> ![导航命令](media/navigation-command.png)
 
 在右侧空格中，从**关系资源管理器**可以按 1:N（一对多）或 N:N（多对多）关系筛选可用关系，也可以查看所有可用关系。 禁用并选中**仅显示未用关系** 复选框。 因此，您只能添加每种关系一次。  
 
 > [!div class="mx-imgBorder"] 
 > ![关系资源管理器](media/relationship-explorer.png)

 若要通过**关系资源管理器**添加关系，只需双击该关系，就会将其添加到在导航区中当前选择的关系下面。 双击导航区域中的关系，而您可以更改**显示**区域中的标签。您可以在**名称**选项卡上查看有关该关系的信息。 使用**编辑**按钮可打开实体定义。  
  
 导航区中有五个组。 可以拖动这些组来重新确定其位置，双击它们可以更改标签，但不能删除它们。 这些组仅在其中有内容时显示。 因此，如果您不希望显示某个组，就不要向其添加任何内容。  
  
 在**插入**选项卡上**控件**组中的**导航链接**按钮，可以添加 Web 资源的链接或外部 URL。  
 
 ![导航链接](media/navigation-link.png)
 
<a name="BKMK_NavigationLinkProperties"></a>   
### <a name="navigation-link-properties"></a>导航链接属性  
 导航链接具有以下属性：  
  
|属性|说明|  
|--------------|-----------------|  
|姓名|**必需**：显示为标签的文本。|  
|图标|使用一个 32x32 像素的 Web 资源。 推荐使用背景透明的 PNG 图像。|  
|Web 资源|指定要在窗体的主窗格中显示的 Web 资源。|  
|外部 URL|指定要在窗体的主窗格中显示的页面的 URL。|  

<a name="BKMK_PrivacyNotices"></a>   

## <a name="privacy-notices"></a>隐私声明  
 [!INCLUDE[cc_privacy_crm_website_preview_control](../../includes/cc-privacy-crm-website-preview-control.md)]    
  
 [!INCLUDE[cc_privacy_multimedia_control](../../includes/cc-privacy-multimedia-control.md)]  

## <a name="next-steps"></a>后续步骤

[窗体编辑器用户界面概述](form-editor-user-interface-legacy.md)
