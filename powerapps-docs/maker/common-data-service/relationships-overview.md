---
title: PowerApps 中的实体概述 | MicrosoftDocs
description: 了解如何使用 PowerApps 门户创建和编辑实体
ms.custom: ''
ms.date: 07/25/2018
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
ms.assetid: ''
caps.latest.revision: 0
ms.author: matp
manager: kvivek
ms.openlocfilehash: 1c45941a7b00e9393aab429d2573b2e48964a4de
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39669109"
---
# <a name="entity-relationships-overview"></a>实体关系概述

实体关系定义了将实体记录与其他实体或同一实体中的记录关联起来的方式。 有两种类型的实体关系。
- **一对多关系**。 在一对多实体关系中，可将多个引用（相关）实体记录与一个被引用（主要）实体记录关联。 某些情况下，被引用实体记录称为“父级”，而引用实体的记录则称为“子级”。  “多对一”关系就是从子级的角度看待“一对多”关系。
- **多对多关系**。 在多对多实体关系中，可将多个实体记录与多个其他实体记录关联。 通过多对多关系关联的记录可视为对等记录，且这种关系是相互的。 

## <a name="see-also"></a>另请参阅
[创建实体间的关系](data-platform-entity-lookup.md) <br/>
[使用 PowerApps 门户在 Common Data Service for Apps 中创建多对多实体关系](create-edit-nn-relationships-portal.md)