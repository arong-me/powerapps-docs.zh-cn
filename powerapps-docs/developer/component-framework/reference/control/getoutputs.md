---
title: getOutputs |MicrosoftDocs
manager: kvivek
ms.date: 10/01/2019
ms.service: powerapps
ms.topic: reference
applies_to: ''
ms.assetid: c83c3a09-f04e-4dc6-8ddf-ccd0b4cc080e
ms.author: nabuthuk
author: Nkrb
ms.openlocfilehash: 408633e1fd87c3c9517ec0984251bbbce056cc50
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345373"
---
# <a name="getoutputs"></a>getOutputs

[!INCLUDE[./includes/getoutputs-description.md](./includes/getoutputs-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用和画布应用（实验性预览）

## <a name="syntax"></a>语法

`getOutputs()`

## <a name="remarks"></a>标记

输出将在清单中包含标记为 `input-output` 或 `bound` 的每个属性的值。
例如，如果清单的属性 `value` 是 `input-output`，并且你希望将该属性设置为本地变量 `myvalue` 应返回：

```javascript
{
    value: myvalue
}
```

## <a name="example"></a>示例

```javascript
MyControl.prototype.getOutputs = function () {
    var result = {
        value: this._value
    };
    return result;
};
```


### <a name="related-topics"></a>相关主题

[控件](../control.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)