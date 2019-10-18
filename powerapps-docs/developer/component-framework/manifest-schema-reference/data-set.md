---
title: DataSet 元素 |Microsoft Docs
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
ms.assetid: 9ffe8930-b290-4252-98d4-a1195b00205f
ms.openlocfilehash: adf672b036d1f49619cbc4a5ef72661fbeebf013
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346546"
---
# <a name="data-set-element"></a>数据集元素

[!INCLUDE [data-set-description](includes/data-set-description.md)]

## <a name="attributes"></a>特性

|名称|描述|类型|需要|适用于|
|--|--|--|--|-------|
|`description-key`|定义属性的说明。|`string`|可有可无|
|`display-name-key`|定义属性的名称。|`string`|是|
|`name`|网格的名称|`string`|是|
|`cds-data-set-options`|如果设置为 true，则显示 Commandbar、ViewSelector、QuickFindSearch |`boolean`|是|

## <a name="parent-elements"></a>父元素

|元素|描述|
|--|--|
|[control](control.md)|[!INCLUDE [control-description](includes/control-description.md)]|

## <a name="example"></a>示例

```xml
 <data-set name="dataSetGrid" display-name-key="DataSetGridProperty" cds-data-set-options="displayCommandBar:true;displayViewSelector:true;displayQuickFindSearch:true">
 </data-set>
```

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)