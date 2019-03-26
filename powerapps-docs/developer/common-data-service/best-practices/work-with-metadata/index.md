---
title: 开发人员：Common Data Service 元数据处理最佳做法和指南 | Microsoft Docs
description: 面向 PowerApps 中 Common Data Service 开发人员的元数据处理最佳做法和指南。
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/12/2018
ms.author: jowells
search.audienceType:
  - developer
search.app:
  - PowerApps
  - D365CE
---

# <a name="best-practices-and-guidance-while-working-with-metadata-for-the-common-data-service"></a>Common Data Service 元数据处理最佳做法和指南

下表包含所有关于在 Common Data Service 中处理和集成元数据的指南和最佳做法。


|最佳做法  |描述  |
|---------|---------|
|[检索已发布的元数据](retrieve-published-metadata.md)     |检索未发布的元数据时，不仅将增加处理请求本身所产生的开销、降低执行速度，还会返回请求者意外之外的元数据。         |
|[通过查询 API 检索特定列是否存在实体](retrieve-specific-columns-entity-via-query-apis.md)     |已提交用来检索数据的查询应在与查询相关的 ColumnSet 实例中包含特定列（而非所有列）。         |

# <a name="see-also"></a>另请参阅
[使用代码处理元数据](../../metadata-services.md)<br />