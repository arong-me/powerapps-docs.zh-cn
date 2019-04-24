---
title: Distinct 函数 | Microsoft 文档
description: PowerApps 中 Distinct 函数的引用信息（包括语法和示例）
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
ms.openlocfilehash: 17a2f2cfca16c5589f74ac434b36326037146b16
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61551206"
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

