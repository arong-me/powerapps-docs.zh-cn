---
title: 运算符和标识符 |Microsoft Docs
description: Power Apps 中的运算符和标识符的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/29/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8c7f982f4d2eca1b097a312f74aff70063bf3396
ms.sourcegitcommit: 129d004e3d33249b21e8f53e0217030b5c28b53f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2020
ms.locfileid: "78265137"
---
# <a name="operators-and-identifiers-in-power-apps"></a>Power Apps 中的运算符和标识符

其中的某些运算符依赖于作者的语言。  有关详细信息，请参阅[全局应用](../global-apps.md)。


|                               符号                                |                        类型                         |                                                                                    语法                                                                                    |                                                                                                                           说明                                                                                                                            |
|---------------------------------------------------------------------|-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                **.**                                |                  属性选择器                  |                                                               **Slider1.Value<br>Color.Red<br>Acceleration.X**                                                               |                                               从[表](../working-with-tables.md)、控件、[信号](signals.md) 或枚举中提取属性。  对于向后兼容性， **!** 也可以使用。                                                |
| **.**<br>[[依赖语言](../global-apps.md)]  |                  小数分隔符                  |                                                             **1.23**                                                           |                                                                              整数和小数之间的分隔符。 字符取决于语言。                                                                              |
|                               **( )**                               |                     括号                     |                                                               **Filter(T, A &lt; 10)**<br><br>**(1 + 2) \* 3**                                                               |                                                                                           强制执行优先顺序和较大表达式中的组子表达式                                                                                           |
|                                **+**                                |                算术运算符                 |                                                                                  **1 + 2**                                                                                   |                                                                                                                             加法                                                                                                                             |
|                                **-**                                |                       &nbsp;                        |                                                                                  **2 - 1**                                                                                   |                                                                                                                       减法和减号                                                                                                                       |
|                              *                               |                       &nbsp;                        |                                                                                  **2 \* 3**                                                                                  |                                                                                                                          乘法                                                                                                                          |
|                                **/**                                |                       &nbsp;                        |                                                                                  **2 / 3**                                                                                   |                                                                                                   除法（另请参阅 **[Mod](function-mod.md)** 函数）                                                                                                    |
|                                **^**                                |                       &nbsp;                        |                                                                                  **2 ^ 3**                                                                                   |                                                                                          求幂，相当于 **[Power](function-numericals.md)** 函数                                                                                          |
|                                **%**                                |                       &nbsp;                        |                                                                                   **20%**                                                                                    |                                                                                                         百分比（相当于&quot;\* 1/100&quot;）                                                                                                          |
|                                **=**                                |                比较运算符                 |                                                                               **Price = 100**                                                                                |                                                                                                                             等于                                                                                                                             |
|                              **&gt;**                               |                       &nbsp;                        |                                                                              **Price &gt; 100**                                                                              |                                                                                                                           大于                                                                                                                           |
|                              **&gt;=**                              |                       &nbsp;                        |                                                                             **Price &gt;= 100**                                                                              |                                                                                                                     大于或等于                                                                                                                     |
|                              **&lt;**                               |                       &nbsp;                        |                                                                              **Price &lt; 100**                                                                              |                                                                                                                            小于                                                                                                                             |
|                              **&lt;=**                              |                       &nbsp;                        |                                                                             **Price &lt;= 100**                                                                              |                                                                                                                      小于或等于                                                                                                                       |
|                            **&lt;&gt;**                             |                       &nbsp;                        |                                                                            **Price &lt;&gt; 100**                                                                            |                                                                                                                           不等于                                                                                                                           |
|                              **&amp;**                              |            字符串连接运算符            |                                                      **&quot;hello&quot; &amp; &quot; &quot; &amp; world &quot;** &quot;                                                       |                                                                                                             使多个字符串连续显示                                                                                                             |
|                      **&amp;&amp;** 或 And                      |                  逻辑运算符                  |                                       **Price &lt; 100 &amp;&amp; Slider1.Value = 20**<br>或 Price  **100 And Slider1.Value = 20&lt;**                                       |                                                                                         逻辑关联，相当于 **[And](function-logicals.md)** 函数                                                                                          |
|                     **&#124;&#124;** 或 **Or**                      |                       &nbsp;                        |                                        **Price &lt; 100 &#124;&#124; Slider1.Value = 20** 或 **Price &lt; 100 Or Slider1.Value = 20**                                        |                                                                                          逻辑或，相当于 **[Or](function-logicals.md)** 函数                                                                                          |
|                          **!** 或 **Not**                           |                       &nbsp;                        |                                                              **!(Price &lt; 100)** 或 **Not (Price &lt; 100)**                                                               |                                                                                           逻辑非，相当于 **[Not](function-logicals.md)** 函数                                                                                           |
|                             **exactin**                             |  [成员运算符](#in-and-exactin-operators)  |                                                                   **Gallery1.Selected exactin SavedItems**                                                                   |                                                                                       属于[集合](../working-with-data-sources.md#collections)或表                                                                                        |
|                             **exactin**                             |                       &nbsp;                        |                                           **&quot;Windows&quot; exactin “To display windows in the Windows operating system...”**                                            |                                                                                                                 子字符串测试（区分大小写）                                                                                                                  |
|                               **in**                                |                       &nbsp;                        |                                                                     **Gallery1.Selected in SavedItems**                                                                      |                                                                                                               属于集合或表                                                                                                               |
|                               **in**                                |                       &nbsp;                        |                                                      **&quot;The&quot; in &quot;The keyboard and the monitor...&quot;**                                                      |                                                                                                                子字符串测试（不区分大小写）                                                                                                                 |
|                                **@**                                | [消除歧义运算符](#disambiguation-operator) |                                                                           **MyTable[@fieldname]**                                                                            |                                                                                                                       字段消除歧义                                                                                                                       |
|                                **@**                                |                       &nbsp;                        |                                                                              **[@MyVariable]**                                                                               |                                                                                                                      全局消除歧义                                                                                                                       |
| **,**<br>[[依赖语言](../global-apps.md)]  |                   列表分隔符                    | **If( X < 10, "Low", "Good" )**<br>**{ X: 12, Y: 32 }**<br>**[ 1, 2, 3 ]** | 分隔： <ul><li>函数调用中的参数</li><li>[记录](../working-with-tables.md#elements-of-a-table)中的字段</li><li>[表](../working-with-tables.md#inline-value-tables)中的记录</li></ul> 此字符取决于语言。 |
| **;**<br>[[依赖语言](../global-apps.md)] |                  公式链接                   |                                     **Collect(T, A); Navigate(S1, &quot;&quot;)**                                     |                                                                          在行为属性中分隔函数的调用。 链接运算符依赖于语言。                                                                          |
|                             **Parent**                              |         [Parent 运算符](#parent-operator)         |                                                                               **Parent.Fill**                                                                                |                                                                                                           控件容器属性的访问权限                                                                                                            |
|                            **ThisItem**                             |       [ThisItem 运算符](#thisitem-operator)       |                                                                            **ThisItem.FirstName**                                                                            |                                                                                                          库或窗体控件字段的访问权限                                                                                                           |

## <a name="in-and-exactin-operators"></a>in 和 exactin 运算符
可以使用 **[in](operators.md#in-and-exactin-operators)** 和 **[exactin](operators.md#in-and-exactin-operators)** 运算符查找[数据源](../working-with-data-sources.md)中的字符串，如集合或导入的表。 **[in](operators.md#in-and-exactin-operators)** 运算符标识匹配项（不区分大小写），而 **[exactin](operators.md#in-and-exactin-operators)** 运算符仅在大小写相同时标识匹配项。 以下是一个示例：

1. 创建或导入一个名为“清单”的集合，并在库中显示它，如[在库中显示图像和文本](../show-images-text-gallery-sort-filter.md)所述的第一个过程。
2. 将库的 **[Items](../controls/properties-core.md)** 属性设置为以下公式：
   <br>**Filter(Inventory, "E" in ProductName)**

    库显示除 Callisto 以外的所有产品，因为该产品的名称是唯一不包含你所指定的字母的产品。
3. 将库的 **[Items](../controls/properties-core.md)** 属性更改为以下公式：
   <br>**Filter(Inventory, "E" exactin ProductName)**

    库仅显示 Europa，因为只有它的名称中包含你所指定的字母。

## <a name="thisitem-operator"></a>ThisItem 运算符
通过将数据绑定到表或集合，可以在 **[库](../controls/control-gallery.md)** 、 **[编辑窗体](../controls/control-form-detail.md)** 或 **[显示窗体](../controls/control-form-detail.md)** 控件中显示数据。  这些控件是其他卡和控件的容器。  容器内的每个卡或控件均能通过 **[ThisItem](operators.md#thisitem-operator)** 运算符访问绑定的数据。   

使用 **[ThisItem](operators.md#thisitem-operator)** 运算符可指定要在外部控件中的每个卡片或控件中显示的数据[列](../working-with-tables.md#columns)。 例如，[在库中显示图像和文本](../show-images-text-gallery-sort-filter.md)的产品库中的运算符指定图像控件显示产品设计、上部标签显示产品名称，而下部标签显示库存单位数。

对于嵌套库， **[ThisItem](operators.md#thisitem-operator)** 指的是最里面的库的项。 假定内部和外部库的行字段不冲突，还可以直接使用未限定的字段（列）名称。 此方法启用内部库中的规则，以引用外部库的项。

## <a name="parent-operator"></a>Parent 运算符
某些控件托管其他控件。 例如， **[屏幕](../controls/control-screen.md)** 、 **[库](../controls/control-gallery.md)** 、 **[卡](../controls/control-card.md)** 、 **[编辑窗体](../controls/control-form-detail.md)** 和 **[显示窗体](../controls/control-form-detail.md)** 控件都是控件的容器。 我们将托管控件称为控件内部的“父级”。

可以从应用内的任何位置按名称引用 Power Apps 中的任何控件。 **Screen1** 可能是应用中屏幕的名称。 若要检索此屏幕的背景色，可以使用 **Screen1.Fill**。

此屏幕上的控件具有其他选项。 它们可以使用相对引用：**Parent.Fill**。 **[Parent](operators.md#parent-operator)** 运算符指的是托管此控件，并使其所有属性可用的控件。 **[Parent](operators.md#parent-operator)** 非常有用，因为它不依赖于控件的名称。 可以复制并粘贴容器控件，无需调整容器内的任何引用。 在读取公式时，此运算符还使子控件和父控件之间的关系更为明确。

## <a name="identifier-names"></a>标识符名称

变量、数据源、列和其他对象的名称可以包含任何[Unicode](https://en.wikipedia.org/wiki/Unicode)。

使用单引号将包含空格或其他特殊字符的名称括起来。  将两个单引号一起使用，以在名称中表示一个单引号。  不包含特殊字符的名称不需要用单引号引起来。

下面是你可能会在表中遇到的一些示例列名称，以及如何在公式中表示它们：

| 数据库中的列名称   | 公式中的列引用 |
|-----------------------------|-------------------------------|
| SimpleName                  | ```SimpleName``` |
| NameWith123Numbers          | ```NameWith123Numbers``` |
| 带有空格的名称            | ```'Name with spaces'``` |
| 用双引号括起来的名称   | ```'Name with "double" quotes'``` |
| 带单引号的名称   | ```'Name with ''single'' quotes'``` |
| 带有 @ at 符号的名称      | ```'Name with an @ at sign'``` |

双引号用于[指定文本字符串](data-types.md#embedded-text)。  

## <a name="display-names-and-logical-names"></a>显示名称和逻辑名称
某些数据源（如 SharePoint 和 Common Data Service）具有两个不同的名称来引用同一表或数据列：

* **逻辑名称**-保证唯一的名称，在创建后不会更改，通常不允许使用空格或其他特殊字符，也不会将其本地化为不同的语言。  因此，名称可能有点难懂。  这些名称由专业开发人员使用。  例如**cra3a_customfield**。  此名称也可以称为 "**架构名称**" 或简称为 "**名称**"。

* **显示名称**-用户友好并应由最终用户查看的名称。  此名称可能不是唯一的，可能会随时间而变化，可能包含空格和任何 Unicode 字符，并且可能已本地化为不同的语言。  对应于上面的示例，显示名称可能是**自定义字段**，并且 receivebegindoc 单词的空格。
 
由于显示名称更易于理解，因此画布应用会建议它们作为选择，而不建议逻辑名称。  尽管不建议使用逻辑名称，但如果直接键入，则仍可使用。

例如，假设已将**自定义字段**添加到 Common Data Service 中的实体。  系统将为你分配逻辑名称，你只能在创建字段时修改该名称。  结果将如下所示：

> [!div class="mx-imgBorder"]  
> 添加了自定义字段 ![帐户实体，显示名称为 "自定义字段"，并且逻辑名称为 "cr5e3_customfield"](media/operators/customfield_portal.png)

在创作对帐户字段的引用时，建议使用 **"自定义字段"** ，因为这是显示名称。  请注意，必须使用单引号，因为此名称包含空格：

> [!div class="mx-imgBorder"]  
> ![Studio 公式栏，显示突出显示名称为 "自定义字段" 的帐户的字段名称建议](media/operators/customfield_suggest_display.png)

选择建议后，"自定义字段" 会显示在公式栏中，并检索数据： 

> [!div class="mx-imgBorder"]  
> 用于显示字段的显示名称 "自定义字段" 用法 ![Studio 公式栏](media/operators/customfield_display.png)

尽管不建议这样做，但我们也可以使用此字段的逻辑名称。  这将导致检索相同的数据。  请注意，不需要任何单引号，因为此名称不包含空格或特殊字符：

> [!div class="mx-imgBorder"]  
> 显示字段的逻辑名称 cr5e3_customfield 使用的 ![Studio 公式栏](media/operators/customfield_logical.png)

在幕后，在公式和基础逻辑名称中发现的显示名称之间保留映射。  由于逻辑名称必须用于与数据源进行交互，因此，此映射用于从当前显示名称自动转换为逻辑名称，这是网络流量中出现的内容。  此映射还用于转换回逻辑名称，以便切换到新的显示名称，例如，如果显示名称更改或其他语言的 maker 编辑应用，则为。

> [!NOTE] 
> 在环境之间移动应用时，不会转换逻辑名称。  对于 Common Data Service 系统实体和字段名称，这不应是问题，因为逻辑名称在环境中保持一致。  但在上面的示例中，任何自定义字段（如**cra3a_customfield** ）可能具有不同的环境前缀（在本例中为**cra3a** ）。  显示名称是首选名称，因为它们可以在新环境中与显示名称匹配。 

## <a name="name-disambiguation"></a>名称歧义
由于显示名称不是唯一的，因此相同的显示名称可能在同一实体中出现多次。  发生这种情况时，会将逻辑名称添加到多个冲突名称中的一个名称的显示名称的末尾。  基于上面的示例，如果有另一个字段具有与**cra3a_customfieldalt**逻辑名称相同的**自定义字段**显示名称，则建议将显示：

> [!div class="mx-imgBorder"]  
> 显示逻辑名称 cr5e3_customfieldalt 使用的 ![Studio 公式栏区分 "自定义字段" 的两个版本](media/operators/customfield_suggest_alt.png)

名称歧义字符串在发生名称冲突的其他情况下添加，例如实体、选项集和其他 Common Data Service 项的名称。 

## <a name="disambiguation-operator"></a>消除歧义运算符
某些函数创建[记录作用域](../working-with-tables.md#record-scope)，从而在处理每个记录时访问表的字段，例如 **Filter**、**AddColumns** 和 **Sum**。  使用记录范围添加的字段名称将替代应用中来自其他位置的同一名称。  在此情况下，仍可以使用 **@** 消除歧义运算符访问来自记录作用域外部的值：

* 若要访问来自嵌套记录作用域的值，请使用 **@** 运算符，其中所操作的表名称使用该模式：<br>_Table_ **[@** _FieldName_ **]**
* 若要访问全局值，如数据源、集合和上下文变量，请使用模式 **[@** _ObjectName_ **]** （无需指派表）。

有关详细信息和示例，请参阅[记录作用域](../working-with-tables.md#record-scope)。

