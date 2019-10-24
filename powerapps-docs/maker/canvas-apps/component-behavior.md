---
title: 用于组件的行为公式 |Microsoft Docs
description: 触发应用程序，以便在基于组件的操作发生时执行一个或多个任务。
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 9/30/2019
ms.author: yifwang
ms.reviewer: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: baf7e74581819b3ea21542f30f96a0a6f517c0d5
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2019
ms.locfileid: "71705046"
---
# <a name="behavior-formulas-for-components"></a>组件的行为公式

> [!IMPORTANT]
> 此功能在默认情况下仍处于实验和禁用状态。 有关详细信息，请参阅[实验性和预览功能](working-with-experimental.md)。

指定一个或多个在事件触发组件实例中的更改时运行的[行为公式](working-with-formulas-in-depth.md)。 例如，将组件的**OnReset**属性设置为一个或多个公式，当**reset**函数在组件实例上运行时，这些公式将执行初始化、清除输入和重置值。

## <a name="onreset"></a>OnReset

选择了组件主机后，在 "属性" 下拉列表中选择 " **OnReset** "，然后输入一个或多个公式。

> [!div class="mx-imgBorder"]
> ![OnReset 示例 ](./media/component-behavior/example-onreset.png)

若要测试**OnReset**，请配置控件以重置组件。 例如，将按钮的**OnSelect**属性设置为以下公式： **Reset**（*ComponentName*）。

### <a name="example---reset-timer"></a>示例-重置计时器

> [!div class="mx-imgBorder"]
> ![OnReset 示例 ](./media/component-behavior/Resettimer.gif)

在此时间选择器组件中，两个变量用于显示时间 _selectedHour 和 _selectedMinute。 当选取器重置时，这些变量应重置为默认值，例如 12:12。  组件的 OnReset 属性具有以下公式： **Set （_selectedHour，12）;Set （_selectedMinute，12）**

若要触发重置，请跳到屏幕并插入组件的实例。 添加一个按钮，并将该按钮的 OnSelect 配置为调用**Reset （TimerComponent_instance）** 来触发 OnReset。

> [!div class="mx-imgBorder"]
> ![Reset 按钮 ](./media/component-behavior/reset-button.png)

## <a name="update-onreset-using-custom-property"></a>使用自定义属性更新 OnReset

除了从组件外部重置组件实例以外，还可以通过另一种方法来触发 OnReset。 "**当值更改时引发 OnReset**" 是创建自定义输入属性时的选项，它允许此属性的值更改触发组件的 OnReset。 此方法设计为易于设置和重置默认值。 

> ![OnReset 示例](./media/component-behavior/property-trigger.png)

### <a name="example"></a>示例

> [!div class="mx-imgBorder"]
> ![OnReset 示例 ](./media/component-behavior/updateordernumber2.gif)

这是查看订单号和更新数字的示例。 使用数值上移和下移组件可以增加或减少订单数。 选择左侧的库时，将重置 "数字上移" 和 "下移" 组件的默认数量，以显示所选工具的订单号。 "**当值更改时引发 OnReset**" 可在输入更改时重置默认值。 

为此，请选中默认输入属性的 "**当值发生更改时引发 OnReset**"。 将该组件的**OnReset**设置为**set （_numericValue，"向上数值增大"。DefaultValue）** 。 _numericValue 是用于存储当前订单值的值的变量。 并将 "文本输入" 控件的**默认值**设置为**If （IsBlank （_numericValue），"向上数字上移"。DefaultValue、_numericValue）** 。 
