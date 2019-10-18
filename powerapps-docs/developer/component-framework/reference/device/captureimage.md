---
title: 捕获映像 |Microsoft Docs
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
ms.assetid: 1d9c0063-add2-4002-acab-1be07ca1f6b6
ms.openlocfilehash: e642af17e02334b45041df87386885536e1810af
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345672"
---
# <a name="captureimage"></a>captureImage

[!INCLUDE[./includes/captureimage-description.md](./includes/captureimage-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.device.captureImage(options)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|`options`|`Object`|否|捕获映像的选项。|

## <a name="return-value"></a>返回值

类型： `Promise<FileObject>`

请参阅[承诺](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise)和[FileObject](../fileobject.md)

## <a name="remarks"></a>标记

@No__t_0 参数对象具有以下属性：

|名称|类型|描述|
| ---|----|-----------|
|`allowEdit`|`Boolean`|指示在保存前是否编辑图像。|
|`height`|`Number`|要捕获的图像的高度。|
|`preferFrontCamera`|`Boolean`|指示是否使用设备的正面照相机捕获映像。|
|`quality`|`Number`|图像文件的质量（以百分比表示）。|
|`width`|`Number`|要捕获的图像的宽度。|


### <a name="related-topics"></a>相关主题

[装置](../device.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)