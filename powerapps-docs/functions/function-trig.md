---
title: "Acos、Acot、Asin、Atan、Atan2、Cos、Cot、Degrees、Pi、Radians、Sin 和 Tan 函数 | Microsoft 文档"
description: "PowerApps 中 Abs 和 Sqrt 函数的参考信息（包括语法和示例）"
services: 
suite: powerapps
documentationcenter: na
author: gregli-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 09/13/2016
ms.author: gregli
ms.openlocfilehash: 245c2a41254c244daa79a082d041231340c40872
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="acos-acot-asin-atan-atan2-cos-cot-degrees-pi-radians-sin-and-tan-functions-in-powerapps"></a>PowerApps 中的 Acos、Acot、Asin、Atan、Atan2、Cos、Cot、Degrees、Pi、Radians、Sin 和 Tan 函数
计算三角函数的值。

## <a name="description"></a>说明
### <a name="primary-functions"></a>主要函数
**Cos** 函数返回其参数的余弦值（用弧度表示的角度）。

**Cot** 函数返回其参数的余切值（用弧度表示的角度）。

**Sin** 函数返回其参数的正弦值（用弧度表示的角度）。

**Tan** 函数返回其参数的正切值（用弧度表示的角度）。

### <a name="inverse-functions"></a>反三角函数
**Acos** 函数返回其参数的反余弦值。 反余弦值是以余弦值作为参数的角度。  返回的角度以弧度表示，范围在 0（零）至 &pi; 之间。

**Acot** 函数返回其参数的反余切主值。  返回的角度以弧度表示，范围在 0（零）至 &pi; 之间。

**Asin** 函数返回其参数的反正弦值。 反正弦值是以正弦值作为参数的角度。  返回的角度以弧度表示，范围在 -&pi;/2 至 &pi;/2 之间。

**Atan** 函数返回其参数的反正切值。 反正切值是以正切值作为参数的角度。 返回的角度以弧度表示，范围在 -&pi;/2 至 &pi;/2 之间。

