---
title: Power Apps 中的实体概述 | MicrosoftDocs
description: 了解如何使用 Power Apps 门户创建和编辑实体
ms.custom: ''
ms.date: 07/25/2018
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
ms.assetid: ''
caps.latest.revision: 0
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 199c7705bd283cbc316b6a2b8056eba7f7507ea1
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "2865411"
---
# <a name="entity-relationships-overview"></a>实体关系概述

实体关系定义实体记录与其他实体记录或同一实体记录关联的方式。 有两种类型的实体关系。
- **一对多关系**。 在一对多的实体关系中，多个引用（相关的）实体记录都与单个被引用（相关的）实体记录相关。 被引用的实体记录有时指的是“父”，而引用实体记录指的是“子”。  多对一关系是一对多关系的所属角度。
- **多对多关系**。 在一个多对多实体关系中，许多实体记录与其他实体记录相关。 可以将使用多对多关系关联的记录视为对等的，并且关系是相互的。 

## <a name="see-also"></a>另请参阅
[创建实体之间的关系](data-platform-entity-lookup.md) <br/>
[使用 Power Apps 门户在 Common Data Service 中创建多对多实体关系](create-edit-nn-relationships-portal.md)
