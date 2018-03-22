---
title: EncodeUrl 和 PlainText 函数 | Microsoft 文档
description: PowerApps 中 EncodeUrl 和 PlainText 函数的参考信息（包括语法和示例）
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: a511d731c8dd94c57ec9846d853fec1bef10ab0a
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="encodeurl-and-plaintext-functions-in-powerapps"></a>PowerApps 中的 EncodeUrl 和 PlainText 函数
编码和解码字符串。

## <a name="description"></a>说明
**EncodeUrl** 函数会对 URL 字符串进行编码，将非字母数字字符替换为 % 和十六进制数字。  

**PlainText** 函数会删除 HTML 和 XML 标记，将这类标记转换为相应的符号：

* **&amp;nbsp;**
* **&amp;quot;**

这些函数的返回值是已编码或已解码的字符串。   

## <a name="syntax"></a>语法
**EncodeUrl**( *String* )

* *String* - 必需。  要编码的 URL。

**PlainText**( *String* )

* *String* - 必需。 将从中去除 HTML 和 XML 标记的字符串。

## <a name="examples"></a>示例
如果文本库中显示 RSS 源，然后将该库中标签的 **[Text](../controls/properties-core.md)** 属性设置为 **ThisItem.description**，该标签可能会显示原始的 HTML 或 XML 代码，如此示例所示：

    <p>We have done an unusually&nbsp;&quot;deep&quot; globalization and localization.<p>

如果将标签的 **[Text](../controls/properties-core.md)** 属性设置为 **PlainText(ThisItem.description)**，将如此示例中所示显示文本：

    We have done an unusually "deep" globalization and localization.
