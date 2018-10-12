---
title: PowerApps 中模型驱动应用的窗体属性 | MicrosoftDocs
description: 了解主窗体属性
Keywords: Main form properties; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: crm-online
ms.topic: article
ms.assetid: 4ed30bb7-dca1-4de8-80f3-842152ea921a
ms.openlocfilehash: 4aec7fd8a117257d4f21ac2f692643785fd21791
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39668432"
---
# <a name="model-driven-app-form-properties"></a>模型驱动应用窗体属性 

可在解决方案资源管理器中访问“窗体属性”。 在“组件”下，展开“实体”，展开所需实体，然后选择“窗体”。 在窗体列表中，打开类型为“主窗体”的窗体。 然后“主页”选项卡上，选择“窗体属性”。

![form-properties](media/form-properties.png)

下表列出了窗体属性：  
  
|Tab|属性|描述|  
|---------|--------------|-----------------|  
|**事件**|**窗体库**|管理窗体中可用的 JavaScript Web 资源以及其加载顺序。|  
||**事件处理程序**|配置窗体库中将为 `OnLoad` 和 `OnSave` 窗体事件运行哪些 JavaScript 函数及其运行的顺序。|  
|**显示**|**窗体名称**|输入将对用户有意义的名称。 使用窗体时，将向用户显示此名称。 如果用户可使用为实体配置的多个窗体，他们将使用此名称来区分可用窗体。|  
||**Description**|输入说明，介绍此窗体有何不同于其他主窗体。 此说明仅在解决方案资源管理器中实体的窗体列表中显示。|  
||**窗体助理**|如果想要启用窗体助理或查看默认展开的窗体，请从复选框中选择。|
||**页导航**|可以选择不显示导航项。<br /><br /> 在已更新实体的窗体中，这意味着当前所查看记录的主名称值不会显示在导航栏中以允许导航到关联的视图。<br /><br /> 在使用经典表示形式的窗体中，窗体左侧选择关联视图的导航选项不会显示。|  
||**图像**|如果实体具有图像字段，且实体的“主要图像”选项已设置，则此设置将启用在此窗体标头中显示图像字段。<br /><br /> 请参阅[启用或禁用实体选项](../common-data-service/edit-entities.md#enable-or-disable-entity-options)，了解有关实体选项的详细信息。|  ||**显示**|设置最大宽度（以像素为单位），限制窗体的宽度。 默认值为 1900。|  
||**显示**|以像素为单位，输入此处窗体所需的最大宽度。|
|**参数**|**参数**|可以使用 URL 通过代码打开每个窗体。 URL 还可以包含可通过使用附加到该 URL 的查询字符串传递给窗体的数据。 查询字符串类似于下例：<br />`?p_firstName=Jim&p_lastName=Daly`<br /><br /> 作为一种安全措施，窗体不会接受任何未知的查询字符串参数。 使用此参数列表指定此窗体应接受的参数，以支持要使用查询字符串将数据传递到窗体的代码。<br /><br /> 数据名称和类型会进行检查，如果向其传递无效的查询字符串参数，则窗体不会打开。<br /><br />**注意：** 名称不能以下划线 (_) 或 crm\_ 开头。 名称必须以字母数字字符开头，后跟下划线 (\_)。 例如，parameter_1 或 1_parameter。 名称不能包含连字符 (-)、冒号 (:)、分号 (;)、逗号 (,)，或句点 (.)。 <br /><br />|  
|**非事件依赖项**|**依赖字段**|每个事件处理程序都具有类似的“依赖字段”属性，以便可注册脚本所需的任何字段。 试图删除依赖字段的任何人都无法将其删除。<br /><br /> 某些脚本在窗体上运行，但未在事件处理程序中配置。 从命令栏启动的脚本没有可注册依赖字段的位置。 此窗体属性为依赖字段提供位置以便注册这些脚本。|  

## <a name="next-steps"></a>后续步骤

[使用主窗体及其组件](use-main-form-and-components.md)