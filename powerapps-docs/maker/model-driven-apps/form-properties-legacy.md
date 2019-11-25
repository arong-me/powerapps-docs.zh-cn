---
title: PowerApps 中模型驱动应用的窗体属性 | MicrosoftDocs
description: 了解主窗体属性
Keywords: 主窗体属性; Dynamics 365
author: Mattp123
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.author: matp
manager: kvivek
ms.date: 06/27/2018
ms.service: powerapps
ms.topic: article
ms.assetid: 4ed30bb7-dca1-4de8-80f3-842152ea921a
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 3a71fe6cf7771a0e15be85e0696e27226e84467e
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2700287"
---
# <a name="model-driven-app-form-properties"></a>模型驱动应用程序的窗体属性 

您可以在解决方案资源管理器中访问**窗体属性**。 在**组件**下，展开**实体**，然后展开所需实体，选择**窗体**。 在窗体列表中，打开**主**类型的窗体。 然后在**主页**选项卡上，选择**窗体属性**。

![窗体属性](media/form-properties.png)

下表列出窗体属性：  
  
|选项卡|属性|说明|  
|---------|--------------|-----------------|  
|**事件**|**窗体库**|管理窗体中可用的 JavaScript Web 资源以及这些资源的加载顺序。|  
||**事件处理程序**|配置将为 `OnLoad` 和 `OnSave` 窗体事件运行窗体库中的哪些 JavaScript 功能以及运行顺序。|  
|**显示器**|**表单名称**|输入一个对用户有意义的名称。 此名称将向使用窗体的用户显示。 如果他们可以使用为实体配置的多个窗体，则将使用此名称区分可用窗体。|  
||**说明**|输入描述，说明此窗体与其他主窗体的不同之处。 此描述仅在解决方案资源管理器中某个实体的窗体列表中显示。|  
||**窗体助理**|如果您要启用窗体助理或在默认展开的情况下查看窗体，请从复选框中选择。|
||**页面导航**|您可以选择不显示导航项。<br /><br /> 在更新的实体的主窗体中，这意味着当前查看的记录的主要名称值不会出现在导航栏中，无法用于导航到关联视图。<br /><br /> 在使用经典表示形式的窗体中，用于在窗体左侧选择关联视图的导航选项不会显示。|  
||**图像**|如果某个实体有图像字段，并且设置了实体的**主图像**选项，则此设置将允许在窗体的标题中显示图像字段。<br /><br /> 有关实体选项的详细信息，请参阅[启用或禁用实体选项](../common-data-service/edit-entities.md#enable-or-disable-entity-options)。|  ||**显示器**|**设置最大宽度（像素）** 可限制窗体的宽度。 默认值为 1900。|  
||**显示器**|以像素为单位在此处输入您希望的窗体最大宽度。|
|**参数**|**参数**|可以使用包含 URL 的代码打开每个窗体。 URL 也可包含数据；可以使用附加到 URL 后面的查询字符串将该数据传递给窗体。 查询字符串像此示例中所示：|<br />`?p_firstName=Jim&p_lastName=Daly`<br /><br /> 作为安全措施，窗体不会接受任何未知的查询字符串参数。 使用此参数列表可指定此窗体应接受的参数，以支持将使用查询字符串向窗体传递数据的代码。<br /><br /> 将检查数据的名称和类型；如果向窗体传递了无效的查询字符串参数，窗体不会打开。<br /><br />**注意：** 该名称也不能以下划线 (_) 或 crm\_ 开头。 必须以字母数字字符加下划线 (\_) 开头。 例如，parameter_1 或 1_parameter。 名称不能包含连字符 (-)、冒号 (:)、分号 (;)、逗号 (,) 或句点 (.)。 <br /><br />|  
|**非事件依赖项**|**从属字段**|每个事件处理程序都有类似的**从属字段** 属性，以便注册脚本所需的任何字段。 任何人都将无法删除从属字段。<br /><br /> 有些脚本在窗体上运行，但未在事件处理程序中配置。 从命令栏启动的脚本没有可注册从属字段的位置。 此窗体属性为要注册的脚本提供了一个从属字段的位置。|  

## <a name="next-steps"></a>后续步骤

[使用“主”窗体及其组件](use-main-form-and-components.md)
