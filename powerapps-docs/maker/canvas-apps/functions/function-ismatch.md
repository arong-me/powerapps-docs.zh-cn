---
title: IsMatch、 Match 和 MatchAll 函数 |Microsoft Docs
description: 参考信息，包括在 PowerApps 中 IsMatch、 Match 和 MatchAll 函数的语法，
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 01/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7141d3b9a2ba6bf18bffe1756d0d7de048606cad
ms.sourcegitcommit: f5013108140276b3d66a9dce13a061df89609d26
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2019
ms.locfileid: "57798366"
---
# <a name="ismatch-match-and-matchall-functions-in-powerapps"></a>PowerApps 中 IsMatch、 Match 和 MatchAll 函数
测试文本字符串的模式匹配或提取部分。

## <a name="description"></a>说明
**IsMatch** 函数用于测试文本字符串是否与包含普通字符、预定义模式或[正则表达式](#regular-expressions)的某种模式相符。  **匹配**并**MatchAll**函数返回什么匹配的包括子匹配项。  

使用 **IsMatch** 函数可验证用户在 **[文本输入](../controls/control-text-input.md)** 控件中输入的内容。 例如，可以在将结果保存到数据源中之前验证用户输入的电子邮件地址是否有效。 如果输入的内容与条件不符，可添加其他控件提示用户更正输入。

使用**匹配**提取第一个文本字符串与模式匹配和**MatchAll**提取所有匹配的文本字符串。 此外可以提取个子匹配来解析复杂的字符串。   

**匹配**返回找到的第一个匹配项的信息的记录，并**MatchAll**返回找到的每个匹配项的记录的表。 或多个记录包含：

| 列 | 类型 | 描述 |
|----|----|----|
| *名为 sub&#8209;匹配或子&#8209;匹配* | Text | 每个命名的子匹配项将具有其各自的列。 通过创建命名的子匹配项 **(？&lt;*名称*&gt;**...**)** 正则表达式中。 如果命名的子匹配项具有作为一个预定义的列 （见下文） 相同的名称，子匹配项优先，并生成一个警告。 若要避免此警告，重命名子匹配项。 |
| **FullMatch** | Text | 所有匹配的文本字符串。 |
| **StartMatch** | Number | 在输入的文本字符串中匹配项的起始位置。 第一个字符的字符串则返回 1。 | 
| **SubMatches** | 文本的单列的表 (列**值**) | 命名和未命名的子匹配正则表达式中出现的顺序的表。 通常情况下，更轻松地使用和鼓励命名的子匹配项。 使用[ **ForAll** ](function-forall.md)函数或[**最后一个**](function-first-last.md)( [ **FirstN**](function-first-last.md)(**...** )) 函数来处理各个子匹配。 如果正则表达式中不定义了任何子匹配项，此表将存在但为空。 |

这些函数支持[ **MatchOptions**](#match-options)。 默认情况下： 
- 这些函数执行区分大小写的匹配项。 使用**IgnoreCase**执行不区分大小写的匹配项。    
- **IsMatch**匹配整个文本字符串 (**完成**MatchOption)，而**匹配**并**MatchAll**搜索匹配项的文本字符串 (中的任意位置**包含**MatchOption)。 使用**完成**， **Contains**，**开头为**，或者**EndsWith**以适合你的方案。

如果文本字符串与模式相符，则 **IsMatch** 函数返回 *true*；否则，返回 *false*。 **匹配**将返回*空白*如果未找到匹配的可以测试[ **IsBlank** ](function-isblank-isempty.md)函数。 **MatchAll**返回一个空表，如果未找到匹配的可以测试[ **IsEmpty** ](function-isblank-isempty.md)函数。

如果您使用的 **MatchAll**要拆分的文本字符串，请考虑使用 **[拆分](function-split.md)** 函数，这是更易于使用且更快。

## <a name="patterns"></a>模式
使用这些函数的关键在于描述要匹配的模式。 你可以组合使用以下文本字符串来描述模式：

* 普通字符，如 **"abc"** 或 **"123"**。
* 预定义模式，如 **Letter**、**MultipleDigits** 或 **Email**。 （**Match** 枚举定义了这些模式。）
* 正则表达式代码，如 **"\d+\s+\d+"** 或 **"[a-z] +"**。

通过结合这些元素[字符串串联运算符**&** ](operators.md)。 例如，**"abc" & Digit & "\s+"** 是一个有效的模式，它表示首先要与字符“a”、“b”和“c”匹配，后面跟一个从 0 到 9 的数字，后面再跟至少一个空格字符。

### <a name="ordinary-characters"></a>普通字符
最简单的模式是一系列要完全匹配的普通字符。

例如，当与一起使用时**IsMatch**函数，字符串"Hello"与模式匹配 **"Hello"** 完全。 不多不少，正好相符。 字符串“hello!” 不会与模式匹配由于感叹号上结束，因为这种情况是错误的字母"h"。 （有关修改这种行为的方法，请参阅 [MatchOptions](#match-options)。）

模式语言中有一些保留字符，这些字符有特殊的用途。 若要使用这些字符，添加前缀与字符 **\\** （反斜杠） 以指示应按字面意思采取字符或更高版本中本主题所述使用预定义的模式之一。 下表列出了这些特殊字符：

| 特殊字符 | 描述 |
| --- | --- |
| **.** |圆点或句点 |
| **?** |问号 |
| **&#42;** |星号 |
| **\+** |加号 |
| **( )** |括号 |
| **[ ]** |方括号 |
| **{ }** |大括号 |
| **^** |脱字号 |
| **$** |美元符号 |
| **\|** |竖线 |
| **\\** |反斜杠 |

例如，可以 使用在问号前加一个反斜杠的模式 **"Hello\\?"** 来匹配“Hello?”。

### <a name="predefined-patterns"></a>预定义模式
预定义的模式提供简单的方法来匹配是一组字符的一个或多个字符的序列。 使用[字符串串联运算符**&** ](operators.md)中的成员的合并你自己的文本字符串**匹配**枚举：

| Match 枚举 | 描述 | 正则表达式 |
| --- | --- | --- |
| **Any** |匹配任何字符。 |`.` |
| **Comma** |匹配逗号。 |`,` |
| **Digit** |匹配单个数字（“0”到“9”）。 |`\d` |
| **Email** |匹配包含（“\@”）符号和包含点（“.”）的域名的电子邮件地址。 |`.+\@.+\\.[^\\.]{2,}` |
| **Hyphen** |匹配连字符。 |`\-` |
| **LeftParen** |匹配左圆括号“(”。 |`\(` |
| **Letter** |匹配一个字母。 |`\p{L}` |
| **MultipleDigits** |匹配一个或多个数字。 |`\d+` |
| **MultipleLetters** |匹配一个或多个字母。 |`\p{L}+` |
| **MultipleNonSpaces** |匹配不包含空白 （不空格、 制表符或换行） 的一个或多个字符。 |`\S+` |
| **MultipleSpaces** |匹配包含空白 （空格、 制表符或换行） 的一个或多个字符。 |`\s+` |
| **NonSpace** |匹配不包含空白的单个字符。 |`\S` |
| **OptionalDigits** |配零个、一个或多个数字。 |`\d*` |
| **OptionalLetters** |匹配零个、一个或多个字母。 |`\p{L}*` |
| **OptionalNonSpaces** |匹配不包含空白的零个、一个或多个字符。 |`\S*` |
| **OptionalSpaces** |匹配包含空白的零个、一个或多个字符。 |`\s*` |
| **Period** |匹配句点或圆点（“.”）。 |`\.` |
| **RightParen** |匹配右圆括号“)”。 |`\)` |
| **Space** |匹配包含空白的字符。 |`\s` |

例如，模式 **"A" & MultipleDigits** 与字母“A”后跟一个或多个数字的形式匹配。  

### <a name="regular-expressions"></a>正则表达式
这些函数将使用的模式是[正则表达式](https://en.wikipedia.org/wiki/Regular_expression)。 普通字符和本主题帮助前面所述的预定义的模式构建正则表达式。  

正则表达式的功能非常强大，许多编程语言中都有提供，并且用途广泛。 它们通常还可以如下所示的标点符号的随机序列。 本文不会介绍正则表达式的所有方面，但包含大量信息，教程，并在 web 上提供了工具。  

正则表达式有不同的方言，PowerApps 使用 JavaScript 方言的变体。 请参阅[正则表达式语法](http://msdn.microsoft.com/library/1400241x.aspx)有关语法的介绍。 支持 （有时称为已命名的捕获组） 的命名子匹配项：

- 名为子匹配项： **(？&lt;*名称*&gt; ...)**
- 名为反向引用：  **\\k&lt;*名称*&gt;**

在中**匹配**枚举本主题前面的表作为其相应的正则表达式在同一行中显示的每个枚举。

## <a name="match-options"></a>匹配选项
可以通过指定一个或多个选项，你可以通过使用字符串串联运算符将结合修改这些函数的行为 (**&amp;**)。  

| MatchOptions 枚举 | 说明 | 对正则表达式的影响 |
| --- | --- | --- |
| **BeginsWith** |模式必须与文本的开头匹配。 |在正则表达式的开头添加 **^**。 |
| **Complete** |默认**IsMatch**。 模式必须与匹配文本，从开始到结束的整个的字符串。 |将添加 **^** 到起始位置和一个 **$** 到正则表达式的末尾。 |
| **Contains** |默认**匹配**并**MatchAll**。 模式必须出现在文本中，但不必与开头或结尾匹配。 |不修改正则表达式。 |
| **EndsWith** |模式必须与匹配的文本字符串的末尾。 |在正则表达式的末尾添加 **$**。 |
| **IgnoreCase** |将大写和小写字母视为相同。 默认情况下，匹配时区分大小写。 |不修改正则表达式。 此选项相当的正则表达式的标准"i"修饰符。  |
| **Multiline** |匹配多行。 |不修改正则表达式。 此选项相当的正则表达式的标准"m"修饰符。 |

使用**MatchAll**相当于正则表达式中使用的标准"g"修饰符。

## <a name="syntax"></a>语法
**IsMatch**( *Text*, *Pattern* [, *Options* ] )

* *Text* – 必需。 要测试的文本字符串。
* *Pattern* – 必需。 要测试文本字符串形式的模式。 将预定义的模式相连接的**匹配**枚举定义，或提供正则表达式。 *模式*没有任何变量、 数据源或其他动态应用程序运行时引用所做的更改必须是常量的公式。
* *Options* – 可选。 文本字符串组合**MatchOptions**枚举值。 默认情况下，使用 **MatchOptions.Complete**。

**Match**( *Text*, *Pattern* [, *Options* ] )

* *Text* – 必需。 要匹配的文本字符串。
* *Pattern* – 必需。 要为一个文本字符串匹配的模式。 将预定义的模式相连接的**匹配**枚举定义，或提供正则表达式。 *模式*没有任何变量、 数据源或其他动态应用程序运行时引用所做的更改必须是常量的公式。
* *Options* – 可选。 文本字符串组合**MatchOptions**枚举值。 默认情况下**MatchOptions.Contains**使用。

**MatchAll**( *Text*, *Pattern* [, *Options* ] )

* *Text* – 必需。 要匹配的文本字符串。
* *Pattern* – 必需。 要为一个文本字符串匹配的模式。 将预定义的模式相连接的**匹配**枚举定义，或提供正则表达式。 *模式*没有任何变量、 数据源或其他动态应用程序运行时引用所做的更改必须是常量的公式。
* *Options* – 可选。 文本字符串组合**MatchOptions**枚举值。 默认情况下**MatchOptions.Contains**使用。

## <a name="ismatch-examples"></a>IsMatch 示例
### <a name="ordinary-characters"></a>普通字符
假设应用包含一个名为 **TextInput1** 的“文本输入”控件。 用户在这个控件中输入的值存储在数据库中。   

用户在 **TextInput1** 中输入 **Hello world**。

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| `IsMatch( TextInput1.Text, "Hello world" )` |测试用户输入的内容是否与完全匹配，字符串"Hello world"。 |**true** |
| `IsMatch( TextInput1.Text, "Good bye" )` |测试用户输入的内容是否与完全匹配，字符串"Good bye"。 |**false** |
| `IsMatch( TextInput1.Text, "hello", Contains )` |测试用户的输入是否包含单词"你好"（区分大小写）。 |**false** |
| `IsMatch( TextInput1.Text, "hello", Contains & IgnoreCase )` |测试用户输入的内容是否包含单词“hello”（不区分大小写）。 |**true** |

### <a name="predefined-patterns"></a>预定义模式

|                                                            公式                                                            |                                                                描述                                                                |  结果   |
|-------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| `IsMatch( "123-45-7890", Digit & Digit & Digit & Hyphen & Digit & Digit & Hyphen & Digit & Digit & Digit & Digit )` |                                              匹配美国社会安全号码                                               | **true**  |
|                                           `IsMatch( "joan@contoso.com", Email )`                                            |                                                         匹配电子邮件地址                                                          | **true**  |
|                              `IsMatch( "123.456", MultipleDigits & Period & OptionalDigits )`                               |                                   匹配一个数字序列，后跟一个句点，后面再跟零个或多个数字。                                   | **true**  |
|                                `IsMatch( "123", MultipleDigits & Period & OptionalDigits )`                                 | 匹配一个数字序列，后跟一个句点，后面再跟零个或多个数字。 中没有句点的文本匹配，因此该模式不匹配。 | **false** |

### <a name="regular-expressions"></a>正则表达式

|                                                                              公式                                                                              |                                                                                                                                  描述                                                                                                                                   |  结果   |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
|                                                                    `IsMatch( "986", "\d+" )`                                                                   |                                                                                                                    匹配大于零的整数。                                                                                                                     | **true**  |
|                                                               `IsMatch( "1.02", "\d+(\.\d\d)?" )`                                                              |                                        匹配正货币金额。 如果输入包含小数点，输入小数点后必须还包含两个数字字符。 例如，3.00 有效，但 3.1 无效。                                         | **true**  |
|                                                            `IsMatch( "-4.95", "(-)?\d+(\.\d\d)?" )`                                                             |                                                        匹配正或负货币金额。 如果输入包含小数点，输入小数点后必须还包含两个数字字符。                                                        | **true**  |
|                                                         `IsMatch( "111-11-1111", "\d{3}-\d{2}-\d{4}" )`                                                        | 匹配美国社会安全号码。 验证提供的输入字段的格式、类型和长度。 要匹配的字符串必须跟一个破折号，则两个数字字符后跟一个破折号，三个数字字符，然后四个数字字符组成。 | **true**  |
|                                                         `IsMatch( "111-111-111", "\d{3}-\d{2}-\d{4}" )`                                                         |                                                                                               与上例相同，但其中一个连字符的位置不对。                                                                                               | **false** |
|                                         `IsMatch( "AStrongPasswordNot", "(?!^[0-9]\*$)(?!^[a-zA-Z]\*$)([a-zA-Z0-9]{8,10})" )`                                        |                                        验证强密码必须包含 8、 9，或 10 个字符，除了至少一个数字和至少一个字母字符。 字符串不能包含特殊字符。                                        | **false** |
| `IsMatch( "<http://microsoft.com>", "(ht&#124;f)tp(s?)\:\/\/\[0-9a-zA-Z\]([-.\w]\*[0-9a-zA-Z])\*(:(0-9)\*)\*(\/?)([a-zA-Z0-9\-\.\?\,\'\/\\\+&%\$#_]\*)?" )` |                                                                                                                     验证 http、https 或 ftp URL。                                                                                                                      | **true**  |

## <a name="match-and-matchall-examples"></a>匹配和 MatchAll 示例

| 公式 | 描述 | 结果 |
|--------|------------|-----------|
| `Match( "Bob Jones <bob.jones@contoso.com>", "<(?<email>" & Match.Email & ")>"` | 提取的联系人信息的电子邮件部分。  | {<br>email:&nbsp;"bob.jones@contoso.com",<br>FullMatch:&nbsp;"&lt;bob.jones@contoso.com>",<br>SubMatches:&nbsp;[&nbsp;"bob.jones@contoso.com"&nbsp;],<br>StartMatch:11<br>}  
| `Match( "Bob Jones <InvalidEmailAddress>", "<(?<email>" & Match.Email & ")>"` | 提取的联系人信息的电子邮件部分。 找到不合法的地址 (没有不 @ 符号)，因此该函数将返回*空白*。 | 空白 |  
| `Match( Language(), "(<language>\w{2})(?:-(?<script>\w{4}))?(?:-(?<region>\w{2}))?" )` | 提取语言的语言、 脚本和区域部分标记 **[语言](function-language.md)** 函数返回。 这些结果反映美国;请参阅[**语言**函数文档](function-language.md)有关更多示例。  **(？:** 运算符而无需创建另一个子匹配项进行分组的字符。 | {<br>语言:"en"，<br>脚本：*空白*， <br>区域："我们"<br>FullMatch: "en-US", <br>SubMatches: [ "en", "", "US" ], <br>StartMatch:1<br>} 
| `Match( "PT2H1M39S", "PT(?:(<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" )` | 从 ISO 8601 持续时间值中提取小时、 分钟和秒。 提取的编号仍采用文本字符串;使用[**值**](function-value.md)函数将其转换为数字之前对其执行数学运算。  | {<br> 小时数："2",<br>分钟数："1",<br>（秒):"39",<br>FullMatch:"PT2H1M39S",<br>SubMatches:&nbsp;[&nbsp;"2",&nbsp;"1",&nbsp;"39"&nbsp;],<br>StartMatch:1<br>} |

让我们来钻取到最后一个示例。 如果你想要将此字符串转换为日期/时间值使用 **[时间](function-date-time.md)** 函数，您必须将传递在命名子匹配项中单独。 若要执行此操作，可以使用 **[ForAll](function-forall.md)** 函数在第一个操作录制 **MatchAll**返回：

``` powerapps-dot
First( 
    ForAll( 
        MatchAll( "PT2H1M39S", "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ), 
        Time( Value( hours ), Value( minutes ), Value( seconds ) )
    )
).Value
```

对于这些示例中，添加[按钮](../controls/control-button.md)控件，将其**OnSelect**到此公式，然后选择该按钮的属性：

``` powerapps-dot
Set( pangram, "The quick brown fox jumps over the lazy dog." )
```
 
| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| `Match( pangram, "THE", IgnoreCase )` | 查找所有匹配项的文本中的""字符串**pangram**变量包含。 该字符串包含两个匹配项，但只有第一个返回正在使用，因此**匹配**而不**MatchAll**。 子匹配项列是空的因为没有子匹配项已定义。  | {<br>FullMatch:"The"和<br>子匹配项: [&nbsp;]，<br>StartMatch:32<br>} |
| `MatchAll( pangram, "the" )` | 在文本字符串中查找"the"的所有匹配项**pangram**变量包含。 测试是区分大小写，因此只找到的"the"的第二个实例。 子匹配项列是空的因为没有子匹配项已定义。  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-one.png) |
| `MatchAll( pangram, "the", IgnoreCase )` | 在文本字符串中查找"the"的所有匹配项**pangram**变量包含。 在这种情况下，测试是不区分大小写，因此找到词的这两个实例。 子匹配项列是空的因为没有子匹配项已定义。  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-two.png) |
| `MatchAll( pangram, "\b\wo\w\b" )` | 在中间查找与"o"的所有三个字母单词。 请注意，"brown"已排除，因为它不是三个字母的单词和，因此，不匹配"\b"（在单词边界）。  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-fox-dog.png) |
| `Match( pangram, "\b\wo\w\b\s\*(?<between>\w.+\w)\s\*\b\wo\w\b" )` | 与"按照 fox"和"dog"之间的所有字符。 | {<br>between:&nbsp;"jumps&nbsp;over&nbsp;the&nbsp;lazy",<br>FullMatch:&nbsp;"fox&nbsp;jumps&nbsp;over&nbsp;the&nbsp;lazy&nbsp;dog",<br>子匹配项: ["跳转通过延迟"]，<br>StartMatch:17<br> } |

若要查看的结果**MatchAll**库中：

1. 在空屏幕中，插入一个空白垂直 **[库](../controls/control-gallery.md)** 控件。

2. 设置库的**项**属性设置为**MatchAll （pangram，"\w+"）** 或**MatchAll (pangram，MultipleLetters)**。

    ![](media/function-ismatch/pangram-gallery1.png)

3. 选择"添加项从插入选项卡"要选择的库模板的库控件的中间。 

5. 添加 **[标签](../controls/control-text-box.md)** 到库模板的控件。  

4. 设置的标签**文本**属性设置为**ThisItem.FullMatch**。  
 
    与我们的示例文本中每个单词的内容库。  调整库的模板和标签控件的大小才能看到一个屏幕上的所有单词。

    ![](media/function-ismatch/pangram-gallery2.png)
