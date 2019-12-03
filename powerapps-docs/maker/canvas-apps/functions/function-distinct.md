---
title: Distinct 函数 | Microsoft 文档
description: Power Apps 中不同函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 09/14/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: b77cdf452250fc30e1b8c61867f82e5f109fff49
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74731227"
---
# <a name="distinct-function-in-power-apps"></a>Power Apps 中的不同函数
对[表](../working-with-tables.md)中的[记录](../working-with-tables.md#records)进行汇总，并删除重复项。

## <a name="description"></a>描述
**Distinct**函数在表的每个记录中计算公式，并返回包含重复值的结果的单列表。  列的名称为**Result**。  

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

[!INCLUDE [delegation-no-one](../../../includes/delegation-no-one.md)]

## <a name="syntax"></a>语法
**Distinct**( *Table*, *Formula* )

* *Table* - 必需。  要对其进行求值的表。
* *Formula* - 必需。  用于对每条记录求值的公式。

## <a name="example"></a>示例

1. 插入[**按钮**](../controls/control-button.md)控件，并将其**OnSelect**属性设置为此公式。

    ```powerapps-dot
    ClearCollect( CityPopulations,
        { City: "London",    Country: "United Kingdom", Population: 8615000 },
        { City: "Berlin",    Country: "Germany",        Population: 3562000 },
        { City: "Madrid",    Country: "Spain",          Population: 3165000 },
        { City: "Hamburg",   Country: "Germany",        Population: 1760000 },
        { City: "Barcelona", Country: "Spain",          Population: 1602000 },
        { City: "Munich",    Country: "Germany",        Population: 1494000 }
    );
    ```

1. 按住 Alt 键的同时选择该按钮。

    公式为 evaluatd，并通过在公式栏中选择**CityPopulations**来创建**CityPopulations**集合：

    > [!div class="mx-imgBorder"]
    > ![结果视图中显示的 CityPopulations 集合](media/function-distinct/citypopulations-create.png)

1. 插入 "[**数据表" 控件，** ](../controls/control-data-table.md)并将其**Items**属性设置为以下公式：

    ```powerapps-dot
    Distinct( CityPopulations, Country )
    ```

    您可以通过选择整个公式来查看公式栏中此公式的结果：

    > [!div class="mx-imgBorder"]
    > 结果视图中显示的不同函数 ![输出](media/function-distinct/citypopulations-distinct.png)

1. 使用数据表的 "属性" 窗格中的 "**编辑字段**" 链接来添加**结果**列：

    > [!div class="mx-imgBorder"]
    > ![数据表中显示的不同函数的输出](media/function-distinct/citypopulations-datatable.png)

1. 插入 "[**标签**](../controls/control-text-box.md)" 控件，并将 " **Text** " 属性设置为公式：

    ```powerapps-dot
    First( Sort( Distinct( CityPopulations, Country ), Result ) ).Result
    ```

    此公式将**不同**于[**排序**](function-sort.md)函数的结果排序，从得到的表中获取第一条记录和[**第一个**](function-first-last.md)函数，并提取**结果**字段以仅获取国家/地区名称。

    > [!div class="mx-imgBorder"]
    > ![按名称显示第一个国家/地区的不同函数的输出](media/function-distinct/citypopulations-first.png)

     
