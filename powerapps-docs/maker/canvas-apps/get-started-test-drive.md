---
title: 根据模板创建画布应用 | Microsoft Docs
description: 分步说明如何根据 Power Apps 模板自动创建画布应用。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 01/29/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d64b1ef3f6d885093fc9f89ecf31b785c07ea6bd
ms.sourcegitcommit: 303d5aed44f2bbb406cabeb6b9c8474d738d9114
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "76918766"
---
# <a name="create-a-canvas-app-from-a-template-in-power-apps"></a>根据 Power Apps 中的模板创建画布应用

基于特定方案的模板自动创建画布应用，例如跟踪预算和计划休假，然后运行应用以理解其默认行为。

若要从模板创建一个应用，需要云存储帐户（如 DropBox、OneDrive 或 Google Drive）来存储模板的示例数据。

如果没有适用于 PowerApps 的许可证，可以[免费注册](../signup-for-powerapps.md)。

## <a name="create-an-app"></a>创建应用

1. 登录到 [Power Apps](https://make.powerapps.com)。

1. 从左侧导航栏中选择“应用”  。 选择“新建应用”下拉菜单，然后选择“画布”   。

    ![新建画布应用](./media/get-started-test-drive/new-canvas-app.png)

    这会在新选项卡中打开 [Power Apps Studio](https://docs.microsoft.com/powerapps/powerapps-overview#power-apps-for-app-makerscreators)。

1. 在“应用模板”磁贴上，选择“手机布局”或“平板电脑布局”    。

    ![模板中的应用磁贴](./media/get-started-test-drive/template-tile.png)

1. 在模板列表中，选择一个模板，然后选择“使用”（靠近右下角）  。

    ![打开 Power Apps 模板](./media/get-started-test-drive/open-template.png)

    Power Apps Studio 会在新选项卡中打开，并会创建应用。

    > [!NOTE]
    > 如果“使用”按钮处于禁用状态，请确保已选择应用的数据源  。 你可以选择数据源，方法是选择底部的“选择”  。
    >
    > ![选择数据源](./media/get-started-test-drive/choose-data-source.png)

## <a name="run-the-app"></a>运行应用
从模板创建的应用可在默认工作区打开，大部分时间都会在该工作区进行自定义。 对应用进行任何更改之前，浏览应用在“预览”模式下的运行方式  。

1. 按 F5（或者单击或点击右上角的右箭头）可在**预览**模式下打开应用。

    ![打开预览模式按钮](./media/get-started-test-drive/open-preview.png)

    应用已使用示例数据进行了填充，以展示应用的功能。 例如，成本估算器应用包含用于创建约会和估算在特定大小的室内安装指定地板产品成本的数据。

4. 通过创建、更新和删除示例数据，浏览应用的默认行为，然后验证云存储帐户中的数据反映了更改。

    例如，创建约会并在成本估算器应用内创建预计成本。

5. 按 Esc（或者单击或点击右上角附近的“X”图标）即可返回默认工作区  。

## <a name="next-steps"></a>后续步骤
1. 按 Ctrl-S，为应用程序命名，然后单击或点击“**保存**”将应用保存到云。

1. 与组织内的其他人[共享应用](share-app.md)。

> [!IMPORTANT]
> 共享应用前，请确保共享对象有权访问数据。 例如，必须在云存储帐户中 [共享 Excel 或其他文件](share-app-data.md)。
