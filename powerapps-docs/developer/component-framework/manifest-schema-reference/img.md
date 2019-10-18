---
title: Image 元素 |Microsoft Docs
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
ms.assetid: 0e776647-a4a2-42c9-85e8-62718154052f
ms.openlocfilehash: f3abd4f6a4061161a86d270f1bb4d0037632880c
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346500"
---
# <a name="img-element"></a>img 元素

[!INCLUDE [img-description](includes/img-description.md)]

## <a name="available-for"></a>适用于

模型驱动应用

## <a name="attributes"></a>特性

|名称|描述|类型|需要|适用于|
|--|--|--|--|-------|
|`path`|映像文件所在位置的相对路径 w.x.y.z 清单|`string`|是|模型驱动应用|

## <a name="parent-elements"></a>父元素

|元素|描述|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|


### <a name="example"></a>示例

```XML
<img path="img/default.png" />
```

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)