---
title: 创建并编辑 Common Data Service for Apps 的实体关系 | Microsoft Docs
ms.custom: ''
ms.date: 05/26/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- PowerApps
ms.assetid: c765b6d9-4d87-4c2d-aae2-5b1c3b664a71
caps.latest.revision: 28
ms.author: matp
manager: brycho
ms.openlocfilehash: 896b026bc72022e66e548db95f78d785e14fdf23
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39667804"
---
# <a name="create-and-edit-relationships-between-entities"></a>创建和编辑实体之间的关系 

实体关系定义记录在数据库中的相互关联。 在最简单的级别上，将查找字段添加到实体会在两个实体间创建一个新的 1:N（一对多）关系，并且你可将查找字段放置在窗体中。 使用查找字段，用户可将该实体的多个子记录与单个父实体记录相关联。  
  
除了简单地定义记录与其他记录的关联外，1:N 实体关系还提供数据以解决以下问题：  
  
- 当我删除记录时，是否还应删除与该记录相关的任何记录？  
- 当我分配记录时，是否还需将与该记录相关的所有记录分配给新的所有者？  
- 当我在现有记录的上下文中创建新的相关记录时，如何简化数据输入过程？  
- 查看记录的人员应如何查看相关记录？  
  
 实体也可参与 N:N（多对多）关系，其中两个实体的任意数量的记录可彼此关联。  

<a name="BKMK_Connections"></a>

## <a name="decide-whether-to-use-entity-relationships-or-connections"></a>决定是否使用实体关系或连接 
 
实体关系是使数据库发生更改的元数据。 通过这些关系，查询可以非常高效地检索相关数据。 使用实体关系来定义那些定义实体或大多数记录可使用的正式关系。 例如，没有潜在客户的商机毫无意义。 “商机”实体也与“竞争对手”实体具有 N:N 关系。 这便可以将多个竞争对手添加到商机中。 你可能希望捕获此数据并创建显示竞争对手的报告。  
  
记录之间存在其他不太正式的关系，称为“连接”。 例如，了解两个联系人是否结婚，他们在工作之外是否是朋友或者某个联系人是否曾为另一客户工作，可能非常有用。 大多数企业不会使用此类信息生成报告，或要求输入此类信息，因此可能不值得创建实体关系。 详细信息：[配置连接角色](configure-connection-roles.md)

  
<a name="BKMK_TypesOfRelationships"></a>
 
## <a name="types-of-entity-relationships"></a>实体关系的类型

查看解决方案资源管理器时，可能会认为有三种类型的实体关系。 实际上，只有两种，如下表所示。  
  
|关系类型|描述|  
|-----------------------|-----------------|  
|**1:N（一对多）**|“主要实体”的实体记录可以与多个其他“相关实体”记录相关联的一种实体关系，因为相关实体上的查找字段。<br /><br /> 查看主要实体记录时，可以看到与之关联的相关实体记录列表。|  
|**N:N（多对多）**|依赖于特殊“关系实体”（有时称为“相交”实体）的实体关系，所以一个实体的多个记录可以与另一个实体的多个记录相关。<br /><br /> 查看 N:N 关系中任意实体的记录时，可以看到与之相关的另一个实体的任意记录列表。|  
  
用户界面中存在 N:1（多对一）关系类型，因为设计器会显示按实体分组的视图。 1:N 关系实际存在于实体之间，将每个实体称为“主要实体”或者“相关实体”。 相关实体（有时称为“子实体”）具有查找字段，允许存储对主要实体（有时称为“父实体”）记录的引用。 N:1 关系只是从相关实体角度看待 1:N 关系。  
 
## <a name="see-also"></a>另请参阅

[实体和元数据概述](create-edit-metadata.md)<br />
[创建和编辑 1:N（一对多）或 N:1（多对一）关系](create-edit-1n-relationships.md)<br />
[创建多对多 (N:N) 实体关系](create-edit-nn-relationships.md)

