---
title: 类型 |Microsoft Docs
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
ms.assetid: d9fb178c-6cc6-48cc-99c0-9972e37dec3e
ms.openlocfilehash: 960f3aee9007c1bc8391ee7cf85a961234bbf3ae
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345948"
---
# <a name="type"></a>type

[!INCLUDE [type-description](includes/type-description.md)]

## <a name="available-for"></a>适用于

模型驱动应用

## <a name="parent-elements"></a>父元素

|元素|描述|
|--|--|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|

## <a name="value-element"></a>值元素

此元素包含具有以下值之一的 `string`：

[!INCLUDE [type-table](includes/type-table.md)]

### <a name="example"></a>示例

```XML
<type-group name="numbers">
      <type>Whole.None</type>
      <type>Currency</type>
      <type>FP</type>
      <type>Decimal</type>
    </type-group>
```

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)