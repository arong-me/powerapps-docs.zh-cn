---
title: PowerApps 中模型驱动应用程序的通用字段属性 | MicrosoftDocs
description: 了解主窗体的通用字段属性
Keywords: 主窗体; 通用字段属性; Dynamics 365
author: Mattp123
ms.author: matp
manager: kvivek
ms.date: 06/18/2018
ms.service: powerapps
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: 2b91ee28-7f09-435e-9fae-5225aa698e22
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e30d84206e92162327f1faf0035450ede9c05a8a
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2701299"
---
# <a name="model-driven-app-common-field-properties"></a>模型驱动应用程序的通用字段属性

 窗体中的字段显示用户用于查看或编辑实体记录中的数据的控件。 可以将字段格式设置成在分区中最多占用四栏。  

您可以在解决方案资源管理器中访问**常见字段属性**。 在**组件**下，展开**实体**，然后展开所需实体，选择**窗体**。 在窗体列表中，打开**主**类型的窗体。 然后双击字段之一查看常见字段属性。

![common-field-properties](media/common-field-properties.png)
  
下表介绍了所有字段具有的属性。 有些类型的字段具有特殊属性。 这些在[特殊字段属性](special-field-properties-legacy.md)中介绍。  
  
|Tab|属性|说明|  
|---------|--------------|-----------------|  
|**显示器**|**标签**|**必需**：默认情况下，标签与字段的显示名称匹配。 通过在此处输入其他标签，可以覆盖窗体的该名称。|  
||**在表单上显示标签**|您可以选择不显示标签。|  
||**字段行为**|使用复选框指定字段级行为。|  
||**锁定**|这将防止从窗体中意外删除字段。 这将防止在删除字段时清除您已经应用于字段的任何配置。 若要删除此字段，定制员需要先清除此设置。|  
||**可见性**|是否显示字段是可选的，并可使用脚本来控制。 详细信息：[可见性选项](visibility-options-legacy.md)|  
||**可用性**|选择您是否希望在电话上提供此选项卡。|
|**格式设置**|**选择控件所占据的栏数**|当包含字段的分区有多栏时，可以将字段设置为最多占据分区具有的栏数。|  
|**详细信息**|**显示名称**、**名称**和**说明**|这些只读字段供参考。 如果要编辑字段定义，单击**编辑**按钮可以方便地访问字段定义。<br /><br /> 窗体中某个字段的每个实例都有一个名称属性，因此可在窗体脚本中引用它们，但此名称由应用程序管理。 字段的第一个实例是在创建字段时指定的字段名称。 更多信息：[创建和编辑字段](../common-data-service/create-edit-fields.md)<br /><br /> 对于将字段放入窗体的其他每个时间，名称后面会附加一个从 1 开始的数字。 因此，如果字段名称为 new_cost，那么，对于窗体中的每个字段实例，第一个实例为 new_cost，第二个实例为 new_cost1，依此类推。<br /><br />**注意：** 字段**说明**值提供字段的工具提示文本；当用户将鼠标悬停在字段上时，将显示该提示。|  
|**事件**|**窗体库**|指定将在字段 `OnChange` 事件处理程序中使用的任何 JavaScript Web 资源。<br /><br />|  
||**事件处理程序**|配置应为字段 `OnChange` 事件调用的窗体库中的函数。 详细信息：[配置事件处理程序](configure-event-handlers-legacy.md)|  
|**业务规则**|**业务规则**|查看和管理引用此字段的任何业务规则。 详细信息：[创建业务规则和建议](create-business-rules-recommendations-apply-logic-form.md)|  
|**控件**|**控件**|添加控件并指定它们在 Web、电话和平板电脑上的可用性。|  

## <a name="next-steps"></a>后续步骤

[使用“主”窗体及其组件](use-main-form-and-components.md)
