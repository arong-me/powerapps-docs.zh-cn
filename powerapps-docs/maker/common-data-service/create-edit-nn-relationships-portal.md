---
title: 使用 PowerApps 门户在 Common Data Service 中创建多对多实体关系 | MicrosoftDocs
description: 了解如何创建多或多关系
ms.custom: ''
ms.date: 06/11/2018
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
ms.openlocfilehash: 9a0a8ec96760c6816ea2b6caaf4bcc760b9852de
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2757696"
---
# <a name="create-many-to-many-entity-relationships-in-common-data-service-using-powerapps-portal"></a>使用 PowerApps 门户在 Common Data Service 中创建多对多实体关系

[PowerApps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)提供为 Common Data Service 创建和编辑多对多实体关系的简单方法。

此门户支持配置最常见的选项，但是某些选项只能使用解决方案资源管理器设置。 详细信息： 
- [创建 N:N（多对多）实体关系](create-edit-nn-relationships.md)
- [使用解决方案资源管理器在 Common Data Service 中创建 N:N（多对多）实体关系](create-edit-nn-relationships-solution-explorer.md)

## <a name="view-many-to-many-entity-relationships"></a>查看多对多实体关系

1. 从 [PowerApps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，选择**模型驱动**或**区域**设计模式。
2. 选择**数据** > **实体**，然后选择具有您要查看的关系的实体。
3. 选择**关系**选项卡后，您可以选择以下视图： 

 |视图|说明|
 |--|--|
 |**所有**| 显示实体的所有关系|
 |**自定义**|仅显示实体的自定义关系|
 |**默认**|仅显示实体的标准关系|
<!-- TODO: What is the actual difference between All and Default? -->

![客户实体关系](media/view-account-relationships-portal.png)

多对多关系将有**多对多**的**关系类型**。

> [!NOTE]
> 您查看的实体可能没有**多对多**关系。

## <a name="create-relationships"></a>创建关系

在[查看实体关系](#view-many-to-many-entity-relationships)时，在命令栏中，选择**添加关系**并选择**多对多**。

![选择关系类型](media/add-relationship-menu-portal.png)

在**多对多**面板中，选择要与当前实体关联的实体。

![包含所选客户实体的多对多面板](media/many-to-many-panel-1.png)

选择**更多选项**查看**关系名称**和**关系实体名称**字段。

![包含所选“更多选项”的多对多面板](media/many-to-many-panel-2.png)

这些字段的值根据选择的实体为您生成。

> [!NOTE]
> 若要创建包含两个相同实体的多个**多对多**关系，则需要编辑生成的**关系名称**和**关系实体名称**字段，以便其是唯一的。

选择**确定**关闭**多对多**面板。 当将更改保存到实体时，将创建关系。 

一旦保存，则不能使用 [PowerApps 门户](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)更改任何内容。 若要编辑模型驱动应用程序的关系的属性，请使用[解决方案资源管理器](create-edit-nn-relationships-solution-explorer.md)。

## <a name="delete-relationships"></a>删除关系

在[查看实体关系](#view-many-to-many-entity-relationships)时，选择要删的关系。

![删除实体关系](media/delete-entity-relationship-portal.png)

在选择省略号 (**...**) 时，您可以使用命令栏或行上下文菜单的**删除关系**命令。

删除多对多关系会删除创建的关系实体。 使用关系连接实体的所有数据都将丢失。

### <a name="see-also"></a>另请参阅

[创建 N:N（多对多）实体关系](create-edit-nn-relationships.md)<br />
[使用解决方案资源管理器在 Common Data Service 中创建 N:N（多对多）实体关系](create-edit-nn-relationships-solution-explorer.md)
