---
title: Shuffle 函数 | Microsoft 文档
description: PowerApps 中 Shuffle 函数的参考信息（包括语法和示例）
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
ms.openlocfilehash: 6d981c410b22dd9db52cdf077a00e6eaae83be75
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="shuffle-function-in-powerapps"></a>PowerApps 中的 Shuffle 函数
随机重新排列[表](../working-with-tables.md)[记录](../working-with-tables.md#records)的顺序。

## <a name="description"></a>说明
**Shuffle** 函数重新排列表记录的顺序。

**Shuffle** 返回一个表，该表与参数具有相同的[列](../working-with-tables.md#columns)和行数。

## <a name="syntax"></a>语法
**Shuffle**( *Table* )

* *Table* - 必需。  要随机排序的表。

## <a name="example"></a>示例
如果已将打牌时的详细信息存储在名为 **Deck** 的[集合](../working-with-data-sources.md#collections)中，则此公式会返回随机排序的该集合的副本。

**Shuffle(Deck)**

