---
title: Blank、Coalesce、IsBlank 和 IsEmpty 函数 | Microsoft 文档
description: PowerApps 中 Blank、Coalesce、IsBlank 和 IsEmpty 函数的参考信息（包括语法和示例）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.component: canvas
ms.date: 08/27/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: fec70eae81568cf2360c3413d878301b3c0dcf0b
ms.sourcegitcommit: 06612108755d386b9df41bd6f45157e94e929511
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2019
ms.locfileid: "70064874"
---
# <a name="blank-coalesce-isblank-and-isempty-functions-in-powerapps"></a>PowerApps 中的 Blank、Coalesce、IsBlank 和 IsEmpty 函数
测试值是否为空白值，或测试[表](../working-with-tables.md)是否不包含任何[记录](../working-with-tables.md#records)，并能创建*空白*值。

## <a name="overview"></a>概述
*Blank* 是“空值”或“未知值”的占位符。  例如, 如果用户未进行选择, 则 **[组合框](../controls/control-combo-box.md)** 控件的**所选**属性为*空白*。 许多数据源可以存储和返回 NULL 值, 这些值在 PowerApps 中表示为*空白*。

PowerApps 中的任何属性或计算值都可以为*空*。  例如，布尔型数据的值通常是：**true** 或 **false**。  但除这两个外, 它还可以为*空*, 表示状态未知。  这类似于 Microsoft Excel, 在这种情况下, 工作表单元格的开头为空白, 不包含任何内容, 但可以保存值**TRUE**或**FALSE** (等等)。 在任何时候, 都可以再次清除单元格的内容, 并将其返回到*空白*状态。

*空字符串*指的是不包含任何字符的字符串。  [ **Len**函数](function-len.md)对于此类字符串返回零, 可以在公式中以两个双引号来编写, 而不是在两者`""`之间。  某些控件和数据源使用空字符串指示 "无值" 条件。  为了简化应用程序创建, **IsBlank**和**合并**函数将测试*空*值或空字符串。    

在**IsEmpty**函数的上下文中,*空*特定于不包含任何记录的表。 即使表只包含[列](../working-with-tables.md#columns)名称，而不包含任何数据，它也是一个完整的表。 一个表刚开始可能是空表，但填入记录后，就不再是空表了；如果将其中的记录删除，那么它又会变成空表。

> [!NOTE]
> 我们正在转换一段时间。  到现在为止, 还使用了*空白*来报告错误, 这使得不可能将有效的 "无值" 与错误区分开来。  出于此原因, 目前只有本地集合支持存储*空白*值。  如果在 "文件" 菜单、"应用设置"、"高级设置" 和 "实验功能" 下启用 "公式级错误管理" 实验功能, 则可以在其他数据源中存储*空白*值。  我们正在积极努力完成此功能, 并将*空白*值正确地分隔开来。

## <a name="description"></a>描述
**Blank** 函数返回*空白*值。 此函数可用于在支持 NULL 值的数据源中存储这些值，进而可以从字段中有效删除所有值。

**IsBlank**函数测试*空*值或空字符串。  此测试包含空字符串以简化应用程序的创建, 因为某些数据源和控件在没有值时使用空字符串。  若要专门测试*空白*值, 请`if( Value = Blank(), ...`使用而不是**IsBlank**。

**合并**函数按顺序计算其参数, 并返回不*为空*或空字符串的第一个值。  使用此函数可将*空*值或空字符串替换为不同的值, 但保留非*空白*和非空字符串值不变。  如果所有参数均为*空白*或空字符串, 则函数将返回*空白*, 从而使**合并**成为将空字符串转换为*空白*值的好方法。  Coalesce 的所有参数必须是同一种类型；例如，不能将数字和文本字符串混合在一起。  

`Coalesce( value1, value2 )`的等效等效项`If( Not IsBlank( value1 ), value1, Not IsBlank( value2 ), value2 )` , 且不需要**value1**和**value2**进行两次计算。  如果在此处没有 "else" 公式, 则[ **if**函数](function-if.md)返回*空白*。

**IsEmpty** 函数用于测试表是否包含记录。 这个函数跟使用 **[CountRows](function-table-counts.md)** 函数的效果相同，只不过它是检查表中的记录数是否为零。 可以结合使用 **IsEmpty** 和 **[Errors](function-errors.md)** 函数，从而检查数据源错误。

**IsBlank** 和 **IsEmpty** 的返回值都是布尔值 **true** 或 **false**。

## <a name="syntax"></a>语法
**Blank**()

**Coalesce**( *Value1* [, *Value2*, ... ] )

* *Value(s)* – 必需。 要测试的值。  每个值都按顺序计算, 直到找到一个不*为*空且未找到空字符串的值。  不计算此点之后的值。  

**IsBlank**( *Value* )

* *Value* - 必需。 要测试是否为*空*值或空字符串的值。

**IsEmpty**( *Table* )

* *Table* - 必需。 要测试是否包含记录的表。

## <a name="examples"></a>示例
### <a name="blank"></a>Blank
> [!NOTE]
> 下面的示例暂只适用于本地集合。  如果在 "文件" 菜单、"应用设置"、"高级设置" 和 "实验功能" 下启用 "公式级错误管理" 实验功能, 则可以在其他数据源中存储*空白*值。  我们正在积极努力完成此功能, 并将*空白*值与错误分离出来。

1. 从头开始创建应用，然后添加一个“按钮”控件。
2. 将该按钮的 **[OnSelect](../controls/properties-core.md)** 属性设置为以下公式：

    ```powerapps-dot
    ClearCollect( Cities, { Name: "Seattle", Weather: "Rainy" } )
    ```
3. 预览应用，单击或点击所添加的按钮，然后关闭预览。  
4. 在“文件”菜单上，单击或点击“集合”。

     此时，“Cities”集合显示，其中包含一条内容为“Seattle”和“Rainy”的记录：

    ![显示“Seattle”对应的“Weather”字段值为“Rainy”的集合](./media/function-isblank-isempty/seattle-rainy.png)
5. 单击或点击后退箭头，返回到默认工作区。
6. 添加一个“标签”控件，然后将“Text”属性设置为以下公式：

    ```powerapps-dot
    IsBlank( First( Cities ).Weather )
    ```

    此标签显示“false”，因为“Weather”字段包含值“Rainy”。
7. 添加第二个按钮，然后将“OnSelect”属性设置为以下公式：

    ```powerapps-dot
    Patch( Cities, First( Cities ), { Weather: Blank() } )
    ```
8. 预览应用，单击或点击所添加的按钮，然后关闭预览。  

    “Cities”集合中第一条记录的“Weather”字段被替换成*空白*值，删除了之前使用的“Rainy”。

    ![显示“Seattle”对应的“Weather”字段值为空白的集合](./media/function-isblank-isempty/seattle-blank.png)

    此标签显示“true”，因为“Weather”字段不再包含值。

### <a name="coalesce"></a>Coalesce

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **合并 (&nbsp;空白 (),&nbsp;1&nbsp;)** |测试从 **Blank** 函数返回的值，此函数始终返回*空白*值。 由于第一个参数为*空*, 因此将继续计算下一个参数, 直到找到非*空*值和非空字符串。 |**1** |
| **合并 ("", 2)** |测试第一个参数为空字符串。 由于第一个参数是空字符串, 因此将继续计算下一个参数, 直到找到非*空*值和非空字符串。 |**2** |
| **合并 (空白 ()、""、空白 ()、""、3、4)** |**合并**从自变量列表的开头开始, 依次计算每个参数, 直到找到非*空*值和非空字符串。  在这种情况下, 前四个参数均返回*空白*或空字符串, 因此求值继续到第五个参数。 第五个参数不为*空*且不为空字符串, 因此计算在此处停止。 将返回第五个参数的值，并且不再评估第六个参数。 |**3** |
| **合并 ("")** | 测试第一个参数为空字符串。 由于第一个参数为空字符串, 并且没有更多的参数, 因此该函数返回*空白*。   |空白 |

### <a name="isblank"></a>IsBlank
1. 从头开始创建应用，然后添加一个文本输入控件，并将其命名为“FirstName”。
2. 添加一个标签，然后将其 **[Text](../controls/properties-core.md)** 属性设置为以下公式：

    ```powerapps-dot
    If( IsBlank( FirstName.Text ), "First Name is a required field." )
    ```

    文本输入控件的“[Text](../controls/properties-core.md)”属性默认设置为“Text input”。 因为此属性包含值，所以它不是空的，标签也不会显示任何消息。
3. 从文本输入控件中删除所有字符（包括空格）。

    由于 **[Text](../controls/properties-core.md)** 属性不再包含任何字符, 因此它为空字符串, 并且**IsBlank (FirstName)** 为**true**。 现在就会显示“必填字段”这样的消息了。

若要了解如何使用其他工具执行验证，请参阅 **[Validate](function-validate.md)** 函数和[使用数据源](../working-with-data-sources.md)。  

其他示例：

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **IsBlank (&nbsp;空白 ()&nbsp;)** |测试从 **Blank** 函数返回的值，此函数始终返回*空白*值。 |**true** |
| **IsBlank( "" )** |不包含任何字符的字符串。 |**true** |
| **IsBlank( "Hello" )** |包含一个或多个字符的字符串。 |**false** |
| **IsBlank( *AnyCollection* )** |由于存在[集合](../working-with-data-sources.md#collections)，所以即使不包含任何记录，它的值也不是空值。 要检查是不是空集合，请使用 **IsEmpty**。 |**false** |
| **IsBlank( Mid( "Hello", 17, 2 ) )** |**[Mid](function-left-mid-right.md)** 函数的起始字符超出了字符串的结束位置。  所以结果是空字符串。 |**true** |
| **IsBlank( If( false, false ) )** |**[If](function-if.md)** 函数没有 *ElseResult* 部分。  由于条件的结果始终是 **false**，所以 **[If](function-if.md)** 函数始终返回 *blank* 值。 |**true** |

### <a name="isempty"></a>IsEmpty
1. 从头开始创建应用，然后添加一个“按钮”控件。
2. 将该按钮的 **[OnSelect](../controls/properties-core.md)** 属性设置为以下公式：

    **Collect (IceCream, {口味:"草莓", 数量:300}, {口味:"巧克力", 数量:100})**
3. 预览应用，单击或点击所添加的按钮，然后关闭预览。  

    创建“IceCream”集合，其中包含以下数据：

    ![](media/function-isblank-isempty/icecream-strawberry-chocolate.png)

    其中有两条记录，所以它不是空集。 **IsEmpty( IceCream )** 返回 **false**，**CountRows( IceCream )** 返回 **2**。
4. 添加第二个按钮，然后将“[OnSelect](../controls/properties-core.md)”属性设置为以下公式：

    **Clear( IceCream )**
5. 预览应用，单击或点击第二个按钮，然后关闭预览。  

    这个集合现在变成了空集：

    ![](media/function-isblank-isempty/icecream-clear.png)

    **[Clear](function-clear-collect-clearcollect.md)** 函数可删除集合中的所有记录，导致集合变成空集。 **IsEmpty( IceCream )** 返回 **true**，**CountRows( IceCream )** 返回 **0**。

还可以使用 **IsEmpty** 测试一个计算的表是不是空表，请参阅以下示例：

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **IsEmpty( [&nbsp;1,&nbsp;2,&nbsp;3 ] )** |单列表包含三条记录，所以，它不是空表。 |**false** |
| **IsEmpty( [&nbsp;] )** |单列表不包含任何记录，所以它是空表。 |**true** |
| **IsEmpty( Filter( [&nbsp;1,&nbsp;2,&nbsp;3&nbsp;], Value > 5 ) )** |单列表不包含任何大于 5 的值。  筛选器没有筛选出任何记录，所以它是空表。 |**true** |

