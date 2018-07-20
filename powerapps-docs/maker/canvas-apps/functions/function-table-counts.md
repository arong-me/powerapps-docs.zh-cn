---
title: Count、CountA、CountIf 和 CountRows 函数 | Microsoft 文档
description: PowerApps 中 Count、CountA、CountIf 和 CountRows 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: df972b02408373b48a028b3ec6d98fdfd6f940fe
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39016366"
---
# <a name="count-counta-countif-and-countrows-functions-in-powerapps"></a>PowerApps 中的 Count、CountA、CountIf 和 CountRows 函数
对[表](../working-with-tables.md)中所有[记录](../working-with-tables.md#records)计数，或对所有满足条件的记录计数。

## <a name="description"></a>描述
**Count** 函数对包含单列表中数值的记录数目进行计数。

**CountA** 函数对单列表中不为空白的记录数进行计数。 此函数包括计数中的[空白](function-isblank-isempty.md)文本 ("")。

**CountIf** 函数对表中逻辑公式为 **true** 的记录数进行计数。  该公式可以引用表的[列](../working-with-tables.md#columns)。

**CountRows** 函数对表中的记录数进行计数。

这些函数每一个都会返回一个数值。

[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>语法
**Count**( *SingleColumnTable* )<br>
**CountA**( SingleColumnTable )

* *SingleColumnTable* - 必需。  要计数的记录的列。  

**CountIf**( *Table*, *LogicalFormula* )

* *Table* - 必需。  要计数的记录的表。
* *LogicalFormula* - 必需。  用于对表中每条记录求值的公式。  对此公式返回 **true** 的记录进行计数。  该公式可以引用表的列。

**CountRows**( *Table* )

* *Table* - 必需。  要计数的记录的表。

## <a name="example"></a>示例
1. 导入或创建一个名为**清单**的[集合](../working-with-data-sources.md#collections)，如[在库中显示图像和文本](../show-images-text-gallery-sort-filter.md)所述的第一个子过程。
2. 添加标签，然后将其 **[Text](../controls/properties-core.md)** 属性设置为以下公式：
   
    **CountIf(Inventory, UnitsInStock < 30)**
   
    标签显示为 **2**，因为有两种产品（Ganymede 和 Callisto）的库存量小于 30 套。
3. 添加另一个标签，然后将其 **[Text](../controls/properties-core.md)** 属性设置为以下公式：
   
    **CountA(Inventory.UnitsInStock)**
   
    标签显示为 **5**，表示 **UnitsInStock** 列中非空单元格的数目。
4. 添加另一个标签，然后将其 **[Text](../controls/properties-core.md)** 属性设置为以下公式：
   
    **CountRows(Inventory)**
   
    标签显示为 **5**，因为该集合包含 5 行。

