---
title: 为门户使用迭代标记 |MicrosoftDocs
description: 了解门户中可用的迭代标记
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 600ddb0ac6e016acf057e592ac638b4e07ddf8ba
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976498"
---
# <a name="iteration-tags"></a>迭代标记

迭代标记用于重复运行/呈现代码块。

## <a name="for"></a>进行

重复执行代码块。 它最常用于循环访问数组或字典中的项。

在 for tag 块中， [forloop 对象](liquid-objects.md#forloop)可用。  

**编写**

```
{% for child_page in page.children %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**输出**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

### <a name="parameters"></a>参数

的的这些参数可以单独使用，也可以组合使用。

**上限**

在给定的项数后退出循环。

**编写**

```
{% for child_page in page.children limit:2 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**输出**

```
<a href=/parent/child1/>Child 1</a>

<a href=/parent/child2/>Child 2</a>
```

**抵销**

启动给定索引处的循环。

**编写**

```
{% for child_page in page.children offset:1 %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**输出**

```
<a href=/parent/child2/>Child 2</a>

<a href=/parent/child3/>Child 3</a>
```

**内**

定义要循环遍历的一系列数字。

**编写**

```
{% assign n = 4 %}

{% for i in (2..n) %}

{{ i }}

{% endfor %}

{% for i in (10..14) %}

{{ i }}

{% endfor }}
```

**输出**

```
2 3 4

10 11 12 14
```

**反向**

从最后一个项开始，按相反的顺序循环访问循环。

**编写**

```
{% for child_page in page.children reversed %}

<a href={{ child_page.url }}>{{ child_page.title }}</a>

{% endfor %}
```

**输出**

```
<a href=/parent/child3/>Child 3</a>

<a href=/parent/child2/>Child 2</a>

<a href=/parent/child1/>Child 1</a>
```

## <a name="cycle"></a>切换

循环遍历一组字符串，并按它们作为参数传递的顺序输出它们。 每次调用循环时，将输出作为参数传递的下一个字符串。

**编写**

```
{% for item in items %}

<div class={% cycle 'red', 'green', 'blue' %}> {{ item }} </div>

{% end %}
```

**输出**

```
<div class=red> Item one </div>

<div class=green> Item two </div>

<div class=blue> Item three </div>

<div class=red> Item four </div>

<div class=green> Item five</div>
```

## <a name="tablerow"></a>system.windows.documents.tablerow>

生成一个 HTML 表。 必须在打开 &lt;表中换行&gt; 并关闭 &lt;/table&gt; HTML 标记。

在 system.windows.documents.tablerow> 标记块中， [tablerowloop](liquid-objects.md#tablerowloop)可用。  

**编写**

```
<table>

{% tablerow child_page in page.children %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**输出**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

<td class=col3>

Child Page 3

</td>

<td class=col4>

Child Page 4

</td>

</tr>

</table>
```

### <a name="parameters"></a>参数

Tablerowcan 的这些参数可以单独使用，也可以组合使用。

**输出**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

</tr>

<tr class=row2>

<td class=col3>

Child Page 3

</td>

<td class=col4>

Child Page 4

</td>

</tr>

</table>
```

**编写**

```
<table>

{% tablerow child_page in page.children cols:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

指示生成的表应具有多少行。

**cols**

**上限**

在给定的项数后退出循环。

**编写**

```
<table>

{% tablerow child_page in page.children limit:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**输出**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 1

</td>

<td class=col2>

Child Page 2

</td>

</tr>

</table>

offset
```

启动给定索引处的循环。

**编写**

```
<table>

{% tablerow child_page in page.children offset:2 %}

{{ child_page.title }}

{% endtablerow %}

</table>
```

**输出**

```
<table>

<tr class=row1>

<td class=col1>

Child Page 3

</td>

<td class=col2>

Child Page 4

</td>

</tr>

</table>
```

**内**

定义要循环遍历的一系列数字。

**编写**

```
<table>

{% tablerow i in (1..3) %}

{{ i }}

{% endtablerow %}

</table>
```

### <a name="see-also"></a>另请参阅


[模板标记](template-tags.md)
[变量标记](variable-tags.md)的[控制流标记](control-flow-tags.md)
[PowerApps common data service 实体标记](portals-entity-tags.md)
