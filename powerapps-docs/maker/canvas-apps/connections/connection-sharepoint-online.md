---
title: SharePoint 连接概述 | Microsoft 文档
description: 请查看可用的函数、响应和 SharePoint 示例
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: anneta
ms.date: 07/12/2017
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0fbc97e6c2663210bea79cc7236ce784110a4950
ms.sourcegitcommit: c6ad6ba7814c5e7b12c3b7b76bf2e7718bf41b8c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2019
ms.locfileid: "58198604"
---
# <a name="connect-to-sharepoint-from-a-canvas-app"></a>画布应用从连接到 SharePoint

![SharePoint](./media/connection-sharepoint-online/sharepointicon.png)

连接到 SharePoint 站点，若要从自定义列表自动生成应用或将数据添加到现有应用程序或生成从零开始的应用程序之前创建的连接。

- 在 SharePoint Online 站点或在本地站点中显示自定义列表中的数据。
- 显示图像和播放视频或音频文件 (仅限 SharePoint Online) 库中。

## <a name="generate-an-app"></a>生成应用

如果你想要管理自定义列表中的数据，PowerApps 可以[自动为你生成三屏应用](../app-from-sharepoint.md)。 用户可以浏览的第一个屏幕上的列表、 在第二个屏幕中，显示的项的详细信息和创建或更新第三个屏幕中的项。

