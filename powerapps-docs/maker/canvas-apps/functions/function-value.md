---
title: Value 函数 | Microsoft 文档
description: Power Apps 中 Value 函数的参考信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/06/2020
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 51ceb1dfc67e24ff0f38f9bf51db37b78410544e
ms.sourcegitcommit: 80120b59d440bb7a3ddca93cd51154607f749f6b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/08/2020
ms.locfileid: "77089756"
---
# <a name="value-function-in-power-apps"></a>Power Apps 中的值函数
将文本字符串转换为数字。

## <a name="description"></a>说明
**Value** 函数将包含数字字符的文本字符串转换为数字值。 需要对用户以文本形式输入的数字执行计算时，请使用此函数。

不同的语言对 **,** 和 **.** 的解释 各不相同。  默认情况下，文本使用当前用户的语言进行解释。  可以通过语言标记指定要使用的语言，使用的语言标记与 **[Language](function-language.md)** 函数返回的语言标记相同。

字符串格式的说明：

* 字符串可能以当前语言所对应的货币符号为前缀。  系统会忽略该货币符号，  但不忽略其他语言的货币符号。
* 字符串可能在末尾包含百分号 ( **%** )，表示这是百分比。  该数字在返回前将被除以 100。  不能混用百分比和货币符号。
* 字符串可能采用科学记数法，将 12 x 10<sup>3</sup> 表示为“12e3”。

如果数字格式不正确，**Value** 将返回空白。

若要转换日期和时间值，请使用 [**DateValue**](function-datevalue-timevalue.md)、[**TimeValue**](function-datevalue-timevalue.md) 或 [**DateTimeValue**](function-datevalue-timevalue.md) 函数。

## <a name="syntax"></a>语法
**Value**( *String* [, *LanguageTag* ] )

* *String* - 必需。 要转换为数字值的字符串。
* *LanguageTag* - 可选。  一种语言标记，可以通过该标记来分析语言。  在未指定该标记的情况下，将使用当前用户的语言。

## <a name="examples"></a>示例
运行这些公式的用户位于美国，且已选择英语作为其语言。  **Language** 函数返回的是“en-US”。

| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **Value( "123.456" )** |将使用默认语言“en-US”，该语言使用句点作为小数分隔符。 |123.456 |
| **Value( "123.456", "es-ES" )** |“es-ES”是在西班牙使用的西班牙语的语言标记。  在西班牙，句点为千位分隔符。 |123456 |
| **Value( "123,456" )** |将使用默认语言“en-US”，该语言使用逗号作为千位分隔符。 |123456 |
| **Value( "123,456", "es-ES" )** |“es-ES”是在西班牙使用的西班牙语的语言标记。  在西班牙，逗号是小数分隔符。 |123.456 |
| **Value( "12.34%" )** |字符串末尾的百分号表示这是一个百分比。 |0.1234 |
| **Value( "$ 12.34" )** |系统会忽略当前语言的货币符号。 |12.34 |
| **Value( "24e3" )** |24 x 10<sup>3</sup>的科学记数法。 |24000 |

