---
title: Shuffle 函数 | Microsoft 文档
description: Power Apps 中的无序函数的参考信息（包括语法和示例）
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
ms.openlocfilehash: c67e8095a7c0ed3246bce0401bbe787becd7cea0
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74730153"
---
# <a name="shuffle-function-in-power-apps"></a>在 Power Apps 中无序播放函数
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

