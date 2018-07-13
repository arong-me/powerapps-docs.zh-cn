---
title: UpdateContext 函数 | Microsoft 文档
description: PowerApps 中 UpdateContext 函数的参考信息（包括语法和示例）
documentationcenter: na
author: gregli-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: reference
ms.component: canvas
ms.date: 11/08/2015
ms.author: gregli
ms.openlocfilehash: e7da24eec1a85a1d57ab83476734639ef0f5dd25
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2018
ms.locfileid: "37898067"
---
# <a name="updatecontext-function-in-powerapps"></a>PowerApps 中的 UpdateContext 函数
创建或更新当前屏幕的[上下文变量](../working-with-variables.md#create-a-context-variable)。

## <a name="overview"></a>概述
使用 **UpdateContext** 函数创建上下文变量，该变量暂时保留一条信息，比如用户已选择某按钮的次数或数据运算的结果。

上下文变量的作用域限于一个屏幕，这意味着不能生成引用另一屏幕上的上下文变量的公式。 如果已使用另一种编程工具，可将上下文变量视为与本地变量类似。  使用 [Set 函数](function-set.md)来处理整个应用中可用的全局变量。  

PowerApps 以公式为基础，这些公式会在用户与应用交互时自动重新计算。  上下文变量不具有此优势，因此在应用的创建和理解上可能难度更大。  使用上下文变量之前，请查看[使用变量](../working-with-variables.md)。

## <a name="description"></a>描述
若要创建或更新上下文变量，请向 **UpdateContext** 函数传递一条[记录](../working-with-tables.md#records)。 在每条记录中指定[列](../working-with-tables.md#columns)的名称，用于定义或匹配变量的名称以及要将该变量设为的值。

* 如果指定之前已定义的变量的名称，**UpdateContext** 会将该变量的值设置为指定的值。
* 如果指定尚不存在的变量的名称，**UpdateContext** 会以该名称创建一个变量并将该变量的值设置为指定的值。
* 如果之前已定义某变量，但未在这一特定 **UpdateContext** 公式中指定它，其值保持不变。

使用 UpdateContext 或 [Navigate 函数](function-navigate.md)隐式创建上下文变量。  无需显式声明。  如果删除所有 UpdateContext 和 Navigate 到上下文变量的引用，则该上下文变量将不复存在。  若要清除变量，请将其值设置为 [Blank 函数](function-isblank-isempty.md)的结果。

在创作环境中，可以使用“文件”菜单下的“变量”视图查看变量的值、定义和使用情况。

使用变量的列名称可引用公式中的上下文变量。 例如，**UpdateContext( { ShowLogo: true } )** 创建一个名为 **ShowLogo** 的上下文变量，并将其值设置为 **true**。 然后可通过在公式中使用名称 **ShowLogo** 来使用此上下文变量的值。  可将 **ShowLogo** 编写为图像控件 **Visible** 属性的公式，然后根据上下文变量的值是 **true** 还是 **false** 来显示或隐藏该控件。

如本主题后面的示例所示，上下文变量可保留多种信息，包括：

* 单个值
* 记录
* 表
* 对象引用
* 公式的任何结果

上下文变量可保留其值，直到应用关闭。  如果定义一个上下文变量并在特定屏幕上设置其值，则该信息保持不变，即使用户切换到不同的屏幕。  应用关闭后，上下文变量的值将丢失，重新加载应用时则必须重新创建该值。  

每个上下文变量的作用于限于一个屏幕。 如果想要在一个屏幕上定义上下文变量，但想要从另一个屏幕修改该变量，必须生成一个基于 **[Navigate](function-navigate.md)** 函数的公式。  或者，使用全局变量。

**UpdateContext** 没有返回值，只可以在[行为公式](../working-with-formulas-in-depth.md)中使用它。

## <a name="syntax"></a>语法
**UpdateContext**( *UpdateRecord* )

* *UpdateRecord* - 必需。 一条记录，其中包含至少一列的名称以及该列的值。 将为每列和指定的值创建或更新上下文变量。

**UpdateContext**( { *ContextVariable1*: *Value1* [, *ContextVariable2*: *Value2* [, ... ] ] } )

* *ContextVariable1* - 必需。  要创建或更新的上下文变量的名称。
* *Value1* - 必需。  要分配给上下文变量的值。
* *ContextVariable2*: *Value2*, ... - 可选。 要创建或更新的其他上下文变量及其值。

## <a name="examples"></a>示例

| 公式 | 描述 | 结果 |
| --- | --- | --- |
| **UpdateContext( {&nbsp;Counter:&nbsp;1&nbsp;} )** |创建或修改上下文变量 **Counter**，将其值设置为 **1**。 |**Counter** 的值为 **1**。 可通过在公式中使用名称 **Counter** 来引用该变量。 |
| **UpdateContext( {&nbsp;Counter:&nbsp;2&nbsp;} )** |将上一示例中 **Counter** 上下文变量的值设置为 **2**。 |**Counter** 的值为 **2**。 |
| **UpdateContext( {&nbsp;Name:&nbsp;"Lily",&nbsp;Score:&nbsp;10&nbsp;} )** |创建或修改上下文变量 **Name** 和 **Score**，分别将它们的值设置为 **Lily** 和 **10**。 |**Name** 的值为 **Lily**，**Score** 的值为 **10**。 |
| **UpdateContext( {&nbsp;Person:&nbsp;{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}&nbsp;} )** |创建或修改上下文变量 **Person**，将其值设置为一条记录。 该记录包含名为“姓名”和“地址”的两列。 “姓名”列为 **Milton**，“地址”列的值为 **1 Main St**。 |**Person** 的值为记录 **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"1&nbsp;Main&nbsp;St"&nbsp;}&nbsp;}**。<br><br>使用名称 **Person** 整体引用此记录，或使用 **Person.Name** 或 **Person.Address** 引用此记录的单个列。 |
| **UpdateContext( {&nbsp;Person: Patch(&nbsp;Person,&nbsp;{Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}&nbsp;) }&nbsp;)** |搭配使用 **[Patch](function-patch.md)** 函数更新 **Person** 上下文变量，将“地址”列的值设置为 **2 Main St**。 |**Person** 现在的值为记录 **{&nbsp;Name:&nbsp;"Milton", Address:&nbsp;"2&nbsp;Main&nbsp;St"&nbsp;}&nbsp;}**。 |

