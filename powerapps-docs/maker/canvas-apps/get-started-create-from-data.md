---
title: 通过 Excel 生成应用 | Microsoft Docs
description: 使用存储在云存储帐户的 Excel 文件，通过 PowerApps 自动生成应用
services: ''
suite: powerapps
documentationcenter: na
author: AFTOWen
manager: kfile
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.custom: mvc
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/18/2018
ms.author: anneta
ms.openlocfilehash: 6556e16fef3908a77be02f270fdb25f2f01ed4b4
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="generate-an-app-from-excel-in-powerapps"></a>使用 Excel 在 PowerApps 中生成应用
在本主题中，将使用 Excel 表中的数据，在 PowerApps 中自动生成你的第一个应用。 将选择一个 Excel 文件，生成一个应用，然后运行生成的应用。 每个生成的应用都包括屏幕，用于浏览记录、显示记录的详细信息以及创建或更新记录。 通过生成应用，可以使用 Excel 数据快速利用应用，然后自定义该应用以更好地满足需要。 

Excel 文件必须位于云存储帐户（如 OneDrive、GoogleDrive 或 Dropbox）中。 本主题使用 OneDrive for Business。

若要了解本主题，请在 Excel 中下载 [Flooring Estimates](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) 文件，并将其保存在[云存储帐户](connections/cloud-storage-blob-connections.md)中。 或者，如果数据格式[已设置为表格](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-E81AA349-B006-4F8A-9806-5AF9DF0AC664)，则可使用自己的 Excel 文件。 

如果没有适用于 PowerApps 的许可证，可以[免费注册](../signup-for-powerapps.md)。

## <a name="generate-the-app"></a>生成应用
1. 登录 [PowerApps](https://web.powerapps.com)。

    ![PowerApps 主页](./media/get-started-create-from-data/sign-in.png)

1. 在“生成类似应用”下，悬停在“从数据开始”上，然后选择“生成此应用”。

    ![用于创建应用的选项](./media/get-started-create-from-data/make-this-app.png)

1. 在“从数据开始”下，在云存储帐户的磁贴上单击或点击“手机布局”。

    ![用于创建应用的选项](./media/get-started-create-from-data/odfb-tile.png)

1. 如果系统提示，请单击或点击“连接”，并为该帐户提供凭据。

1. 在“**选择 Excel 文件**”下，浏览到“**FlooringEstimates.xlsx**”，然后单击或点击该文件。 

1. 在“**选择表**”下，单击或点击“**FlooringEstimates**”，然后单击或点击“**连接**”。

    ![用于创建应用的选项](./media/get-started-create-from-data/choose-table.png)

## <a name="run-the-app"></a>运行应用
1. 按 F5（或者单击或点击右上角附近的播放图标）即可打开预览。

    ![打开预览](./media/get-started-create-from-data/open-preview.png)

1. 通过单击或点击右上角附近的排序图标切换排序顺序。

    ![排序图标](./media/get-started-create-from-data/sort-icon.png)

1. 通过键入或粘贴搜索框中的一个或多个字符来筛选列表。

1. 单击或点击加号图标以添加记录，添加所需的任何数据，然后单击或点击选中标记图标以保存更改。

1. 单击或点击添加的记录的下一步箭头，单击或点击铅笔图标以编辑记录，更新一个或多个字段，然后单击或点击选中标记图标以保存更改。

1. 单击或点击添加的记录的下一步箭头，单击或点击铅笔图标以编辑记录，更新一个或多个字段，然后单击或点击取消图标以放弃更改。

1. 单击或点击添加的记录的下一步箭头，然后单击或点击垃圾桶图标以删除该记录。

## <a name="next-steps"></a>后续步骤
自定义默认浏览屏幕以更好地满足需求。 例如，可以按产品名称（而不是类别）对列表进行排序和筛选。

> [!div class="nextstepaction"]
> [自定义默认浏览屏幕](customize-layout-sharepoint.md)。