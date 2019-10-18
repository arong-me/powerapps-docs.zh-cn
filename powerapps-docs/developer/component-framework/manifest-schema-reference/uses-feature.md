---
title: 使用-功能 |Microsoft Docs
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
ms.assetid: 87f5e921-4114-4710-a362-db741426a69b
ms.openlocfilehash: fe4d384c8dd53fc0f9efcf5558252984a4be74a3
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345879"
---
# <a name="uses-feature-element"></a>使用-feature 元素

指示要使用的组件的功能。

## <a name="available-for"></a>适用于

模型驱动应用

## <a name="parent-element"></a>父元素

|元素|描述|
|--|--|
|功能用法|功能使用情况元素充当使用-功能元素周围的包装器，这些元素本身允许开发人员声明其组件要使用哪些功能。 如果未定义任何使用-功能元素，则不需要使用此功能元素。|

## <a name="child-elements"></a>子元素

|元素|描述|类型|需要|
|--|--|---|----|
|路径名|组件中声明的功能的名称|`string`|是|
|必填|指示组件是否需要该功能|`boolean`|是|

### <a name="example"></a>示例 

```XML
<feature-usage>
    <uses-feature name="WebAPI" required="true" />
</feature-usage>
```

下表显示了这些设置与运行时代码中发生的情况的关系，是否可以根据清单中定义的使用情况设置调用功能函数。

|体现|如果主机支持|如果主机不支持|
|----|----|-----|
|`uses-feature name="device.captureImage" required=”true"`|`Context.device.captureImage != null`，不需要检查。|设计时出现警告。 组件加载会在运行时失败。|
|`uses-feature name="device.captureImage" required=”false"`|`Context.device.captureImage != null`|`Context.device.captureImage == null`，组件可在运行时自适应检查此情况。 |
|内容|`Context.device.captureImage == null` |`Context.device.captureImage == null` |

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)