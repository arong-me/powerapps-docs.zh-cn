---
title: openFile |Microsoft Docs
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
ms.assetid: ae94e467-d12c-4a74-96f0-05a09e03c5f8
ms.openlocfilehash: 5de6eefb37450fde50127829f2a922252d08a4fb
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342682"
---
# <a name="openfile"></a>openFile

[!INCLUDE [openfile-description](includes/openfile-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.navigation.openFile(file, options)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|文件|`FileObject`|是|描述要打开的文件的对象。FileObject 具有以下属性： <br/>- **fileContent**： `String`。 文件的内容。 <br/>- **文件名**： `String`。 文件的名称。<br/>- **fileSize**： `Number`。 文件大小（KB）。 <br/>- **mimeType**： `String`。 文件 MIME 类型。|
|选项|`Object`|否|一个对象，该对象描述是否打开或保存文件。 对象具有以下特性： <br/>- **openMode**：指定1以打开;2：保存。 
如果未指定此参数，则默认情况下将传递1（开放式）。 此参数仅在统一接口上受支持。|

## <a name="return-value"></a>返回值

类型： `Promise`

## <a name="remarks"></a>标记

请参阅[承诺](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise)和[FileObject](../fileobject.md)


### <a name="related-topics"></a>相关主题

[导航](../navigation.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)