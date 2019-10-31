---
title: 在 PowerApps 中打开模型驱动应用程序窗体编辑器 | MicrosoftDocs
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
ms.assetid: 8478a07a-c697-4784-874b-36958eb4f95d
caps.latest.revision: 63
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="open-the-model-driven-app-form-editor"></a>打开模型驱动应用程序窗体编辑器 
通过窗体编辑器，您通过将组件（如分区、选项卡、字段和控件）放入窗体编辑器区域来设计窗体。 在本主题中，您将了解几个访问窗体编辑器的不同方法。
 
如果编辑窗体的过程创建任何新的解决方案组件（例如，Web 资源），组件的名称将使用默认解决方案的解决方案发布商自定义前缀，而这些组件将仅包括在默认解决方案中。 如果要将任何新的解决方案组件包括在某个特定的非托管解决方案中，则应通过该非托管解决方案打开窗体编辑器。  

## <a name="access-the-form-editor-from-the-powerapps-site"></a>从 PowerApps 站点访问窗体编辑器

1. 登录到 [PowerApps](https://web.powerapps.com/)。 

2. 选择**数据** > **实体** >，然后选择所需实体，如客户实体。 

3. 选择**窗体**选项卡，然后打开所需实体，如**客户**主窗体。

## <a name="access-the-form-editor-from-solution-explorer"></a>从解决方案资源管理器访问窗体编辑器
  
1.  打开[解决方案资源管理器](advanced-navigation.md#solution-explorer)。
  
2.  在**组件**下，展开**实体**，然后展开所需的实体，再单击**窗体**。  
  
3.  在窗体列表中，单击要编辑的窗体。  
  

## <a name="access-the-form-editor-through-the-command-bar-within-a-model-driven-app"></a>通过模型驱动应用程序内的命令栏访问窗体编辑器 
  
1.  打开记录。  
  
2.  如果实体有多个主窗体，请确认您要编辑的那个窗体。 如果它不是您要编辑的窗体，请使用窗体选择器选择要编辑的窗体。  
  
3.  选择**更多命令**按钮 ![“约会活动”中的“更多命令”按钮](media/more-commands.gif "“约会活动”中的“更多命令”按钮")。  
  
4.  选择**窗体编辑器**。  

## <a name="access-the-form-editor-from-within-app"></a>从站点内部访问窗体编辑器
  
 依据实体，您可通过命令栏或功能区访问窗体编辑器。 这两种方法都将在默认解决方案的上下文中打开窗体。 

## <a name="access-the-form-editor-for-an-unmanaged-solution"></a>访问非托管解决方案的窗体编辑器  
  
1.  打开[解决方案](advanced-navigation.md#solutions)。  
  
2.  双击要使用的非托管解决方案。  
  
3.  查找具有要编辑的窗体的实体。 如果没有实体，则需要添加实体。 详细信息：[向非托管解决方案添加实体](#add-an-entity-to-an-unmanaged-solution) 
  
### <a name="add-an-entity-to-an-unmanaged-solution"></a>将实体添加到非托管解决方案  
  
1.  选择**实体** 节点，然后在列表上方的工具栏中单击**添加现有项**。  
  
2.  在**选择解决方案组件**对话框中，将**组件类型**选择器设置为**实体**，选择要添加的实体，然后单击**确定**。  
  
3.  出现**缺少必需组件** 对话框时，如果不打算将此非托管解决方案导出到其他环境，则可单击**否，不包含必需组件**。 如果此时选择不包含缺少的必需组件，可以在以后添加这些组件。 将来导出此解决方案时，您会再次收到通知。  
  
5.  在解决方案资源管理器中，展开具有要编辑的窗体的实体，然后选择**窗体** 。  
  
6.  在窗体列表中，双击要编辑的窗体。  

## <a name="next-steps"></a>后续步骤

[创建和设计窗体](create-design-forms.md)
