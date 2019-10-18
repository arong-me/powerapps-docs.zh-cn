---
title: Popup | Microsoft Docs
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
ms.assetid: b0af1803-ae3a-41c2-a8a5-b15970bd6f96
ms.openlocfilehash: bb28a979ac721eded06025a56588023c211ea6f9
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342199"
---
# <a name="popup"></a>Popup

[!INCLUDE [popup-description](includes/popup-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="properties"></a>属性

### <a name="closeonoutsideclick"></a>closeOnOutsideClick

指示在鼠标外单击时是否关闭弹出窗口。 如果设置为 "`false`"，则在鼠标外单击时不会关闭弹出窗口。

**类型**： `boolean`

### <a name="content"></a>Content

要插入的静态 DOM 元素。

**类型**： [HTMLElement](https://developer.mozilla.org/docs/Web/API/HTMLElement)

### <a name="id"></a>id

要设置为定位点组件（如果有）的 id。

**类型**： `string`

### <a name="name"></a>路径名

弹出项的名称。 用作打开弹出窗口的引用。

**类型**： `string`

### <a name="popuptoopen"></a>popupToOpen

应打开的弹出窗口的名称。

**类型**： `string`

### <a name="remarks"></a>标记

只应在根弹出窗口中定义。 若要打开嵌套的弹出窗口，应提供类似 `rootName.nestedName.[allOtherNestedNames]` 的字符串。 若要关闭弹出窗口，应提供空字符串。 此属性将自动传播到子节点。

## <a name="type"></a>type

弹出项的类型，在枚举 PopupType 中介绍。 对于每组弹出窗口，只能有一个 `root` 的弹出窗口。

**类型**： `enum`

@No__t_0 值是具有以下可能值的枚举

|Value|成员|
|--|--|
|1|Root|
|2|嵌|

### <a name="remarks"></a>标记

对于每组弹出窗口，只能有一个 `Root` Popup。

### <a name="related-topics"></a>相关主题

[PowerApps 组件框架 API 参考](../reference/index.md)<br/>
[PowerApps 组件框架概述](../overview.md)