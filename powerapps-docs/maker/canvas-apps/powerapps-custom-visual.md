---
title: 适用于 Power BI 的 Power Apps 自定义视觉对象 |Microsoft Docs
description: 有关嵌入使用相同数据源并可像 PowerBI 中其他报表项一样进行筛选的画布应用的步骤和限制
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/02/2019
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: c5814eedfd05ea5bba19a469dad1b3e28c311974
ms.sourcegitcommit: 6f94650ea540db69d2723c3c5dff9de8c59056cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/10/2020
ms.locfileid: "75859117"
---
# <a name="power-apps-custom-visual-for-power-bi"></a>适用于 Power BI 的 Power Apps 自定义视觉对象

Power BI 可实现数据见解和更好的决策，而使用 Power Apps，每个人都可以构建和使用连接到业务数据的应用。 使用 Power Apps 自定义视觉对象，可以将上下文感知数据传递给画布应用，这会在对报表进行更改时进行实时更新。 现在，应用用户可直接通过 Power BI 报表和仪表板获取业务见解并相应采取行动。

## <a name="using-the-power-apps-custom-visual"></a>使用 Power Apps 自定义视觉对象

让我们看一下在 Power BI 报表中使用 Power Apps 自定义视觉对象所需的步骤。

1. 默认情况下，在 Power BI 服务中提供 Power Apps 自定义视觉对象。 如果你正在使用 Power BI Desktop 但看不到此版本，则必须升级到 Power BI Desktop 的最新版本。

2. 将 "Power Apps" 视觉对象添加到报表，并设置与其关联的数据字段。

    ![选择报表数据](./media/powerapps-custom-visual/add-visual-set-data.png)

    你可以选择现有应用或创建一个应用，但必须将报表发布到 Power BI 服务并在 Microsoft Edge 或 Google Chrome 中打开。

3.  如果选择创建应用，可以选择要在其中创建应用的环境。

    ![新应用或现有应用](./media/powerapps-custom-visual/create-new-or-choose-app.png)

    如果选择使用现有的应用，视觉对象会提示你在 Power Apps 中打开应用。 然后，视觉对象在应用中设置所需的组件，以便 Power BI 可以将数据发送到 Power Apps。

    如果你创建一个新应用程序，电源应用程序将创建一个简单的应用程序，其中已设置了所需的组件。

    > [!NOTE]
    > 你必须在 Power BI 报表中从 Power Apps 自定义视觉对象创建新应用，以使 `PowerBIIntegration.Refresh()` 函数在应用中可用。

    ![新建应用](./media/powerapps-custom-visual/new-app.png)

4. 现在，在 Power Apps Studio 中，可以使用在步骤2中设置的数据字段。 `PowerBIIntegration` 对象的行为类似于任何其他 Power Apps 只读数据源或集合。 可以使用该对象填充任何控件，或与其他数据源联接和使用其他数据源过滤。

    ![自定义公式](./media/powerapps-custom-visual/custom-formula.png)

    此公式联接 Power BI 数据和客户数据源：`LookUp(Customer,Customer_x0020_Name=First(PowerBIIntegration.Data).Customer_Name)`

   已启动的 Power BI 报表和 Power Apps Studio 实例共享实时数据连接。 当它们都处于打开状态时，可以筛选或更改报表中的数据，以在 Power Apps Studio 中立即看到更新后的数据反映在应用中。

5. 完成对应用程序的生成或更改后，请在 Power Apps 中保存并发布应用程序，以查看 Power BI 报表中的应用程序。

6. 对更改感到满意后，请确保与报表用户共享 Power Apps 应用，然后保存报表。

7. 现已通过以上方式创建一个报表，用户可通过报表中的数据获取见解并相应采取行动。

    ![工作报表](./media/powerapps-custom-visual/working-report.gif)

    如果需要对应用进行更改，请在编辑模式下打开报表，再单击或点击 Power Apps 视觉对象上的 "**更多选项**" （ **...** ），然后选择 "**编辑**"。

    ![编辑应用](./media/powerapps-custom-visual/edit-app.png)

## <a name="limitations-of-the-power-apps-custom-visual"></a>Power Apps 自定义视觉对象的限制

适用于 Power Apps 自定义视觉对象的以下限制：

- 如果更改与视觉对象关联的数据字段，必须通过选择省略号 (...)，然后选择“编辑”，从 Power BI 服务内部编辑应用。 否则，所做的更改不会传播到 Power Apps，应用将以意外的方式运行。
- Power Apps 自定义视觉对象无法触发刷新 Power BI 报表和 Power BI Power BI Desktop 内的数据源。 如果将应用程序中的数据写回与报表相同的数据源，则所做的更改将不会立即反映在 Power BI Desktop 中。 更改会在下一个计划的刷新后得到反映。
- Power Apps 自定义视觉对象无法筛选数据或将任何数据发送回报表。
- 需要与报表分开共享 "Power Apps" 应用。 了解如何[在 Power apps 中共享应用](share-app.md)。
- Power BI 报表服务器不支持 Power Apps 自定义视觉对象。
- 使用 `PowerBIIntegration.Refresh()` 函数时，以下限制适用：
    - 若要在应用中使用此功能，必须在 Power BI 报表中从 Power Apps 自定义视觉对象创建新应用。
    - 必须使用支持[directquery](https://docs.microsoft.com/power-bi/desktop-directquery-data-sources)的源，并且必须使用 DirectQuery 方法创建数据连接。
- Power BI Desktop 中的 power Apps 为在创建应用时，而不是在编辑时为 Power Apps Studio 提供数据。 使用 Power BI Web 在编辑应用时预览数据。

> [!NOTE]
> 建议先将报表发布到 Power BI 服务，然后创建或修改应用。

## <a name="browser-support"></a>浏览器支持

下表列出了可用于查看、创建和修改 Power Apps 自定义视觉对象操作的浏览器可支持性。 支持的浏览器和操作由复选标记（&check;）标识。

|浏览器|视图|创建|修改
|-|-|-|-
|Microsoft Edge|&check;|&check;|&check;
|Internet Explorer 11|&check;
|Google Chrome|&check;|&check;|&check;
|Safari \*|&check;
|Mozilla Firefox
|所有其他浏览器

在 Safari 中 \*，你必须启用跨站点跟踪（**首选项** > **隐私**，并清除**阻止跨站点跟踪**）以查看 Power Apps 自定义视觉对象。

## <a name="accessibility-support"></a>辅助功能支持

若要使用键盘导航 Power Apps 视觉对象，请执行以下步骤：

1. 在所需的电源应用视觉对象的 Power BI 报表上选择焦点。
2. 使用键盘上的**Tab**键，直到突出显示视觉对象。
3. 使用键盘上的**Ctrl + 右键**进入视觉对象。
3. 使用键盘上的**Tab**键，直到选择了视觉对象的所需组件。

有关详细信息，请参阅： [Power BI 辅助功能文档]( https://docs.microsoft.com/power-bi/desktop-accessibility)


## <a name="next-steps"></a>后续步骤

* 演练简单的[分步教程](embed-powerapps-powerbi.md)。
* 请查看我们的[视频](https://aka.ms/powerappscustomvisualvideo)。
