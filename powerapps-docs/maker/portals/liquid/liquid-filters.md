---
title: 为门户使用液体过滤器 |MicrosoftDocs
description: 了解门户中可用的液体筛选器。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 996b31766641376e9a01cbefc876f3eb2b7aabc7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73543238"
---
# <a name="available-liquid-filters"></a>可用 Liquid 筛选器

液体过滤器用于修改字符串、数字、变量和对象的输出。 它们是由 | 将它们应用到的值。

`{{ 'hal 9000' | upcase }} <!-- Output: HAL 9000 -->`

某些筛选器接受参数。 筛选器也可以合并，并按从左至右的顺序应用。

```
{{ 2 | times: 2 | minus: 1 }} <!-- Output: 3 -->

{{ "Hello, " | append: user.firstname }} <!-- Output: Hello, Dave -->
```
以下部分介绍了各种筛选器。 

## <a name="array-filters"></a>数组筛选器

数组筛选器用于处理[数组](liquid-types.md#array)。  

### <a name="batch"></a>批处理

将一个数组分成多个具有给定大小的数组。

**编写**

```
{% assign batches = entityview.records | batch: 2 %}

{% for batch in batches %}

<ul>

{% for item in batch %}

<li>{{ item.fullname }}</li>

{% endfor %}

</ul>

{% endfor %}
```

**输出**

```
<ul>

<li>John Smith</li>

<li>Dave Thomas</li>

</ul>

<ul>

<li>Jake Johnson</li>

<li>Jack Robinson</li>

</ul>
```

### <a name="concat"></a>concat

将两个数组连接到一个新数组。

根据给定的单个项作为参数，concat 返回一个新数组，该数组包含原始数组，给定项作为最后一个元素。

**编写**

```
Group #1: {{ group1 | join: ', ' }}

Group #2: {{ group2 | join: ', ' }}

Group #1 + Group #2: {{ group1 | concat: group2 | join: ', ' }}

Group #1 + Leslie: {{ group1 | concat: 'Leslie' | join: ', ' }}
```

**输出**

```
Group #1: John, Pete, Hannah

Group #2: Joan, Bill

Group #1 + Group #2: John, Pete, Hannah, Joan, Bill

Group #1 + Leslie: John, Pete, Hannah, Leslie
```

### <a name="except"></a>只有

选择数组中给定属性不具有给定值的所有对象。 （这是**where**的反向。）

**编写**

```
{% assign redmond = entityview.records | except: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**输出**

```
Jack Robinson
```

### <a name="first"></a>1

返回数组的第一个元素。

如果需要在标记内使用，则第一种方法还可以与特殊的点表示法一起使用。

**编写**

```
{% assign words = This is a run of text | split:   %}

{{ words | first }}

{% if words.first == This %}

The first word is This.

{% endif %}
```

**输出**

```
This

The first word is This.
```

### <a name="group_by"></a>group_by

按给定属性对数组中的项进行分组。

**编写**

```
{% assign groups = entityview.records | group_by: 'address1_city' %}

{% for group in groups %}

{{ group.key }}:

{% for item in group.items %}

{{ item.fullname }}

{% endfor %}

{% endfor %}
```

**输出**

```
Redmond:

John Smith

Dave Thomas

Jake Johnson

New York:

Jack Robinson
```

### <a name="join"></a>收听

使用作为参数传递的字符来联接数组的元素。 结果是单个字符串。

**编写**

```
{% assign words = This is a run of text | split:   %}

{{ words | join: ,  }}
```

**输出**

```
This, is, a, run, of, text
```

### <a name="last"></a>时间

返回数组的最后一个元素。

如果需要在标记内使用，则最后还可以使用特殊的点表示法。

**编写**

```
{% assign words = This is a run of text | split:   -%}

{{ words | last }}

{% if words.last == text -%}

The last word is text.

{% endif -%}
```

**输出**

```
text

The last word is text.
```

### <a name="order_by"></a>排序\_

返回按数组元素的给定特性排序的数组元素。

（可选）可以提供 desc 作为第二个参数，以便按降序对元素进行排序，而不是按升序排序。

**编写**

```
{{ entityview.records | order_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'fullname', 'desc' | join: ', ' }}
```

**输出**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="random"></a>随机

返回数组中随机选择的单个项。

**编写**

```
{{ group1 | join: ', ' }}

{{ group1 | random }}
```

**输出**

```
John, Pete, Hannah

Pete
```

### <a name="select"></a>单击

为数组中的每个项选择给定属性的值，并将这些值作为数组返回。

**编写**

```
{{ entityview.records | select: 'address1_city' | join: ', ' }}
```

**输出**

```
Redmond, New York
```

### <a name="shuffle"></a>无

应用到数组，以随机顺序返回具有相同项的新数组。

**编写**

```
{{ group1 | join: ', ' }}

{{ group1 | shuffle | join: ', ' }}
```

**输出**

```
John, Pete, Hannah

Hannah, John, Pete
```

### <a name="size"></a>规格

返回数组中的项数。

如果需要在标记内使用，则大小也可以与特殊的点表示法一起使用。

**编写**

```
{% assign words = This is a run of text | split:   -%}

{{ words | size }}

{% if words.size == 6 -%}

The text contains 6 words.

{% endif -%}
```

**输出**

```
6

The text contains 6 words.
```

### <a name="skip"></a>skip

在数组中跳过给定数量的项，并返回剩余项。

**编写**

```
{% assign words = This is a run of text | split:   %}

{{ words | skip: 3 | join: ', ' }}
```

**输出**

```
run, of, text
```

### <a name="take"></a>长

从数组中获取给定数量的项，并返回所获取的项。

**编写**

```
{% assign words = This is a run of text | split:   %}

{{ words | take: 3 | join: ', ' }}
```
**输出**

```

This, is, a
```

### <a name="then_by"></a>然后\_

将其他后续排序添加到按**order\_** 排序的数组。

（可选）可以提供 desc 作为第二个参数，以便按降序对元素进行排序，而不是按升序排序。

**编写**

```
{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'address1_city' | then_by: 'fullname', 'desc' | join: ', ' }}
```

**输出**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="where"></a>其中

选择数组中给定特性具有给定值的所有对象。

**编写**

```
{% assign redmond = entityview.records | where: 'address1_city', 'Redmond' %}

