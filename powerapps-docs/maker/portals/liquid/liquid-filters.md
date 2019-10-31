---
title: 为门户使用 Liquid 筛选器 | MicrosoftDocs
description: 了解门户中的可用 liquid 筛选器。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="available-liquid-filters"></a>可用 Liquid 筛选器

Liquid 筛选器用于修改字符串、数字、变量和对象的输出。 这些筛选器使用 | 与应用到的值分隔开。

`{{ 'hal 9000' | upcase }} <!-- Output: HAL 9000 -->`

某些筛选器接受参数。 筛选器还可合并，并按从左至右的顺序应用。

```
{{ 2 | times: 2 | minus: 1 }} <!-- Output: 3 -->

{{ "Hello, " | append: user.firstname }} <!-- Output: Hello, Dave -->
```
以下部分介绍各个筛选器。 

## <a name="array-filters"></a>数组筛选器

数组筛选器用于处理[数组](liquid-types.md#array)。  

### <a name="batch"></a>批处理

将数组划分为指定大小的多个数组。

**代码**

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

将两个数组连接到一个新的数组。

指定单个项目作为参数，concat 返回包含原始数组的新数组，将指定项目作为最后元素。

**代码**

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

### <a name="except"></a>except

选择指定属性没有指定值的数组中的所有对象。 （这与 **where** 相反。）

**代码**

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

### <a name="first"></a>第一

返回数组的第一个元素。

在需要在标记内使用 first 时，也可以使用特殊点符号。

**代码**

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

按指定属性分组数组中的项目。

**代码**

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

### <a name="join"></a>join

将数组的元素与作为参数传递的字符结合。 结果是一个字符串。

**代码**

```
{% assign words = This is a run of text | split:   %}

{{ words | join: ,  }}
```

**输出**

```
This, is, a, run, of, text
```

### <a name="last"></a>最后

返回数组的最后一个元素。

在需要在标记内使用 last 时，也可以使用特殊点符号。

**代码**

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

### <a name="order_by"></a>order\_by

返回按数组元素的指定属性进行排序的数组的元素。

或者，您可以提供 desc 作为第二个参数来以降序排序元素，而不是升序。

**代码**

```
{{ entityview.records | order_by: 'fullname' | join: ', ' }}

{{ entityview.records | order_by: 'fullname', 'desc' | join: ', ' }}
```

**输出**

```
Dave Thomas, Jack Robinson, Jake Johnson, John Smith

John Smith, Jake Johnson, Jack Robinson, Dave Thomas
```

### <a name="random"></a>random

返回数组的一个随机选择的项目。

**代码**

```
{{ group1 | join: ', ' }}

{{ group1 | random }}
```

**输出**

```
John, Pete, Hannah

Pete
```

### <a name="select"></a>select

选择数组中每个项目的指定属性值，并作为数组返回这些值。

**代码**

```
{{ entityview.records | select: 'address1_city' | join: ', ' }}
```

**输出**

```
Redmond, New York
```

### <a name="shuffle"></a>shuffle

适用于数组，以随机顺序返回包含相同项目的数组。

**代码**

```
{{ group1 | join: ', ' }}

{{ group1 | shuffle | join: ', ' }}
```

**输出**

```
John, Pete, Hannah

Hannah, John, Pete
```

### <a name="size"></a>size

返回数组中的项数。

在需要在标记内使用 size 时，也可以使用特殊点符号。

**代码**

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

跳过数组中指定的项目数，并返回其余项目。

**代码**

```
{% assign words = This is a run of text | split:   %}

{{ words | skip: 3 | join: ', ' }}
```

**输出**

```
run, of, text
```

### <a name="take"></a>take

从数组中获取指定的项目数量，返回获取的项目。

**代码**

```
{% assign words = This is a run of text | split:   %}

{{ words | take: 3 | join: ', ' }}
```
**输出**

```

This, is, a
```

### <a name="then_by"></a>then\_by

将其他后续排序添加到已按 **order\_by** 排序的数组。

或者，您可以提供 desc 作为第二个参数来以降序排序元素，而不是升序。

**代码**

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

选择指定属性具有指定值的数组中的所有对象。

**代码**

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

日期筛选器可以用于日期算术或将 DateTime 值转换为不同格式。

### <a name="date"></a>日期

使用 .NET 格式字符串确定 DateTime 值的格式。

[标准日期和时间格式字符串](https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings)  

[自定义日期和时间格式字符串](https://docs.microsoft.com/en-us/dotnet/standard/base-types/custom-date-and-time-format-strings)  

**代码**

```
{{ now | date: 'g' }}

{{ now | date: 'MMMM dd, yyyy' }}
```

**输出**

```
5/7/2018 7:20 AM

May 07, 2018
```

### <a name="date_add_days"></a>date\_add\_days

添指定的整数和小数天数来确定 DateTime 值。 参数可以是正数或负数。

**代码**

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

### <a name="date_add_hours"></a>date\_add\_hours

添指定的整数和小数小时数来确定 DateTime 值。 参数可以是正数或负数。

**代码**

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

### <a name="date_add_minutes"></a>date\_add\_minutes

添指定的整数和小数分钟数来确定 DateTime 值。 参数可以是正数或负数。

**代码**

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

### <a name="date_add_months"></a>date\_add\_months

添指定的整数和小数月数来确定 DateTime 值。 参数可以是正数或负数。

**代码**

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

### <a name="date_add_seconds"></a>date\_add\_seconds

添指定的整数和小数秒数来确定 DateTime 值。 参数可以是正数或负数。

**代码**

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

### <a name="date_add_years"></a>date\_add\_years

添指定的整数和小数年数来确定 DateTime 值。 参数可以是正数或负数。

**代码**

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

### <a name="date_to_iso8601"></a>date\_to\_iso8601

根据 [ISO 8601](http://en.wikipedia.org/wiki/ISO_8601) 标准确定 DateTime 值的格式。 在创建 [*Atom 源*](http://tools.ietf.org/html/rfc4287)或 HTML5 &lt;time&gt; 元素时有用。  

**代码**

```
{{ now | date_to_iso8601 }}
```

**输出**

```
2018-05-07T07:20:46Z
```

### <a name="date_to_rfc822"></a>date\_to\_rfc822

根据 [RFC 822](https://www.ietf.org/rfc/rfc0822.txt) 标准确定 DateTime 值的格式。 在创建 [*RSS 源*](http://cyber.law.harvard.edu/rss/rss.html)时有用。  

**代码**

```
{{ now | date_to_rfc822 }}
```

**输出**

```
Mon, 07 May 2018 07:20:46 Z
```


## <a name="entity-list-filters"></a>实体列表筛选器

实体列表筛选器用于处理某些 [entitylist](liquid-objects.md#entitylist) 属性值，并帮助创建实体列表视图。  

### <a name="current_sort"></a>current\_sort

指定的排序表达式，返回指定属性的当前排序方向。

**代码**

```
{{ 'name ASC, createdon DESC' | current_sort: 'createdon' }}
```

**输出**

```
DESC
```

### <a name="metafilters"></a>metafilters

将 [entitylist](liquid-objects.md#entitylist) filter\_definition JSON 值解析为筛选器选项组对象。  

metafilters 可以有选择地随当前属性筛选器查询和当前 [entitylist](liquid-objects.md#entitylist) 提供，允许返回的筛选器对象标记为已选择或未选择。

**代码**

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

### <a name="reverse_sort"></a>reverse\_sort

指定排序方向，返回相反排序顺序。

**代码**

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

数学筛选器允许您对[数字](liquid-types.md#number)执行数学运算。  

与所有筛选器一样，数学筛选器可以累积并按从左到右的顺序进行应用。

**代码**

```
{{ 10 | times: 2 | minus: 5 | divided_by: 3 }}
```

**输出**

```
5
```

### <a name="ceil"></a>ceil

将值四舍五入到最接近的整数。

**代码**

```
{{ 4.6 | ceil }}

{{ 4.3 | ceil }}
```

**输出**

```
5

5
```

### <a name="divided_by"></a>divided\_by

用另一个数除以某个数。

**代码**

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

### <a name="floor"></a>楼层

将值四舍五入到最接近的整数。

**代码**

```
{{ 4.6 | floor }}

{{ 4.3 | floor }}
```

**输出**

```
4

4
```

### <a name="minus"></a>减

从另一个数中减去一个数。

**代码**

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

### <a name="modulo"></a>模数

用另一个数除以某个数，并返回余数。

**代码**

```
{{ 12 | modulo: 5 }}
```

**输出**

```
2
```

### <a name="plus"></a>加

将一个数添加到另一个数。

**代码**

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

### <a name="round"></a>四舍五入

将某个值四舍五入到最接近的整数或指定的小数位数。

**代码**

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

### <a name="times"></a>乘

用另一个数乘以某个数。

**代码**

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

字符串筛选器处理[字符串](liquid-types.md#string)。  

### <a name="append"></a>追加

追加字符串到其他字符串末尾。

**代码**

```
{{ 'filename' | append: '.js' }}
```

**输出**

```
filename.js
```

### <a name="capitalize"></a>**capitalize**

大写字符串的第一个字词。

**代码**

```
{{ 'capitalize me' | capitalize }}
```

**输出**

```
Capitalize Me
```

### <a name="downcase"></a>**downcase**

将字符串转换为小写。

**代码**

```
{{ 'MIxed Case TExt' | downcase }}
```

**输出**

```
mixed case text
```

### <a name="escape"></a>**escape**

HTML 换码字符串。

**代码**

```
{{ '<p>test</p>' | escape }}
```

**输出**

```
&lt;p&gt;test&lt;/p&gt;
```

### <a name="newline_to_br"></a>**newline\_to\_br**

在字符串的每个换行符处插入 &lt;br /&gt; 换行 HTML 标记。

**代码**

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

### <a name="prepend"></a>**prepend**

预置字符串到其他字符串开头。

**代码**

```
{{ 'Jane Johnson' | prepend: 'Dr. ' }}
```

**输出**

```
Dr. Jane Johnson
```

### <a name="remove"></a>**remove**

从字符串中移除所有出现的子串。

**代码**

```
{{ 'Hello, Dave. How are you, Dave?' | remove: 'Dave' }}
```

**输出**

```
Hello, . How are you, ?
```

### <a name="remove_first"></a>**remove\_first**

从字符串中移除第一个出现的子串。

**代码**

```
{{ 'Hello, Dave. How are you, Dave?' | remove_first: 'Dave' }}
```

**输出**

```
Hello, . How are you, Dave?
```

### <a name="replace"></a>**replace**

替换所有出现的含子串的字符串。

**代码**

```
{{ 'Hello, Dave. How are you, Dave?' | replace: 'Dave', 'John' }}
```

**输出**

```
Hello, John. How are you, John?
```

### <a name="replace_first"></a>**replace\_first**

替换第一个出现的包含子串的字符串。

**代码**

```
{{ 'Hello, Dave. How are you, Dave?' | replace_first: 'Dave', 'John' }}
```

**输出**

```
Hello, John. How are you, Dave?
```

### <a name="split"></a>**split**

split 筛选器将子串作为参数。 子串用作分隔符将字符串划分到数组。

**代码**

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

### <a name="strip_html"></a>**strip\_html**

从字符串剥离所有 HTML 标记。

**代码**

```
<p>Hello</p>
```

**输出**

```
Hello
```

### <a name="strip_newlines"></a>**strip\_newlines**

从字符串剥离任何换行符。

**代码**

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

### <a name="text_to_html"></a>**text\_to\_html**

将纯文本字符串格式转化为简单的 HTML。 所有文本都会是 HTML 编码，空行分隔的文本块将在段落 &lt;p&gt; 标记处换行，单个换行符将替换为 &lt;br&gt;，URL 将转换为超链接。

**代码**

```
{{ note.notetext | text_to_html }}
```

**输出**

```
<p>This is the first paragraph of notetext. It contains a URL: <a href="http://example.com/" rel="nofollow">http://example.com</a></p>

<p>This is a second paragraph.</p>
```

### <a name="truncate"></a>**truncate**

将字符串截断为指定数量的字符。 省略号 (...) 追加到字符串并包括在字符数内。

**代码**

```
{{ 'This is a long run of text.' | truncate: 10 }}
```

**输出**

```
This is...
```

### <a name="truncate_words"></a>**truncate\_words**

将字符串截断为指定数量的字词。 省略号 (...) 追加到截断的字符串。

**代码**

```
{{ 'This is a long run of text.' | truncate_words: 3 }}
```

**输出**

```
This is a...
```

### <a name="upcase"></a>**upcase**

将字符串转换为大写。

**代码**

```
{{ 'MIxed Case TExt' | upcase }}
```

**输出**

```
MIXED CASE TEXT
```

### <a name="url_escape"></a>**url\_escape**

URI 换码字符串，在 URL 中包括。

**代码**

```
{{ 'This & that//' | url_escape }}
```

**输出**

```
This+%26+that%2F%2F
```

### <a name="xml_escape"></a>**xml\_escape**

XML 换码字符串，在 XML 输出中包括。

**代码**

```
{{ '<p>test</p>' | xml_escape }}
```

**输出**

```
&lt;p&gt;test&lt;/p&gt;
```


## <a name="type-filters"></a>类型筛选器

类型筛选器允许您将一个类型的值转换为其他类型。

### <a name="boolean"></a>**boolean**

尝试将字符串值转换为布尔值。 如果值已是布尔值，它将不做更改返回。 如果值不能转换为布尔值，将返回 null。

该筛选器还会接受“打开”、“已启用”或“是”为 true，“关闭”、“禁用“和“否”为 false。

**代码**

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

### <a name="decimal"></a>**decimal**

尝试将字符串值转换为十进制数。 如果值已是十进制数，它将不做更改返回。 如果值不能转换为十进制数，将返回 null。

**代码**

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

### <a name="integer"></a>**integer**

尝试将字符串值转换为整数。 如果值已是整数，它将不做更改返回。 如果值不能转换为整数，将返回 null。

**代码**

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

### <a name="string"></a>**string**

尝试将字符串值转换为其字符串表示形式。 如果值已是字符串，它将不做更改返回。 如果值为 null，将返回 null。



## <a name="url-filters"></a>URL 筛选器

URL 筛选器允许您构建或提取部分 URL。

### <a name="add_query"></a>**add\_query**

将查询字符串参数追加到 URL。 如果参数已存在于 URL 中，将更新参数值。

如果此筛选器应用于整个绝对 URL，则将生成更新的绝对 URL。 如果将其应用于路径，则将生成更新的路径。

**代码**

```
{{ 'http://example.com/path?page=1' | add_query: 'foo', 'bar' }}

{{ '/path?page=1' | add_query: 'page', 2 }}
```

**输出**

```
http://example.com/path?page=1&foo=bar

/path?page=2
```

### <a name="base"></a>**base**

获取特定 URL 的基本 URL。

**代码**

```
{{ 'http://example.com/path?foo=bar&page=2' | base }}
```

**输出**

```
http://example.com
```

### <a name="host"></a>**host**

获取 URL 的主机部分。

**代码**

```
{{ 'http://example.com/path?foo=bar&page=2' | host }}
```

**输出**

```
example.com
```

### <a name="path"></a>**path**

获取 URL 的路径部分。

**代码**

```
{{ 'http://example.com/path?foo=bar&page=2' | path }}

{{ '/path?foo=bar&page=2' | path }}
```

**输出**

```
/path

/path
```

### <a name="path_and_query"></a>**path\_and\_query**

获取 URL 的路径和查询部分。

**代码**

```
{{ 'http://example.com/path?foo=bar&page=2' | path_and_query }}

{{ '/path?foo=bar&page=2' | path_and_query }}
```

**输出**

```
/path?foo=bar&page=2

/path?foo=bar&page=2
```

### <a name="port"></a>**port**

获取 URL 的端口号。

**代码**

```
{{ 'http://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com/path?foo=bar&page=2' | port }}

{{ 'https://example.com:9000/path?foo=bar&page=2' | port }}
```

**输出**

```
80

443

9000
```

### <a name="remove_query"></a>**remove\_query**

从 URL 中移除查询字符串参数。 如果 URL 中不存在该参数，将返回未更改的 URL。

如果此筛选器应用于整个绝对 URL，则将生成更新的绝对 URL。 如果将其应用于路径，则将生成更新的路径。

**代码**

```
{{ 'http://example.com/path?page=1' | remove_query: 'page' }}

{{ '/path?page=1' | remove_query: 'page' }}
```

**输出**

```
http://example.com/path

/path
```

### <a name="scheme"></a>**scheme**

获取 URL 的架构部分。

**代码**

```
{{ 'http://example.com/path?foo=bar&page=2' | scheme }}

{{ 'https://example.com/path?foo=bar&page=2' | scheme }}
```

**输出**

```
http

https
```


## <a name="additional-filters"></a>其他筛选器

这些筛选器提供有用的常规功能。

### <a name="default"></a>**default**

返回所有没有分派值（即 null）的变量的默认值。

**代码**

```
{{ snippets[Header] | default: 'My Website' }}
```

**输出**

```
<!-- If a snippet with the name Header returns null -->

My Website
```

### <a name="file_size"></a>**file\_size**

适用于表示多个字节的数字值，使用适当比例单位返回已设定格式的文件大小。

有时，精度参数可以传递，用以控制结果中的小数位数。 默认精度为 1。

**代码**

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

### <a name="has_role"></a>**has\_role**

应用于 [user](liquid-objects.md#user)，如果用户属于指定角色返回 true。 如果不属于返回 false。  

**代码**

```
{% assign is_admin = user | has_role: 'Administrators' %}

{% if is_admin %}

User is an administrator.

{% endif %}
```

### <a name="liquid"></a>**liquid**

作为 Liquid 代码呈现字符串。 此代码有权访问当前 Liquid 执行上下文（变量等）。

> [!Note] 
> 应小心地使用此筛选器，通常仅应适用于门户内容作者或其他可信的编写 Liquid 代码的用户的排除控件的下值。

**代码**

```
{{ page.adx_copy | liquid }}
```

### <a name="see-also"></a>另请参阅

[使用 Web 模板存储源内容](store-content-web-templates.md)  
[了解 Liquid 运算符](liquid-operators.md) 
[Liquid 类型](liquid-types.md)  
[Liquid 对象](liquid-objects.md)  
[Liquid 标记](liquid-tags.md)  
[Liquid 筛选器](liquid-filters.md)  
