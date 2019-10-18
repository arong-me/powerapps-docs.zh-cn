---
title: CSS 元素 |Microsoft Docs
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
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: b6119424-c0a4-4412-b25c-8239da6cbe36
ms.openlocfilehash: b7c96ba2bbb3e5d6d20df92e58ef0bc4005e7d37
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346569"
---
# <a name="css-element"></a>css 元素

[!INCLUDE [css-description](includes/css-description.md)]

## <a name="available-for"></a>适用于

模型驱动应用和画布应用（实验性预览）

## <a name="attributes"></a>特性

|名称|描述|类型|需要|适用于|
|--|--|--|--|-----|
|`path`|CSS 文件所在位置的相对路径|`string`|是|模型驱动应用和画布应用（实验预览）（试验性预览）|
|`order`|CSS 文件的加载顺序|`Positive integer`|可有可无|模型驱动应用和画布应用（实验预览）（试验性预览）|

## <a name="parent-elements"></a>父元素

|元素|描述|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="example"></a>示例

```xml
<css path="css/JS_HelloWorldControl.css" order="1" />
```

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)
