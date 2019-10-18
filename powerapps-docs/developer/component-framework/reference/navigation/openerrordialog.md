---
title: openErrorDialog |Microsoft Docs
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
ms.assetid: 10c154b9-45a0-44ee-a621-73d6a9009c6d
ms.openlocfilehash: c3371b7c3ea8bde869acc261ab7d4fc8f28ba7da
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342429"
---
# <a name="openerrordialog"></a>openErrorDialog

[!INCLUDE [openerrordialog-description](includes/openerrordialog-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.navigation.openErrorDialog(options)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|选项|`ErrorDialogOptions`|是|错误对话框选项。 ErrorDialogOptions 具有以下属性： <br/>- **详细信息**： `String`。 有关错误的详细信息。 当你指定此项时，将在错误消息中提供 "**下载日志文件**" 按钮，单击该按钮可让用户使用此属性中指定的内容下载文本文件。<br/>- **errorCode**： `Number`。 错误代码。 如果只是设置了 errorCode，则会从服务器中自动检索错误代码的消息，并将其显示在错误对话框中。 如果指定**errorCode**值，则会显示一个错误对话框，其中包含默认错误消息。<br/>- **消息**： `String`。 要在错误对话框中显示的消息。 必须设置**错误代码**或**消息**属性。|

## <a name="return-value"></a>返回值

类型： `Promise`

## <a name="remarks"></a>标记

请参阅[承诺](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise)和[文件](https://developer.mozilla.org/docs/Web/API/File)


### <a name="related-topics"></a>相关主题

[导航](../navigation.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)