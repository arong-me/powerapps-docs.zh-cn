---
title: 实体关系元数据 | Microsoft Docs
description: 了解有关 Common Data Service for Apps 中使用的实体关系元数据的信息。
services: ''
suite: powerapps
documentationcenter: na
author: JimDaly
manager: faisalmo
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/12/2018
ms.author: jdaly
ms.openlocfilehash: da8899151fdb40713d19ca1cb82444a486526549
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="entity-relationship-metadata"></a>实体关系元数据

查看解决方案资源管理器或 `EntityMetadata` 中三个关系集合时，可能会认为有三种类型的实体关系。 实际上，只有两种，如下表所示。

|关系类型|说明|
|--|--|
|一对多<br />[OneToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.onetomanyrelationshipmetadata)|“主要实体”的实体记录可以与多个其他“相关实体”记录相关联的一种实体关系，因为相关实体上的查找字段。<br />查看主要实体记录时，可以看到与之关联的相关实体记录列表。|
|多对多<br />[ManyToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.manytomanyrelationshipmetadata)|依赖于特殊“关系实体”（有时称为“相交”实体）的实体关系，所以一个实体的多个记录可以与另一个实体的多个记录相关。<br />查看“多对多”关系中任意实体的记录时，可以看到与之相关的另一个实体的任意记录列表。|

`EntityMetadata` `ManyToOneRelationships` 集合包含 [OneToManyRelationshipMetadata](/dotnet/api/microsoft.xrm.sdk.metadata.onetomanyrelationshipmetadata) 类型。 “一对多”关系存在于实体之间，将每个实体称为“主要实体”或者“相关实体”。 相关实体（有时称为“子实体”）具有查找属性，允许存储对主要实体（有时称为“父实体”）记录的引用。 “多对一”关系只是从相关实体角度看待“一对多”关系。

> [!NOTE]
> 尽管相关实体有时称为子实体，但是不要将其与表示如何将安全应用到相关实体的[子实体](entity-metadata.md#child-entities)混淆。

详细信息：
- [Dynamics 365 客户参与自定义指南：创建和编辑实体之间的关系](/dynamics365/customer-engagement/customize/create-edit-entity-relationships)
- [Dynamics 365 客户参与开发人员指南：自定义实体关系元数据](/dynamics365/customer-engagement/developer/customize-entity-relationship-metadata)

## <a name="cascade-configuration"></a>级联配置

存在“一对多”实体关系时，有级联行为可以配置为保留数据完整性并自动化业务流程。

详细信息：

- [Dynamics 365 客户参与自定义指南：创建 1:N（一对多）或 N:1（多对一）关系 > 关系行为](/dynamics365/customer-engagement/customize/create-and-edit-1n-relationships#relationship-behavior)
- [Dynamics 365 客户参与开发人员指南：实体关系行为](/dynamics365/customer-engagement/developer/entity-relationship-behavior)


## <a name="create-a-hierarchy-of-entities"></a>创建实体的层次结构

在自我引用的“一对多”关系中，可以通过将 `IsHierarchical` 属性设置为 `true` 设置层次结构。

借助模型驱动应用可以查看并与层次结构交互。 

对于开发人员，这样可以基于使用 `Under` 和 `Not Under` 运算符的层次机构启用新的查询类型。

详细信息：[Dynamics 365 客户参与开发人员指南：按层次结构查询和可视化相关数据](/dynamics365/customer-engagement/customize/query-visualize-hierarchical-data)

### <a name="see-also"></a>另请参阅

[Common Data Service for Apps 实体](entities.md)