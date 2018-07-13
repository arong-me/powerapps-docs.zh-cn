---
title: Char 函数 | Microsoft 文档
description: PowerApps 中 Char 函数的参考信息（包括语法和示例）
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: b5d63b26498b94943f5340d9f57f3255390c7c94
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2018
ms.locfileid: "37895974"
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

