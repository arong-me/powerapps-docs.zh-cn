---
title: Resources 元素 |Microsoft Docs
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
ms.assetid: 66599c2f-6651-4b27-92da-a38897acdfb5
ms.openlocfilehash: a7df2dde98667fd0de8489943094ad6f4ff210f0
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346063"
---
# <a name="resources-element"></a>resources 元素

[!INCLUDE [resources-description](includes/resources-description.md)]

## <a name="available-for"></a>适用于

模型驱动应用和画布应用（实验性预览）

## <a name="parent-elements"></a>父元素

|元素|描述|
|--|--|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|

## <a name="child-elements"></a>子元素

|元素|描述|次数|
|--|--|--|
|[code](code.md)|[!INCLUDE [code-description](includes/code-description.md)]|1|
|[css](css.md)|[!INCLUDE [css-description](includes/css-description.md)]|0或更多|
|[img](img.md)|[!INCLUDE [img-description](includes/img-description.md)]|0或更多|
|[html](html.md)|[!INCLUDE [html-description](includes/html-description.md)]|0或更多|
|[resx](resx.md)|[!INCLUDE [resx-description](includes/resx-description.md)]|0或更多|

## <a name="example"></a>示例

```xml
<resources>
  <code path="JS_HelloWorldControl.js" order="1" />
<css path="css/JS_HelloWorldControl.css" order="1" />
        </resources>
```

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)