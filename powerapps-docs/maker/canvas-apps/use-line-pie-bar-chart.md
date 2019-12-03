---
title: 在画布应用中创建图表 | Microsoft Docs
description: 在 Power Apps 中，在画布应用中将数据类别显示为折线图、饼图或条形图
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/23/2016
ms.author: fikaradz
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 8b5a5366f3de487b7d34d60d989274223340f4e6
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732419"
---
# <a name="show-data-in-a-line-pie-or-bar-chart-in-power-apps"></a>在 Power Apps 中的折线图、饼图或条形图中显示数据

使用折线图、饼图和条形图显示画布应用中的数据。 使用图表时，所导入数据的结构应基于以下条件：

* 各系列应在第一行。
* 标签应在最左边的列。

例如，数据看起来应与下图类似：

![][9]

可以在 Power Apps 中创建并使用这些图表。 现在就开始吧。

## <a name="prerequisites"></a>必备组件

* [注册](../signup-for-powerapps.md)Power Apps，然后使用注册所用的同一凭据[登录](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
* 通过[模板](get-started-test-drive.md)、[数据](get-started-create-from-data.md)或[从头开始](get-started-create-from-blank.md)构建应用。
* 了解如何在 Power Apps 中[配置控件](add-configure-controls.md)。
* 下载 [ChartData.zip](https://pwrappssamples.blob.core.windows.net/samples/ChartData.zip)，其中包含 XML 文件形式的示例数据。 按照本主题中的步骤将其直接导入到应用中。 也可以解压缩该 .zip 文件，在 Excel 中打开 XML 文件，然后将其保存到[云存储帐户](connections/cloud-storage-blob-connections.md)。

## <a name="import-the-sample-data"></a>导入示例数据
在以下步骤中，我们将示例数据导入到名为“ProductRevenue”的集合。

1. 在“插入”选项卡上，依次选择“控件”和“导入”：  

    ![][11]  

2. 将控件的 **[OnSelect](controls/properties-core.md)** 属性设置为下面的函数：  

   ```Collect(ProductRevenue, Import1.Data)```

3. 按 F5 打开预览模式，然后选择“导入数据”按钮。

4. 在“打开”对话框中，选择 ChartData.zip，选择“打开”，然后按 Esc。

5. 在“文件”菜单中选择“集合”。

    随即会列出包含已导入的图表数据的 ProductRevenue 集合：

    ![][1]  

   > [!NOTE]
   > 导入控件用于导入类似于 Excel 的数据并创建集合。 导入控件在创建应用和预览应用时导入数据。 目前，导入控件不在发布应用时导入数据。
   >

6. 按 Esc 返回默认工作区。

## <a name="add-a-pie-chart"></a>添加饼图
1. 在“插入”选项卡上，选择“图表”，然后选择“饼图”。

2. 将饼图移到“导入数据”按钮下面。

3. 在饼图控件中，选择饼图的中间：   

    ![][10]

4. 将饼图的 [Items](controls/properties-core.md) 属性设置为以下表达式：`ProductRevenue.Revenue2014`

    ![][2]  

    该饼图显示 2014 年以来的收入数据。

    ![][3]  

## <a name="add-a-bar-chart-to-display-your-data"></a>添加条形图以显示数据
现在，让我们在条形图中使用此 ProductRevenue 集合：

1. 在“主页”选项卡上，添加一个屏幕。

2. 在“插入”选项卡上，选择“图表”，然后选择“柱形图”。

3. 选择柱形图的中间。 将柱形图的 **[Items](controls/properties-core.md)** 属性设置为 ```ProductRevenue```：

    ![][12]  

    该柱形图显示 2012 年以来的收入数据：

    ![][4]  

4. 在柱形图中，选择中心方形：

    ![][5]

5. 在“图表”选项卡上，选择“系列数”，然后在公式栏中输入 **3**：

    ![][6]  

    该柱形图显示每个产品三年的收入数据：

    ![][7]  

[1]: ./media/use-line-pie-bar-chart/productrevenuecollection.png
[2]: ./media/use-line-pie-bar-chart/itemsexpression.png
[3]: ./media/use-line-pie-bar-chart/piechart.png
[4]: ./media/use-line-pie-bar-chart/columnchart.png
[5]: ./media/use-line-pie-bar-chart/columnchartseries.png
[6]: ./media/use-line-pie-bar-chart/columnchartseriesfunction.png
[7]: ./media/use-line-pie-bar-chart/columnchartthreeyears.png
[8]: ./media/use-line-pie-bar-chart/preview.png
[9]: ./media/use-line-pie-bar-chart/tableformat.png
[10]: ./media/use-line-pie-bar-chart/middlepiechart.png
[11]: ./media/use-line-pie-bar-chart/import.png
[12]: ./media/use-line-pie-bar-chart/itemscolumnchart.png
