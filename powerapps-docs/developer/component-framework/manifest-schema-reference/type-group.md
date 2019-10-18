---
title: 类型组元素 |Microsoft Docs
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
ms.assetid: ec7c1ad4-b834-4755-8a04-2c8940f75674
ms.openlocfilehash: 7b09fad6097bb837c19116d59bb90afbde4d46b2
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345971"
---
# <a name="type-group-element"></a>类型-组元素

[!INCLUDE [type-group-description](includes/type-group-description.md)]

## <a name="available-for"></a>适用于

模型驱动应用和画布应用（实验性预览）

## <a name="attributes"></a>特性

|名称|描述|类型|需要|
|--|--|--|--|
|`name`|数据类型的名称|`string`|是|

## <a name="parent-elements"></a>父元素

|元素|描述|
|--|--|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|


## <a name="child-elements"></a>子元素

|元素|描述|次数|
|--|--|--|
|[类别](type.md)|[!INCLUDE [type-description](includes/type-description.md)]|1或更多|


在此实验性预览中，类型组对画布应用提供有限支持。 尝试导入组件时出现以下问题：

1. 如果类型组中列出的所有类型都是兼容的 javascript 类型，则开发人员尝试选择列出的最常见的选项。 被视为兼容的类型为：
   - 字符串： Regexoptions.singleline、多个、Regexoptions.singleline、Regexoptions.singleline、Regexoptions.singleline、regexoptions.singleline、Regexoptions.singleline、。
   - 数字：十进制、浮点、整。无、货币。
   - 日期： Formatting.dateandtime.custom. Formatting.dateandtime.custom，Formatting.dateandtime.custom. DateOnly。

2. 如果组中列出的类型不被视为兼容，则该参数将被视为类型组中列出的第一个类型。

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