---
title: 在 Power BI 报表中嵌入新的画布应用 | Microsoft Docs
description: 嵌入一个使用相同数据源并且可以像其他报表项一样进行筛选的新画布应用
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/15/2018
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d82db4deaa123e460bce043bff10cc30ea409f15
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61560122"
---
# <a name="embed-a-new-canvas-app-in-a-power-bi-report"></a>在 Power BI 报表中嵌入新的画布应用

使用 Power BI 时可扩展其功能，方法是向报表添加“自定义视觉对象”。 本教程使用 PowerApps 自定义视觉对象，创建可嵌入到示例报表中的画布应用。 此应用可与报表中的其他项进行交互。

如果没有 PowerApps 订阅，请在开始之前先创建一个[免费帐户](../signup-for-powerapps.md)。

在本教程中，了解如何：
> [!div class="checklist"]
> * 将 PowerApps 自定义视觉对象导入 Power BI 报表
> * 创建可使用报表数据的新应用
> * 在报表中查看应用

## <a name="prerequisites"></a>先决条件

* [Google Chrome](https://www.google.com/chrome/browser/) 或 [Microsoft Edge](https://www.microsoft.com/windows/microsoft-edge) 浏览器
* 安装了[机会分析示例](https://docs.microsoft.com/power-bi/sample-opportunity-analysis#get-the-content-pack-for-this-sample)的 [Power BI 订阅](https://docs.microsoft.com/power-bi/service-self-service-signup-for-power-bi)
* 了解如何[在 PowerApps 中创建应用](data-platform-create-app-scratch.md)以及如何[编辑 Power BI 报表](https://docs.microsoft.com/power-bi/service-the-report-editor-take-a-tour)

## <a name="import-the-powerapps-custom-visual"></a>导入 PowerApps 自定义视觉对象

第一步是导入 PowerApps 自定义视觉对象，以便在示例报表中使用。

1. 在机会分析示例报表中，单击或点击“临近的机会”选项卡。

2. 在报表顶部，单击或点击“编辑报表”。

3. 在“可视化效果”窗格中，单击或点击省略号 (...) &gt;“从市场导入”。 

    ![从市场导入](media/embed-powerapps-powerbi/import-visual.png)

4. 在“Power BI 视觉对象”屏幕上，搜索“PowerApps”，然后单击或点击“添加”。 Power BI 将自定义视觉对象图标添加到“可视化效果”窗格底部。

    ![PowerApps 视觉对象图标](media/embed-powerapps-powerbi/powerapps-icon.png)

5. 保存报告。

## <a name="create-a-new-app"></a>创建新应用
现在，将自定义视觉对象添加到报表并基于报表中的数据创建新应用。 创建应用时，它会通过 PowerApps 与 Power BI 之间的实时数据连接启动 PowerApps Studio。

1. 移动某些报表磁贴并调整其大小，为应用留出空间。

    ![移动报表磁贴并调整其大小](media/embed-powerapps-powerbi/move-resize.png)

2. 单击或点击 PowerApps 自定义视觉对象图标，然后调整磁贴大小以适应所提供的空间。

3. 在“字段”窗格中，选择“名称”、“产品代码”和“销售阶段”。 

    ![选择字段](media/embed-powerapps-powerbi/select-fields.png)

4. 在自定义视觉对象磁贴中，选择想要在其中创建应用的 PowerApps 环境，然后单击或点击“新建”。

    ![创建新应用](media/embed-powerapps-powerbi/create-new-app.png)

    在 PowerApps Studio 中，会看到已创建一个基本应用，以及一个库，显示有 Power BI 中所选的一个字段。

5.  调整库大小使其仅占用屏幕的一半。 

6. 在左窗格中，单击或点击“Screen1”，然后将屏幕的“填充”属性设置为“LightBlue”（以便更好地呈现在报表中）。

    ![库的大小已调整的应用](media/embed-powerapps-powerbi/app-gallery.png)

6. 在库下添加“标签”控件，同时“文本”属性设为 `"Opportunity Count: " & CountRows(Gallery1.AllItems)`。 它现在会显示数据集中的机会的总数。

    ![机会计数](media/embed-powerapps-powerbi/opportunity-count.png)

7. 保存应用并命名为“机会”。 


## <a name="view-the-app-in-the-report"></a>在报表中查看应用
应用现已在报表中可用，并且由于共享相同的数据源，所以可与其他视觉对象交互。

在 Power BI 报表中，选择切片器中的“一月”，这会筛选整个报表（包括应用中的数据）。

![已筛选的报表](media/embed-powerapps-powerbi/filtered-report.png)

请注意，应用中的机会计数应与报表左上角的计数相匹配。 可以选择报表中的其他项和应用更新中的数据。


## <a name="clean-up-resources"></a>清理资源
如果不想再使用机会分析示例，可删除仪表板、报表和数据集。


## <a name="next-steps"></a>后续步骤
在本教程中，了解如何：
> [!div class="checklist"]
> * 将 PowerApps 自定义视觉对象导入 Power BI 报表
> * 创建可使用报表数据的新应用
> * 在报表中查看应用

前进到下一篇文章了解详细信息
> [!div class="nextstepaction"]
> [适用于 Power BI 的 PowerApps 自定义视觉对象](powerapps-custom-visual.md)

