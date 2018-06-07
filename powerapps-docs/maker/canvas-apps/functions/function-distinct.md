---
title: Distinct 函数 | Microsoft 文档
description: PowerApps 中 Distinct 函数的引用信息（包括语法和示例）
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
ms.openlocfilehash: 101c28f2b4ac8135a9b4def9421f886f373105bf
ms.sourcegitcommit: 68fc13fdc2c991c499ad6fe9ae1e0f8dab597139
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "31825570"
---
# <a name="distinct-function-in-powerapps"></a>PowerApps 中的 Distinct 函数
对[表](../working-with-tables.md)中的[记录](../working-with-tables.md#records)进行汇总，并删除重复项。

## <a name="description"></a>描述
**Distinct** 函数对表中的各条记录进行公式求值。 **Distinct** 返回一个包含结果的单列表，其中删除了重复项。  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

## <a name="syntax"></a>语法
**Distinct**( *Table*, *Formula* )

* *Table* - 必需。  要对其进行求值的表。
* *Formula* - 必需。  用于对每条记录求值的公式。

## <a name="example"></a>示例
如果 **Employees** 表中包含 **Department** 列，无论每个部门名称在表中出现多少次，以下函数都会在该列中列出每个唯一部门名称：

**Distinct(Employees, Department)**

