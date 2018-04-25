---
title: 从模板创建应用 | Microsoft 文档
description: 基于 PowerApps 模板自动创建应用的分步说明。
services: ''
suite: powerapps
documentationcenter: na
author: AFTOwen
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/19/2018
ms.author: anneta
ms.openlocfilehash: 809856ca0139377a86894c6a5b8d3be4f2d99c1b
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="create-an-app-from-a-powerapps-template"></a>从 PowerApps 模板创建应用
基于特定方案的模板自动创建应用，例如跟踪预算和计划休假，然后运行应用以理解其默认行为。

若要从模板创建一个应用，需要云存储帐户（如 DropBox、OneDrive 或 Google Drive）来存储模板的示例数据。

如果没有适用于 PowerApps 的许可证，可以[免费注册](../signup-for-powerapps.md)。

## <a name="create-an-app"></a>创建应用
1. 登录 [PowerApps](http://web.powerapps.com)。

    ![PowerApps 主页](./media/get-started-test-drive/sign-in.png)

1. 在“生成类似应用”下，悬停在“从数据开始”上，然后单击或点击“生成此应用”。

    ![生成此应用磁贴](./media/get-started-test-drive/make-this-app.png)

1. 在“应用模板”磁贴上，单击或点击“手机布局”或“平板电脑布局”。

    ![模板中的应用磁贴](./media/get-started-test-drive/template-tile.png)

4. 在模板列表中，单击或点击一个模板，然后单击或点击“**使用**”（靠近右下角）。

    ![打开 PowerApps 模板](./media/get-started-test-drive/open-template.png)

    示例数据将复制到云存储帐户，应用将得以创建，此应用主页也将显示。

## <a name="run-the-app"></a>运行应用
从模板创建的应用可在默认工作区打开，大部分时间都会在该工作区进行自定义。 对应用进行任何更改之前，浏览应用在“预览”模式下的运行方式。

1. 按 F5（或者单击或点击右上角的右箭头）可在**预览**模式下打开应用。

    ![打开预览模式按钮](./media/get-started-test-drive/open-preview.png)

    应用已使用示例数据进行了填充，以展示应用的功能。 例如，成本估算器应用包含用于创建约会和估算在特定大小的室内安装指定地板产品成本的数据。

4. 通过创建、更新和删除示例数据，浏览应用的默认行为，然后验证云存储帐户中的数据反映了更改。

    例如，创建约会并在成本估算器应用内创建预计成本。

5. 按 Esc（或者单击或点击右上角附近的“X”图标）即可返回默认工作区。

## <a name="next-steps"></a>后续步骤
1. 按 Ctrl-S，为应用程序命名，然后单击或点击“**保存**”将应用保存到云。

1. 与组织内的其他人[共享应用](share-app.md)。

> [!IMPORTANT]
> 共享应用前，请确保共享对象有权访问数据。 例如，必须在云存储帐户中 [共享 Excel 或其他文件](share-app-data.md)。