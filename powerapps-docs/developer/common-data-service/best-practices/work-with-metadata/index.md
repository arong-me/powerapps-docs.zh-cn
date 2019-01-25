---
title: 开发人员：在处理面向应用程序的 Common Data Service 元数据时的最佳做法和指南 | Microsoft Docs
description: 在 PowerApps 中针对面向应用程序的 Common Data Service 的开发人员处理元数据时的最佳做法和指南。
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
ms.openlocfilehash: 938d3ea2337137b1c78a1f4849191a261ac7a30a
ms.sourcegitcommit: 11486fb4c16095e3fef785126003cac3e3e06c0d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/14/2019
ms.locfileid: "54271316"
---
# <a name="best-practices-and-guidance-while-working-with-metadata-for-the-common-data-service-for-apps"></a>在处理面向应用程序的 Common Data Service 元数据时的最佳做法和指南

下表中包含在面向应用程序的 Common Data Service 中处理元数据和与之交互时的所有相关指南和最佳做法。


|最佳做法  |描述  |
|---------|---------|
|[检索已发布的元数据](retrieve-published-metadata.md)     |检索未发布的元数据时，不仅将增加处理请求本身所产生的开销、降低执行速度，还会返回请求者意外之外的元数据。         |
|[通过查询 API 检索特定列是否存在实体](retrieve-specific-columns-entity-via-query-apis.md)     |已提交用来检索数据的查询应在与查询相关的 ColumnSet 实例中包含特定列（而非所有列）。         |

# <a name="see-also"></a>另请参阅
[使用代码处理元数据](../../metadata-services.md)<br />