---
title: Shuffle 函数 | Microsoft 文档
description: PowerApps 中 Shuffle 函数的参考信息（包括语法和示例）
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
ms.openlocfilehash: 3fd93ce6cf9703e9e9fbf69c5826213d9aa78e02
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61519170"
---
# <a name="shuffle-function-in-powerapps"></a>PowerApps 中的 Shuffle 函数
随机重新排列[表](../working-with-tables.md)[记录](../working-with-tables.md#records)的顺序。

## <a name="description"></a>描述
**Shuffle** 函数重新排列表记录的顺序。

**Shuffle** 返回一个表，该表与参数具有相同的[列](../working-with-tables.md#columns)和行数。

## <a name="syntax"></a>语法
**Shuffle**( *Table* )

* *Table* - 必需。  要随机排序的表。

## <a name="example"></a>示例
如果已将打牌时的详细信息存储在名为 **Deck** 的[集合](../working-with-data-sources.md#collections)中，则此公式会返回随机排序的该集合的副本。

**Shuffle(Deck)**

