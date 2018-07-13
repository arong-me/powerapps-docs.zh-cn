---
title: 云存储连接概述 | Microsoft 文档
description: 了解如何连接云存储帐户，并在应用中显示 Excel 数据
author: lancedMicrosoft
ms.service: powerapps
ms.topic: reference
ms.component: canvas
ms.date: 07/12/2016
ms.author: lanced
ms.openlocfilehash: 04bfdd2d59b870184e5e42ac06135d00f52dcc70
ms.sourcegitcommit: 79b8842fb0f766a0476dae9a537a342c8d81d3b3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/07/2018
ms.locfileid: "37895675"
---
# <a name="connect-to-cloud-storage-from-powerapps"></a>从 PowerApps 连接到云存储
PowerApps 提供多个云存储连接。 使用其中任何一种连接，都可以存储 Excel 文件，并将其中的信息用于整个应用。 这些连接包括：  

| **Azure Blob** | **Box** | **Dropbox** | **Google 云端硬盘** | **OneDrive** | **OneDrive<br>for Business** |
| --- | --- | --- | --- | --- | --- |
| ![图标](./media/cloud-storage-blob-connections/blobicon.png) |![API 图标][boxicon] |![API 图标][dropboxicon] |![API 图标][googledriveicon] |![API 图标][onedriveicon] |![API 图标][onedriveforbusinessicon] |

[!INCLUDE [connection-requirements](../../../includes/connection-requirements.md)]

* 数据[已格式化为表](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664)的 Excel 文件：
  
  1. 打开 Excel 文件，然后在数据中选择要使用的任意单元格。
  2. 选择插入”选项卡上的“表格”。
  3. 在“另存为表”对话框中，选中“我的表包含标题”复选框，然后选择“确定”。
  4. 保存所做更改。

## <a name="connect-to-the-cloud-storage-connection"></a>连接云存储连接
1. 在 [powerapps.com](https://web.powerapps.com) 中，展开“管理”，然后选择“连接”：  
   
    ![选择“连接”](./media/cloud-storage-blob-connections/connections.png)
2. 依次选择“新建连接”和云存储连接。 例如，选择“OneDrive”。
3. 此时，系统会提示你输入云存储帐户的用户名和密码。 输入用户名和密码，然后选择“登录”：  
    ![输入用户名和密码](./media/cloud-storage-blob-connections/signin.png)
   
    登录后，即可在应用中使用此连接。
4. 在应用中，单击或点击功能区“视图”选项卡上的“数据源”。 在右侧窗格中，单击或点击“添加数据源”，接着单击或点击云存储连接，然后选择 Excel 表。
5. 选择“连接”。
   
    此表会被列为数据源：
   
    ![选择 Excel 表](./media/cloud-storage-blob-connections/selecttable.png)
   
    > [!NOTE]
   > 请注意，必须将 Excel 数据格式化为表。

## <a name="using-the-excel-data-in-your-app"></a>在应用中使用 Excel 数据
1. 在“插入”选项卡上，依次选择“库”和“包含文本”库控件。
2. 将库的**[“Items”](../controls/properties-core.md)** 属性设为 Excel 表。 例如，如果 Excel 表名为“Table1”，请将此属性设为 Table1：  
   
    ![项属性](./media/cloud-storage-blob-connections/itemsproperty.png)  
   
    此时，库会自动更新为包含 Excel 表中的信息。
3. 在库中，选择第二个或第三个“标签”控件。 默认情况下，你会发现，第二个和第三个标签的“Text”属性自动设置为“`ThisItem.something`”。 可以将这些标签设置为表中的任意列。
   
    在以下示例中，第二个标签设置为“`ThisItem.Name`”，第三个标签设置为“`ThisItem.Notes`”：  
   
    ![第二个标签](./media/cloud-storage-blob-connections/items-secondtextbox.png)  
   
    ![第三个标签](./media/cloud-storage-blob-connections/items-thirdtextbox.png)  
   
    示例输出：  
    ![第二个和第三个标签](./media/cloud-storage-blob-connections/secondthirdtextboxes.png)
   
> [!NOTE]
> 第一个框实际上是图像控件。 如果 Excel 表中没有图像，可以删除图像控件，然后在原处添加一个标签控件。 [添加和配置控件](../add-configure-controls.md)是一个好资源。

[了解表和记录](../working-with-tables.md)介绍了更多详细信息和一些示例。  

## <a name="sharing-your-app"></a>共享应用
可以与组织中的其他人共享[应用](../share-app.md)、[资源](../share-app-resources.md)（如连接器）和[数据](../share-app-data.md)。

若要共享 Dropbox 中的文件夹，必须将共享文件夹附加到用户的 Dropbox 帐户。

涉及 Excel 文件的连接器存在[某些限制](#sharing-excel-tables)。

## <a name="known-limitations"></a>已知的限制
如果尝试在应用中使用 Excel 连接时，**数据类型不受支持**或**未格式化为表**，请[将数据格式化为表](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664)。

如果 Excel 数据包含计算列，则无法用于生成应用，也无法将相应数据添加到现有应用中。

### <a name="sharing-excel-tables"></a>共享 Excel 表
若要共享 Excel 文件中的数据，请执行以下操作：

* 在 OneDrive for Business 中，共享文件本身。
* 在 OneDrive 中，共享包含文件的文件夹，并指定任何介质的文件路径，而非 URL。
* 在 Dropbox 或 Google 云端硬盘中，共享文件或文件夹。

## <a name="helpful-links"></a>有用链接
查看所有[可用连接](../connections-list.md)。  
了解如何向应用[添加连接](../add-manage-connections.md)和[数据源](../add-data-connection.md)。  
[了解表和记录](../working-with-tables.md)（内含表数据源）。  
其他一些库资源包括[显示项列表](../add-gallery.md)和[显示库中的图像和文本](../show-images-text-gallery-sort-filter.md)。

<!--Icon references-->
[boxicon]: ./media/cloud-storage-blob-connections/boxicon.png
[dropboxicon]: ./media/cloud-storage-blob-connections/dropboxicon.png
[googledriveicon]: ./media/cloud-storage-blob-connections/googledriveicon.png
[onedriveicon]: ./media/cloud-storage-blob-connections/onedriveicon.png
[onedriveforbusinessicon]: ./media/cloud-storage-blob-connections/onedriveforbusinessicon.png
