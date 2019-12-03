---
title: SharePoint 连接概述 | Microsoft 文档
description: 请参阅适用于 SharePoint 的函数、响应和示例。
author: NickWaggoner
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/03/2019
ms.author: niwaggon
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0c0f4744e7b323e3262a63278e7c12348142a99b
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74727725"
---
# <a name="connect-to-sharepoint-from-a-canvas-app"></a>从画布应用连接到 SharePoint

![SharePoint](./media/connection-sharepoint-online/sharepointicon.png)

在将数据添加到现有应用或从头开始生成应用之前，请连接到 SharePoint 站点以自动从自定义列表生成应用或创建连接。

根据数据所在的位置，可以采用以下两种方法之一或这两种方法：

- 在 SharePoint Online 站点或本地站点的自定义列表中显示数据。
- 在库中显示图像并播放视频或音频文件（仅限 SharePoint Online）。

## <a name="generate-an-app"></a>生成应用

如果要在自定义列表中管理数据，则 Power Apps 会[自动为你生成三屏应用](../app-from-sharepoint.md)。 用户可以在第一个屏幕上浏览列表，在第二个屏幕中显示项的详细信息，并在第三个屏幕中创建或更新项。

> [!NOTE]
> 如果 SharePoint 列表包含 "**选择**"、"**查找**" 或 "用户"**或 "组**" 列，请参阅本主题后面的在[库中显示数据](connection-sharepoint-online.md#show-list-columns-in-a-gallery)。

## <a name="create-a-connection"></a>创建连接

1. [登录到 Power Apps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，在左侧导航栏中选择 "**数据** > **连接**"，然后选择左上角附近的 "**新建连接**"。

    > [!div class="mx-imgBorder"]
    > ![在左侧导航栏中选择 "数据 > 连接"，然后选择左上角附近的 "新建连接"。](./media/connection-sharepoint-online/new-connection.png)

1. 在右上角附近的 "搜索" 框中，键入或粘贴 " **sharepoint**"，然后选择 " **sharepoint**"。

    > [!div class="mx-imgBorder"]
    > ![在右上角附近的 "搜索" 框中，键入或粘贴 "SharePoint"，然后选择 "SharePoint"。](./media/connection-sharepoint-online/select-sharepoint.png)

1. 执行下列一组步骤：

    - 若要连接到 SharePoint Online，请选择 "**直接连接（云服务）** "，选择 "**创建**"，然后提供凭据（如果提示）。

        > [!div class="mx-imgBorder"]
        > ![若要连接到 SharePoint Online，请选择 "直接连接（云服务）"](./media/connection-sharepoint-online/select-online.png)

        创建连接后，可以将数据添加到现有应用或从头开始构建应用。

    - 若要连接到本地站点，请选择 "**使用本地数据网关连接**"。

        > [!div class="mx-imgBorder"]
        > ![连接到本地站点，请选择 "使用本地数据网关连接"，然后选择 "使用本地数据网关连接"](./media/connection-sharepoint-online/select-onprem.png)

        指定 **Windows** 作为身份验证类型，然后指定凭据。 （如果凭据包括域名，则将其指定为 域\别名。）

        > [!div class="mx-imgBorder"]
        > ![指定凭据](./media/connection-sharepoint-online/specify-creds.png)

        在 "**选择网关**" 下，选择要使用的网关，然后选择 "**创建**"。

        > [!NOTE]
        > 如果未安装本地数据网关，请[安装一个](../gateway-reference.md)网关，然后选择该图标来刷新网关列表。

        > [!div class="mx-imgBorder"]
        > ![选择网关](./media/connection-sharepoint-online/choose-gateway.png)

        创建连接后，可以将数据添加到现有应用或从头开始构建应用。

## <a name="add-data-to-an-existing-app"></a>将数据添加到现有应用

1. 在 Power Apps Studio 中，打开要更新的应用程序，选择 "**视图**" 选项卡，然后选择 "**数据源**"。

    > [!div class="mx-imgBorder"]
    > !["查看" 选项卡，然后选择 "数据源"](./media/connection-sharepoint-online/view-data-sources.png)

1. 在 "**数据**" 窗格中，选择 " > **SharePoint** **添加数据源**"。

1. 在 "**连接到 SharePoint 站点**" 下，选择 "最近使用的**站点**" 列表中的条目（或键入或粘贴要使用的站点的 URL），然后选择 "**连接**"。

    > [!div class="mx-imgBorder"]
    > ![选择站点](./media/connection-sharepoint-online/select-sp-site.png)

1. 在 "**选择列表**" 下，选中要使用的**文档**或一个或多个列表的复选框，然后选择 "**连接**"：

    > [!div class="mx-imgBorder"]
    > ![在 "选择列表" 下，选中要使用的文档或一个或多个列表的复选框，然后选择 "连接"](./media/connection-sharepoint-online/select-sp-tables.png)

    默认情况下，并非所有类型的列表都会显示。 Power Apps 支持自定义列表，而不支持基于模板的列表。 如果要使用的列表名称未显示，请滚动到底部，然后在 "**输入自定义表名称**" 框中键入列表的名称。

    > [!div class="mx-imgBorder"]
    > ![在包含 "输入自定义列表名称" 的框中键入列表名称。](./media/connection-sharepoint-online/custom-list.png)

    数据源已添加到应用中。

## <a name="build-your-own-app-from-scratch"></a>从头开始构建你自己的应用

应用[从头开始创建应用](../get-started-create-from-blank.md)的概念，而不是 Excel。

## <a name="show-list-columns-in-a-gallery"></a>显示库中的列表列

如果您的自定义列表包含这些类型的列中的任何一种，则使用编辑栏在**库**控件中显示该数据，以设置该库中一个或多个**标签**控件的**Text**属性：

- 对于 "**选择**" 或 "**查找**" 列，请指定**ThisItem。** _ColumnName_ **。值**以显示该列中的数据。

    例如，如果具有名为 **Location** 的“选择”列，请指定 **ThisItem.Location.Value**，如果有名为 **PostalCode** 的“查找”列，请指定 **ThisItem.PostalCode.Value**。

- 对于 "**人员" 或 "组**" 列，请指定**ThisItem。** _ColumnName_ **。DisplayName**显示用户或组的显示名称。

    例如，指定 **ThisItem.Manager.DisplayName** 以显示名为 **Manager** 的“用户或用户组”列中的显示名称。

    还可以显示关于用户的其他信息，如电子邮件地址或职务等。 若要显示选项的完整列表，请指定**ThisItem。** _ColumnName_ **。** （包括尾随句点）。

    > [!NOTE]
    > 对于**system.createdby**列，请指定**ThisItem**以显示创建列表中的项的用户的显示名称。 对于“修改者”列，请指定 **ThisItem.Editor.DisplayName** 以显示更改列表中的项的用户的显示名称。

- 对于 "**托管元数据**" 列，请指定**ThisItem。** _ColumnName_ **。** 用于显示该列中的数据的标签。

    例如，如果具有名为 **Languages** 的“托管元数据”列，请指定 **ThisItem.Languages.Label**。

## <a name="show-data-from-a-library"></a>显示库中的数据

如果在 SharePoint 库中有多个图像，则可以向应用程序中添加一个**下拉**控件，以便用户可以指定要显示的图像。 您还可以将相同的原则应用于其他控件，如**库**控件和其他类型的数据（如视频）。

1. 如果尚未这样做，请[创建一个连接](#create-a-connection)，然后[将数据添加到现有应用](#add-data-to-an-existing-app)。

1. 添加**下拉**控件，并将其命名为**ImageList**。

1. 将**ImageList**的 " **Items** " 属性设置为 "**文档**"。

1. 在右侧窗格的 "**属性**" 选项卡上，打开 "**值**" 列表，然后选择 "**名称**"。

    库中的图像的文件名显示为**ImageList**。

    > [!div class="mx-imgBorder"]
    > 图像 ![列表](./media/connection-sharepoint-online/dropdown-items.png)

1. 添加**图像**控件，并将其 " **image** " 属性设置为以下表达式：

    `ImageList.Selected.'Link to item'`

1. 按 F5，然后选择**ImageList**中的其他值。

    此时将显示您指定的图像。

    > [!div class="mx-imgBorder"]
    > ![示例图像](./media/connection-sharepoint-online/golden-honey.png)

您可以[下载示例应用程序，该应用程序](https://pwrappssamples.blob.core.windows.net/samples/spdoclib_blogapp.msapp)演示了更复杂的方法来显示 SharePoint 库中的数据。

1. 下载应用后，打开[Power Apps Studio](https://us.create.powerapps.com/studio/#)，在左侧导航栏中选择 "**打开**"，然后选择 "**浏览**"。
1. 在 "**打开**" 对话框中，找到并打开已下载的文件，然后按照本主题中的前两个步骤，将 SharePoint 库添加为数据源。

> [!NOTE]
> 默认情况下，此应用显示[委派警告](../delegation-overview.md)，但如果库包含的项目少于500，你可以忽略这些警告。

在此屏幕应用程序中，左下角的列表显示库中的所有文件。

- 可以通过在顶部附近的 "搜索" 框中键入或粘贴一个或多个字符来搜索文件。
- 如果你的库包含文件夹，则可以通过在标题栏下的文件夹列表中选择筛选器图标来筛选文件列表。

找到所需的文件后，选择该文件以将其显示在右侧的 "**视频**"、"**图像**" 或 "**音频**" 控件中。

> [!div class="mx-imgBorder"]
> ![示例图像](./media/connection-sharepoint-online/library-app.png)

## <a name="known-issues"></a>已知问题

### <a name="lists"></a>表

Power Apps 可以读取包含空格的列名，但空格将替换为十六进制转义代码 **"\_x0020\_"** 。 例如，当在数据布局中显示或用于公式时，SharePoint 中的 **"Column Name"** 将显示为 Power Apps 中的 **"Column_x0020_Name"** 。

并非所有类型的列都受支持，并且并非所有类型的列都支持所有类型的卡。

| 列类型 | 支持 | 默认卡 |
| --- | --- | --- |
| 单行文本 |是 |查看文本 |
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

- 无法将文件从 Power Apps 上传到库。
- 无法在 PDF 查看器控件中从库中显示 PDF 文件。
- Power Apps Mobile 不支持**下载**功能。
- 如果用户将在 Power Apps Mobile 或 Windows 10 应用中运行应用，请使用**启动**功能在库中显示库内容。

## <a name="next-steps"></a>后续步骤

- 了解如何[显示来自数据源的数据](../add-gallery.md)。
- 了解如何[查看详细信息和创建或更新记录](../add-form.md)。
- 请参阅其他可连接的[数据源](../connections-list.md)类型。
