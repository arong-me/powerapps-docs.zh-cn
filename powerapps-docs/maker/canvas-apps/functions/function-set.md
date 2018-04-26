---
title: Set 函数 | Microsoft 文档
description: PowerApps 中 Set 函数的参考信息（包括语法和示例）
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 06/29/2017
ms.author: gregli
ms.openlocfilehash: 3615328bf1c272425779998545b0d16ac5626297
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="set-function-in-powerapps"></a>PowerApps 中的 Set 函数
设置全局变量的值。

## <a name="overview"></a>概述
使用 **Set** 函数设置全局变量的值，该变量暂时保留一条信息，如用户已选择某按钮的次数或数据运算的结果。  

全局变量可用于应用的所有屏幕。  它们是最简单的变量类型，并且可满足多数场景的需求。  另外，还有上下文变量，它们的作用域仅限于单个屏幕和允许对表进行行级别修改的集合。  有关这些其他选项的详细信息，请参阅[使用变量](../working-with-variables.md)。

PowerApps 以公式为基础，这些公式会在用户与应用交互时自动重新计算。  全局变量不具有此优势，因此，在应用的创建和理解上可能难度更大。  使用变量之前，请参阅[使用变量](../working-with-variables.md)。

## <a name="description"></a>说明
全局变量是使用 **Set** 函数隐式创建而成。  无需显式声明。  如果删除了全局变量的所有 **Set** 函数，则该全局变量将不再存在。  若要清除变量，请将其值设置为 [Blank 函数](function-isblank-isempty.md)的结果。

在创作环境中，可以使用“文件”菜单下的“变量”视图查看变量的值、定义和使用情况。

如本主题后面的示例所示，全局变量可保留多种信息，包括：

* 单个值
* 记录
* 表
* 对象引用
* 公式的任何结果

全局变量可保留其值，直到应用关闭。  应用关闭后，全局变量的值将丢失，重新加载应用时则必须重新创建该值。

全局变量使用的名称不能与已有集合或控件相同。  其使用的名称可以与上下文变量相同。  若要区分这两者，请使用[消除歧义运算符](operators.md#disambiguation-operator)。

**Set** 没有返回值，只可以在[行为公式](../working-with-formulas-in-depth.md)中使用它。

## <a name="syntax"></a>语法
**Set**( *VariableName*, *Value* )

* *VariableName* - 必需。  要创建或更新的全局变量名称。
* *Value* - 必需。  要分配给上下文变量的值。

## <a name="examples"></a>示例
| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **Set(&nbsp;Counter,&nbsp;1&nbsp;)** |创建或修改全局变量 **Counter**，将其值设置为 **1**。 |**Counter** 的值为 **1**。 可通过在公式中使用名称 **Counter** 来在任意屏幕上引用该变量。 |
| **Set(&nbsp;Counter,&nbsp;2&nbsp;)** |将上一示例中 **Counter** 全局变量的值设置为 **2**。 |**Counter** 的值为 **2**。 |
| **Set(&nbsp;Counter,&nbsp;Counter + 1&nbsp;)** |将上一示例中 **Counter** 全局变量的值增加至 **3**。 |**Counter** 的值为 **3**。 |
| **Set(&nbsp;Name,&nbsp;"Lily" )** |创建或修改全局变量 **Name**，将其值设置为 **Lily**。 |**Name** 的值为 **Lily**。 |
| **Set(&nbsp;Person,&nbsp;{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;} )** |创建或修改全局变量 **Person**，将其值设置为一条记录。 该记录包含名为“姓名”和“地址”的两列。 “姓名”列为 **Milton**，“地址”列的值为 **1 Main St**。 |**Person** 的值为记录 **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}**。<br><br>使用名称 **Person** 整体引用此记录，或使用 **Person.Name** 或 **Person.Address** 引用此记录的单个列。 |
| **Set(&nbsp;Person, Patch(&nbsp;Person,&nbsp;{Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}&nbsp;)&nbsp;)** |搭配使用 **[Patch](function-patch.md)** 函数更新 **Person** 全局变量，将“地址”列的值设置为 **2 Main St**。 |**Person** 现在的值为记录 **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}**。 |