{% for item in redmond %}

{{ item.fullname }}

{% endfor %}
```

**输出**

```
John Smith

Dave Thomas

Jake Johnson
```


## <a name="date-filters"></a>日期筛选器

日期筛选器可用于日期算法，或将日期时间值转换为各种格式。

### <a name="date"></a>日期

使用 .NET 格式字符串设置 DateTime 值的格式。

[标准日期和时间格式字符串](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)  

[自定义日期和时间格式字符串](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)  

**编写**

```
{{ now | date: 'g' }}

{{ now | date: 'MMMM dd, yyyy' }}
```

**输出**

```
5/7/2018 7:20 AM

May 07, 2018
```

### <a name="date_add_days"></a>添加\_天\_日期

将由整数和小数部分组成的指定天数加到 DateTime 值。 参数可以是正数也可以是负数。

**编写**

```
{{ now }}

{{ now | date_add_days: 1 }}

{{ now | date_add_days: -2.5 }}
```

**输出**

```
5/7/2018 7:20:46 AM

5/8/2018 7:20:46 AM

5/4/2018 7:20:46 PM
```

### <a name="date_add_hours"></a>添加\_小时\_日期

将由整数和小数部分组成的指定小时数添加到 DateTime 值。 参数可以是正数也可以是负数。

**编写**

```
{{ now }}

{{ now | date_add_hours: 1 }}

{{ now | date_add_hours: -2.5 }}
```

**输出**

```
5/7/2018 7:20:46 AM

5/7/2018 8:20:46 AM

5/7/2018 4:50:46 AM
```

### <a name="date_add_minutes"></a>添加\_分钟\_日期

将由整数和小数部分组成的指定分钟数添加到 DateTime 值。 参数可以是正数也可以是负数。

**编写**

```
{{ now }}

{{ now | date_add_minutes: 10 }}

{{ now | date_add_minutes: -2.5 }}
```


**输出**

```
5/7/2018 7:20:46 AM

5/7/2018 7:30:46 AM

5/7/2018 7:18:16 AM
```

### <a name="date_add_months"></a>添加\_个月\_日期

将指定的整月数加到 DateTime 值。 参数可以是正数也可以是负数。

**编写**

```
{{ now }}

{{ now | date_add_months: 1 }}

{{ now | date_add_months: -2 }}
```

**输出**

```
5/7/2018 7:20:46 AM

6/7/2018 7:20:46 AM

3/7/2018 7:20:46 AM
```

### <a name="date_add_seconds"></a>添加\_秒\_日期

将由整数和小数部分组成的指定秒数加到 DateTime 值。 参数可以是正数也可以是负数。

**编写**

```
{{ now }}

