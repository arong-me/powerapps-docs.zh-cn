---
title: Round、RoundDown 和 RoundUp 函数 | Microsoft 文档
description: PowerApps 中 Round、RoundDown 和 RoundUp 函数的参考信息（包括语法）
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
ms.openlocfilehash: 07771027ea728d65bfb35d79fb67bdef1ac80f1a
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="round-rounddown-and-roundup-functions-in-powerapps"></a>PowerApps 中的 Round、RoundDown 和 RoundUp 函数
舍入数值。

## <a name="description"></a>说明
**Round**、**RoundDown** 和 **RoundUp** 函数可将数值舍入到指定的小数位数：

* 如果后一位数字等于或大于 5，**Round** 函数会向上舍入， 否则向下舍入。
* **RoundDown** 函数始终向下舍入到前一个较小的数值。
* **RoundUp** 函数始终向上舍入到下一个较大的数值。

如果传递单个数值，则返回值为这个数值的舍入版本。  如果传递包含数值的单列[表](../working-with-tables.md)，则返回值为舍入数值的单列表。 如果你有多列表，可以将其调整为单列表，如[使用表](../working-with-tables.md)中所述。

## <a name="syntax"></a>语法
**Round**( *Number*, *DecimalPlaces* )<br>**RoundDown**( *Number*, *DecimalPlaces* )<br>**RoundUp**( *Number*, *DecimalPlaces* )

* *Number* - 必需。 要舍入的数值。
* *DecimalPlaces* - 必需。  要舍入的小数点右边的位数。  使用 0 表示舍入为整数。  

