---
title: 使用示例应用 | Microsoft 文档
description: 分步介绍如何基于 PowerApps 的示例创建画布应用
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/11/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e6ebc516c6b07f149e2b965b967966c3832476c9
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675500"
---
# <a name="create-a-canvas-app-from-a-sample-in-powerapps"></a>从 PowerApps 中的示例创建画布应用
在本快速入门教程中，将根据示例创建一个画布应用，以便探索设计的可能性，并发现在开发自己的应用时可以应用的概念。

每个示例均展示了一个实际场景，但使用的是虚构数据。 若要存储此数据，需要一个云存储帐户，如 Dropbox、GoogleDrive 或 OneDrive。

如果没有适用于电源应用的许可证，可以[免费注册](../signup-for-powerapps.md)。

## <a name="open-a-sample-app"></a>打开示例应用
1. 登录 [PowerApps](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

1. 在示例应用列表中，将鼠标悬停在示例应用（如成本估算器）上。

    ![](./media/open-and-run-a-sample-app/cost-estimator.png)

1. 单击或点击手机图标以创建适用于移动设备的应用版本（或保留选定的平板电脑图标），然后单击或点击“生成此应用”。

1. 在 Power Apps Studio 中，单击或点击屏幕顶部附近的横幅中的 "**创建我自己的应用**"。

    ![](./media/open-and-run-a-sample-app/banner.png)

1. 指定要存储此应用虚构数据的云存储帐户，然后为该帐户提供凭据。

1. 按 F5（或者单击或点击靠近右上角的播放按钮）即可打开预览模式。

    ![](./media/open-and-run-a-sample-app/open-preview.png)

    每个示例表示不同的场景，其中包含各种屏幕和其他控件。 如果打开了成本估算器示例，则可以使用默认应用执行以下任务：

    - 创建一个约会，用于估算在一个特定大小的室内安装地板产品的成本。
    - 捕获地址和使用面积等详细信息，并基于折扣和税率计算价格。
    - 筛选约会列表可显示已为其创建估算值的约会、尚未为其创建估算值的约会或所有约会。
    
1. 完成浏览应用后，按 Esc 键（或者单击或点击右上角附近的关闭图标，具体位于 PowerApps 的标题栏下方），关闭预览模式。

## <a name="save-the-app"></a>保存应用
1. 在左上角附近，单击或点击“文件”选项卡。

1. 在“应用设置”页中，查看默认设置。

    ![](./media/open-and-run-a-sample-app/app-settings.png)

1. 在左边缘附近单击或点击“保存”。 

## <a name="next-steps"></a>后续步骤
在本快速入门中，你基于一个示例创建了自己的应用，该示例使用你的云帐户中存储的虚构数据。 若要深入了解如何创建应用，还可以基于其他源（例如 Common Data Service、SharePoint 或 Excel）中的数据自动生成应用。

> [!div class="nextstepaction"]
> [生成应用](data-platform-create-app.md)
