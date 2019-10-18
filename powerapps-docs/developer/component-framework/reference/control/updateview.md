---
title: updateView |MicrosoftDocs
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: reference
applies_to: Dynamics 365 (online)
ms.assetid: 899d6eb3-62b4-4c1f-947c-aed1f8643caa
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: d7ac81ef617aa4e9e3564ade01bc469b0d7f5bc8
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345327"
---
# <a name="updateview"></a>updateView

[!INCLUDE[./includes/updateview-description.md](./includes/updateview-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用和画布应用（实验性预览）

## <a name="syntax"></a>语法

`updateView(context)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|快捷|`context`|是|包含由自定义程序设置的值，这些值映射到清单中定义的名称，以及实用工具函数|

## <a name="example"></a>示例

```JavaScript
MyNameSpace.JSHelloWorldControl.prototype.updateView = function (context) {
    this._labelElement.innerText = "Hello World! (JS)";
};
```

## <a name="remarks"></a>标记

将字段组件的值设置为配置字段中的原始值


### <a name="related-topics"></a>相关主题

[控件](../control.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)