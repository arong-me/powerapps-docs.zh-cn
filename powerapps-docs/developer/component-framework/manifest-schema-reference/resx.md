---
title: Resx 元素 |Microsoft Docs
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
ms.assetid: 38acfda3-4adc-4aa2-bb8b-f29ba572a6e5
ms.openlocfilehash: 29c89541c2519b36559ab49d2b0483f19b545573
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346017"
---
# <a name="resx-element"></a>resx 元素

[!INCLUDE [resx-description](includes/resx-description.md)]

## <a name="available-for"></a>适用于

模型驱动应用和画布应用（实验性预览）

## <a name="attributes"></a>特性

|名称|描述|类型|需要|
|--|--|--|--|
|`path`|.Resx 文件所在的相对路径|`string`|是|
|`version`|Resx 文件的当前版本|`string`|是|

## <a name="parent-elements"></a>父元素

|元素|描述|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

## <a name="example"></a>示例

```xml
<resources>
      <code path="TS_LocalizationAPI.js" order="1" />
        <css path="css/TS_LocalizationAPI.css" order="1" />
      <resx path="strings/TSLocalizationAPI.1033.resx" version="1.0.0" />
      <resx path="strings/TSLocalizationAPI.1035.resx" version="1.0.0" />
      <resx path="strings/TSLocalizationAPI.3082.resx" version="1.0.0" />
    </resources>
```

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)
