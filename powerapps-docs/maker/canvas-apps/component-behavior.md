---
title: 组件的行为公式 |Microsoft Docs
description: 触发应用程序的基于组件的操作发生时执行一个或多个任务。
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 05/24/2019
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7275395a4c21afaebc60e9635461afc08f5e84a0
ms.sourcegitcommit: afe958805d8e1cfa4fdf02c7bceea947185f71f2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/30/2019
ms.locfileid: "66420305"
---
# <a name="behavior-formulas-for-components"></a>组件的行为公式

> [!IMPORTANT]
> 此功能是仍实验，且默认情况下禁用。 有关详细信息，请参阅[实验性和预览功能](working-with-experimental.md)。

指定一个或多个[行为公式](working-with-formulas-in-depth.md)运行时事件触发中组件实例的更改。 例如，设置组件的**OnReset**到一个或多个公式执行初始化、 清除输入，并将重置的属性值时**重置**函数在组件实例上运行。

## <a name="onreset"></a>OnReset ##

所选组件，选择**OnReset**属性 （在编辑栏右端） 上的下拉列表中，然后输入一个或多个公式。

> [!div class="mx-imgBorder"]
> ![OnReset 示例](./media/component-behavior/example-onreset.png)

若要测试**OnReset**，配置控件以重置该组件。 例如，设置**OnSelect**为以下公式的按钮的属性：**Reset**(*ComponentName*)

> [!div class="mx-imgBorder"]
> ![重置按钮](./media/component-behavior/reset-button.png)
