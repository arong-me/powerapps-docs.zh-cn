---
title: PickFile |Microsoft Docs
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
ms.assetid: aae27c64-33c4-47f1-b833-4c04161c01e2
ms.openlocfilehash: a36731edc7ee5cc8edede499fc791595bc00bc8c
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72344614"
---
# <a name="pickfile"></a>pickFile

[!INCLUDE[./includes/pickfile-description.md](./includes/pickfile-description.md)]

## <a name="syntax"></a>语法

`context.device.pickFile(options)`

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|`options`|`Object`|否|用于选择文件的选项。|

## <a name="return-value"></a>返回值

类型： `Promise<FileObject[]>`

请参阅[承诺](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise)和[FileObject](../fileobject.md)

## <a name="remarks"></a>标记

@No__t_0 参数对象具有以下属性：

|名称|类型|描述|
|--|--|--|
|`accept`|`String`|要选择的图像文件类型。 有效值为 "*音频*"、"*视频*" 或 "*图像*"。|
|`allowMultipleFiles`|`Boolean`|指示是否允许选择多个文件|
|`maximumAllowedFileSize`|`Number`|要选择的文件的最大大小|


### <a name="related-topics"></a>相关主题

[装置](../device.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)