### <a name="step-by-step-example"></a>分步示例
1. 将默认屏幕命名为 **Source**，添加另一个屏幕，将其命名为 **Target**。
2. 在 **Source** 屏幕上，添加两个按钮，设置它们的 **[Text](../controls/properties-core.md)** 属性，让其中一个按钮显示“英语”，另一个显示“西班牙语”。
3. 将“英语”按钮的 **[OnSelect](../controls/properties-core.md)** 属性设置为此表达式：<br>**Navigate(Target, ScreenTransition.Fade, {Language:"English"})**
4. 将“西班牙语”按钮的 **[OnSelect](../controls/properties-core.md)** 属性设置为此表达式：<br>**Navigate(Target, ScreenTransition.Fade, {Language:"Spanish"})**
5. 在 **Target** 屏幕，添加一个标签，将其 **[Text](../controls/properties-core.md)** 属性设置为此表达式：<br>**If(Language="English", "Hello!", "Hola!")**
6. 在 **Target** 屏幕上，在“插入”选项卡上选择“形状”，然后选择“返回”箭头。
7. 将“返回”箭头的 **[OnSelect](../controls/properties-core.md)** 属性设置为此公式：<br>**Navigate(Source, ScreenTransition.Fade)**
8. 从 **Source** 屏幕上，按 F5，然后选择表示任一语言的按钮。

    在 **Target** 屏幕上，标签将以对应于所选按钮的语言显示。
9. 选择“返回”箭头返回到 **Source** 屏幕，然后选择表示其他语言的按钮。

    在 **Target** 屏幕上，标签将以对应于所选按钮的语言显示。
10. 按 Esc 返回默认工作区。

[其他示例](../add-screen-context-variables.md)

