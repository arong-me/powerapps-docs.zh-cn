---
title: EncodeUrl 和 PlainText 函数 | Microsoft 文档
description: PowerApps 中 EncodeUrl 和 PlainText 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c21cae9e39e3a9a1461ac3fafe576f40b70c0818
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71985014"
---
# <a name="encodeurl-and-plaintext-functions-in-powerapps"></a>PowerApps 中的 EncodeUrl 和 PlainText 函数
编码和解码字符串。

## <a name="description"></a>描述
**EncodeUrl**函数对 URL 字符串进行编码，并用% 和十六进制数替换某些非字母数字字符。  

**纯文本**函数删除 HTML 和 XML 标记，并将某些标记（如这些标记）转换为适当的符号：

* **&amp;nbsp;**
* **&amp;quot;**

这些函数的返回值是已编码或已解码的字符串。 此函数不会删除所有 HTML 和 XML 标记。 

## <a name="syntax"></a>语法
**EncodeUrl**( *String* )

* *String* - 必需。  要编码的 URL。

**PlainText**( *String* )

* *String* - 必需。 将从中去除 HTML 和 XML 标记的字符串。

## <a name="examples"></a>示例
如果文本库中显示 RSS 源，然后将该库中标签的 **[Text](../controls/properties-core.md)** 属性设置为 **ThisItem.description**，该标签可能会显示原始的 HTML 或 XML 代码，如此示例所示：

```html
    <p>We have done an unusually&nbsp;&quot;deep&quot; globalization and localization.<p>
```

如果将标签的 **[Text](../controls/properties-core.md)** 属性设置为 **PlainText(ThisItem.description)** ，将如此示例中所示显示文本：

```
    We have done an unusually "deep" globalization and localization.
```