{{ now | date_add_seconds: 10 }}

{{ now | date_add_seconds: -1.25 }}
```

**输出**

```
5/7/2018 7:20:46 AM

5/7/2018 7:20:56 AM

5/7/2018 7:20:45 AM
```

### <a name="date_add_years"></a>添加\_年\_日期

将指定的整年数加到 DateTime 值。 参数可以是正数也可以是负数。

**编写**

```
{{ now }}

{{ now | date_add_years: 1 }}

{{ now | date_add_years: -2 }}
```

**输出**

```
5/7/2018 7:20:46 AM

5/7/2019 7:20:46 AM

5/7/2016 7:20:46 AM
```

### <a name="date_to_iso8601"></a>\_iso8601 的日期\_

根据[ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)标准设置日期时间值的格式。 创建[*Atom 馈送*](https://tools.ietf.org/html/rfc4287)或 HTML5 &lt;time&gt; 元素时非常有用。  

**编写**

```
{{ now | date_to_iso8601 }}
```

**输出**

```
2018-05-07T07:20:46Z
```

### <a name="date_to_rfc822"></a>\_rfc822 的日期\_

根据[RFC 822](https://www.ietf.org/rfc/rfc0822.txt)标准设置日期时间值的格式。 创建[*RSS 源*](https://cyber.law.harvard.edu/rss/rss.html)时非常有用。  

**编写**

```
{{ now | date_to_rfc822 }}
```

**输出**

```
Mon, 07 May 2018 07:20:46 Z
```


## <a name="entity-list-filters"></a>实体列表筛选器

实体列表筛选器用于处理某些[entitylist](liquid-objects.md#entitylist)属性值，并帮助创建实体列表视图。  

### <a name="current_sort"></a>当前\_排序

给定一个排序表达式，返回给定特性的当前排序方向。

**编写**

```
{{ 'name ASC, createdon DESC' | current_sort: 'createdon' }}
```

**输出**

```
DESC
```

### <a name="metafilters"></a>metafilters

将[entitylist](liquid-objects.md#entitylist)筛选器\_定义 JSON 值分析为筛选器选项组对象。  

metafilters 可以根据当前的属性筛选器查询和当前[entitylist](liquid-objects.md#entitylist)提供，并允许将返回的筛选器对象标记为选中或未选中。

**编写**

```
{% assign filters = entitylist | metafilters: params.mf, entityview %}
{% if filters.size > 0 %}
  <ul id=entitylist-filters>
    {% for filter in filters %}
      <li class=entitylist-filter-option-group>
        {% if filter.selection_mode == 'Single' %}
          {% assign type = 'radio' %}
        {% else %}
          {% assign type = 'checkbox' %}
        {% endif %}
        <h4 class=entitylist-filter-option-group-label
          data-filter-id={{ filter.id | h }}>
          {{ filter.label | h }}
        </h4>
        <ul>
          {% for option in filter.options %}
            <li class=entitylist-filter-option>
              {% if option.type == 'text' %}
                <div class=input-group entitylist-filter-option-text>
                  <span class=input-group-addon>
                    <span class=fa fa-filter aria-hidden=true></span>
                  </span>
                  <input class=form-control
                    type=text
                    name={{ filter.id | h }}
                    value={{ option.text | h }} />
                </div>
              {% else %}
                <div class={{ type | h }}>
                  <label>
                    <input
                      type={{ type | h }}
                      name={{ filter.id | h }}
                      value={{ option.id | h }}
                      {% if option.checked %}
                        checked=checked
                        data-checked=true{% endif %}
                      />
                    {{ option.label | h }}
                  </label>
                </div>
              {% endif %}
            </li>
          {% endfor %}
        </ul>
      </li>
    {% endfor %}
  </ul>
  <button class=btn btn-default data-serialized-query=mf data-target=#entitylist-filters>Apply Filters</button>
{% endif %}
```

### <a name="reverse_sort"></a>反向\_排序

对于排序方向，返回相反的排序方向。

**编写**

```
<!-- Sort direction is not case-sensitive -->

{{ 'ASC' | reverse_sort }}

{{ 'desc' | reverse_sort }}
```

**输出**

```
DESC

ASC
```


## <a name="math-filters"></a>数学筛选器

数学筛选器允许对[数字](liquid-types.md#number)执行数学运算。  

与所有筛选器一样，数学筛选器可以链接在一起，并按从左至右的顺序应用。

**编写**

```
{{ 10 | times: 2 | minus: 5 | divided_by: 3 }}
```

**输出**

```
5
```

### <a name="ceil"></a>ceil

将值向上舍入到最接近的整数。

**编写**

```
{{ 4.6 | ceil }}

