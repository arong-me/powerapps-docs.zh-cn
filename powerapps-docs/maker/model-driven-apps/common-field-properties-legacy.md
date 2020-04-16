---
title: Power Apps 中模型驱动应用程序的通用字段属性 | MicrosoftDocs
description: 了解主窗体的通用字段属性
Keywords: 主窗体; 通用字段属性; Dynamics 365
author: Mattp123
ms.author: matp
manager: kvivek
ms.date: 02/25/2020
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
ms.openlocfilehash: 8729292ca14cff762b31ef886ecdc0c90856110e
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136421"
---
# <a name="model-driven-app-common-field-properties"></a>模型驱动应用程序的通用字段属性

您可以使用 Power Apps 解决方案资源管理器或 Power Apps 门户查看和编辑模型驱动应用的实体字段的通用属性。 Power Apps 门户提供通过 Common Data Service 创建和编辑实体字段的简单方法。
此门户支持配置最常见的选项，但是某些选项只能使用解决方案资源管理器设置。

## <a name="common-field-properties-in-power-apps-portal"></a>Power Apps 门户中的通用字段属性

1. 从 [Power Apps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，选择**数据** > **实体**，然后选择具有您要查看的字段的实体。

2. 选择要查看的字段。

    > [!div class="mx-imgBorder"]
    > <img src="media/common-field-prop-powerapps.png" alt="Common field properties in Power Apps portal" height="658" width="300">


下表介绍了字段的通用属性。 有些类型的字段具有特殊属性。 这些在[创建和编辑 Common Data Service 的字段](../common-data-service/create-edit-field-portal.md)中进行了介绍。

 |属性|说明|
 |--|--|
 |**显示名称**|用户界面中要为字段显示的文本。|
 |**名称**|在整个环境中的唯一名称。 名称将根据您输入的显示名称为您生成，不过您可以在保存之前进行编辑。 在创建字段后，不能更改名称，因为它将在您的应用程序或代码中引用。 名称会将 **Common Data Service 默认发布商**的自定义项前缀附加到字段的前面。|
 |**数据类型**|控制值如何在某些应用程序中存储以及如何确定格式。 一旦保存字段，将无法更改数据类型，除非将文本字段转换为自动编号字段。|
 |**必填**| 如果此字段中无数据，将无法保存记录。 |
 |**可搜索**| 此字段会出现在“高级查找”中，并且可在自定义视图时使用。 |
 |**计算或汇总**| 用于自动化手动计算。 使用值、日期或文本。|
 |**高级选项**| 添加说明，并指定字段的最大长度和 IME 模式。

有许多不同类型的字段，但是，您只能创建其中一部分。 有关所有字段类型的详细信息，请参阅[字段类型和字段数据类型](../common-data-service/types-of-fields.md)。 您可以根据所选择的**数据类型**设置其他选项。

## <a name="common-field-properties-in-solution-explorer"></a>解决方案资源管理器中的通用字段属性
 
窗体中的字段显示用户用于查看或编辑实体记录中的数据的控件。 可以将字段格式设置成在分区中最多占用四栏。  

您可以在解决方案资源管理器中访问**常见字段属性**。 在**组件**下，展开**实体**，然后展开所需实体，选择**窗体**。 在窗体列表中，打开**主**类型的窗体。 然后双击字段之一查看常见字段属性。

![解决方案资源管理器中的通用字段属性](media/common-field-properties.png "解决方案资源管理器中的通用字段属性")
  
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
