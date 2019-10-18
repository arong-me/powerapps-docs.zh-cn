---
title: Code 元素 |Microsoft Docs
description: ''
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 06/4/2018
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
ms.assetid: 44d9fcfb-0cd8-48cc-aace-dd589099dd79
ms.openlocfilehash: 2caf89a73dba006240c5bb6e8c874dfdd795d8c2
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346638"
---
# <a name="code-element"></a>代码元素

[!INCLUDE [code-description](includes/code-description.md)]

## <a name="available-for"></a>适用于

模型驱动应用和画布应用（实验性预览）

## <a name="attributes"></a>特性

|名称|描述|类型|需要|适用于|
|--|--|--|--|-----|
|`path`|放置资源文件所在位置|`String`|是|模型驱动应用和画布应用（实验预览）（试验性预览）|
|`order`|资源文件的加载顺序|`Positive integer`|是|模型驱动应用和画布应用（实验预览）（试验性预览）|

## <a name="parent-elements"></a>父元素

|元素|描述|
|--|--|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|

### <a name="example"></a>示例

```XML
<code path="TS_IncrementControl.js" order="1" />
        <css path="css/TS_IncrementControl.css" order="1" />
      <resx path="strings/TSIncrementControl.1033.resx" version="1.0.0" />
```

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)