**Atan2** 函数返回以指定 *x* 和 *y* 坐标作为参数的反正切值。 这个反正切值是指从 *x* 轴到包含原点 (0, 0) 和坐标为 (*x*, *y*) 的点的直线的角度。 角度以弧度表示，范围在 -&pi; 和 &pi; 之间，不包括 -&pi;。  结果为正表示从 *x* 轴开始的逆时针角度；结果为负表示顺时针角度。  **Atan2(&nbsp;*a*,&nbsp;*b*&nbsp;)** 等于 **Atan(&nbsp;*b*/*a*&nbsp;)**，不过 **Atan2** 函数的 ***a*** 可以等于 0（零）。

### <a name="helper-functions"></a>Helper 函数
**Degrees** 函数可将弧度转换为角度。  弧度 &pi; 等于 180 度。

**Pi** 函数返回超越数 &pi;，前几位是 3.141592...

**Radians** 函数可将角度转换为弧度。  

### <a name="notes"></a>说明
如果将单个数值传递给这些函数，则返回值为单个结果。  如果你传递包含数字的单列[表](../working-with-tables.md)，则返回单列表结果值，参数表中每条记录都对应一个结果。 如果你有多列表，可以将其调整为单列表，如[使用表](../working-with-tables.md)中所述。  

如果参数的结果值是未定义的值，则结果为 *blank*。  例如，当反三角函数使用超出范围的参数时，可能就会出现这种情况。

## <a name="syntax"></a>语法
### <a name="primary-functions"></a>主要函数
**Cos**( *Radians* )<br>**Cot**( *Radians* )<br>**Sin**( *Radians* )<br>**Tan**( *Radians* )

* *Radians* - 必需。 要计算的角度。

**Cos**( *SingleColumnTable* )<br>**Cot**( *SingleColumnTable* )<br>**Sin**( *SingleColumnTable* )<br>**Tan**( *SingleColumnTable* )

* *SingleColumnTable* - 必需。 要计算的角度的单列表。

### <a name="inverse-functions"></a>反三角函数
**Acos**( *Number* )<br>**Acot**( *Number* )<br>**Asin**( *Number* )<br>**Atan**( *Number* )

* *Number* - 必需。 要计算的数字。

**Acos**( *SingleColumnTable* )<br>**Acot**( *SingleColumnTable* )<br>**Asin**( *SingleColumnTable* )<br>**Atan**( *SingleColumnTable* )

* *SingleColumnTable* - 必需。 要计算的单列表数字。

**Atan2**( *X*, *Y* )

* *X* - 必需。  *X* - 轴坐标。
* *Y* - 必需。  *Y* - 轴坐标。

### <a name="helper-functions"></a>Helper 函数
**Degrees**( *Radians* )

* *Radians* - 必需。  以弧度表示，要转换为度数的角度。

**Pi**()

**Radians**( *Degrees* )

* *Degrees* - 必需。  以度数表示，要转换为弧度的角度。

## <a name="examples"></a>示例
### <a name="single-number"></a>单个数字
| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **Cos(&nbsp;1.047197&nbsp;)** |返回 1.047197 弧度或 60 度的余弦值。 |0.5 |
| **Cot(&nbsp;Pi()/4&nbsp;)** |返回 0.785398... 弧度或 45 度的余切值。 |1 |
| **Sin(&nbsp;Pi()/2&nbsp;)** |返回 1.570796... 弧度或 90 度的正弦值。 |1 |
| **Tan(&nbsp;Radians(60)&nbsp;)** |返回 1.047197... 弧度或 60 度的正切值。 |1.732050... |
| **Acos(&nbsp;0.5&nbsp;)** |返回 0.5 的反余弦值（以弧度表示）。 |1.047197... |
| **Acot(&nbsp;1&nbsp;)** |返回 1 的反余切值（以弧度表示）。 |0.785398... |
| **Asin(&nbsp;1&nbsp;)** |返回 1 的反正弦值（以弧度表示） |1.570796... |
| **Atan(&nbsp;1.732050&nbsp;)** |返回 1.732050 的反正切值（以弧度表示）。 |1.047197... |
| **Atan2(&nbsp;5,&nbsp;3&nbsp;)** |返回从 *x* 轴到包含原点 (0,0) 和坐标 (5,3) 的直线的角度（约为 31 度）的反正切值。 |0.540419... |
| **Atan2(&nbsp;4,&nbsp;4&nbsp;)** |返回从 *x* 轴到包含原点 (0,0) 和坐标 (4,4) 的直线的角度（刚好为 &pi;/4 弧度或 45 度）的反正切值。 |0.785398... |
| **Degrees(&nbsp;1.047197&nbsp;)** |返回 1.047197 弧度的相等度数。 |60 |
| **Pi()** |返回超越数 &pi;。 |3.141592... |
| **Radians(&nbsp;15&nbsp;)** |返回 15 度的相等弧度。 |0.261799... |

### <a name="single-column-table"></a>单列表
本部分的示例使用名为 **ValueTable** 的[数据源](../working-with-data-sources.md)，其中包括以下数据。  表中的最后一条记录是 &pi;/2 弧度或 90 度。

![](media/function-trig/values.png)

| 公式 | 说明 | 结果 |
| --- | --- | --- |
| **Cos(&nbsp;ValueTable&nbsp;)** |返回表中每个数字的余弦值。 |<style> img { max-width: none } </style> ![](media/function-trig/values-cos.png) |
| **Cot(&nbsp;ValueTable&nbsp;)** |返回表中每个数字的余切值。 |<style> img { max-width: none } </style> ![](media/function-trig/values-cot.png) |
| **Sin(&nbsp;ValueTable&nbsp;)** |返回表中每个数字的正弦值。 |<style> img { max-width: none } </style> ![](media/function-trig/values-sin.png) |
| **Tan(&nbsp;ValueTable&nbsp;)** |返回表中每个数字的正切值。 |<style> img { max-width: none } </style> ![](media/function-trig/values-tan.png) |
| **Acos(&nbsp;ValueTable&nbsp;)** |返回表中每个数字的反余弦值。 |<style> img { max-width: none } </style> ![](media/function-trig/values-acos.png) |
| **Acot(&nbsp;ValueTable&nbsp;)** |返回表中每个数字的反余切值。 |<style> img { max-width: none } </style> ![](media/function-trig/values-acot.png) |
| **Asin(&nbsp;ValueTable&nbsp;)** |返回表中每个数字的反正弦值。 |<style> img { max-width: none } </style> ![](media/function-trig/values-asin.png) |
| **Atan(&nbsp;ValueTable&nbsp;)** |返回表中每个数字的反正切值。 |<style> img { max-width: none } </style> ![](media/function-trig/values-atan.png) |
| **Degrees(&nbsp;ValueTable&nbsp;)** |返回表中每个数字的相等度数，假设以弧度表示角度。 |<style> img { max-width: none } </style> ![](media/function-trig/values-degrees.png) |
| **Radians(&nbsp;ValueTable&nbsp;)** |返回表中每个数字的相等弧度数，假设以度表示角度。 |<style> img { max-width: none } </style> ![](media/function-trig/values-radians.png) |

