---
title: Power Apps 中模型驱动应用主窗体的快速视图控件属性 | MicrosoftDocs
description: 了解主窗体的快速视图控件属性
Keywords: 快速视图控件属性; Dynamics 365; 主窗体
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 10/28/2019
ms.service: powerapps
ms.topic: article
ms.assetid: 68f68d5b-6c71-4b95-bb46-d48c59d9008e
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 549728e2fb100f927de6660dd5fc5d5aa0da4f68
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873670"
---
# <a name="model-driven-app-quick-view-control-properties"></a>模型驱动应用程序的快速视图控件属性

模型驱动应用窗体上的快速视图控件在窗体上显示查找时选择的记录中的数据。 控制中显示的数据是使用快速视图窗体定义的。 显示的数据不可编辑，但是，当快速视图窗体中包括主字段时，主字段将成为用于打开相关记录的链接。 详细信息：[创建和编辑快速视图窗体](create-edit-quick-view-forms.md)  

> [!div class="mx-imgBorder"] 
> ![客户窗体上的联系人快速视图窗体](media/quick-view-form-contact.png "客户窗体上的联系人快速视图窗体")  

您可以从 Power Apps 站点访问**快速视图控件属性**。 
1.  登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。  


2.  展开**数据**，选择**实体**，选择所需实体，然后选择**窗体**选项卡。 

3. 在窗体列表中，打开**主**类型的窗体。 然后在**插入**选项卡上，选择**快速视图窗体**查看快速视图控件属性。

    ![快速视图控件](media/quick-view-control.png)
  
|属性|说明|  
|--------------|-----------------|  
|**名称**|**必需**：快速视图窗体的唯一名称，在脚本中引用快速视图窗体时使用该名称。|  
|**标签**|**必需**：要为快速视图窗体显示的标签。|  
|**在窗体上显示标签**|在窗体上显示标签。|  
|**查找字段**|选择窗体中包含的某个查找字段。|  
|**相关实体**|此值取决于您选择的**查找字段** 。 这通常是查找的 1:N 实体关系的主要实体。<br /><br /> 如果该实体包括能接受客户或联系人的**潜在客户**查找，则在**快速视图窗体**字段中， 您可以通过更改此值并选择另一个快速视图窗体，为客户和联系人选择快速视图窗体。|  
|**快速视图窗体**|如果**相关实体** 有任何快速视图窗体，则可在此处选择。 否则，可选择**新建**创建一个。<br /><br /> 选择**编辑**可更改选择的快速视图窗体。|  
|**其他属性**|您可以通过选择复选框指定默认呈现样式。|

## <a name="next-steps"></a>后续步骤

[使用“主”窗体及其组件](use-main-form-and-components.md)
 
