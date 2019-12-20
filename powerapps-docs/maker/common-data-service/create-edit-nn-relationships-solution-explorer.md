---
title: 使用解决方案资源管理器在 Common Data Service 中创建 N:N（多对多）实体关系 | MicrosoftDocs
description: 了解如何创建多或多关系
ms.custom: ''
ms.date: 05/29/2018
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
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 8c5239874449772922ec9fa89ece7d2b3a5d7f06
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2861327"
---
# <a name="create-nn-many-to-many-entity-relationships-in-common-data-service-using-solution-explorer"></a>使用解决方案资源管理器在 Common Data Service 中创建 N:N（多对多）实体关系

解决方案资源管理器为创建和编辑 Common Data Service 的 N:N（多对多）提供一种方法。

[Power Apps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)支持配置最常见的选项，但是某些选项只能使用解决方案资源管理器设置。 详细信息：
- [创建多对多 (N:N) 实体关系](create-edit-nn-relationships.md)
- [使用 Power Apps 门户在 Common Data Service 中创建多对多实体关系](create-edit-nn-relationships-portal.md)

  
## <a name="open-solution-explorer"></a>打开解决方案资源管理器

您创建的任何自定义关系的名称中都包含自定义前缀。 这是根据您在其中工作的解决方案的解决方案发布商设置的。 如果您关心自定义前缀，请确保在非托管解决方案中工作，其中的自定义前缀是您需要的此实体的前缀。 详细信息：[更改解决方案发布商前缀](change-solution-publisher-prefix.md) 

[!INCLUDE [cc_navigate-solution-from-powerapps-portal](../../includes/cc_navigate-solution-from-powerapps-portal.md)]

## <a name="view-entity-relationships"></a>查看实体关系

在解决方案资源管理器中，展开**实体**并选择一个实体。 在该实体中，选择 **N:N 关系**。

![查看 N:N 实体关系](media/view-nn-entity-relationships-solution-explorer.png)

## <a name="create-relationships"></a>创建关系

在[查看实体关系](#view-entity-relationships)时，从命令栏选择**新建多对多关系**。

> [!NOTE]
> 如果命令不可用，实体则没有资格创建自定义关系。

![新建多对多关系窗体](media/new-nn-entity-relationship-form-solution-explorer.png)

在**其他实体**组中，在**实体名称**字段中，选择要与其创建关系的实体。 这将填充**关系定义**组中的**名称**和**关系实体名称**字段。

您可以单击![“保存实体关系”按钮](media/save-entity-icon-solution-explorer.png)来保存实体并继续编辑。 详细信息：[编辑关系](#edit-relationships)

> [!NOTE]
> 如果**名称**或**关系实体名称**值在系统中已经存在，在您保存时将会收到错误消息。 编辑值使其是唯一值，然后重试。

## <a name="edit-relationships"></a>编辑关系

在[查看实体关系](#view-entity-relationships)时，选择要编辑的实体。 

> [!NOTE]
> 托管解决方案的发布商可以阻止其解决方案一部分的关系的自定义。

在创建关系后，可以编辑以下关系属性。

> [!IMPORTANT]
> 在编辑这些属性后，必须发布自定义项，然后它们才能够在模型驱动应用程序中生效。

### <a name="edit-display-options"></a>编辑显示选项

对于**当前实体**和**其他实体**，可以编辑控制模型驱动应用程序的相关实体如何显示的显示选项字段。

|字段|说明|
|--|--|
|**显示选项**|相关实体列表应如何显示。 详细信息：[显示选项](#display-options)|
|**自定义标签**|在选择**使用自定义标签**作为**显示选项**时，请指定要使用的可本地化文本而不是复数名称。|
|**显示区域**|选择用于显示此列表的一个可用分组。 可用选项包括：**详细信息**（对于*公用*组）、**市场营销**、**销售**和**服务**。 |
|**显示顺序**|控制导航项在所选显示区域中的位置。 允许的数字范围从 10,000 开始。 具有较低值的导航窗格项出现在具有较高值的其他关系上方。|

<!-- TODO: Not sure whether Display Area or Display Order are still used anymore. Might only be used in the Outlook client?-->

#### <a name="display-options"></a>显示选项

这些是可用显示选项：

|选项|说明|
|--|--|
|**不显示**|不显示此关系的相关实体。|
|**使用自定义标签**|在选择此选项时，**自定义标签**字段将启用，以便您可以指定要使用的可本地化文本，而不是复数名称。|
|**使用复数名称**|使用为相关实体定义的复数显示名称。|

### <a name="searchable"></a>可搜索

可以通过将**可搜索**字段设置为**否**来从模型驱动应用程序中的**高级查找**中隐藏关系。

## <a name="delete-relationships"></a>删除关系

在[查看实体关系](#view-entity-relationships)时，选择要删除的实体关系并单击![删除命令](media/delete.gif)命令。

删除关系会删除创建的关系实体。 使用关系连接实体的所有数据都将丢失。

### <a name="see-also"></a>另请参阅

[创建多对多 (N:N) 实体关系](create-edit-nn-relationships.md)<br />
[使用 Power Apps 门户在 Common Data Service 中创建多对多实体关系](create-edit-nn-relationships-portal.md)<br />
[创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships.md)
