---
title: Table 函数 | Microsoft 文档
description: PowerApps 中 Table 函数的参考信息（包括语法和示例）
services: ''
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 2f543a75019bfe5d665aedb2e6171200e8321690
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="table-function-in-powerapps"></a>PowerApps 中的 Table 函数
创建一个临时[表](../working-with-tables.md)。

## <a name="description"></a>说明
**Table** 函数从[记录](../working-with-tables.md#records)的参数列表创建表。

该表的[列](../working-with-tables.md#columns)将是所有参数记录的所有属性的联合。 如果某个列的记录不包含值，则向该列添加空白值。

表是 PowerApps 中的一个值，与字符串或数字类似。 可将表指定为函数的参数，函数可以返回表作为结果。 **Table** 不创建永久表， 而是返回由参数组成的临时表。  可以将该临时表指定为另一函数的参数、在库中将其可视化，或者将其嵌入另一表中。  请参阅[使用表](../working-with-tables.md)，了解更多详情。

也可按照 **[ value1, value2, ... ]** 语法创建单个列的表。

## <a name="syntax"></a>语法
**Table**( *Record1* [, *Record2*, ... ] )

* *Record(s)* - 必需。 要添加到表的记录。

## <a name="examples"></a>示例
* 将列表框的 **[Items](../controls/properties-core.md)** 属性设置为以下公式：
  <br>**Table({Color:"red"}, {Color:"green"}, {Color:"blue"})**
  
    列表框将每种颜色显示为一个选项。
* 添加一个文本库，然后将其 **[Items](../controls/properties-core.md)** 属性设置为以下函数：<br>
  **Table({Item:"Violin123", Location:"France", Owner:"Fabrikam"}, {Item:"Violin456", Location:"Chile"})**
  
    该库显示两条记录，每个记录都包含项的名称和位置。 只有一条记录包含所有者的名称。