{{ 4.3 | ceil }}
```

**输出**

```
5

5
```

### <a name="divided_by"></a>除以\_

将数字除以另一个数字。

**编写**

```
{{ 10 | divided_by: 2 }}

{{ 10 | divided_by: 3 }}

{{ 10.0 | divided_by: 3 }}
```

**输出**

```
5

3

3.333333
```

### <a name="floor"></a>突破

将值向下舍入到最接近的整数。

**编写**

```
{{ 4.6 | floor }}

{{ 4.3 | floor }}
```

**输出**

```
4

4
```

### <a name="minus"></a>差

从一个数中减去另一个数。

**编写**

```
<!-- entityview.page = 11 -->

{{ entityview.page | minus: 1 }}

{{ 10 | minus: 1.1 }}

{{ 10.1 | minus: 1 }}
```

**输出**

```
10

9

9.1
```

### <a name="modulo"></a>模

将数字除以另一个数字并返回余数。

**编写**

```
{{ 12 | modulo: 5 }}
```

**输出**

```
2
```

### <a name="plus"></a>加号

将数字添加到另一个数字。

**编写**

```
<!-- entityview.page = 11 -->

{{ entityview.page | plus: 1 }}

{{ 10 | plus: 1.1 }}

{{ 10.1 | plus: 1 }}
```

**输出**

```
12

11

11.1
```

### <a name="round"></a>圆满

将值舍入到最接近的整数或指定的小数位数。

**编写**

```
{{ 4.6 | round }}

{{ 4.3 | round }}

{{ 4.5612 | round: 2 }}
```

**输出**

```
5

4

4.56
```

### <a name="times"></a>随时

将一个数与另一个数相乘。

**编写**

```
{{ 10 | times: 2 }}

{{ 10 | times: 2.2 }}

{{ 10.1 | times: 2 }}
```

**输出**

```
20

20

20.2
```


## <a name="string-filters"></a>字符串筛选器

字符串筛选器操作[字符串](liquid-types.md#string)。  

### <a name="append"></a>附加

将一个字符串追加到另一个字符串的末尾。

**编写**

```
{{ 'filename' | append: '.js' }}
```

**输出**

```
filename.js
```

### <a name="capitalize"></a>**大写**

将字符串中的第一个单词设为大写。

**编写**

```
{{ 'capitalize me' | capitalize }}
```

**输出**

```
Capitalize Me
```

### <a name="downcase"></a>**downcase**

将字符串转换为小写。

**编写**

```
{{ 'MIxed Case TExt' | downcase }}
```

**输出**

```
mixed case text
```

### <a name="escape"></a>**esc**

HTML-对字符串进行转义。

**编写**

```
{{ '<p>test</p>' | escape }}
```

**输出**

```
&lt;p&gt;test&lt;/p&gt;
```

### <a name="newline_to_br"></a>**向\_br\_的行**

在字符串中的每个换行符处插入一个 &lt;br/&gt; 分行符 HTML 标记。

**编写**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | newline_to_br }}
```

**输出**

```
A<br />

B<br />

C<br />
```

### <a name="prepend"></a>**挂起**

在另一个字符串的开头前面预置一个字符串。

**编写**

```
{{ 'Jane Johnson' | prepend: 'Dr. ' }}
```

**输出**

```
Dr. Jane Johnson
```

### <a name="remove"></a>**取消**

删除字符串中出现的所有子字符串。

**编写**

```
{{ 'Hello, Dave. How are you, Dave?' | remove: 'Dave' }}
```

**输出**

```
Hello, . How are you, ?
```

### <a name="remove_first"></a>**删除\_首先**

从字符串中移除子字符串的第一个匹配项。

**编写**

```
{{ 'Hello, Dave. How are you, Dave?' | remove_first: 'Dave' }}
```

**输出**

```
Hello, . How are you, Dave?
```

### <a name="replace"></a>**全部**

将出现的所有字符串替换为子字符串。

**编写**

```
{{ 'Hello, Dave. How are you, Dave?' | replace: 'Dave', 'John' }}
```

**输出**

```
Hello, John. How are you, John?
```

### <a name="replace_first"></a>**首先替换\_**

用子串替换字符串的第一个匹配项。

**编写**

```
{{ 'Hello, Dave. How are you, Dave?' | replace_first: 'Dave', 'John' }}
```

**输出**

