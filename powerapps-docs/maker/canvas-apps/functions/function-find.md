---
title: Find 函数 | Microsoft 文档
description: PowerApps 中 Find 函数的引用信息（包括语法和示例）
author: gregli-msft
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
ms.openlocfilehash: 04f257b40e778d3611203f2bdc17aad5554a4ac6
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551022"
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

