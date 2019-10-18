---
title: RetrieveMultipleResponse |Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08ea66d3-b4af-44af-a3ae-cb2ebad043e8
ms.openlocfilehash: 0e5b2cad047bcf91b0c63e27c4a7ceb35c1ed538
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72341302"
---
# <a name="retrievemultipleresponse"></a>RetrieveMultipleResponse

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="properties"></a>属性

### <a name="entities"></a>条目

JSON 对象的数组，其中每个对象都表示检索到的实体记录，其中包含特性及其值。

**类型**： `Entity[]`

### <a name="nextlink"></a>nextLink

如果要检索的记录数多于请求中 `maxPageSize` 参数中指定的值，则此属性返回 URL 以返回下一组记录。

**类型**： `string`


### <a name="related-topics"></a>相关主题

[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)