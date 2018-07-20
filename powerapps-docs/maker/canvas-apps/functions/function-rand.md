---
title: Rand 函数 | Microsoft 文档
description: PowerApps 中 Rand 函数的参考信息（包括语法）
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/09/2018
ms.author: gregli
ms.openlocfilehash: 4246ce5564886402c6d785a462cdc9dd93270c81
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39021311"
---
# <a name="rand-function-in-powerapps"></a>PowerApps 中的 Rand 函数
返回一个伪随机数。

## <a name="description"></a>描述
**Rand** 函数返回一个大于或等于 0 并小于 1 的伪随机数。

## <a name="volatile-functions"></a>易失函数
**Rand** 是一种易失函数。  每次计算该函数时会返回不同的值。  

在数据流公式中使用易失函数时，如果对含有该函数的公式进行重新计算，该函数会返回不同的值。  如果公式中没有任何其他更改，在应用执行期间，它会具有相同的值。

例如，如果一个标签控件设为 Label1.Text = Rand()，则应用处于活动状态时，该控件不会改变。  只有关闭和重新打开应用会得到新值。

如果包含该函数的公式的其他内容发生了任何更改，会导致该函数进行重新计算。  例如，如果将示例更改为包含一个滑块控件，即设为 Label1.Text = Slider1.Value + Rand()，则每当滑块控件的值发生更改时会生成一个新的随机数字，标签的 text 属性会进行重新计算。  请参阅下文查看此示例。

如果在[行为公式](../working-with-formulas-in-depth.md)中使用 Rand，则每当计算该公式时，也会计算该函数。  请参阅下文查看示例。

## <a name="syntax"></a>语法
**Rand**()

## <a name="examples"></a>示例

#### <a name="display-a-different-random-number-as-user-input-changes"></a>将不同的随机数字显示为用户输入更改
1. 添加一个[滑块](../controls/control-slider.md)控件，然后将其重命名为 Slider1（如果它具有不同名称）。

1. 添加一个[标签](../controls/control-text-box.md)控件，然后将“Text”属性设置为以下公式：

    **Slider1.Value + Rand()**

    标签显示 50（滑块的默认值）外加一个随机的十进制小数：

    ![屏幕显示一个标签控件，标签显示 50.741](media/function-rand/rand-slider-1.png)

1. 按住 Alt 键可更改滑块的值。

    每次更改滑块的值时，标签的小数部分会显示一个不同的随机数字：

    ![四个屏幕分别显示对应标签控件四个不同滑块设置的四个不同随机十进制值 70.899、84.667、90.134、99.690](media/function-rand/rand-slider-results.png)

#### <a name="create-a-table-of-random-numbers"></a>创建一个随机数字表
1. 添加“**[按钮](../controls/control-button.md)**”控件，并将其 **[OnSelect](../controls/properties-core.md)** 属性设置为以下公式：

    **ClearCollect( RandomNumbers, ForAll( [ 1, 2, 3, 4, 5 ], Rand() ))**

    此公式创建一个单列的表，用于循环五次，从而得到五个随机数字。

1. 添加一个[数据表](../controls/control-data-table.md)，将其“Items”属性设置为“RandomNumbers”，并显示“Value”字段。

    ![屏幕显示一个数据表，该表含有五个不同的十进制值 0.857、0.105、0.979、0.167、0.814](media/function-rand/set-show-data.png)

1. 按住 Alt 键，通过单击或点击按钮来选择按钮。

    数据表显示五个随机十进制数字：

    ![屏幕显示一个数据表，该表含有五个不同的十进制值 0.857、0.105、0.979、0.167、0.814](media/function-rand/rand-collection-1.png)

1. 再次选择该按钮以显示不同的随机数字列表：

    ![同一屏幕显示一个数据表，该表含有五个不同的新的十进制值 0.414、0.128、0.860、0.303、0.568](media/function-rand/rand-collection-2.png)

若要生成单个随机数字而不是一个表，可使用 Set( RandomNumber, Rand() )。
