---
title: openConfirmDialog |Microsoft Docs
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
ms.assetid: 83f2c208-696c-48b1-b65c-2ba7374d6cfc
ms.openlocfilehash: 8b7bda89b9c8d83614a4a95281853676db9cf568
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342475"
---
# <a name="openconfirmdialog"></a>openConfirmDialog

[!INCLUDE [openconfirmdialog-description](includes/openconfirmdialog-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.navigation.openConfirmDialog(confirmStrings, options)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|confirmStrings|`ConfirmDialogStrings`|是|对话框中使用的字符串。 ConfirmDialogStrings 具有以下属性：<br/>- **标题**： `String`。 要在确认对话框中显示的标题。 <br/>- **副标题**： `String`。 要在确认对话框中显示的副标题。<br/>- **文本**： `String`。 要在确认对话框中显示的消息。<br/>- **confirmButtonLabel**： `String`。 "确认" 按钮标签。 如果未指定按钮标签，则将 **"确定"** （用户首选语言）用作按钮标签。<br/>- **cancelbuttonlabel 设置**： `String` "取消" 按钮标签。 如果未指定 "取消" 按钮标签，则**取消**将用作按钮标签。|
|选项|`ConfirmDialogOptions`|否|对话框的选项。 ConfirmDialogOptions 具有以下属性：<br/>- **高度**： `Number`。 确认对话框的高度（以像素为单位）。 <br/>- **width**： `Number`。 确认对话框的宽度（以像素为单位）|

## <a name="return-value"></a>返回值

类型： `Promise<ConfirmDialogResponse>`

说明：返回一个对象，其中传递了已确认的（布尔）特性，该属性指示是否单击了 "确认" 按钮以关闭对话框。

## <a name="remarks"></a>标记

请参阅[承诺](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise) 


### <a name="related-topics"></a>相关主题

[导航](../navigation.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)