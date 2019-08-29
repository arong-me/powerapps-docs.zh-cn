---
title: With 函数 |Microsoft Docs
description: PowerApps 中 With 函数的参考信息 (包括语法)
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 08/15/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c8d793fcfd2992a781f92d529002e22a34a9df5a
ms.sourcegitcommit: 742a5a21e73a811e9cea353d8275f09c22366afc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2019
ms.locfileid: "70130341"
---
# <a name="with-function-in-powerapps"></a>PowerApps 中的 With 函数
计算值并对单个[记录](../working-with-tables.md#records)执行操作, 包括命名值的内联记录。

## <a name="description"></a>描述

**With**函数为单个记录计算公式。  该公式可以计算值并/或执行操作，例如修改数据或使用连接。  使用[ **ForAll**函数](function-forall.md)可以计算记录表中所有记录的公式。

[!INCLUDE [record-scope](../../../includes/record-scope.md)]

使用**With**可以通过将复杂公式划分为较小的命名子公式来改善其可读性。  这些命名值的作用类似于**通过**的范围限制为的简单局部变量。  与[ **UpdateContext**函数](function-updatecontext.md)一起使用的内联记录语法可以与**with**一起使用。  使用**With**比上下文或全局变量优先, 因为它是自包含的, 易于理解, 并且可在任何声明性公式上下文中使用。  

使用**With**来访问由函数 (例如[**Patch**](function-patch.md)或[**Match**](function-ismatch.md)) 返回的记录的字段。  **包含**这些函数的值长时间足以用于进一步计算或操作。  

如果的*记录*参数为错误, 则函数将返回该错误, 并且不会计算*公式*。

## <a name="syntax"></a>语法
**带有**(*记录*,*公式*)

* *Record* –必需。 要处理的记录。  对于名称值, 请使用内联语法`{ name1: value1, name2: value2, ... }`
* *Formula* –必需。  要为*记录*计算的公式。  公式可以直接将*记录*的任何字段作为记录范围引用。

## <a name="examples"></a>示例

### <a name="simple-named-values"></a>简单命名值

```powerapps-dot
With( { radius: 10, 
        height: 15 },
    Pi() * (radius*radius) * height
)
// Result: 4712.38898038 (as shown in a label control)
```

此示例使用已命名值的记录来计算圆柱体的体积。  使用**With**来捕获所有输入值, 以便轻松地将它们与计算本身隔开。  

### <a name="nested-with"></a>嵌套方式

![使用 With function 的兴趣计算器](media/function-with/interest-calculator.gif)

```powerapps-dot
With( { AnnualRate: RateSlider/8/100,        // slider moves in 1/8th increments and convert to decimal
        Amount: AmountSlider*10000,          // slider moves by 10,000 increment
        Years: YearsSlider,                  // slider moves in single year increments, no adjustment required
        AnnualPayments: 12 },                // number of payments per year
      With( { r: AnnualRate/AnnualPayments,  // interest rate
              P: Amount,                     // loan amount
              n: Years*AnnualPayments },     // number of payments
            r*P / (1 - (1+r)^-n)             // standard interest calculation
      )
)  
```

此示例**使用**函数嵌套, 为[每月抵押付款](https://en.wikipedia.org/wiki/Mortgage_calculator#Monthly_payment_formula)创建两层计算。  只要没有冲突,**具有**命名值的所有外部都将在内的内部使用。

由于滑块控件只能以1为增量移动, 因此, 滑块会被分割或相乘以有效地创建自定义增量。  对于利率, **RateSlider**将其**最大**属性设置为**48**, 将1/8 百分比点增量除以8除以 8, 并除以100从百分比转换为十进制, 涵盖范围 0.125% 到 6%。  对于贷款量, **AmountSlider**的**Max**属性设置为**60** , 乘以 10000, 涵盖范围10000到600000。

当滑块移动并显示新的贷款付款时, 将自动重新计算**With** 。  不使用任何变量, 并且无需使用滑块控件的**OnChange**属性。

下面是有关创建此应用程序的详细说明:
1. 创建新的应用。
2. 添加[**滑块**控件](../controls/control-slider.md), 并将其命名为**RateSlider**。  将它的**Max**属性设置为48。
3. 将 " [**标签**" 控件](../controls/control-text-box.md)添加到滑块控件的左侧。  将其**Text**属性设置为 **"利率:"** 。
3. 将 "**标签**" 控件添加到滑块控件的右侧。  将其**Text**属性设置为公式**RateSlider/8 & "&nbsp;%"** 。
3. 添加另一个**滑块**控件, 并将其命名为**AmountSlider**。  将它的**Max**属性设置为60。
3. 将 "**标签**" 控件添加到此滑块控件的左侧。  将其**Text**属性设置为 **"贷款量:"** 。 
3. 将 "**标签**" 控件添加到此滑块控件的右侧。  将其**Text**属性设置为公式**AmountSlider/8 * 10000**。
4. 添加另一个**滑块**控件, 并将其命名为**YearsSlider**。  将它的**Max**属性设置为40。
3. 将 "**标签**" 控件添加到此滑块控件的左侧。  将其**Text**属性设置为 **"年数:"** 。 
3. 将 "**标签**" 控件添加到此滑块控件的右侧。  将其**Text**属性设置为公式**YearsSlider**。
5. 添加 "**标签**" 控件, 并将其 " **Text** " 属性设置为上面所示的公式。
3. 将 "**标签**" 控件添加到最后一个 "标签" 控件的左侧。  将其**Text**属性设置为 **"每月定期付款:"** 。  

### <a name="primary-key-returned-from-patch"></a>从修补程序返回的主键

```powerapps-dot
With( Patch( Orders, Defaults( Orders ), { OrderStatus: "New" } ),
      ForAll( NewOrderDetails, 
              Patch( OrderDetails, Defaults( OrderDetails ), 
                     { Order: OrderID,          // from With's first argument, primary key of Patch result
                       Quantity: Quantity,      // from ForAll's NewOrderDetails table
                       ProductID: ProductID }   // from ForAll's NewOrderDetails table
              )
      )
)
```

此示例将记录添加到 SQL Server 的**Order**表中。  然后, 它使用 "订单**id** " 字段中的**Patch**函数返回的订单返回的主密钥来创建**OrderDetails**表中的相关记录。  

### <a name="extracted-values-with-a-regular-expression"></a>使用正则表达式提取值

```powerapps-dot
With( 
    Match( "PT2H1M39S", "PT(?:<hours>\d+)H)?(?:(?<minutes>\d+)M)?(?:(?<seconds>\d+)S)?" ),
    Time( Value( hours ), Value( minutes ), Value( seconds ) )
)
// Result: 2:01 AM (as shown in a label control, use the Text function to see the seconds)
```

此示例从 ISO 8601 duration 值提取小时、分钟和秒, 并使用这些子匹配创建日期/时间值。 

请注意, 尽管子匹配项包含数字, 但它们仍位于文本字符串中。  在执行数学运算之前, 请使用[**Value**](function-value.md)函数转换为数字。  

