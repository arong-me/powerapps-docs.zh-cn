---
title: Find 函数 | Microsoft 文档
description: PowerApps 中 Find 函数的引用信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/07/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fbdd29ed1757301f076ab6bebea548fcd7a963cc
ms.sourcegitcommit: 7dae19a44247ef6aad4c718fdc7c68d298b0a1f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "71984953"
---
# <a name="find-function-in-powerapps"></a>PowerApps 中的 Find 函数
在其他字符串中查找文本字符串（如果存在）。

## <a name="description"></a>说明
**Find** 函数在其他字符串中查找字符串，且区分大小写。 若要忽略大小写，需首先对参数使用 **[Lower](function-lower-upper-proper.md)** 函数。

**Find** 返回找到的字符串的起始位置。  位置 1 是字符串的第一个字符。 如果在其中进行搜索的字符串中不包含要搜索的字符串，**Find** 将返回空白。

## <a name="syntax"></a>语法
**Find**( *FindString*, *WithinString* [, *StartingPosition* ] )

* *FindString* - 必需。  要查找的字符串。
* *WithinString* - 必需。  要在其中搜索的字符串。
* *StartingPosition* - 可选。  开始搜索的起始位置。  位置 1 是第一个字符。

