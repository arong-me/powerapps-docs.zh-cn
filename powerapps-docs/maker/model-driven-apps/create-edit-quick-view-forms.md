---
title: 在 Power Apps 中创建或编辑模型驱动应用的快速视图窗体 | MicrosoftDocs
description: 了解如何创建或编辑快速视图窗体
ms.custom: ''
ms.date: 03/13/2020
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
ms.assetid: 9b101734-cc11-4d05-bd45-eb611eae9931
caps.latest.revision: 14
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1e94b836fc7718f3aa259b677edc58419c98af06
ms.sourcegitcommit: 9f2694bd14d70798310b89a4673672c1bfad989d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "3167090"
---
# <a name="create-a-model-driven-app-quick-view-form-to-view-information-about-a-related-entity"></a>创建模型驱动应用程序的快速视图窗体以查看有关相关实体的信息

在本主题中，您可以了解如何创建快速视图窗体，以及如何向主窗体添加快速视图控件。 

快速视图窗体可以作为快速视图控件添加到其他窗体。 可以提供一个模板，用于查看其他实体记录的窗体中相关实体记录的信息。 这意味着，您的应用用户不需要导航到不同的记录就能查看他们工作所需的信息。  
  
 快速视图控件与窗体中包含的某个查找字段关联。 如果没有设置该查找字段的值，则快速视图控件将不可见。 快速视图控件中的数据不可编辑，并且快速视图控件不支持窗体脚本。  
  
 因为快速视图窗体是使用窗体中的快速视图控件查看的，因此它们不包括标题、脚注或导航区。 不能向快速视图窗体分派安全角色，也无法将其激活或停用。  
  
<a name="BKMK_CreateQFV"></a>   
## <a name="create-a-quick-view-form"></a>创建快速视图窗体  
 使用窗体编辑器创建快速查看窗体，方式与创建其他窗体的方式类似。 快速查看窗体为只读。 用其创建只读窗体。  
  
1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

2. 展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。 
  
3. 在工具栏上，选择**添加窗体** > **快速视图窗体**。  
  
5. 在**窗体**面板中，输入**显示名称**和**说明**以区分此快速视图窗体与其他窗体。  
  
6. 在窗体设计器中，将任何字段从**字段资源管理器**拖到窗体中的各个分区。

    > [!IMPORTANT]
    > 不能从窗体中删除必填字段。 如果向窗体中添加了必填字段并想将其删除，则必须先删除该窗体，然后再重新创建。 在为某个字段设置“必需”属性时，如果该字段中没有数据，则无法保存记录。

7. 要保存窗体，选择**保存**。  

8. 选择**发布**查看应用程序中的新窗体。 <!-- Which app? What does Publish do?-->
  
<a name="BKMK_EditQVF"></a>   
## <a name="edit-a-quick-view-form"></a>编辑快速视图窗体  
 快速视图窗体采用了简化的布局，因为其设计目的就是供在窗体分区中查看。 只有一个单栏选项卡可用。 只能再添加一个单栏分区、字段、子网格和空间。   
  
  > [!IMPORTANT]
  > 无法删除必填字段。 如果在窗体中添加了必填字段，则不能将其删除。 如果您希望窗体中无此字段，必须删除窗体再重新创建。
  
 辑快速视图窗体时，必须先发布您做的更改，然后才会在应用程序中显示它们。  
  
<a name="BKMK_AddQVF"></a>   
## <a name="add-a-quick-view-control-to-a-main-form"></a>向主窗体添加快速视图控件  
 只能将快速视图窗体添加存在查找字段的主窗体中，查找的目标是快速视图窗体的实体。  
  
1.  登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  

2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。  

3. 选择**类型**为**主**的窗体。

4. 在窗体设计器中，从“组件”窗格，选择**快速视图**。  
  
5.  在**选择快速视图窗体**对话框中，选择**查找**字段，然后选择“查找”字段值。 详细信息：[快速视图控件属性](quick-view-control-properties-legacy.md)  

    > [!div class="mx-imgBorder"] 
    > ![添加快速视图控件](media/add-quick-view-control.png "将快速视图控件添加到主窗体")

6.  选择**完成**关闭**选择快速视图窗体**对话框。 快速视图窗体将显示在窗体中。

7.  要保存窗体，选择**保存**。  

## <a name="next-steps"></a>后续步骤   
 [创建和设计窗体](create-design-forms.md)   
 [创建或编辑快速创建窗体](create-edit-quick-create-forms.md)
