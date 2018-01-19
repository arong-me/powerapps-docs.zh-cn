---
title: "Char 函数 | Microsoft 文档"
description: "PowerApps 中 Char 函数的参考信息（包括语法和示例）"
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
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 7ce510840845b1a1df2d590c4f3ffdddfc5bfb9c
ms.sourcegitcommit: 33099e6197c0139679cd08c42e9e2a5717904c92
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/12/2018
---
# <a name="char-function-in-powerapps"></a>PowerApps 中的 Char 函数
将字符代码转换为字符串。

## <a name="description"></a>说明
**Char** 函数可返回包含适用于你的平台的相应 ASCII 字符的字符串。

## <a name="syntax"></a>语法
**Char**( *CharacterCode* )

* *CharacterCode* - 必需。 要转换的 ASCII 字符代码。

## <a name="examples"></a>示例
| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **Char( 65 )** |返回 ASCII 代码 65 对应的字符。 |A |
| **Char( 105 )** |返回 ASCII 代码 105 对应的字符。 |i |
| **Char( 35 )** |返回 ASCII 代码 35 对应的字符。 |# |

