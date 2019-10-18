---
title: Property 元素 |Microsoft Docs
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
ms.assetid: 45f4872d-c1d2-4c5a-8721-251b96ede370
ms.openlocfilehash: ee4e0b0259d5978f3e84757d4023827ada45f01e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346132"
---
# <a name="property-element"></a>property 元素

[!INCLUDE [property-description](includes/property-description.md)]

## <a name="available-for"></a>适用于

模型驱动应用和画布应用（实验性预览）

## <a name="attributes"></a>特性

|名称|描述|类型|需要|
|--|--|--|--|
|`name`|属性的名称|`string`|是|
|`display-name-key`|在自定义屏幕中用作描述属性名称的本地化字符串。|`string`|是|
|`of-type`|定义属性的数据类型|请参阅 "[备注](#remarks)"|可有可无|
|`usage`|Usage 特性用于标识属性是否用于表示组件可以更改的实体属性（绑定）或只读值（输入）|`bound` 或 `input`|可有可无|
|`required`|属性是否是必需的|`boolean`|可有可无|
|`of-type-group`|清单中定义的类型组的名称|`string`|可有可无|
|`description-key`|在自定义屏幕中用作描述属性说明的本地化字符串。|`string`|可有可无|
|`default-value`|向组件提供的默认配置值。 在模型驱动的应用中，只允许对输入使用此属性，因为绑定参数需要关联字段。|`string`|可有可无|

### <a name="remarks"></a>标记

@No__t_0 属性值必须是下列值之一：

[!INCLUDE [type-table](includes/type-table.md)]

## <a name="parent-elements"></a>父元素

|元素|描述|
|--|--|
|[manifest](manifest.md)|[!INCLUDE [manifest-description](includes/manifest-description.md)]|


## <a name="example"></a>示例

```xml
<property name="myFirstProperty" display-name-key="myFirstProperty_Display_Key" 
description-key="myFirstProperty_Desc_Key" of-type="SingleLine.Text" usage="bound" required="true" />
```

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)
