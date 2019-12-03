---
title: IsMatch、Match 和 MatchAll 函数 |Microsoft Docs
description: Power Apps 中的 IsMatch、Match 和 MatchAll 函数的参考信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fb150fc9e640801588e8ab7a5bef4640438679f8
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730780"
---
# <a name="ismatch-match-and-matchall-functions-in-power-apps"></a>Power Apps 中的 IsMatch、Match 和 MatchAll 函数
测试是否匹配或根据模式提取文本字符串的某些部分。

## <a name="description"></a>描述
**IsMatch** 函数用于测试文本字符串是否与包含普通字符、预定义模式或[正则表达式](#regular-expressions)的某种模式相符。  **Match**和**MatchAll**函数返回匹配的内容，包括子匹配。  

使用 **IsMatch** 函数可验证用户在 **[文本输入](../controls/control-text-input.md)** 控件中输入的内容。 例如，可以在将结果保存到数据源中之前验证用户输入的电子邮件地址是否有效。 如果输入的内容与条件不符，可添加其他控件提示用户更正输入。

使用**Match**提取与 Pattern 和**MatchAll**匹配的第一个文本字符串，以便提取所有匹配的文本字符串。 您还可以提取子匹配以分析复杂字符串。   

**Match**返回找到的第一个匹配项的信息记录， **MatchAll**返回找到的每个匹配项的记录表。 记录或记录包含：

| 列 | 类型 | 描述 |
|----|----|----|
| *命名的&#8209;子匹配项&#8209;或子匹配项* | Text | 每个命名的子匹配都将有自己的列。 使用 **（？&lt;*名称*&gt;** 创建命名的子匹配项。 **）** 。 如果已命名的子匹配的名称与预定义列之一相同（如下所示），则子匹配优先，并生成警告。 若要避免出现此警告，请重命名子匹配。 |
| **FullMatch** | Text | 所有匹配的文本字符串。 |
| **StartMatch** | Number | 输入文本字符串中的匹配项的起始位置。 字符串的第一个字符返回1。 | 
| **子** | 单列表文本（**列值）** | 按其在正则表达式中出现的顺序匹配的已命名和未命名子匹配的表。 通常，命名的子匹配项的使用和建议更简单。 使用[**ForAll**](function-forall.md)函数或[**Last**](function-first-last.md)（ [**FirstN**](function-first-last.md)（ **...** ））函数可处理单独的子匹配项。 如果正则表达式中未定义子匹配项，则此表将存在但为空。 |

这些函数支持[**MatchOptions**](#match-options)。 默认情况下： 
- 这些函数执行区分大小写的匹配。 使用**regexoptions.ignorecase**可执行不区分大小写的匹配项。    
- **IsMatch**匹配整个文本字符串（**Complete** MatchOption），而**Match**和**MatchAll**在文本字符串（**包含**MatchOption）的任意位置搜索匹配项。 根据你的方案，使用**Complete**、 **Contains**、**开头为**或**EndsWith** 。

如果文本字符串与模式相符，则 **IsMatch** 函数返回 *true*；否则，返回 *false*。 如果找不到可通过[**IsBlank**](function-isblank-isempty.md)函数进行测试的匹配项，则**Match**返回*空白*。 如果未找到可使用[**IsEmpty**](function-isblank-isempty.md)函数进行测试的匹配项， **MatchAll**将返回一个空表。

如果使用**MatchAll**拆分文本字符串，请考虑使用 **[split](function-split.md)** 函数，该函数的使用和速度更快。

## <a name="patterns"></a>模式
使用这些函数的关键是描述要匹配的模式。 你可以组合使用以下文本字符串来描述模式：

* 普通字符，如 **"abc"** 或 **"123"** 。
* 预定义模式，如 **Letter**、**MultipleDigits** 或 **Email**。 （**Match** 枚举定义了这些模式。）
* 正则表达式代码，如 **"\d + \s + \d +"** 或 **"[a-z] +"** 。

使用[字符串串联运算符 **&** ](operators.md)来合并这些元素。 例如， **"abc" & Digit & "\s+"** 是一个有效的模式，它表示首先要与字符“a”、“b”和“c”匹配，后面跟一个从 0 到 9 的数字，后面再跟至少一个空格字符。

### <a name="ordinary-characters"></a>普通字符
最简单的模式是一系列要完全匹配的普通字符。

例如，与**IsMatch**函数一起使用时，字符串 "hello" 与模式 **"hello"** 完全匹配。 不多不少，正好相符。 字符串“hello!” 由于末尾有惊叹号，而不匹配模式，因为字母 "h" 的大小写错误。 （有关修改这种行为的方法，请参阅 [MatchOptions](#match-options)。）

模式语言中有一些保留字符，这些字符有特殊的用途。 若要使用这些字符，请使用 **\\** （反斜杠）作为字符的前缀，以指示应按原义字符，或使用本主题后面部分介绍的预定义模式之一。 下表列出了这些特殊字符：

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
预定义的模式提供了一种简单的方法来匹配一组字符或多个字符的序列。 使用[字符串串联运算符 **&** ](operators.md)将您自己的文本字符串与**Match**枚举的成员合并：

| Match 枚举 | 描述 | 正则表达式 |
| --- | --- | --- |
| **Any** |匹配任何字符。 |`.` |
| **Comma** |匹配逗号。 |`,` |
| **Digit** |匹配单个数字（“0”到“9”）。 |`\d` |
| **Email** |匹配包含（“\@”）符号和包含点（“.”）的域名的电子邮件地址。 |`.+\@.+\\.[^\\.]{2,}` |
| **Hyphen** |匹配连字符。 |`\-` |
| **LeftParen** |匹配左圆括号“(”。 |`\(` |
| **Letter** |匹配一个字母。 |`\p{L}` |
| **MultipleDigits** |与一个或多个数字匹配。 |`\d+` |
| **MultipleLetters** |匹配一个或多个字母。 |`\p{L}+` |
| **MultipleNonSpaces** |匹配一个或多个不加空格的字符（非空格、制表符或换行符）。 |`\S+` |
| **MultipleSpaces** |与一个或多个字符（空格、制表符或换行）相匹配。 |`\s+` |
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
这些函数使用的模式是一个[正则表达式](https://en.wikipedia.org/wiki/Regular_expression)。 本主题前面所述的普通字符和预定义模式可帮助生成正则表达式。  

正则表达式的功能非常强大，许多编程语言中都有提供，并且用途广泛。 它们还可能类似于标点符号的随机序列。 本文不介绍正则表达式的所有方面，但 web 上提供丰富的信息、教程和工具。  

正则表达式采用不同的方言，而 Power Apps 使用 JavaScript 方言的变体。 有关语法的简介，请参阅[正则表达式语法](https://msdn.microsoft.com/library/1400241x.aspx)。 支持命名的子匹配项（有时称为命名捕获组）：

- 命名的子匹配项： **（？&lt;*名称*&gt; ...）**
- 命名的反向引用： **\\k&lt;*名称*&gt;**

在本主题前面的 "**匹配**枚举" 表中，每个枚举显示在其对应的正则表达式所在的行中。

## <a name="match-options"></a>匹配选项
您可以通过指定一个或多个选项来修改这些函数的行为，可以使用字符串连接运算符（ **&amp;** ）组合这些选项。  

| MatchOptions 枚举 | 描述 | 对正则表达式的影响 |
| --- | --- | --- |
| **BeginsWith** |模式必须与文本的开头匹配。 |在正则表达式的开头添加 **^** 。 |
| **Complete** |**IsMatch**的默认值。 模式必须与文本的整个字符串保持一致，从开始到结尾。 |将 **^** 添加到正则表达式末尾的开头和 **$** 。 |
| **Contains** |**Match**和**MatchAll**的默认值。 模式必须出现在文本中，但不必与开头或结尾匹配。 |不修改正则表达式。 |
| **EndsWith** |模式必须与文本字符串的末尾匹配。 |在正则表达式的末尾添加 **$** 。 |
| **IgnoreCase** |将大写字母和小写字母视为相同。 默认情况下，匹配时区分大小写。 |不修改正则表达式。 此选项等效于正则表达式的标准 "i" 修饰符。  |
| **Multiline** |匹配多行。 |不修改正则表达式。 此选项等效于正则表达式的标准 "m" 修饰符。 |

使用**MatchAll**等效于对正则表达式使用标准的 "g" 修饰符。

## <a name="syntax"></a>语法
**IsMatch**( *Text*, *Pattern* [, *Options* ] )

* *Text* – 必需。 要测试的文本字符串。
* *Pattern* – 必需。 要作为文本字符串测试的模式。 连接**匹配**枚举定义的预定义模式，或提供正则表达式。 在应用运行时，*模式*必须是不包含任何变量、数据源或其他动态引用的常量公式。
* *Options* – 可选。 **MatchOptions**枚举值的文本字符串组合。 默认情况下，使用 **MatchOptions.Complete**。

**Match**（ *Text*， *Pattern* [， *Options* ]）

* *Text* – 必需。 要匹配的文本字符串。
* *Pattern* – 必需。 要作为文本字符串匹配的模式。 连接**匹配**枚举定义的预定义模式，或提供正则表达式。 在应用运行时，*模式*必须是不包含任何变量、数据源或其他动态引用的常量公式。
* *Options* – 可选。 **MatchOptions**枚举值的文本字符串组合。 默认情况下，使用**MatchOptions** 。

**MatchAll**（ *Text*， *Pattern* [， *Options* ]）

* *Text* – 必需。 要匹配的文本字符串。
* *Pattern* – 必需。 要作为文本字符串匹配的模式。 连接**匹配**枚举定义的预定义模式，或提供正则表达式。 在应用运行时，*模式*必须是不包含任何变量、数据源或其他动态引用的常量公式。
* *Options* – 可选。 **MatchOptions**枚举值的文本字符串组合。 默认情况下，使用**MatchOptions** 。

## <a name="ismatch-examples"></a>IsMatch 示例
### <a name="ordinary-characters"></a>普通字符
假设应用包含一个名为 **TextInput1** 的“文本输入”控件。 用户在这个控件中输入的值存储在数据库中。   

用户在 **TextInput1** 中输入 **Hello world**。

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| `IsMatch( TextInput1.Text, "Hello world" )` |测试用户输入的内容是否与字符串 "Hello world" 完全匹配。 |**true** |
| `IsMatch( TextInput1.Text, "Good bye" )` |测试用户输入的内容是否与字符串 "好再见" 完全匹配。 |**false** |
| `IsMatch( TextInput1.Text, "hello", Contains )` |测试用户输入是否包含单词 "hello" （区分大小写）。 |**false** |
| `IsMatch( TextInput1.Text, "hello", Contains & IgnoreCase )` |测试用户输入的内容是否包含单词“hello”（不区分大小写）。 |**true** |

### <a name="predefined-patterns"></a>预定义模式

|                                                            公式                                                            |                                                                描述                                                                |  结果   |
|-------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| `IsMatch( "123-45-7890", Digit & Digit & Digit & Hyphen & Digit & Digit & Hyphen & Digit & Digit & Digit & Digit )` |                                              匹配美国社会安全号码                                               | **true**  |
|                                           `IsMatch( "joan@contoso.com", Email )`                                            |                                                         匹配电子邮件地址                                                          | **true**  |
|                              `IsMatch( "123.456", MultipleDigits & Period & OptionalDigits )`                               |                                   匹配一个数字序列，后跟一个句点，后面再跟零个或多个数字。                                   | **true**  |
|                                `IsMatch( "123", MultipleDigits & Period & OptionalDigits )`                                 | 匹配一个数字序列，后跟一个句点，后面再跟零个或多个数字。 时间段未出现在要匹配的文本中，因此此模式不匹配。 | **false** |

### <a name="regular-expressions"></a>正则表达式

|                                                                              公式                                                                              |                                                                                                                                  描述                                                                                                                                   |  结果   |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
|                                                                    `IsMatch( "986", "\d+" )`                                                                   |                                                                                                                    匹配大于零的整数。                                                                                                                     | **true**  |
|                                                               `IsMatch( "1.02", "\d+(\.\d\d)?" )`                                                              |                                        匹配正货币金额。 如果输入包含小数点，则输入还必须在小数点后包含两个数字字符。 例如，3.00 有效，但 3.1 无效。                                         | **true**  |
|                                                            `IsMatch( "-4.95", "(-)?\d+(\.\d\d)?" )`                                                             |                                                        匹配正或负货币金额。 如果输入包含小数点，则输入还必须在小数点后包含两个数字字符。                                                        | **true**  |
|                                                         `IsMatch( "111-11-1111", "\d{3}-\d{2}-\d{4}" )`                                                        | 匹配美国社会安全号码。 验证提供的输入字段的格式、类型和长度。 要匹配的字符串必须包含三个数字字符，后跟一个短划线，然后是两个数字字符，后跟一个短划线，然后是四个数字字符。 | **true**  |
|                                                         `IsMatch( "111-111-111", "\d{3}-\d{2}-\d{4}" )`                                                         |                                                                                               与上例相同，但其中一个连字符的位置不对。                                                                                               | **false** |
|                                         `IsMatch( "AStrongPasswordNot", "(?!^[0-9]\*$)(?!^[a-zA-Z]\*$)([a-zA-Z0-9]{8,10})" )`                                        |                                        验证强密码，该密码除了包含至少一个数字和至少一个字母字符外，还必须包含8、9或10个字符。 字符串不能包含特殊字符。                                        | **false** |
| `IsMatch( "<https://microsoft.com>", "(ht&#124;f)tp(s?)\:\/\/\[0-9a-zA-Z\]([-.\w]\*[0-9a-zA-Z])\*(:(0-9)\*)\*(\/?)([a-zA-Z0-9\-\.\?\,\'\/\\\+&%\$#_]\*)?" )` |                                                                                                                     验证 http、https 或 ftp URL。                                                                                                                      | **true**  |

## <a name="match-and-matchall-examples"></a>Match 和 MatchAll 示例

| 公式 | 描述 | 结果 |
|--------|------------|-----------|
| `Match( "Bob Jones <bob.jones@contoso.com>", "<(?<email>" & Match.Email & ")>"` | 仅提取联系人信息的电子邮件部分。  | {<br>电子邮件：&nbsp;"bob.jones@contoso.com"，<br>FullMatch：&nbsp;"&lt;bob.jones@contoso.com>"，<br>子匹配：&nbsp;[&nbsp;"bob.jones@contoso.com"&nbsp;]，<br>StartMatch：11<br>}  
| `Match( "Bob Jones <InvalidEmailAddress>", "<(?<email>" & Match.Email & ")>"` | 仅提取联系人信息的电子邮件部分。 找不到合法地址（没有 @ 符号），因此该函数返回*空白*。 | *blank* |  
| `Match( Language(), "(<language>\w{2})(?:-(?<script>\w{4}))?(?:-(?<region>\w{2}))?" )` | 提取 **[language 函数返回的语言标记](function-language.md)** 的语言、脚本和区域部分。 这些结果反映美国;有关更多示例，请参阅[**语言**函数文档](function-language.md)。  **（？：** 运算符对字符进行分组，而不创建另一个匹配项。 | {<br>language： "en"，<br>脚本：*空白*， <br>区域： "US"、<br>FullMatch： "en-us"， <br>子匹配项： ["en"，""，"US"]， <br>StartMatch：1<br>} 
| `Match( "PT2H1M39S", "PT(?:<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" )` | 从 ISO 8601 持续时间值中提取小时、分钟和秒。 提取的数字仍位于文本字符串中;在对其执行数学运算之前，使用[**Value**](function-value.md)函数将其转换为数字。  | {<br> 小时： "2"，<br>分钟： "1"，<br>秒： "39"，<br>FullMatch: "PT2H1M39S",<br>子匹配项：&nbsp;[&nbsp;"2"，&nbsp;"1"，&nbsp;"39"&nbsp;]，<br>StartMatch：1<br>} |

我们来深入探讨最后的示例。 如果希望使用 **[time](function-date-time.md)** 函数将此字符串转换为日期/时间值，则必须单独传入命名的子匹配项。 为此，您可以对**匹配**返回的记录使用 **[With](function-with.md)** 函数操作：

``` powerapps-dot
With( 
    Match( "PT2H1M39S", "PT(?:(?<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ), 
    Time( Value( hours ), Value( minutes ), Value( seconds ) )
)
```

对于这些示例，请添加一个[按钮](../controls/control-button.md)控件，将其**OnSelect**属性设置为此公式，然后选择按钮：

``` powerapps-dot
Set( pangram, "The quick brown fox jumps over the lazy dog." )
```
 
| 公式 | 描述 | 结果 |
|---------|-------------|--------|
| `Match( pangram, "THE", IgnoreCase )` | 查找**pangram**变量包含的文本字符串中的所有匹配项。 该字符串包含两个匹配项，但只返回第一个匹配项，因为使用的是**Match**而不是**MatchAll**。 子匹配列是空的，因为未定义子匹配。  | {<br>FullMatch： "the"、<br>子匹配项： [&nbsp;]，<br>StartMatch：32<br>} |
| `MatchAll( pangram, "the" )` | 查找**pangram**变量包含的文本字符串中的所有匹配项。 测试区分大小写，因此仅找到第二个 "" 的实例。 子匹配列是空的，因为未定义子匹配。  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-one.png) |
| `MatchAll( pangram, "the", IgnoreCase )` | 查找**pangram**变量包含的文本字符串中的所有匹配项。 在这种情况下，测试不区分大小写，因此会找到单词的两个实例。 子匹配列是空的，因为未定义子匹配。  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-the-two.png) |
| `MatchAll( pangram, "\b\wo\w\b" )` | 查找中间包含 "o" 的所有三个字母的单词。 请注意，"棕色" 已排除，因为它不是三个字母的单词，因此无法匹配 "\b" （单词边界）。  | <style> img { max-width: none } </style> ![](media/function-ismatch/pangram-fox-dog.png) |
| `Match( pangram, "\b\wo\w\b\s\*(?<between>\w.+\w)\s\*\b\wo\w\b" )` | 匹配 "fox" 和 "dog" 之间的所有字符。 | {<br>between：&nbsp;"跳转&nbsp;&nbsp;&nbsp;延迟"，<br>FullMatch：&nbsp;"fox&nbsp;跳过&nbsp;&nbsp;&nbsp;懒惰&nbsp;dog"）。<br>子匹配项： ["跳过延迟"]，<br>StartMatch：17<br> } |

若要查看库中的**MatchAll**的结果：

1. 在空屏幕中，插入一个空白垂直 **[库](../controls/control-gallery.md)** 控件。

2. 将库的**Items**属性设置为**MatchAll （pangram，"\w +"）** 或**MatchAll （pangram，MultipleLetters）** 。

    ![](media/function-ismatch/pangram-gallery1.png)

3. 从库控件中间的 "插入" 选项卡中选择 "添加项"，以选择库的模板。 

5. 向库模板添加 " **[标签](../controls/control-text-box.md)** " 控件。  

4. 将标签的 " **Text** " 属性设置为**ThisItem. FullMatch**。  
 
    库中的每个单词在示例文本中填充。  调整库的模板和 "标签" 控件的大小，以便在一个屏幕上查看所有单词。

    ![](media/function-ismatch/pangram-gallery2.png)
