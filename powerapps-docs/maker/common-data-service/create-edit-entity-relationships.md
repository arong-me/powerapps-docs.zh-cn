---
title: Common Data Service 的实体关系概述 | MicrosoftDocs
ms.custom: ''
ms.date: 05/26/2018
ms.reviewer: ''
ms.service: powerapps
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
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="entity-relationships-overview"></a>实体关系概述

实体关系定义记录如何在数据库中相互关联。 最简单的情况是，向实体中添加查找字段将在两个实体之间形成一个新的 1:N（一对多）关系，并使您能够将该查找字段放在窗体中。 利用查找字段，用户可以将该实体的多个*子*记录与单个*父*实体记录关联。  
  
除了简单地定义记录如何相互关联以外，1:N 实体关系还提供可解决以下问题的数据：  
  
- 在删除某个记录时，是否还应删除与该记录相关的所有记录？  
- 分派记录时，是否还需将与该记录相关的所有记录分派给新负责人？  
- 在某个现有记录的上下亠中创建新的相关记录时，如何简化数据录入流程？  
- 查看某个记录的用户如何才能查看关联的记录？  
  
 实体还可以参与 N:N（多对多）关系，其中两个实体的任意数量的记录都可以彼此关联。  

<a name="BKMK_Connections"></a>

## <a name="decide-whether-to-use-entity-relationships-or-connections"></a>决定是使用实体关系还是连接 
 
实体关系是对数据库进行更改的元数据。 这些查询关系允许查询以便非常高效地检索相关数据。 使用实体关系可以定义能定义实体或者大多数记录可以使用的正式关系。 例如，没有潜在客户的商机不是非常有用。 “商机”实体还与“竞争对手”实体有 N:N 关系。 此使得可以将多个竞争添加到商机中。 您可能需要获取此数据，并创建显示竞争对手的报表。  
  
在称为*连接*的记录之间还存在其他不太正式的各种关系。 例如，了解两个联系人是否结婚，是工作外的朋友关系，或者是为另一个客户工作的联系人，可能会很有用。 大多数企业不会使用这种信息生成报表，或者要求输入此类信息，因此可能不值得创建实体关系。 详细信息：[配置连接角色](configure-connection-roles.md)

  
<a name="BKMK_TypesOfRelationships"></a>
 
## <a name="types-of-entity-relationships"></a>实体关系类型

在查看解决方案资源管理器时，可能会想到有三种类型的实体关系。 实际上，只有下表中所示的两种关系。  
  
|关系类型|说明|  
|-----------------------|-----------------|  
|**1:N（一对多）**|在这种实体关系中，**主要实体**的一个实体记录可以根据相关实体上的查找字段与多个其他**相关实体**记录关联。<br /><br /> 在查看主要实体记录时，可以看到与其关联的相关实体记录的列表。|  
|**N:N（多对多）**|依赖于特殊**关系实体**（有时称为相交实体）的实体关系，使一个实体的多个记录可以与另一个实体的多个记录关联。<br /><br /> 在查看 N:N 关系中的任一实体的记录时，可以看到与其相关的另一个实体的所有记录的列表。|  
  
**N:1（多对一）** 关系类型存在于用户界面中，因为设计器会显示按实体分组的视图。 1:N 关系实际上存在于实体*之间*，并将每个实体称为**主要实体**或**相关实体**。 相关实体（有时称为*子*实体）有一个查找字段，可用于存储对主要实体（有时称为*父*实体）中的记录的引用。 N:1 关系只是从相关实体角度来看的 1:N 关系。  
 
## <a name="see-also"></a>另请参阅

[实体和元数据概述](create-edit-metadata.md)<br />
[创建和编辑 1:N（一对多）或 N:1（多对一）关系](create-edit-1n-relationships.md)<br />
[创建多对多 (N:N) 实体关系](create-edit-nn-relationships.md)

