---
title: 使用门户的模板标记 |MicrosoftDocs
description: 了解门户中可用的模板标记
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 4475e9e2ccc474a6eeb3e7a2e959b360b3250aa8
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543293"
---
# <a name="template-tags"></a>模板标记

模板标记以各种方式控制模板的输出，并允许将多个模板组合到一个输出中。

## <a name="include"></a>包括

按名称包含另一个模板的内容。 在 PowerApps 门户中，此其他模板的源通常为[web 模板](store-content-web-templates.md)。 这允许在多个位置重复使用常用模板片段。  

当模板包含在另一个模板中时，包含的模板将有权访问父模板中定义的任何变量。

`{% include 'My Template' %}`

还可以向 include 标记传递任意数量的命名参数。 然后，这些变量将被定义为包含的模板中的变量。

`{% include 'My Template' a:x, b:y %}`

## <a name="block"></a>模块

与扩展结合使用以提供模板继承。 请参阅扩展以供使用。

## <a name="extends"></a>延续

与 block 标记结合使用，提供了模板继承。 这允许多个模板使用共享布局，同时覆盖父布局的特定区域。

在 PowerApps 门户中，提供给标记的父模板名称通常是指[web 模板](store-content-web-templates.md)的名称。  

使用扩展时，它必须是模板中的第一个内容，并且只能后跟一个或多个块标记。

如果未重写父模板中定义的块，则将呈现其父模板中的内容（如果有）。

## <a name="comment"></a>comment

允许您将未呈现的代码保留在液体模板中。 将不会呈现块中的任何内容，并且中的任何液体代码都不会执行。

**编写**

`Hello{% comment %}, {{ user.fullname }}{% endcomment %}. My name is Charles.`

**输出**

`Hello. My name is Charles.`

## <a name="raw"></a>原材料

允许在页面上输出液体代码，而无需对其进行分析和执行。

**输出**

`Hello, {{ user.fullname }}. My name is Charles.`

### <a name="see-also"></a>另请参阅

[控制流标记](control-flow-tags.md)<br>
[迭代标记](iteration-tags.md)<br>
[变量标记](variable-tags.md)<br>
[PowerApps common data service 实体标记](portals-entity-tags.md)
