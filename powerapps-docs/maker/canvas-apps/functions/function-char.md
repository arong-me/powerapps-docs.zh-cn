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
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: aec27b788fff8434cfdc4e0e130487f718a42aa6
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42826356"
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

