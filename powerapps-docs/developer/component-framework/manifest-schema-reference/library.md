---
title: 库元素 |Microsoft Docs
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
ms.assetid: 90f2b4c9-7396-4ab9-bc9f-810189dc18b7
ms.openlocfilehash: bd766864e6ef971b5245afad7d49af54b9369087
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346293"
---
# <a name="library-element"></a>库元素

[!INCLUDE [library-description](includes/library-description.md)]

## <a name="attributes"></a>特性

|名称|描述|类型|需要|
|--|--|--|--|
|`name`|库的名称|`string`|是|
|`version`|当前库版本|正整数|是|
|`order`|库文件的加载顺序|正整数|是|

## <a name="parent-elements"></a>父元素

|元素|描述|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="child-elements"></a>子元素

|元素|描述|次数|
|--|--|--|
|[packaged_library]||0或更多|

## <a name="example"></a>示例

```xml
<resources>
<library name="AngularJSCore" version=">=1" order="1">
<packaged_library path="libs/angular.min.js" version="1.5.8" />
</library>
  </resources>
```

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)