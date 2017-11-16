---
title: "IsMatch 函数 | Microsoft 文档"
description: "PowerApps 中 IsMatch 函数的参考信息（包括语法）。"
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
ms.date: 02/05/2017
ms.author: gregli
ms.openlocfilehash: b15a394db060617aeae8324094a70aa8cadf6755
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="ismatch-function-in-powerapps"></a>PowerApps 中的 IsMatch 函数
测试文本字符串是否符合某种模式。

## <a name="description"></a>说明
**IsMatch** 函数用于测试文本字符串是否与包含普通字符、预定义模式或[正则表达式](#regular-expressions)的某种模式相符。  

使用 **IsMatch** 函数可验证用户在**[文本输入](../controls/control-text-input.md)**控件中输入的内容。 例如，可以在将结果保存到数据源中之前验证用户输入的电子邮件地址是否有效。 如果输入的内容与条件不符，可添加其他控件提示用户更正输入。

默认情况下，**IsMatch** 函数在匹配整个文本字符串时区分大小写。 你可以通过指定一个或多个 [**MatchOptions**](#match-options) 来修改这种行为。

如果文本字符串与模式相符，则 **IsMatch** 函数返回 *true*；否则，返回 *false*。

## <a name="patterns"></a>模式
使用 **IsMatch** 函数的关键在于描述要匹配的模式。 你可以组合使用以下文本字符串来描述模式：

* 普通字符，如 **"abc"** 或 **"123"**。
* 预定义模式，如 **Letter**、**MultipleDigits** 或 **Email**。 （**Match**  枚举定义了这些模式。）
* 正则表达式代码，如 **"\d+\s+\d+"** 或 **"[a-z]+"**。

通过使用[字符串连接运算符 **&**](operators.md) 可以组合这些元素。 例如，**"abc" & Digit & "\s+"** 是一个有效的模式，它表示首先要与字符“a”、“b”和“c”匹配，后面跟一个从 0 到 9 的数字，后面再跟至少一个空格字符。

### <a name="ordinary-characters"></a>普通字符
最简单的模式是一系列要完全匹配的普通字符。

例如，字符串“Hello”与模式 **"Hello"** 完全匹配。 不多不少，正好相符。 字符串“hello!” 就与这个模式不匹配，因为它的末尾有一个感叹号，并且字母“h”的大小写错误。 （有关修改这种行为的方法，请参阅 [MatchOptions](#match-options)。）

模式语言中有一些保留字符，这些字符有特殊的用途。 要使用这些字符，请使用 **\\**（反斜杠）作为前缀，这表示应将后面的字符当作普通字符，你也可以使用提供的预定义模式之一。 下表列出了这些特殊字符：

| 特殊字符 | 说明 |
| --- | --- |
| **.** |圆点或句点 |
| **?** |问号 |
| **&#42;** |星号 |
| **\+** |加号 |
| **( )** |圆括号 |
| **[ ]** |方括号 |
| **{ }** |大括号 |
| **^** |脱字号 |
| **$** |美元符号 |
| **&#124;** |竖线 |
| **\\** |反斜杠 |

例如，可以 使用在问号前加一个反斜杠的模式 **"Hello\\?"** 来匹配“Hello?”。

### <a name="predefined-patterns"></a>预定义模式
预定义模式提供了一种简单方法来匹配一组字符中的一个字符或一个多字符序列。 使用[字符串连接运算符 **&**](operators.md) 可将你自己的文本字符串与 **Match**  枚举中的模式进行组合：

| Match 枚举 | 说明 | 正则表达式 |
| --- | --- | --- |
| **Any** |匹配任何字符。 |**.** |
| **Comma** |匹配逗号。 |**,** |
| **Digit** |匹配单个数字（“0”到“9”）。 |**\\d** |
| **Email** |匹配包含“@”符号和包含点（“.”）的域名的电子邮件地址。 |**.+@.+\\.[^\\.]{2,}** |
| **Hyphen** |匹配连字符。 |**\\-** |
| **LeftParen** |匹配左圆括号“(”。 |**\\(** |
| **Letter** |匹配一个字母。 |**\\p{L}** |
| **MultipleDigits** |匹配一个或多个数字。 |**\\d+** |
| **MultipleLetters** |匹配一个或多个字母。 |**\\p{L}+** |
| **MultipleNonSpaces** |匹配不包含空白（空格、制表符、换行符）的一个或多个字符。 |**\\S+** |
| **MultipleSpaces** |匹配可间断（包含空格、制表符、换行符）的一个或多个字符。 |**\\s+** |
| **NonSpace** |匹配不包含空白的单个字符。 |**\\S** |
| **OptionalDigits** |配零个、一个或多个数字。 |**\\d** |
| **OptionalLetters** |匹配零个、一个或多个字母。 |**\\p{L}** |
| **OptionalNonSpaces** |匹配不包含空白的零个、一个或多个字符。 |**\\S** |
| **OptionalSpaces** |匹配包含空白的零个、一个或多个字符。 |**\\s** |
| **Period** |匹配句点或圆点（“.”）。 |**\\.** |
| **RightParen** |匹配右圆括号“)”。 |**\\)** |
| **Space** |匹配包含空白的字符。 |**\\s** |

例如，模式 **"A" & MultipleDigits** 与字母“A”后跟一个或多个数字的形式匹配。  

### <a name="regular-expressions"></a>正则表达式
**IsMatch** 函数使用的模式是*正则表达式*。 上述普通字符和预定义模式可以帮助你构建正则表达式。  

正则表达式的功能非常强大，许多编程语言中都有提供，并且用途广泛。 本文无法详细介绍正则表达式的每个方面，不过网络上有大量的信息和教程供你参考。  

正则表达式有不同的方言，PowerApps 使用 JavaScript 方言的一种变体。 有关详细信息，请参阅[正则表达式语法](http://msdn.microsoft.com/library/1400241x.aspx)。

在上述 **Match**  枚举表中，每个枚举都可以扩展为一个正则表达式，“正则表达式”列中的文本字符串就是相应的定义。

## <a name="match-options"></a>匹配选项
你可以通过指定一个或多个选项（可使用字符串连接运算符 (**&amp;**) 进行组合）修改 **IsMatch** 函数的行为。  

默认情况下，**IsMatch** 函数会检测整个文本字符串是否完全匹配。

| MatchOptions 枚举 | 说明 | 对正则表达式的影响 |
| --- | --- | --- |
| **BeginsWith** |模式必须与文本的开头匹配。 |在正则表达式的开头添加 **^**。 |
| **Complete** |默认值。  模式必须与整个文本从头到尾完全匹配。 |在正则表达式的开头添加 **^**，并且在末尾添加 **$**。 |
| **Contains** |模式必须出现在文本中，但不必与开头或结尾匹配。 |不修改正则表达式。 |
| **EndsWith** |模式必须与文本的结尾匹配。 |在正则表达式的末尾添加 **$**。 |
| **IgnoreCase** |匹配字母时不区分大小写。 默认情况下，匹配时区分大小写。 |不修改正则表达式。 |
| **Multiline** |匹配多行。 |不修改正则表达式。 |

## <a name="syntax"></a>语法
**IsMatch**( *Text*, *Pattern* [, *Options* ] )

* *Text* – 必需。  要测试的文本字符串。
* *Pattern* – 必需。  要作为文本字符串测试的模式。  连接 **Match** 枚举定义的预定义模式或提供正则表达式。
* *Options* – 可选。  **MatchOptions** 枚举值的文本字符串组合。  默认情况下，使用 **MatchOptions.Complete**。

## <a name="examples"></a>示例
### <a name="ordinary-characters"></a>普通字符
假设应用包含一个名为 **TextInput1** 的“文本输入”控件：  用户在这个控件中输入的值存储在数据库中。   

用户在 **TextInput1** 中输入 **Hello world**。

| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **IsMatch( TextInput1.Text, "Hello world" )** |测试用户输入的内容是否与字符串“Hello world”完全匹配。 |**true** |
| **IsMatch( TextInput1.Text, "Good bye" )** |测试用户输入的内容是否与字符串“Good bye”完全匹配。 |**false** |
| **IsMatch( TextInput1.Text, "hello", Contains )** |测试用户输入的内容是否包含单词“hello”（区分大小写）。 |**false** |
| **IsMatch( TextInput1.Text, "hello", Contains & IgnoreCase )** |测试用户输入的内容是否包含单词“hello”（不区分大小写）。 |**true** |

### <a name="predefined-patterns"></a>预定义模式
| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **IsMatch( "123-45-7890", Digit & Digit & Digit & Hyphen & Digit & Digit & Hyphen & Digit & Digit & Digit & Digit & Digit )** |匹配美国社会安全号码。 |**true** |
| **IsMatch( "joan@contoso.com", Email )** |匹配电子邮件地址。 |**true** |
| **IsMatch( "123.456", MultipleDigits & Period & OptionalDigits )** |匹配一个数字序列，后跟一个句点，后面再跟零个或多个数字。 |**true** |
| **IsMatch( "123", MultipleDigits & Period & OptionalDigits )** |匹配一个数字序列，后跟一个句点，后面再跟零个或多个数字。 文本中没有句点，因此该模式不匹配。 |**false** |

### <a name="regular-expressions"></a>正则表达式
| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **IsMatch( "986", "\d+" )** |匹配大于零的整数。 |**true** |
| **IsMatch( "1.02", "\d+(\.\d\d)?" )** |匹配正货币金额。 如果输入的内容包含小数点，则小数点后还要有 2 个数字字符。 例如，3.00 有效，但 3.1 无效。 |**true** |
| **IsMatch( "-4.95", "(-)?\d+(\.\d\d)?" )** |匹配正或负货币金额。 如果输入的内容包含小数点，则小数点后还要有 2 个数字字符。 |**true** |
| **IsMatch( "111-11-1111", "\d{3}-\d{2}-\d{4}" )** |匹配美国社会安全号码。  验证提供的输入字段的格式、类型和长度。 要匹配的字符串必须包含 3 个数字字符，后跟一个短划线，再跟 2 个数字字符，再跟一个短划线，最后跟 4 个数字字符。 |**true** |
| **IsMatch( "111-111-111", "\d{3}-\d{2}-\d{4}" )** |与上例相同，但其中一个连字符的位置不对。 |**false** |
| **IsMatch( "weakpassword", "(?!^[0-9]\*$)(?!^[a-zA-Z]\*$)([a-zA-Z0-9]{8,10})" )** |验证强密码，除包含至少一个数字和至少一个字母字符外，还必须包含 8、9 或 10 个字符。 字符串不能包含特殊字符。 |**false** |
| **IsMatch( "http://microsoft.com", "(ht&#124;f)tp(s?)\:\/\/\[0-9a-zA-Z\]([-.\w]\*[0-9a-zA-Z])\*(:(0-9)\*)\*(\/?)([a-zA-Z0-9\-\.\?\,\'\/\\\+&amp;%\$#_]\*)?" )** |验证 http、https 或 ftp URL。 |**true** |
