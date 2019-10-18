---
title: 属性集元素 |Microsoft Docs
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
ms.assetid: 996f10e5-8057-40ea-9680-555e4cd682ff
ms.openlocfilehash: 98e0bcf7588e72f001e45471c87f0050dd0846ba
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346224"
---
# <a name="property-set-element"></a>属性集元素

[!INCLUDE [property-set-description](includes/property-set-description.md)]

## <a name="available-for"></a>适用于

模型驱动应用

## <a name="attributes"></a>特性

|名称|描述|类型|需要|
|--|--|--|--|
|`name`|字段的名称|`string`|是|
|`display-name-key`|作为说明属性名称的本地化字符串用于自定义屏幕|`string`|是|
|`description-key`|作为说明属性说明的本地化字符串用于自定义屏幕|`string`|可有可无|
|`of-type`|定义属性的数据类型|请参阅 "[备注](#remarks)"|可有可无|
|`required`|指示属性是否为必需的|`boolean`|可有可无|
|`of-type-group`|清单中定义的类型组的名称|`string`|可有可无|
|`usage`|Usage 特性用于标识属性是否用于表示组件可以更改的实体属性（绑定）或只读值（输入）|`bound` 或 `input`|是|

## <a name="parent-elements"></a>父元素

|元素|描述|
|--|--|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|

## <a name="child-elements"></a>子元素

|元素|描述|次数|
|--|--|--|
|[各种](types.md)||0或更多|

### <a name="remarks"></a>标记

@No__t_0 属性值必须是下列值之一：

[!INCLUDE [type-table](includes/type-table.md)]

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)