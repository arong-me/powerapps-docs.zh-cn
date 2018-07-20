---
title: Char 函数 | Microsoft 文档
description: PowerApps 中 Char 函数的参考信息（包括语法和示例）
dauthor: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 9c701527fb02613332cfa5bc542681f8c119f3b3
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39014549"
---
# <a name="char-function-in-powerapps"></a>PowerApps 中的 Char 函数
将字符代码转换为字符串。

## <a name="description"></a>描述
**Char** 函数可返回包含适用于你的平台的相应 ASCII 字符的字符串。

## <a name="syntax"></a>语法
**Char**( *CharacterCode* )

* *CharacterCode* - 必需。 要转换的 ASCII 字符代码。

## <a name="examples"></a>示例

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Char( 65 )** |返回 ASCII 代码 65 对应的字符。 |A |
| **Char( 105 )** |返回 ASCII 代码 105 对应的字符。 |i |
| **Char( 35 )** |返回 ASCII 代码 35 对应的字符。 |# |