```
Hello, John. How are you, Dave?
```

### <a name="split"></a>**分割**

拆分筛选器使用子字符串作为参数。 子字符串用作将字符串拆分为数组的分隔符。

**编写**

```
{% assign words = This is a demo of the split filter | split: ' ' %}

First word: {{ words.first }}

First word: {{ words[0] }}

Second word: {{ words[1] }}

Last word: {{ words.last }}

All words: {{ words | join: ', ' }}
```

**输出**

```
First word: This

First word: This

Second word: is

Last word: filter

All words: This, is, a, demo, of, the, split, filter
```

### <a name="strip_html"></a>**去除\_html**

从字符串中去除所有 HTML 标记。

**编写**

```
<p>Hello</p>
```

**输出**

```
Hello
```

### <a name="strip_newlines"></a>**去除\_换行符**

从字符串中去除任何分行符。

**编写**

```
{% capture text %}

A

B

C

{% endcapture %}

{{ text | strip_newlines }}
```

**输出**

```
ABC
```

### <a name="text_to_html"></a>**\_html 的文本\_**

将纯文本字符串的格式设置为简单的 HTML。 所有文本都将经过 HTML 编码，以空行分隔的文本块将换行 &lt;p&gt; 标记中，将用 &lt;br&gt;替换单个换行符，并将 Url 转换为超链接。

**编写**

```
{{ note.notetext | text_to_html }}
```

**输出**

```
<p>This is the first paragraph of notetext. It contains a URL: <a href="https://example.com/" rel="nofollow">https://example.com</a></p>

<p>This is a second paragraph.</p>
```

### <a name="truncate"></a>**去**

将字符串截断到给定数量的字符。 省略号（...）追加到字符串，并包含在字符计数中。

**编写**

```
{{ 'This is a long run of text.' | truncate: 10 }}
```

**输出**

```
This is...
```

### <a name="truncate_words"></a>**截断\_字词**

将字符串截断到给定数量的单词。 省略号（...）将追加到截断后的字符串中。

**编写**

```
{{ 'This is a long run of text.' | truncate_words: 3 }}
```

**输出**

```
This is a...
```

### <a name="upcase"></a>**upcase**

将字符串转换为大写。

**编写**

```
{{ 'MIxed Case TExt' | upcase }}
```

**输出**

```
MIXED CASE TEXT
```

### <a name="url_escape"></a>**url\_转义**

对字符串进行 URI 转义，使其包含在 URL 中。

**编写**

```
{{ 'This & that//' | url_escape }}
```

**输出**

```
This+%26+that%2F%2F
```

### <a name="xml_escape"></a>**xml\_escape**

XML-为包含在 XML 输出中的转义字符串。

**编写**

```
{{ '<p>test</p>' | xml_escape }}
```

**输出**

```
&lt;p&gt;test&lt;/p&gt;
```


## <a name="type-filters"></a>类型筛选器

类型筛选器允许您将一种类型的值转换为其他类型。

### <a name="boolean"></a>**变量**

尝试将字符串值转换为布尔值。 如果该值已经是布尔值，则将返回未更改的值。 如果值不能转换为布尔值，则将返回 null。

此筛选器还将接受 "打开"、"已启用" 或 "是" 作为 true、"关闭"、"禁用" 和 "否" 为 false。

**编写**

```
{{ true | boolean }}

{{ 'false' | boolean }}

{{ 'enabled' | boolean }}

{{ settings['something/enabled'] | boolean | default: false }}
```

**输出**

```
true

false

true

false
```

### <a name="decimal"></a>**式**

尝试将字符串值转换为十进制数字。 如果该值已经是一个十进制数，则返回的值将保持不变。 如果值不能转换为十进制数，则返回 null。

**编写**

```
{{ 10.1 | decimal }}

{{ '3.14' | decimal }}

{{ 'text' | decimal | default: 3.14 }}
```

**输出**

```
10.1

3.14

3.14
```

### <a name="integer"></a>**整数**

尝试将字符串值转换为整数。 如果该值已经是整数，则返回的值将保持不变。 如果值不能转换为整数，则返回 null。

**编写**

```
{{ 10 | integer }}

{{ '10' | integer }}

{{ '10.1' | integer }}

{{ 'text' | integer | default: 2 }}
```

**输出**

```
10

10


2
```

### <a name="string"></a>**类似**

尝试将值转换为其字符串表示形式。 如果该值已经是字符串，则返回的值将保持不变。 如果该值为 null，则返回 null。



## <a name="url-filters"></a>URL 筛选器

