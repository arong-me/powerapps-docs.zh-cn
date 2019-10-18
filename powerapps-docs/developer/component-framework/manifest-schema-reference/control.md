---
title: Control 元素 |Microsoft Docs
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
ms.assetid: 4dacd337-c9df-458e-86f3-bfb3ab543ea7
ms.openlocfilehash: aa02b89ce1e032a3cf2fdedca8f0fdf79cb84045
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72346615"
---
# <a name="control-element"></a>control 元素

[!INCLUDE [control-description](includes/control-description.md)]

## <a name="available-for"></a>适用于

模型驱动应用和画布应用（实验性预览）

## <a name="attributes"></a>特性

|名称|描述|类型|需要|适用于|
|--|--|--|--|--------|
|`namespace`|定义组件的对象原型|[!INCLUDE [alphanumerictype-description](includes/alphanumerictype-description.md)]|是|模型驱动应用和画布应用（实验预览）（试验性预览）|
|`constructor`|用于初始化对象的方法|[!INCLUDE [alphanumerictype-description](includes/alphanumerictype-description.md)]|是|模型驱动应用和画布应用（实验预览）（试验性预览）|
|`control-type`|标准|[!INCLUDE [controltype-description](includes/controltype-description.md)]|否|模型驱动应用和画布应用（实验预览）（试验性预览）|
|`description-key`|定义将在 UI 上显示的组件的说明。|`string`|否|模型驱动应用和画布应用（实验预览）（试验性预览）|
|`display-name-key`|定义显示在 UI 上的控件的名称。|`string`|是|模型驱动应用和画布应用（实验预览）（试验性预览）|
|`preview-image`|将用于自定义屏幕的图像，用于显示组件的预览。|`string`|否|模型驱动应用|
|`version`|定义[语义版本控制](https://semver.org)中定义的组件的版本|`string`|是|模型驱动应用和画布应用（实验预览）（试验性预览）|
<!--|`hidden`|定义是否应隐藏组件|[!INCLUDE [booleantype-description](includes/booleantype-description.md)]| 否|模型驱动应用|-->

## <a name="parent-elements"></a>父元素

|元素|描述|
|--|--|
|[manifest](manifest.md)|[!INCLUDE [manifest-description](includes/manifest-description.md)]|

## <a name="child-elements"></a>子元素

|元素|描述|次数|
|--|--|--|
|[data-set](data-set.md)|[!INCLUDE [data-set-description](includes/data-set-description.md)]|0或更多|
|[property](property.md)|[!INCLUDE [property-description](includes/property-description.md)]|0或更多|
|[resources](resources.md)|[!INCLUDE [resources-description](includes/resources-description.md)]|1|
|[type-group](type-group.md)|[!INCLUDE [type-group-description](includes/type-group-description.md)]|0或更多|

## <a name="example"></a>示例

```xml
<control namespace="MyNameSpace" constructor="JSHelloWorldControl" version="1.0.0"
 display-name-key="JS_HelloWorldControl_Display_Key" description-key="JS_HelloWorldControl_Desc_Key"
 control-type="standard" preview-image="img/preview.png">
</control>
  ```

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架清单架构参考](index.md)<br/>
[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)