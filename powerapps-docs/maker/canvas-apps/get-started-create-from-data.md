---
title: 通过 Excel 生成画布应用 | Microsoft Docs
description: 使用存储在云存储帐户的 Excel 文件，通过 PowerApps 自动生成画布应用
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/14/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 7ab85f09ebf88c30b35c963242895cd74ca6a966
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61554902"
---
# <a name="generate-a-canvas-app-from-excel-in-powerapps"></a>使用 Excel 在 PowerApps 中生成画布应用

在本主题中，将使用 Excel 表中的数据，在 PowerApps 中自动生成你的第一个画布应用。 将选择一个 Excel 文件，生成一个应用，然后运行生成的应用。 每个生成的应用都包括屏幕，用于浏览记录、显示记录的详细信息以及创建或更新记录。 通过生成应用，可以使用 Excel 数据快速利用应用，然后自定义该应用以更好地满足需要。 

Excel 文件必须位于云存储帐户（如 OneDrive、GoogleDrive 或 Dropbox）中。 本主题使用 OneDrive for Business。

如果没有适用于 PowerApps 的许可证，可以[免费注册](../signup-for-powerapps.md)。

## <a name="prerequisites"></a>先决条件

若要完全按照本主题执行操作，请在 Excel 中下载 [Flooring Estimates](https://az787822.vo.msecnd.net/documentation/get-started-from-data/FlooringEstimates.xlsx) 文件，并将其保存在[云存储帐户](connections/cloud-storage-blob-connections.md)中。

> [!IMPORTANT]
> 可以使用自己的 Excel 文件，但必须将数据格式设置为表格。 有关详细信息，请参阅[设置表格格式](how-to-excel-tips.md)。 

## <a name="generate-the-app"></a>生成应用

1. 登录 [PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

1. 在“生成自己的应用”下，将鼠标悬停在“从数据开始”上，然后选择“生成此应用”。

    ![用于创建应用的选项](./media/get-started-create-from-data/start-from-data.png)

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

    例如，键入或粘贴**蜜标**以显示仅记录为其字符串出现在产品的名称、 类别或概述。

    ![筛选器示例](./media/get-started-create-from-data/filter-example.png)

1. 添加一条记录：

    1. 选择加号图标。

        ![加号图标](./media/get-started-create-from-data/plus-icon.png)

    1. 添加所需的任何数据，然后选择复选标记图标以保存所做的更改。

        ![保存图标](./media/get-started-create-from-data/save-icon.png)

1. 编辑记录：

    1. 选择你想要编辑的记录的箭头。

        ![“下一步”箭头](./media/get-started-create-from-data/next-arrow.png)

    1. 选择铅笔图标。

        ![铅笔图标](./media/get-started-create-from-data/pencil-icon.png)

    1. 更新一个或多个字段，然后选择复选标记图标以保存所做的更改。

        ![保存图标](./media/get-started-create-from-data/save-icon.png)

        或者，选择取消图标以放弃所做的更改。

1. 删除一条记录：

    1. 选择你想要删除的记录的下一步箭头。

        ![“下一步”箭头](./media/get-started-create-from-data/next-arrow.png)

    1. 选择垃圾桶图标。

        ![“垃圾桶”图标](./media/get-started-create-from-data/trash-icon.png)

## <a name="next-steps"></a>后续步骤

自定义默认浏览屏幕以更好地满足需求。 例如，可以进行排序和筛选列表依据仅产品名称、 不是类别或概述。

> [!div class="nextstepaction"]
> [自定义默认浏览屏幕](customize-layout-sharepoint.md)。
