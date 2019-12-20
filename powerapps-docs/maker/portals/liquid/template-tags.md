---
title: 为门户使用模板标记 | MicrosoftDocs
description: 了解门户中的可用模板标记
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 951b4055aa47a6fba31df5473bd517ed67c8f17d
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873209"
---
# <a name="template-tags"></a>模板标记

模板标记通过各种方式控制模板的输出，并允许将多个模板合并到单个输出。

## <a name="include"></a>包括

按名称在另一个模板中包括某个模板的内容。 在 Power Apps 门户中，此其他模板来源通常是 [Web 模板](store-content-web-templates.md)。 这允许在多个位置重用常见模板片段。  

在另一个模板中包括某个模板时，包括的模板可以访问父模板中定义的所有变量。

`{% include 'My Template' %}`

还可以将任何数量的已命名参数传递到包括标记。 然后，这些参数将定义为包括模板中的变量。

`{% include 'My Template' a:x, b:y %}`

## <a name="block"></a>阻止

与 extends 结合使用，以提供模板继承。 有关使用情况，请参阅 extends。

## <a name="extends"></a>扩展

与 block 标记结合使用，以提供模板继承。 这允许多个模板使用一个共享布局，同时替代父布局中特定区域。

在 Power Apps 门户中，提供给标记的父模板名称通常是指  [Web 模板](store-content-web-templates.md)的名称。  

使用 extends 时，它必须是模板中的第一个内容，并且仅可后跟一个或多个 block 标记。

如果未替代父模板中定义的区块，则将呈现其父模板（如果有）中的内容。

## <a name="comment"></a>评论

允许将未呈现的代码留在 Liquid 模板中。 不会呈现区块中的任何内容，也不会执行其中任何 Liquid 代码。

**代码**

`Hello{% comment %}, {{ user.fullname }}{% endcomment %}. My name is Charles.`

**输出**

`Hello. My name is Charles.`

## <a name="raw"></a>原始

允许在页面上输出 Liquid 代码，无需解析和执行。

**输出**

`Hello, {{ user.fullname }}. My name is Charles.`

## <a name="substitution"></a>替代

如果用户已启用页眉和页脚缓存，但是希望避免缓存特定节输出，可使用此标记。 此标记在其中不缓存包装的内容块的输出的页眉和页脚中提供内容块。 如果用户使用可能经常更新的对象（如请求、页面、语言和日期），这非常有用。 例如，参考[启用了页眉和页脚缓存](../configure/enable-header-footer-output-caching.md)时的页眉和页脚 Web 模板源代码更新方案。

### <a name="see-also"></a>另请参阅

[控制流标记](control-flow-tags.md)<br>
[迭代标记](iteration-tags.md)<br>
[变量标记](variable-tags.md)<br>
[Power Apps Common Data Service 实体标记](portals-entity-tags.md)
