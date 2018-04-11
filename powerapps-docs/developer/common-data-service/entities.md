---
title: Common Data Service for Apps 实体 | Microsoft Docs
description: 了解 Common Data Service for Apps 中的可用实体。
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
ms.date: 03/19/2018
ms.author: jdaly
ms.openlocfilehash: 98f2360e29af7cb0bdf5caf041dfa13b933e6323
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="common-data-service-for-apps-entities"></a>Common Data Service for Apps 实体

提供数据存储是 Common Data Service for Apps 最重要的功能。 通用数据服务包括一组基本实体，用于提供数据结构供商业应用程序使用。 

你可以在 [Common Data Service for Apps 实体引用](reference/about-entity-reference.md)中查看这组基本实体。

## <a name="modify-entities"></a>修改实体

你可以使用多种不同方法修改实体元数据。

### <a name="use-designers"></a>使用设计器

有几种方法可以使用设计器编辑实体元数据。


|设计器  |说明  |
|---------|---------|
|powerapps.com|修改架构最简单且最常用方法是使用 [powerapps.com](https://web.powerapps.com/) 站点编辑与环境关联的通用数据服务。 此处应用的更改在非托管 Common Data Service 默认解决方案上下文中执行。 <!-- TODO: Add link to topic that describes this -->|
|Common Data Service 默认解决方案资源管理器|编辑通用数据服务时，[powerapps.com](https://web.powerapps.com/) 站点中有另一个设计器可用。 单击左下角的“高级”按钮将打开到 Common Data Service 默认解决方案的解决方案资源管理器。 |
|针对你的解决方案的解决方案资源管理器 |如果你要分发解决方案，应在用来开发解决方案的非托管解决方案上下文中创建新的实体、特性或关系。 <br /> 详细信息：[创建解决方案发布商和解决方案](introduction-solutions.md#create-a-solution-publisher-and-solution)|
|从窗体编辑器|编辑实体的模型驱动应用窗体时，可以单击“字段资源管理器”中的“新建字段”按钮。 如果你创建查找字段，需要创建一个新的实体关系来支持它。|

### <a name="import-a-solution"></a>导入解决方案

解决方案可能包含实体元数据和其他自定义组件。 将托管或非托管解决方案导入通用数据服务租户将包含这些实体，或者通过它们包含的新实体元数据扩展现有实体。

### <a name="from-a-data-source-using-power-query"></a>从使用 Power Query 的数据源

你可以创建新的实体并使用 Power Query 填充数据。 详细信息：[使用 Power Query 将数据添加到 Common Data Service 中的实体](../../maker/common-data-service/data-platform-cds-newentity-pq.md)

### <a name="use-metadata-services"></a>使用元数据服务

Common Data Service 内公开的 Web 服务包括创建、读取、写入和删除实体元数据的功能。 这些服务常用于读取元数据，因为该数据可以在运行时通知代码环境如何自定义。

详细信息：[元数据服务](use-web-services.md#metadata-services)

## <a name="entity-metadata"></a>实体元数据

数据模型是指存储在通用数据服务中的元数据。 有关架构的此数据被称为“实体元数据”。 

- [EntityMetadata 类](/dotnet/api/microsoft.xrm.sdk.metadata.entitymetadata)通过组织服务定义此数据。 
- [EntityMetadata EntityType](/dynamics365/customer-engagement/web-api/entitymetadata) 为 Web API 定义此数据。 

实体元数据包含以下信息：


|数据  |说明  |
|---------|---------|
|实体属性|每个实体有接近 100 种属性，描述如何标识它以及它的用途。  详细信息：[实体元数据](entity-metadata.md)|
|特性|实体 `Attributes` 属性是特性的集合。 每个特性有接近 50 种属性，描述如何标识它、它包含的数据类型、它的格式以及它的用途。 详细信息：[特性元数据](entity-attribute-metadata.md)|
|关系|这三个实体属性是实体间关系的集合。 这些集合包含不同的关系类型：多对多、多对一以及一对多。 详细信息：[实体关系元数据](entity-relationship-metadata.md)|
|特权|其中一个实体属性是介于 0 和 8 个特权的集合，这些特权使用与其他实体关联的唯一标识符标识可对该实体执行的数据操作类型。 这些操作包括：追加、追加到、分配、创建、删除、读取、共享和写入。|
|键|默认情况下，每个实体有一个 GUID （全局唯一标识符）特性，且 `Keys` 属性为空集合。 你可以将备用键添加到实体。 详细信息：[实体键](entity-metadata.md#entity-keys)|

> [!TIP]
> 提升对系统中实体元数据的理解可以帮助你理解通用数据服务的工作原理。 还有许多属性控制模型驱动该应用中的实体可以实现的操作。 可用于编辑元数据的设计器无法显示在元数据中找到的所有详细信息。 可以安装名为“元数据浏览器”的模型驱动应用，这样就可以查看在系统中找到的所有隐藏实体和元数据属性。 详细信息：[Dynamics 365 客户参与开发人员指南：浏览组织的元数据](/dynamics365/customer-engagement/developer/browse-your-metadata)

### <a name="see-also"></a>另请参阅

[Common Data Service for Apps 开发人员概述](overview.md)


