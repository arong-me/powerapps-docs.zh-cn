---
title: 销毁 |MicrosoftDocs
ms.topic: reference
applies_to: ''
ms.assetid: ba66b513-2a7b-4ba6-b2d5-446ea2b42fdb
author: nkrb
ms.author: nabuthuk
manager: kvivek
ms.date: 10/01/2019
ms.openlocfilehash: 195a6b56ee440cebfdc46c3aa3bb3fc2b5ce3101
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72345442"
---
# <a name="destroy"></a>destroy

[!INCLUDE[./includes/destroy-description.md](./includes/destroy-description.md)]

## <a name="available-for"></a>适用于 

模型驱动应用和画布应用（实验性预览）

## <a name="syntax"></a>语法

`destroy()`

## <a name="example"></a>示例

```javascript
MyControl.prototype.destroy = function () {
 this.button.removeEventListener("click", this.onButtonClick);
};
```

### <a name="related-topics"></a>相关主题

[控件](../control.md)<br/>
[PowerApps 组件框架 API 参考](../../reference/index.md)<br/>
[PowerApps 组件框架概述](../../overview.md)