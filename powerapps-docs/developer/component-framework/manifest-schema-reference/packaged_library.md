---
title: 打包的库元素 |Microsoft Docs
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
ms.assetid: 41c50db2-3096-4990-ac2b-e702c161bf4f
ms.openlocfilehash: 011aa2ab527cc2bd16fc99842e2388a3a6b0918e
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346178"
---
# <a name="packaged_library-element"></a>packaged_library 元素

[!INCLUDE [packaged_library-description](includes/packaged_library-description.md)]

## <a name="available-for"></a>适用于

模型驱动应用

## <a name="attributes"></a>特性

|名称|描述|类型|需要|适用于|
|--|--|--|--|-------|
|`path`|放置打包库文件的位置|`string`|是|模型驱动应用|
|`version`|打包库的当前版本|`string`|是|模型驱动应用|

## <a name="parent-elements"></a>父元素

|元素|描述|
|--|--|
|[类库](library.md)|[!INCLUDE [library-description](includes/library-description.md)]|

## <a name="example"></a>示例

```xml
<resources>
    <library name="AngularJSCore" version=">=1" order="1">
    <packaged_library path="libs/angular.min.js" version="1.5.8" />
    </library>
```

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)
