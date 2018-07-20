---
title: First、FirstN、Last 和 LastN 函数 | Microsoft 文档
description: PowerApps 中 First、FirstN、Last 和 LastN 的引用信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 11/07/2015
ms.author: gregli
ms.openlocfilehash: 3d94a3a250041ec7524460640f0bca4351ddcacf
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39021104"
---
# <a name="first-firstn-last-and-lastn-functions-in-powerapps"></a>PowerApps 中的 First、FirstN、Last 和 LastN 函数
返回表中的第一组或最后一组[记录](../working-with-tables.md#records)。

## <a name="description"></a>描述
**First** 函数返回[表](../working-with-tables.md)中的第一条记录。

**FirstN** 函数返回表中的第一组记录，第二个参数指定要返回的记录数。

**Last** 函数返回表中的最后一条记录。

**LastN** 函数返回表中的最后一组记录，第二个参数指定要返回的记录数。

**First** 和 **Last** 都返回单个记录。  **FirstN** 和 **LastN** 都返回一个表，即使仅指定了单个记录。

[!INCLUDE [delegation-no](../../../includes/delegation-no.md)]

## <a name="syntax"></a>语法
**First**( *Table* )<br>**Last**( *Table* )

* *Table* - 必需。 要运算的表。

**FirstN**( *Table* [, *NumberOfRecords* ] )<br>**LastN**( *Table* [, *NumberOfRecords* ] )

* *Table* - 必需。 要运算的表。
* *NumberOfRecords* - 可选。  要返回的记录数。 如果未指定此参数，函数将返回一条记录。

## <a name="examples"></a>示例
此公式返回名为 **Employees** 的表中的第一条记录：<br>
**First(Employees)**

此公式返回名为 **Employees** 的表中的最后 15 条记录：<br>
**LastN(Employees, 15)**

