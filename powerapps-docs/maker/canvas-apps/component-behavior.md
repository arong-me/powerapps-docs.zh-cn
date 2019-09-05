---
title: 用于组件的行为公式 |Microsoft Docs
description: 触发应用程序，以便在基于组件的操作发生时执行一个或多个任务。
author: yifwang
ms.service: powerapps
ms.topic: article
ms.date: 05/24/2019
ms.author: yifwang
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c8ec4edd835f12fb6fccf04ba0fb27f1e755cac0
ms.sourcegitcommit: ea3ab5926541c60a9e7c17f52f937c9812d48c71
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2019
ms.locfileid: "70310059"
---
# <a name="behavior-formulas-for-components"></a>组件的行为公式

> [!IMPORTANT]
> 此功能在默认情况下仍处于实验和禁用状态。 有关详细信息，请参阅[实验性和预览功能](working-with-experimental.md)。

指定一个或多个在事件触发组件实例中的更改时运行的[行为公式](working-with-formulas-in-depth.md)。 例如，将组件的**OnReset**属性设置为一个或多个公式，当**reset**函数在组件实例上运行时，这些公式将执行初始化、清除输入和重置值。

## <a name="onreset"></a>OnReset

选择某个组件后，在 "属性" 下拉列表中选择 " **OnReset** " （位于公式栏右侧），然后输入一个或多个公式。

> [!div class="mx-imgBorder"]
> ![OnReset 示例](./media/component-behavior/example-onreset.png)

若要测试**OnReset**，请配置控件以重置组件。 例如，将按钮的 " **OnSelect** " 属性设置为此公式：**重置**（*ComponentName*）

> [!div class="mx-imgBorder"]
> ![重置按钮](./media/component-behavior/reset-button.png)
