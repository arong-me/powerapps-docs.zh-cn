---
title: 用于组件的行为公式 |Microsoft Docs
description: 当发生基于组件的操作时，在画布应用中执行一项或多项任务。
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 02/20/2020
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 28ea432e5d09684029f104d69f593e24dcc4cc14
ms.sourcegitcommit: 59f0b3adc56279b5673cbf04b4a55bd7678e1ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2020
ms.locfileid: "77910976"
---
# <a name="behavior-formulas-for-components"></a>组件的行为公式

> [!IMPORTANT]
> 此功能仍处于公共预览版中。 有关详细信息，请参阅[实验性功能和预览功能](working-with-experimental.md)。

指定一个或多个在事件触发组件实例中的更改时运行的[行为公式](working-with-formulas-in-depth.md)。 

例如，将组件的**OnReset**属性设置为一个或多个执行初始化的公式，清除 input。 当**reset**函数在组件实例上运行时，和将重置值。

## <a name="onreset"></a>OnReset

选择了组件主机后，在 "属性" 下拉列表中选择 " **OnReset** "，然后输入一个或多个公式。

> [!div class="mx-imgBorder"]
> ![OnReset 示例](./media/component-behavior/example-onreset.png)

若要测试**OnReset**，请配置控件以重置组件。 例如，将按钮的**OnSelect**属性设置为以下公式： **Reset**（*ComponentName*）。

### <a name="example---reset-timer"></a>示例-重置计时器

> [!div class="mx-imgBorder"]
> ![OnReset 示例](./media/component-behavior/Resettimer.gif)

在此时间选择器组件中，两个变量用于显示时间 _selectedHour 和 _selectedMinute。 当选取器重置时，这些变量应重置为默认值，例如 12:12。  组件的 OnReset 属性具有以下公式： **Set （_selectedHour，12）;Set （_selectedMinute，12）**

若要触发重置，请跳到屏幕并插入组件的实例。 添加一个按钮，并将该按钮的 OnSelect 配置为调用**Reset （TimerComponent_instance）** 以触发 OnReset。

> [!div class="mx-imgBorder"]
> ![重置 "按钮](./media/component-behavior/reset-button.png)

## <a name="update-onreset-using-custom-property"></a>使用自定义属性更新 OnReset

除了在组件外部重置组件实例以外，还有另一种方法可以触发 OnReset。 创建自定义输入属性时，"**当值更改时引发 OnReset**" 是一个选项。 它允许此属性的值更改触发组件的 OnReset。 此方法设计为易于设置和重置默认值。 

> ![OnReset 示例](./media/component-behavior/property-trigger.png)

### <a name="example"></a>示例

> [!div class="mx-imgBorder"]
> ![OnReset 示例](./media/component-behavior/updateordernumber2.gif)

上面的示例演示了查看订单号和更新数字的情况。 使用数值上移和下移组件可以增加或减少订单数。 选择左侧的库时，将重置 "数字上移" 和 "下移" 组件的默认数量，以显示所选工具的订单号。 "**当值更改时引发 OnReset**" 可在输入更改时重置默认值。 

为此，请选中默认输入属性的 "**当值发生更改时引发 OnReset**"。 将该组件的**OnReset**设置为**set （_numericValue，"向上数字上移"。DefaultValue）** 。 _numericValue 是存储当前订单值值的变量。 并将 "文本输入" 控件的**默认值**设置为**If （IsBlank （_NumericValue） "数字向上减小"。DefaultValue、_numericValue）** 。 

### <a name="see-also"></a>另请参阅

- [画布应用组件概述](create-component.md)
- [画布应用组件库](component-library.md)
