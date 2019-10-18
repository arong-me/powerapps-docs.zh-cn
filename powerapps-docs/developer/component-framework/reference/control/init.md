---
title: init |MicrosoftDocs
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: reference
applies_to: ''
ms.assetid: 4485b7d4-c68f-4298-8676-1820eb33c1ad
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 57a5ce0d4e930184bf42502f1dc16b6a648f1292
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345488"
---
# <a name="init"></a>init

[!INCLUDE[./includes/init-description.md](./includes/init-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用和画布应用（实验性预览）

## <a name="syntax"></a>语法

`init(context,notifyOutputChanged,state,container)`

## <a name="parameters"></a>参数

| 参数名称|类型|需要|描述|
| ------------- |----|--------|-----------|
|快捷|[Context](../context.md)|是|*输入属性*，其中包含参数、组件元数据和接口函数。|
|notifyOutputChanged|`function`|否|通知框架具有新输出的方法|
|状态|`Dictionary`|否|在上一个会话中从*setControlState*保存的组件状态|
|容器|[HTMLDivElement](https://developer.mozilla.org/docs/Web/API/HTMLDivElement)|否|要呈现的 div 元素|

## <a name="example"></a>示例

```JavaScript
MyNameSpace.JSHelloWorldControl.prototype.init = function (context, notifyOutputChanged, state, container) {
    this._labelElement = document.createElement("label");
    this._labelElement.setAttribute("class", "JS_HelloWorldColor");
    container.appendChild(this._labelElement);
};
```

### <a name="related-topics"></a>相关主题

[控件](../control.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)
