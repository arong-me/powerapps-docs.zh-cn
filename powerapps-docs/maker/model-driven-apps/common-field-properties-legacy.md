---
title: PowerApps 中的模型驱动应用常用字段属性 | MicrosoftDocs
description: 了解 Dynamics 365 for Customer Engagement 中用于主窗体的常用字段属性
Keywords: Main form; Common field properties; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/18/2018
ms.service: crm-online
ms.topic: article
ms.assetid: 2b91ee28-7f09-435e-9fae-5225aa698e22
ms.openlocfilehash: 74e67dd4299d06a54d5ec85765e4e5d03710b432
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667911"
---
# <a name="model-driven-app-common-field-properties"></a>模型驱动应用常用字段属性

 窗体中的字段显示人们查看或编辑实体记录中的数据所使用的控件。 字段格式可以设置为在一个节中最多占用四列。  

可在解决方案资源管理器中访问“常用字段属性”。 在“组件”下，展开“实体”，展开所需实体，然后选择“窗体”。 在窗体列表中，打开类型为“主窗体”的窗体。 然后双击其中一个字段以查看“常用字段属性”。

![common-field-properties](media/common-field-properties.png)
  
下表介绍了所有字段都具有的属性。 某些类型的字段具有特殊属性。 这些内容在[特殊字段属性](special-field-properties-legacy.md)中进行介绍。  
  
|选项卡|属性|描述|  
|---------|--------------|-----------------|  
|**显示**|**标签**|必需：默认情况下，标签将与字段的显示名称匹配。 可在此处输入其他标签来替代窗体的名称。|  
||**在窗体上显示标签**|可选择完全不显示标签。|  
||**字段行为**|使用复选框指定字段级别行为。|  
||**锁定**|该属性将防止意外从窗体删除字段。 这将防止在删除字段时清除已应用于字段的任何配置（例如事件处理程序）。 若要删除此字段，定制员需要先清除此设置。|  
||**可见性**|显示字段是可选的，可使用脚本控制。 详细信息：[可见性选项](visibility-options-legacy.md)|  
||**可用性**|选择是否要在手机上显示该选项卡。|
|**格式设置**|**选择控件占用的列数**|如果包含字段的分区具有多列，可将该字段的占用列数上限设置为该分区所具有的列数。|  
|**详细信息**|“显示名称”、“名称”和“说明”|这些只读字段用于参考目的。 若要编辑，请单击“编辑”按钮以快速访问字段定义。<br /><br /> 窗体中每个字段的实例都有一个名称属性，以便可在窗体脚本中引用它们，但此名称由应用程序托管。 字段的第一个实例是创建该字段时指定的名称。 详细信息：[创建和编辑字段](../common-data-service/create-edit-fields.md)<br /><br /> 每当窗体中新增一个字段时，名称都会在末尾追加一个以 1 开头的数字。 因此，如果字段名称为“new_cost”，则第一个实例为“new_cost”，第二个实例为“new_cost1”，依此类推，表示窗体中字段的每个实例。<br /><br />**注意：** 将光标放在字段上时，字段“说明”值提供该字段的工具提示文本。|  
|**事件**|**窗体库**|指定将在字段 `OnChange` 事件处理程序中使用的任何 JavaScript Web 资源。<br /><br />|  
||**事件处理程序**|从窗体库中配置应针对字段 `OnChange` 事件调用的函数。 详细信息：[配置事件处理程序](configure-event-handlers-legacy.md)|  
|**业务规则**|**业务规则**|查看和管理引用此字段的任何业务规则。 详细信息：[创建业务规则和建议](create-business-rules-recommendations-apply-logic-form.md)|  
|**控件**|**控件**|添加控件并指定其在 Web、手机和平板电脑上的可用性。|  

## <a name="next-steps"></a>后续步骤

[使用主窗体及其组件](use-main-form-and-components.md)
