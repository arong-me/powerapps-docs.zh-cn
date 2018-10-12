---
title: 在 PowerApps 中打开模型驱动的应用窗体编辑器 | Microsoft Docs
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
ms.assetid: 8478a07a-c697-4784-874b-36958eb4f95d
caps.latest.revision: 63
ms.author: matp
manager: kvivek
ms.openlocfilehash: e0fe15df88fccbaee3c13a344416a434e1f92923
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667896"
---
# <a name="open-the-model-driven-app-form-editor"></a>打开模型驱动的应用窗体编辑器 
使用窗体编辑器，可通过将组件（如节、选项卡、字段和控件）拖放到窗体编辑器画布上来设计窗体。 本主题将介绍访问窗体编辑器的几种不同方法。
 
如果在编辑窗体的过程中创建了任何新的解决方案组件（例如 Web 资源），则组件的名称将使用默认解决方案的解决方案发布者自定义前缀，且这些组件将仅包含在默认解决方案中。 如果要在特定的非托管解决方案中包含任何新的解决方案组件，则应通过该非托管解决方案打开窗体编辑器。  

## <a name="access-the-form-editor-from-the-powerapps-site"></a>从 PowerApps 站点访问窗体编辑器

1. 登录 [PowerApps](https://web.powerapps.com/)。 

2. 选择“模型驱动” > “数据” > “实体”>，然后选择所需实体，例如帐户实体。 

3. 选择“窗体”选项卡，然后打开所需窗体，例如“帐户”主窗体。

## <a name="access-the-form-editor-from-solution-explorer"></a>从解决方案资源管理器访问窗体编辑器
  
1.  打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。
  
2.  在“组件”下，展开“实体”，然后展开所需实体，最后单击“窗体”。  
  
3.  在窗体列表中，单击要编辑的窗体。  
  

## <a name="access-the-form-editor-through-the-command-bar-within-a-model-driven-app"></a>通过模型驱动的应用中的命令栏访问窗体编辑器 
  
1.  打开记录。  
  
2.  如果实体有多个主窗体，验证该窗体是否是要编辑的窗体。 如果不是，使用窗体选择器选择要编辑的窗体。  
  
3.  选择“更多命令”按钮![“约会活动”中的“更多命令”按钮](media/more-commands.gif "More Commands button in Appointment Activity")。  
  
4.  选择“窗体编辑器”。  

## <a name="access-the-form-editor-from-within-dynamics-365-customer-engagement"></a>从 Dynamics 365 客户参与中访问窗体编辑器
  
 可通过命令栏或功能区访问 Dynamics 365 客户参与中的窗体编辑器，具体取决于实体。 这两种方法都将在默认解决方案的上下文中打开窗体。 

## <a name="access-the-form-editor-for-an-unmanaged-solution"></a>访问非托管解决方案的窗体编辑器  
  
1.  打开[解决方案](advanced-navigation.md#solutions)。  
  
2.  双击要使用的非托管解决方案。  
  
3.  找到包含要编辑的窗体的实体。 如果该实体不存在，则需添加该实体。 详细信息：[将实体添加到非托管解决方案中](#add-an-entity-to-an-unmanaged-solution) 
  
### <a name="add-an-entity-to-an-unmanaged-solution"></a>将实体添加到非托管解决方案中  
  
1.  选择“实体”节点，然后在列表上方的工具栏中单击“添加现有项”。  
  
2.  在“选择解决方案组件”对话框中，将“组件类型”选择器设置为“实体”，选择要添加的实体，然后单击“确定”。  
  
3.  如果出现“缺少必需组件”对话框，且你不打算将此非托管解决方案导出到其他环境，则可单击“否，不包含必需组件”。 如果此时选择不包含缺少的必需组件，则可稍后添加它们。 如果将来导出此解决方案，你将再次收到通知。  
  
5.  在解决方案资源管理器中，展开包含要编辑的窗体的实体，然后选择“窗体”。  
  
6.  在窗体列表中，双击要编辑的窗体。  

## <a name="next-steps"></a>后续步骤

[创建并设计窗体](create-design-forms.md)
