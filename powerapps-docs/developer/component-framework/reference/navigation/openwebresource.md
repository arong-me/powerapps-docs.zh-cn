---
title: openWebResource |Microsoft Docs
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
ms.assetid: 27a1e54c-71fe-450f-8f84-b4cc125970bf
ms.openlocfilehash: 577c26dd87149fabebafe32b77395029ef4df335
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342245"
---
# <a name="openwebresource"></a>openWebResource

[!INCLUDE [openwebresource-description](includes/openwebresource-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.navigation.openWebResource(name, options, data)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|路径名|`String`|是|要打开的 HTML web 资源的名称。|
|选项|`OpenWebResourceOptions`|否|用于打开 web 资源的窗口选项。 OpenWebResourceOptions 具有以下属性：<br/>- **高度**： `Number`。 窗口的高度，以像素为单位显示结果页。<br/>- **width**： `Number`。 要以像素为单位显示结果页的窗口宽度。<br/>- **openInNewWindow**： `Boolean`。 指示是否在新窗口中打开 web 资源。|
|数据|`String`|否|要传递到数据参数的数据。

### <a name="related-topics"></a>相关主题

[导航](../navigation.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)