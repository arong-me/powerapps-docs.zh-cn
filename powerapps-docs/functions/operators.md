---
title: "运算符 | Microsoft 文档"
description: "PowerApps 中运算符的引用信息（包括语法和示例）"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/24/2017
ms.author: gregli
ms.openlocfilehash: 3250251e02170d2dd7bab441bc3c94705216ec00
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="operators-and-data-types-in-powerapps"></a>PowerApps 中的运算符和数据类型
其中的某些运算符依赖于作者的语言。  有关详细信息，请参阅[全局应用](../global-apps.md)。

| 符号 | 类型 | 语法 | 说明 |
| --- | --- | --- | --- |
| **.** |属性选择器 |**Slider1.Value<br>Color.Red<br>Acceleration.X** |从[表](../working-with-tables.md)、控件、[信号](signals.md) 或枚举中提取属性。  对于向后兼容性，**!** 也可以使用。 |
| **.**<br>[或 **,** [，具体取决于语言](../global-apps.md)] |小数分隔符 |**1.23**<br>[或 **1,23**，具体取决于语言] |整数和小数之间的分隔符。  字符取决于语言。 |
| **( )** |括号 |**Filter(T, A &lt; 10)**<br><br>**(1 + 2) * 3** |强制执行优先顺序和较大表达式中的组子表达式 |
| **+** |算数运算符 |**1 + 2** |加法 |
| **-** |&nbsp; |**2 - 1** |减法和减号 |
| **\*** |&nbsp; |**2 * 3** |乘法 |
| **/** |&nbsp; |**2 / 3** |除法（另请参阅 **[Mod](function-mod.md)** 函数） |
| **^** |&nbsp; |**2 ^ 3** |求幂，相当于  **[Power](function-numericals.md)**  函数 |
| **%** |&nbsp; |**20%** |百分比（相当于&quot;* 1/100&quot;） |
| **=** |比较运算符 |**Price = 100** |等于 |
| **&gt;** |&nbsp; |**Price &gt; 100** |大于 |
| **&gt;=** |&nbsp; |**Price &gt;= 100** |大于或等于 |
| **&lt;** |&nbsp; |**Price &lt; 100** |小于 |
| **&lt;=** |&nbsp; |**Price &lt;= 100** |小于或等于 |
| **&lt;&gt;** |&nbsp; |**Price &lt;&gt; 100** |不等于 |
| **&amp;** |字符串连接运算符 |**&quot;hello&quot; &amp; &quot; &quot; &amp; &quot;world&quot;** |使多个字符串连续显示 |
| &amp;&amp; 或 And |逻辑运算符 |**Price &lt; 100 &amp;&amp; Slider1.Value = 20**<br>或 Price &lt; 100 And Slider1.Value = 20 |逻辑关联，相当于 **[And](function-logicals.md)** 函数 |
| **&#124;&#124;** 或 **Or** |&nbsp; |**Price &lt; 100 &#124;&#124; Slider1.Value = 20** 或 **Price &lt; 100 Or Slider1.Value = 20** |逻辑或，相当于 **[Or](function-logicals.md)** 函数 |
| **!** 或 **Not** |&nbsp; |**!(Price &lt; 100)** 或 **Not (Price &lt; 100)** |逻辑非，相当于 **[Not](function-logicals.md)** 函数 |
| **exactin** |[成员运算符](#in-and-exactin-operators) |**Gallery1.Selected exactin SavedItems** |属于[集合](../working-with-data-sources.md#collections)或表 |
| **exactin** |&nbsp; |**&quot;Windows&quot; exactin “To display windows in the Windows operating system...”** |子字符串测试（区分大小写） |
| **in** |&nbsp; |**Gallery1.Selected in SavedItems** |属于集合或表 |
| **in** |&nbsp; |**&quot;The&quot; in &quot;The keyboard and the monitor...&quot;** |子字符串测试（不区分大小写） |
| **@** |[消除歧义运算符](#disambiguation-operator) |**MyTable[@fieldname]** |字段消除歧义 |
| **@** |&nbsp; |**[@MyVariable]** |全局消除歧义 |
| **,**<br>[或 **;** [，具体取决于语言](../global-apps.md)] |列表分隔符 |**If( X < 10, "Low", "Good" )**<br>**{ X: 12, Y: 32 }**<br>**[ 1, 2, 3 ]**<br>[or **If( X < 10; "Low"; "Good" )<br>{ FirstName: "Jane"; LastName: "Doe" }<br>[ 1; 2; 3 ]** ] |分隔： <ul><li>函数调用中的参数</li><li>[记录](../working-with-tables.md#elements-of-a-table)中的字段</li><li>[值表](../working-with-tables.md#inline-syntax)中的记录</li></ul>。  此字符取决于语言。 |
| **;**<br>[或 **;;** [，具体取决于语言](../global-apps.md)] |公式链接 |**Collect(T, A); Navigate(S1, &quot;&quot;)**<br>[or **Collect(T; A);; Navigate(S1; &quot;&quot;)**] |在行为属性中分隔函数的调用。  链接运算符取决于语言。 |
| **Parent** |[Parent 运算符](#parent-operator) |**Parent.Fill** |控件容器属性的访问权限 |
| **ThisItem** |[ThisItem 运算符](#thisitem-operator) |**ThisItem.FirstName** |库或窗体控件字段的访问权限 |

## <a name="in-and-exactin-operators"></a>in 和 exactin 运算符
可以使用 **[in](operators.md#in-and-exactin-operators)** 和 **[exactin](operators.md#in-and-exactin-operators)** 运算符查找[数据源](../working-with-data-sources.md)中的字符串，如集合或导入的表。 **[in](operators.md#in-and-exactin-operators)** 运算符标识匹配项（不区分大小写），而 **[exactin](operators.md#in-and-exactin-operators)** 运算符仅在大小写相同时标识匹配项。 下面是一个示例：

1. 创建或导入一个名为“清单”的集合，并在库中显示它，如[在库中显示图像和文本](../show-images-text-gallery-sort-filter.md)所述的第一个过程。
2. 将库的 **[Items](../controls/properties-core.md)** 属性设置为以下公式：
   <br>**Filter(Inventory, "E" in ProductName)**
   
    库显示除 Callisto 以外的所有产品，因为该产品的名称是唯一不包含你所指定的字母的产品。
3. 将库的 **[Items](../controls/properties-core.md)** 属性更改为以下公式：
   <br>**Filter(Inventory, "E" exactin ProductName)**
   
    库仅显示 Europa，因为只有它的名称中包含你所指定的字母。

## <a name="thisitem-operator"></a>ThisItem 运算符
通过将数据绑定到表或集合，可以在**[库](../controls/control-gallery.md)**、**[编辑窗体](../controls/control-form-detail.md)**或**[显示窗体](../controls/control-form-detail.md)**控件中显示数据。  这些控件是其他卡和控件的容器。  容器内的每个卡或控件均能通过 **[ThisItem](operators.md#thisitem-operator)** 运算符访问绑定的数据。   

使用 **[ThisItem](operators.md#thisitem-operator)** 运算符指定外部控件内的每个卡或控件的数据的[列](../working-with-tables.md#columns)。 例如，[在库中显示图像和文本](../show-images-text-gallery-sort-filter.md)的产品库中的运算符指定图像控件显示产品设计、上部标签显示产品名称，而下部标签显示库存单位数。

对于嵌套库，**[ThisItem](operators.md#thisitem-operator)** 指的是最里面的库的项。 假定内部和外部库的行字段不冲突，还可以直接使用未限定的字段（列）名称。 此方法启用内部库中的规则，以引用外部库的项。

## <a name="parent-operator"></a>Parent 运算符
某些控件托管其他控件。 例如，**[屏幕](../controls/control-screen.md)**、**[库](../controls/control-gallery.md)**、**[卡](../controls/control-card.md)**、**[编辑窗体](../controls/control-form-detail.md)**和**[显示窗体](../controls/control-form-detail.md)**控件都是控件的容器。 我们将托管控件称为控件内部的“父级”。

PowerApps 中的任何控件都可由应用内任何位置的名称引用。 **Screen1** 可能是应用中屏幕的名称。 若要检索此屏幕的背景色，可以使用 **Screen1.Fill**。

此屏幕上的控件具有其他选项。 它们可以使用相对引用：**Parent.Fill**。 **[Parent](operators.md#parent-operator)** 运算符指的是托管此控件，并使其所有属性可用的控件。 **[Parent](operators.md#parent-operator)**非常有用，因为它不依赖于控件的名称。 可以复制并粘贴容器控件，无需调整容器内的任何引用。 在读取公式时，此运算符还使子控件和父控件之间的关系更为明确。

## <a name="disambiguation-operator"></a>消除歧义运算符
某些函数创建[记录作用域](../working-with-tables.md#record-scope)，从而在处理每个记录时访问表的字段，例如 **Filter**、**AddColumns** 和 **Sum**。  使用记录作用域添加的字段名称将替代应用中来自其他位置的同一名称。  在此情况下，仍可以使用 **@** 消除歧义运算符访问来自记录作用域外部的值：

* 若要访问来自嵌套记录作用域的值，请使用 **@** 运算符，其中所操作的表名称使用模式 ***Table*[@*FieldName*]**。  
* 若要访问全局值，如数据源、集合和上下文变量，请使用模式 **[@*ObjectName*]**（无需指派表）。

有关详细信息和示例，请参阅[记录作用域](../working-with-tables.md#record-scope)上探讨的内容。
