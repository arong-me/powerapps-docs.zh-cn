---
title: 适用于 Power BI 的 PowerApps 自定义视觉对象 | Microsoft Docs
description: 有关嵌入使用相同数据源并可像 PowerBI 中其他报表项一样进行筛选的画布应用的步骤和限制
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/15/2018
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: bd4219a42b0674927370dfca1aa4ba681dd741bd
ms.sourcegitcommit: e58a6d9c23445e6d00317ec990a8aa0c2650bf7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2019
ms.locfileid: "70201083"
---
# <a name="powerapps-custom-visual-for-power-bi"></a>适用于 Power BI 的 PowerApps 自定义视觉对象

借助 Power BI 可获取数据见解，更好地制定决策，同时每个人都可以借助 PowerApps 生成并使用可连接到业务数据的应用。 使用 PowerApps 自定义视觉对象，可以将上下文感知的数据传递到画布应用，当对报表进行更改时，这些数据会相应实时更新。 现在，应用用户可直接通过 Power BI 报表和仪表板获取业务见解并相应采取行动。

## <a name="using-the-powerapps-custom-visual"></a>使用 PowerApps 自定义视觉对象

现在来了解如何在 Power BI 报表中使用 PowerApps 自定义视觉对象。

1. 从 [AppSource](https://appsource.microsoft.com/product/power-bi-visuals/WA104381378?tab=Overview) 获取自定义视觉对象或直接将其导入 Power BI 服务中。

    ![市场中的自定义视觉对象](./media/powerapps-custom-visual/powerapps-store.png) 

2. 将 PowerApps 视觉对象添加到报表，并设置与其关联的数据字段。

    ![选择报表数据](./media/powerapps-custom-visual/add-visual-set-data.png)

    你可以选择现有应用或创建一个应用，但必须将报表发布到 Power BI 服务并在 Microsoft Edge 或 Google Chrome 中打开。

3.  如果选择创建应用，可以选择要在其中创建应用的环境。

    ![新应用或现有应用](./media/powerapps-custom-visual/create-new-or-choose-app.png)

    如果选择使用现有应用，视觉对象会提示在 PowerApps 中打开该应用。 然后视觉对象会设置应用中的所需组件，以便 Power BI 可以将数据发送到 PowerApps。

    如果创建新的应用，PowerApps 会创建一个已设置好所需组件的简单应用。

    ![新建应用](./media/powerapps-custom-visual/new-app.png)

4. 现在 PowerApps Studio 中，可使用步骤 2 中设置的数据字段。 `PowerBIIntegration` 对象可充当任何其他 PowerApps 只读数据源或集合。 可以使用该对象填充任何控件，或与其他数据源联接和使用其他数据源过滤。

    ![自定义公式](./media/powerapps-custom-visual/custom-formula.png)

    此公式联接 Power BI 数据和客户数据源：`LookUp(Customer,Customer_x0020_Name=First(PowerBIIntegration.Data).Customer_Name)`

   Power BI 报表和已启动的 PowerApps Studio 实例共享实时数据连接。 当二者均处于打开状态时，可筛选或更改报表中的数据，更新后的数据可在 PowerApps Studio 中的应用中立即得到反映。

5. 生成或更改应用后，在 PowerApps 中保存并发布应用，以便在 Power BI 报表中查看应用。

6. 确定最终完成更改后，请确保与报表用户共享 PowerApps 应用，然后保存报表。

7. 现已通过以上方式创建一个报表，用户可通过报表中的数据获取见解并相应采取行动。

    ![工作报表](./media/powerapps-custom-visual/working-report.gif)

    如果需要对应用进行更改，以编辑模式打开报表，单击或点击 PowerApps 视觉对象上的“更多选项”(...)，选择“编辑”。

    ![编辑应用](./media/powerapps-custom-visual/edit-app.png)

## <a name="limitations-of-the-powerapps-custom-visual"></a>PowerApps 自定义视觉对象的限制

PowerApps 自定义视觉对象在预览版中可用，但具有以下限制：

- 仅在 Microsoft Edge 和 Google Chrome 浏览器上支持使用 PowerApps 自定义视觉对象创建、修改和查看应用。 建议首先将报表发布到 Power BI 服务。 然后使用 Microsoft Edge 或 Google Chrome 创建和更新应用。
- 如果更改与视觉对象关联的数据字段，必须通过选择省略号 (...)，然后选择“编辑”，从 Power BI 服务内部编辑应用。 否则所做的更改不会传播到 PowerApps，且应用不会正常运行。
- PowerApps 自定义视觉对象无法触发刷新 Power BI 报表和 Power BI Power BI Desktop 内的数据源。 如果将应用程序中的数据写回与报表相同的数据源, 则所做的更改将不会立即反映在 Power BI Desktop 中。 更改会在下一个计划的刷新后得到反映。
- PowerApps 自定义视觉对象无法筛选数据或将任何数据发送回报表。
- 你需要单独从报表共享 PowerApps 应用。 了解如何[在 PowerApps 中共享应用](share-app.md)。
- 这些技术不支持 PowerApps 自定义视觉对象:Power BI 报表服务器, Power BI 的移动应用, 以及 Internet Explorer。
- 如果使用 PowerBIIntegration () 函数, 则必须使用支持[directquery](https://docs.microsoft.com/en-us/power-bi/desktop-directquery-data-sources)的源, 并且必须使用 DirectQuery 方法创建数据连接。 

## <a name="next-steps"></a>后续步骤

* 演练简单的[分步教程](embed-powerapps-powerbi.md)。
* 请查看我们的[视频](https://aka.ms/powerappscustomvisualvideo)。
