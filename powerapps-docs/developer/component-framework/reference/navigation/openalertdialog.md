---
title: openAlertDialog |Microsoft Docs
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
ms.assetid: 4acd3f17-74c0-4de1-9326-3778ff413f1e
ms.openlocfilehash: f1f5a2a78faf3dd9c6a1d6d197fab61772969084
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72342498"
---
# <a name="openalertdialog"></a>openAlertDialog

[!INCLUDE [openalertdialog-description](includes/openalertdialog-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用

## <a name="syntax"></a>语法

`context.navigation.openAlertDialog(alertStrings, options)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|alertStrings|`AlertDialogStrings`|是|要在警报对话框中使用的字符串。 AlertDialogStrings 具有以下属性：<br/>- **文本**： `string`。 要在警报对话框中显示的消息。 <br/>- **confirmButtonLabel**： `string`。 "确认" 按钮标签。 如果未指定按钮标签，则将 **"确定"** （用户首选语言）用作按钮标签。|
|选项|`AlertDialogOptions`|是|对话框选项。 AlertDialogOptions 具有以下属性：<br/>- **高度**： `number`。 警报对话框的高度（以像素为单位）。 <br/>- **width**： `number`。 警报对话框的宽度（以像素为单位）|

## <a name="return-value"></a>返回值

类型： `Promise`

## <a name="remarks"></a>标记

请参阅[承诺](https://developer.mozilla.org/docs/Web/JavaScript/reference/Global_Objects/Promise)和[文件](https://developer.mozilla.org/docs/Web/API/File)

## <a name="example"></a>示例 

```TypeScript
context.navigation.openAlertDialog({text:"This is an alert.", confirmButtonLabel : "Yes",}).then(
        function success()
        {
            document.getElementById("openAlertDialogButton")!.innerHTML = "Alert dialog closed";
        },
        function()
        {
            document.getElementById("openAlertDialogButton")!.innerHTML = "Error in Alert Dialog";
        }
    );
```

### <a name="related-topics"></a>相关主题

[导航](../navigation.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)