URL 筛选器允许您生成或提取部分 Url。

### <a name="add_query"></a>**添加\_查询**

将查询字符串参数追加到 URL。 如果 URL 中已存在此参数，则将更新参数值。

如果将此筛选器应用于完全绝对 URL，则会生成一个更新的绝对 URL。 如果将它应用于路径，则会生成更新的路径。

**编写**

```
{{ 'https://example.com/path?page=1' | add_query: 'foo', 'bar' }}

{{ '/path?page=1' | add_query: 'page', 2 }}
```

**输出**

```
https://example.com/path?page=1&foo=bar

/path?page=2
```

### <a name="base"></a>**基座**

获取给定 URL 的基 URL。

**编写**

```
{{ 'https://example.com/path?foo=bar&page=2' | base }}
```

**输出**

```
https://example.com
```

### <a name="host"></a>**主持人**

获取 URL 的主机部分。

**编写**

```
{{ 'https://example.com/path?foo=bar&page=2' | host }}
```

**输出**

```
example.com
```

### <a name="path"></a>**通道**

获取 URL 的路径部分。

**编写**

```
{{ 'https://example.com/path?foo=bar&page=2' | path }}

{{ '/path?foo=bar&page=2' | path }}
```

**输出**

```
/path

/path
```

### <a name="path_and_query"></a>**路径\_和\_查询**

获取 URL 的路径和查询部分。

**编写**

```
{{ 'https://example.com/path?foo=bar&page=2' | path_and_query }}

{{ '/path?foo=bar&page=2' | path_and_query }}
```

**输出**

```
/path?foo=bar&page=2

/path?foo=bar&page=2
```

### <a name="port"></a>**口**

获取 URL 的端口号。

**编写**

```
{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com:9000/path?foo=bar&page=2' | port }}
```

**输出**

```
80

443

9000
```

### <a name="remove_query"></a>**删除\_查询**

从 URL 中删除查询字符串参数。 如果 URL 中不存在此参数，则将返回未更改的 URL。

如果将此筛选器应用于完全绝对 URL，则会生成一个更新的绝对 URL。 如果将它应用于路径，则会生成更新的路径。

**编写**

```
{{ 'https://example.com/path?page=1' | remove_query: 'page' }}

{{ '/path?page=1' | remove_query: 'page' }}
```

**输出**

```
https://example.com/path

/path
```

### <a name="scheme"></a>**机制**

获取 URL 的方案部分。

**编写**

```
{{ 'https://example.com/path?foo=bar&page=2' | scheme }}

{{ 'https://example.com/path?foo=bar&page=2' | scheme }}
```

**输出**

```
http

https
```


## <a name="additional-filters"></a>其他筛选器

这些筛选器提供有用的常规功能。

### <a name="default"></a>**缺省值**

返回没有赋值的任何变量的默认值（即 null）。

**编写**

```
{{ snippets[Header] | default: 'My Website' }}
```

**输出**

```
<!-- If a snippet with the name Header returns null -->

My Website
```

### <a name="file_size"></a>**文件\_大小**

应用于表示字节数的数字值后，将返回具有适当刻度单位的格式化文件大小。

还可以通过传递精度参数来控制结果中的小数位数。 默认精度为1。

**编写**

```
{{ 10000000 | file_size }}

{{ 2050 | file_size: 0 }}

{{ entity.notes.first.filesize | file_size: 2 }}
```

**输出**

```
9.5 MB

2 KB

207.14 KB
```

### <a name="has_role"></a>**具有\_角色**

应用于[用户](liquid-objects.md#user)，如果用户属于给定角色，则返回 true。 如果不是，则返回 false。  

**编写**

```
{% assign is_admin = user | has_role: 'Administrators' %}

{% if is_admin %}

User is an administrator.

{% endif %}
```

### <a name="liquid"></a>**输送**

将字符串呈现为液体代码。 此代码将具有对当前液体执行上下文（变量等）的访问权限。

> [!Note] 
> 应慎用此筛选器，并且通常只应应用于门户内容作者特有控制的值，或者只应用于可信任以编写液体代码的其他用户。

**编写**

```
{{ page.adx_copy | liquid }}
```

### <a name="see-also"></a>另请参阅

[使用 web 模板存储源内容](store-content-web-templates.md)  
[了解液体运算符](liquid-operators.md) 
[液体类型](liquid-types.md)  
[液体对象](liquid-objects.md)  
[液体标记](liquid-tags.md)  
[液体过滤器](liquid-filters.md)  
