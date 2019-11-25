---
title: 在 PowerApps 中编辑实体 | MicrosoftDocs
description: 了解各种可以编辑实体的方法
ms.custom: ''
ms.date: 05/15/2018
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
ms.assetid: 8b00780c-74f0-4e3a-b570-b9289d0d5383
caps.latest.revision: 41
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3ec64583e2146703711b88456ff7bc91ece3e921
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757432"
---
# <a name="edit-an-entity"></a>编辑实体

您可以编辑您自己创建的任何自定义实体。 标准实体或自定义托管实体可能会对您能做的更改有限制。  
  
> [!NOTE]
> **标准**实体是包含在您的环境中的常用实体，不是**系统**或**自定义**实体。 *托管自定义实体*是通过导入托管解决方案添加到系统中的实体。 您对这些实体的编辑程度取决于为每个实体设置的托管属性。 任何不能编辑的属性都将被禁用。 

可以采用两种方法使用设计器编辑实体：

|设计器|说明|
|--|--|
|[PowerApps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)|提供简单的简化体验，但是有些特殊设置不可用。|
|解决方案资源管理器|不那么简单，但提供更多灵活性可减少常见要求。|

在 PowerApps 门户和解决方案资源管理器中可执行以下操作：

- **编辑实体字段**。 更多信息：[创建和编辑 Common Data Service 的字段](create-edit-fields.md)
  
- **编辑实体关系**。 详细信息：[创建和编辑实体之间的关系](create-edit-entity-relationships.md)

- **键**。 [定义引用记录的备用键](define-alternate-keys-reference-records.md)
  
您还可以对支持实体的记录进行更改：  

- **业务规则**。 详细信息：[创建业务规则和建议以在窗体中应用逻辑](../model-driven-apps/create-business-rules-recommendations-apply-logic-form.md)

- **查看次数**。 详细信息：[创建或编辑视图](../model-driven-apps/create-edit-views.md)
  
- **窗体**。 详细信息：[创建和设计窗体](../model-driven-apps/create-design-forms.md)

- **仪表板**。 详细信息：[创建或编辑仪表板](../model-driven-apps/create-edit-dashboards.md)

- **图表**。 [创建或编辑系统图表](../model-driven-apps/create-edit-system-chart.md)

## <a name="edit-using-powerapps-portal-designer"></a>使用 PowerApps 门户设计器进行编辑

在 PowerApps 门户设计器中，仅有三个实体属性可以编辑：
 - 显示名称
 - 复数显示名称
 - 说明

在设计器中，选择要编辑的实体，然后单击它打开实体编辑器。 若要修改实体属性，单击**设置**命令查看**编辑实体**窗体，如下所示：

![编辑实体属性](media/edit-entity-properties-powerapps-portal-designer.png)

> [!NOTE]
>  许多标准实体名称也可以在应用程序的其他文本中使用。 若要查找并更改使用此名称的文本，请参阅[编辑标准实体消息](edit-system-entity-messages.md)

要对实体选项进行任何其他更改，必须使用解决方案资源管理器编辑实体。

## <a name="edit-using-solution-explorer"></a>使用解决方案资源管理器进行编辑

在使用解决方案资源管理器编辑实体时，您需要找到要向其添加实体的非托管解决方案。

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]
  
<a name="BKMK_ChangeEntityName"></a> 
  
## <a name="change-the-name-of-an-entity"></a>更改实体名称  

使用**显示名称**和**复数名称**属性可以更改实体在应用程序中的名称。 

> [!NOTE]
>  许多标准实体名称也可以在应用程序的其他文本中使用。 若要查找并更改使用此名称的文本，请参阅[编辑标准实体消息](edit-system-entity-messages.md)
  
<a name="BKMK_ChangeEntityIcon"></a>   

###  <a name="change-the-icons-used-for-custom-entities"></a>更改用于自定义实体的图标  

默认情况下，Web 应用程序中的所有自定义实体具有相同的图标。 您可以为自定义实体所需要的图标创建图像 Web 资源。 详细信息：[更改自定义实体的图标](../model-driven-apps/change-custom-entity-icons.md)。  
  
<a name="BKMK_EnableOptions"></a>  
 
###  <a name="entity-options-that-can-only-be-enabled"></a>只能启用的实体选项  

下表列出了可以为实体启用的选项，但是，在启用了这些项目后，就不能将它们禁用：  

[!INCLUDE [cc_entity-set-once-options-table](../../includes/cc_entity-set-once-options-table.md)] 
  
<a name="BKMK_EnableDisableOptions"></a>  
 
###  <a name="enable-or-disable-entity-options"></a>启用或禁用实体选项  

下表列出了您可以随时启用或禁用的实体选项。  

[!INCLUDE [cc_entity-changeable-options-table](../../includes/cc_entity-changeable-options-table.md)] 

### <a name="see-also"></a>另请参阅

[创建实体](create-edit-entities.md)<br />
[使用解决方案资源管理器创建和编辑实体](create-edit-entities-solution-explorer.md)
