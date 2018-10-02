---
title: 使用 PowerApps 门户创建和编辑一对多或多对一实体关系 | MicrosoftDocs
description: 了解如何使用 PowerApps 门户创建一对多或多对一实体关系
ms.custom: ''
ms.date: 06/11/2018
ms.reviewer: ''
ms.service: crm-online
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
---
# <a name="create-and-edit-one-to-many-or-many-to-one-entity-relationships-using-powerapps-portal"></a>使用 PowerApps 门户创建和编辑一对多或多对一实体关系

[PowerApps 门户](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)提供为面向应用程序的 Common Data Service 创建和编辑 1:N（一对多）或 N:1（多对一）关系的简单方法。

此门户支持配置最常见的选项，但是某些选项只能使用解决方案资源管理器设置。 详细信息： 
- [创建和编辑 1:N（一对多）或 N:1（多对一）关系](create-edit-1n-relationships.md)
- [使用解决方案资源管理器创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships-solution-explorer.md)。

## <a name="view-entity-relationships"></a>查看实体关系

1. 从 [PowerApps 门户](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，选择**模型驱动**或**画布**设计模式。
2. 选择**数据** > **实体**，然后选择具有您要查看的关系的实体。
3. 选择**关系**选项卡后，您可以选择以下视图： 

 |视图|说明|
 |--|--|
 |**所有**| 显示实体的所有关系|
 |**自定义**|仅显示实体的自定义关系|
 |**默认**|仅显示实体的标准关系|
<!-- TODO: What is the actual difference between All and Default? -->

![客户实体关系](media/view-account-relationships-portal.png)

## <a name="create-relationships"></a>创建关系

在[查看实体关系](#view-entity-relationships)时，在命令栏中，选择**添加关系**并选择**多对一**或**一对多**。

![选择关系类型](media/add-relationship-menu-portal.png)

> [!NOTE]
> 有关**多对多**关系的信息，请参阅[创建 N:N（多对多）关系](create-edit-nn-relationships.md)

<!-- This may change going forward, but this is the way it is now. #2534972 -->
> [!Important]
> 此门户使用不同于解决方案资源管理器的术语。 术语是相反的。 解决方案资源管理器**相关实体**是此门户中的**主要实体**。 同样，解决方案资源管理器中的**主要实体**是此门户中的**相关实体**。

根据您的选择，您将看到：

<!-- These are the correct screenshots from the UI as of 6/11/18 -->
|类型 |面板|
|--|--|
|**多对一**|![多对一关系面板](media/many-to-one-relationship-panel.png)|
|**一对多**|![一对多关系面板](media/one-to-many-relationship-panel.png)|

为您要在两个实体之间创建的关系选择**相关实体**或**主要实体**。 

> [!NOTE]
> 不论选择哪一项，查找字段都将在*主要*实体上创建。

在选定实体后，您可以编辑关系的详细信息。 在本示例中，多个联系人实体记录可以与单个客户关联。

<!-- These are the correct screenshots from the UI as of 6/11/18 -->
![一对多关系客户和联系人](media/One-to-many-account-contact.png)

在保存前可以编辑提供的默认值。 选择**更多选项**查看**关系名称**和**查找字段描述**值

|字段|说明|
|--|--|
|**查找字段显示名称**|将在相关实体上创建的查找字段的可本地化文本。<br />这以后可进行编辑。|
|**查找字段名称**|将在相关实体上创建的查找字段的名称。|
|**关系名称**|将创建的关系的名称。|
|**查找字段描述**|对查找字段的描述。 在模型驱动应用程序中，当用户将鼠标悬停在该字段上时，这将显示为工具提示。 <br />这以后可进行编辑。|

您可以继续编辑实体。 选择**保存实体**创建您配置的关系。

## <a name="edit-relationships"></a>编辑关系

在[查看实体关系](#view-entity-relationships)时，选择要编辑的关系。

> [!NOTE]
> 每种关系都可以在主要实体或相关实体内作为**多对一**或**一对多**关系找到。 虽然在哪个位置都可以编辑，但是同一个关系。
>
> 托管解决方案的发布商可以阻止其解决方案一部分的一些关系的自定义。

您可以编辑的字段只有**查找字段显示名称**和**查找字段描述**。 这些字段还可以在相关实体的查找字段的属性中编辑。 详细信息：[编辑字段](create-edit-field-portal.md#edit-a-field)

## <a name="delete-relationships"></a>删除关系

在[查看实体关系](#view-entity-relationships)时，选择要删的关系。

![删除实体关系](media/delete-entity-relationship-portal.png)

在单击省略号 (**...**) 时，您可以使用命令栏或行上下文菜单的**删除关系**命令。

删除关系将删除相关实体上的查找字段。

> [!NOTE]
> 您将无法删除具有依赖项的关系。 例如，如果已向相关实体的窗体添加了查找字段，则必须在删除关系前从窗体中删除字段。

### <a name="see-also"></a>另请参阅

[创建和编辑实体之间的关系](create-edit-entity-relationships.md)<br />
[创建和编辑 1:N（一对多）或 N:1（多对一）关系](create-edit-1n-relationships.md)<br />
[使用解决方案资源管理器创建和编辑 1:N（一对多）或 N:1（多对一）实体关系](create-edit-1n-relationships-solution-explorer.md)<br />
[编辑字段](create-edit-field-portal.md#edit-a-field)
