---
title: Paging | Microsoft Docs
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
ms.assetid: 12891e96-972c-4289-bbde-2bc261cd1f12
ms.openlocfilehash: ccf68c94e0b11f8a1227199609a9c21c1923ad7b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342176"
---
# <a name="paging"></a>Paging

[!INCLUDE [paging-description](includes/paging-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="properties"></a>属性

### <a name="totalresultcount"></a>totalResultCount

服务器上当前查询的结果总数。

**类型**： `number`

### <a name="hasnextpage"></a>hasNextPage

结果集是否可以向后翻页。

**类型**： `boolean`

### <a name="haspreviouspage"></a>hasPreviousPage

结果集是否可以向后翻页。

**类型**： `boolean`

## <a name="methods"></a>方法

|付款方式 | 描述 |
| ------|-------------|
|[loadNextPage](paging/loadnextpage.md)|[!INCLUDE [loadnextpage-description](paging/includes/loadnextpage-description.md)]|
|[loadPreviousPage](paging/loadpreviouspage.md)|[!INCLUDE [loadpreviouspage-description](paging/includes/loadpreviouspage-description.md)]|
|[&](paging/reset.md)|[!INCLUDE [reset-description](paging/includes/reset-description.md)]|
|[setPageSize](paging/setpagesize.md)|[!INCLUDE [setpagesize-description](paging/includes/setpagesize-description.md)]|
|pageSize|每个数据集页返回的记录数。 在窗体上，dataset pageSize 的格式设置（行数）和其他用户可以选择个人选项。|


### <a name="related-topics"></a>相关主题

[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)