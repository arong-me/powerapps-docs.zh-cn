---
title: 为门户使用模板标记 | MicrosoftDocs
description: 了解门户中的可用模板标记
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/24/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: a152fc23b71b2e564bad28a9f1717c15acfe9a60
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "3108057"
---
# <a name="template-tags"></a>模板标记

模板标记通过各种方式控制模板的输出，并允许将多个模板合并到单个输出。

## <a name="fetchxml"></a>fetchxml

让您可以从 CDS 查询数据，并通过页面显示结果。

> [!NOTE]
> 可以在[使用 FetchXML 查询数据](https://docs.microsoft.com/powerapps/developer/common-data-service/use-fetchxml-construct-query)中了解有关使用 fetchxml 查询数据的详细信息。

```
{% fetchxml resultVariable %}
<!— Fetchxml query -->
...
{% endfetchxml %}
```

### <a name="results-attribute"></a>结果属性

提供的变量（上面的示例中为“resultVariable”）中的结果属性中存储 FetchXML 查询结果和其他一些属性。

- *实体*

    此属性中包含 fetchxml 查询的结果。 可以循环访问结果，并将其用于 Web 模板中。

    ```
    <table> 
    {% for entityVariable in resultVariable.results.entities %} 
    <tr> 
    <td>Attribut-1: {{ entityVariable.attribute1 }}</td> 
    <td>Attribut-2: {{ entityVariable.attribute2 }}</td> 
    </tr> 
    {% endfor %} 
    </table> 
    ```

- *EntityName*

    获取实体的逻辑名称。

- *延长日期*

    获取包含额外数据的结构。

- *MinActiveRowVersion*

    获取最低活动行版本值。

- *MoreRecords*

    了解是否有更多可用记录。

- *PagingCookie*

    获取当前分页信息。

- *TotalRecordCount*

    获取集合中的记录总数。 <br/>
    执行查询时，ReturnTotalRecordCount 为 true。

- *TotalRecordCountLimitExceeded*

    获取查询结果是否超过记录总计数。

### <a name="xml-attribute"></a>XML 属性

提供的变量（上面的示例中为“resultVariable”）中的 XML 属性中存储可用于从 Common Data Service 获取数据的结果查询。 当您希望了解如何对此 *fetchxml* 标记应用实体权限时，此属性对调试用途非常有用。  

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