> [!NOTE]
> 如果 SharePoint 列表包含**选**，**查找**，或**个人或组**列中，请参阅[显示库中的数据](connection-sharepoint-online.md#show-data-in-a-gallery)本主题中更高版本。

## <a name="create-a-connection"></a>创建连接

1. [登录到 PowerApps](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，选择**数据** > **连接**左侧导航栏中，然后选择**新连接**附近左上角。

    > [!div class="mx-imgBorder"]
    > ![选择数据 > 在左侧的导航栏中，连接，然后选择左上角附近的新连接。](./media/connection-sharepoint-online/new-connection.png)

1. 在右上角附近的搜索框中，键入或粘贴**SharePoint**，然后选择**SharePoint**。

    > [!div class="mx-imgBorder"]
    > ![在右上角附近的搜索框中，键入或粘贴 SharePoint，，然后选择 SharePoint。](./media/connection-sharepoint-online/select-sharepoint.png)

1. 执行这些步骤集之一：

    - 若要连接到 SharePoint Online，请选择**直接连接 （云服务）**，选择**创建**，然后提供凭据 （如果提示）。

        > [!div class="mx-imgBorder"]
        > ![若要连接到 SharePoint Online，请选择直接连接 （云服务）](./media/connection-sharepoint-online/select-online.png)

        创建连接，并可以将数据添加到现有应用程序，也可以生成从零开始的应用程序。

    - 若要连接到本地站点，请选择**使用的本地数据网关连接**。

        > [!div class="mx-imgBorder"]
        > ![若要连接到本地站点上，选择 * * 使用本地数据网关连接)](./media/connection-sharepoint-online/select-onprem.png)

        指定 **Windows** 作为身份验证类型，然后指定凭据。 （如果凭据包括域名，则将其指定为 域\别名。）

        > [!div class="mx-imgBorder"]
        > ![指定凭据](./media/connection-sharepoint-online/specify-creds.png)

        下**选择一个网关**，选择你想要使用，然后选择的网关**创建**。

        > [!NOTE]
        > 如果你没有安装，一个在本地数据网关[安装一个](../gateway-reference.md)，然后选择图标来刷新网关列表。

        > [!div class="mx-imgBorder"]
        > ![选择网关](./media/connection-sharepoint-online/choose-gateway.png)

        创建连接，并可以将数据添加到现有应用程序，也可以生成从零开始的应用程序。

## <a name="add-data-to-an-existing-app"></a>将数据添加到现有应用程序

1. 在 PowerApps Studio 中打开应用，你想要更新，请选中**视图**选项卡，然后选择**数据源**。

    > [!div class="mx-imgBorder"]
    > ![在视图选项卡，然后选择数据源](./media/connection-sharepoint-online/view-data-sources.png)

1. 在中**数据**窗格中，选择**添加数据源** > **SharePoint**。

1. 下**连接到 SharePoint 站点**，选择中的条目**最近使用的站点**列表 （或键入或粘贴你想要使用的站点的 URL），然后选择**Connect**。

    > [!div class="mx-imgBorder"]
    > ![选择站点](./media/connection-sharepoint-online/select-sp-site.png)

1. 下**选择列表**，选中的复选框**文档**或你想要使用，然后选择的一个或多个列表**Connect**:

    > [!div class="mx-imgBorder"]
    > ![在选择列表中，选择所需的一个或多个列表或文档的复选框，然后选择连接](./media/connection-sharepoint-online/select-sp-tables.png)

    默认情况下，并非所有类型的列表都会显示。 PowerApps 支持自定义列表，而不是基于模板的列表。  如果要使用的列表名称未显示，请滚动到底部，再在“输入自定义列表名称”框中键入列表名称。

    > [!div class="mx-imgBorder"]
    > ![包含输入自定义列表名称框中键入列表的名称。](./media/connection-sharepoint-online/custom-list.png)

    数据源添加到您的应用程序。

## <a name="build-your-own-app-from-scratch"></a>生成从零开始应用

应用中的概念[从头开始创建应用](../get-started-create-from-blank.md)到 SharePoint 而不是 Excel。

## <a name="show-list-columns-in-a-gallery"></a>显示库中的列表列

如果您自定义列表包含以下任何类型的列，显示在该数据**库**控件中的使用编辑栏设置**文本**属性的一个或多个**标签**在库中的控件：

- 对于“选择”或“查找”列，请指定 **ThisItem.[ColumnName].Value** 以显示该列中的数据。

    例如，如果具有名为 **Location** 的“选择”列，请指定 **ThisItem.Location.Value**，如果有名为 **PostalCode** 的“查找”列，请指定 **ThisItem.PostalCode.Value**。

- 对于“用户或用户组”列，请指定 **ThisItem.[ColumnName].DisplayName** 以显示该用户或用户组的显示名称。

    例如，指定 **ThisItem.Manager.DisplayName** 以显示名为 **Manager** 的“用户或用户组”列中的显示名称。

    还可以显示关于用户的其他信息，如电子邮件地址或职务等。 若要显示完整的选项列表，请指定 **ThisItem.[ColumnName].** （含结尾句点）。

    > [!NOTE]
    > 有关**CreatedBy**列中，指定**ThisItem.Author.DisplayName**若要显示在列表中创建项的用户的显示名称。 对于“修改者”列，请指定 **ThisItem.Editor.DisplayName** 以显示更改列表中的项的用户的显示名称。

- 对于“托管元数据”列，请指定 **ThisItem.[ColumnName].Label** 以显示该列中的数据。

    例如，如果具有名为 **Languages** 的“托管元数据”列，请指定 **ThisItem.Languages.Label**。

## <a name="show-data-from-a-library"></a>显示库中的数据

如果您在 SharePoint 库中的多个映像，您可以添加**下拉列表**控制对您的应用程序，以便用户可以指定要显示的映像。 您还可以应用相同的原则于其他控件，如**库**控件和其他类型的数据，例如视频。

1. 如果你尚未准备好，[创建的连接](#create-a-connection)，然后[将数据添加到现有应用程序](#add-data-to-an-existing-app)。

1. 添加**下拉列表**控件，并将其命名**ImageList**。

1. 设置**项**的属性**ImageList**到**文档**。

1. 上**属性**选项卡的右侧窗格中，打开**值**列表，并选择**名称**。

    你的库中映像的文件名称中显示**ImageList**。

    > [!div class="mx-imgBorder"]
    > ![映像的列表](./media/connection-sharepoint-online/dropdown-items.png)

1. 添加**图像**控件，并设置其**映像**属性设置为此表达式：

    `ImageList.Selected.'Link to item'`

1. 按 F5，并选择在不同的值**ImageList**。

    指定图像将显示。

    > [!div class="mx-imgBorder"]
    > ![示例图像](./media/connection-sharepoint-online/golden-honey.png)

你可以[下载示例应用程序](https://pwrappssamples.blob.core.windows.net/samples/spdoclib_blogapp.msapp)更复杂的方法演示如何对从 SharePoint 库中显示的数据。

1. 下载应用后，打开[PowerApps Studio](https://us.create.powerapps.com/studio/#)，选择**打开**左侧导航栏中，然后选择**浏览**。
1. 在中**打开**对话框中，找到并打开你下载的文件，并添加 SharePoint 库作为数据源按照本主题中的前两个过程。

> [!NOTE]
> 默认情况下，此应用显示[委派警告](../delegation-overview.md)，但如果你的库包含少于 500 个项可以忽略它们。

在此单个屏幕应用，左下角的列表中显示库中的所有文件。

- 可以通过键入或粘贴一个搜索的文件或顶部附近的搜索框中的多个字符。
- 如果你的库包含文件夹，可以通过在标题栏正下方的文件夹列表中选择一个筛选器图标中筛选文件的列表。

找到所需的文件后，选择它以显示在**视频**，**映像**，或**音频**沿右侧的控件。

> [!div class="mx-imgBorder"]
> ![示例图像](./media/connection-sharepoint-online/library-app.png)

## <a name="known-issues"></a>已知问题

### <a name="lists"></a>列出了

PowerApps 可以读取列名称包含空格，但空格被替换的十六进制转义代码 **"\_x0020\_"**。 例如，如果 SharePoint 中的“Column Name”在数据布局中显示或用于公式，它将在 PowerApps 中显示为“Column_x0020_Name”。

支持不是所有类型的列，并不是所有类型的列都支持所有类型的卡。

| 列类型 | 支持 | 默认卡 |
| --- | --- | --- |
| 单行文本 |是 |视图文本 |
| 多行文本 |是 |查看文本 |
| 选择 |是 |视图查找<br>编辑查找<br>查看多选<br>编辑多选 |
| Number |是 |视图百分比<br>视图分级<br>查看文本 |
| 货币 |是 |视图百分比<br>视图分级<br>查看文本 |
| 日期和时间 |是 |查看文本 |
| 查找 |是 |视图查找<br>编辑查找<br>查看多选<br>编辑多选 |
| 布尔值（是/否） |是 |查看文本<br>视图切换 |
| 用户或用户组 |是 |视图查找<br>编辑查找<br>查看多选<br>编辑多选 |
| 超链接 |是 |视图 URL<br>查看文本 |
| 图片 |是（只读） |视图图像<br>查看文本 |
| 附件 |是（只读） |查看附件|
| 已计算 |是（只读） | |
| 任务结果 |否 | |
| 外部数据 |否 | |
| 托管元数据 |是（只读） | |
| 评分 |否 | |

### <a name="libraries"></a>库

- 无法上传文件从 PowerApps 到一个库。
- 您不能在 PDF 查看器控件中显示库中的 PDF 文件。
- 不支持 PowerApps Mobile**下载**函数。
- 如果你的用户将在 PowerApps Mobile 或 Windows 10 应用中运行该应用，使用**启动**函数显示在库中的库内容。

## <a name="next-steps"></a>后续步骤

- 了解如何[显示来自数据源的数据](../add-gallery.md)。
- 了解如何[查看详细信息和创建或更新记录](../add-form.md)。
- 请参阅其他可连接的[数据源](../connections-list.md)类型。
