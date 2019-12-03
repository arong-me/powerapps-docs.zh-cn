---
title: Defaults 函数 | Microsoft 文档
description: Power Apps 中的默认函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 11/01/2015
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ad3d8198d73a698abb771aef7230c12b48ff0f56
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731123"
---
# <a name="defaults-function-in-power-apps"></a>Power Apps 中的默认函数
返回[数据源](../working-with-data-sources.md)的默认值。  

## <a name="description"></a>描述
使用 **Defaults** 函数可预填充数据输入表单，简化操作。

这个函数返回包含数据源默认值的[记录](../working-with-tables.md#records)。  如果数据源中的[列](../working-with-tables.md#columns)没有默认值，则不会有这个属性。

数据源中提供的默认信息量可能不同，甚至可能不提供任何信息。  使用[集合](../working-with-data-sources.md#collections)或不支持默认值的其他数据源时，**Defaults** 函数会返回 [empty](function-isblank-isempty.md) 记录。

结合使用 **Defaults** 函数和 **[Patch](function-patch.md)** 函数可[创建记录](../working-with-data-sources.md)。

## <a name="syntax"></a>语法
**Defaults**( *DataSource* )

* *DataSource* - 必需。 需要其默认值的数据源。

## <a name="examples"></a>示例

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **Defaults(&nbsp;Scores&nbsp;)** |返回 **Scores** 数据源的默认值。 |**{ Score: 0 }** |

