---
title: 在解决方案中创建画布应用 |Microsoft Docs
description: 在 Power Apps 中，在解决方案中创建一个画布应用，以便将应用部署到另一个环境
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/23/2018
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: f6b34a5ea1b2f269a26ad70de6a6a530a30bc240
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679330"
---
# <a name="create-a-canvas-app-from-within-a-solution"></a>从解决方案中创建画布应用

例如，如果想要将应用部署到其他环境，请在解决方案中创建应用。 解决方案不仅可包含应用，还可以包含自定义实体、选项集和其他组件。 你可以通过从解决方案中创建应用和其他组件、导出解决方案，然后将其导入到另一个环境，以多种方式快速自定义环境。

有关解决方案的详细信息，请参阅[解决方案概述](../common-data-service/solutions-overview.md)。

## <a name="prerequisite"></a>先决条件

若要执行本主题中的步骤，必须切换到包含 Common Data Service 数据库的环境。

## <a name="create-a-solution"></a>创建解决方案

如果你已经有一个要在其中创建应用程序或要将应用程序链接到的解决方案，则可以跳过此过程。

1. [登录](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 Power Apps，然后（如有必要）切换到相应的环境：

    - 如果要从解决方案中创建应用，请切换到包含 Common Data Service 数据库的任何环境。
    - 如果要将现有应用链接到解决方案，请切换到包含该应用的环境。

1. 在左侧导航栏中，选择 "**解决方案**"。

    > [!div class="mx-imgBorder"]
    > ![左侧导航栏中的 "解决方案" 选项](./media/add-app-solution/left-nav.png "左侧导航栏中的 "解决方案" 选项")

1. 在标题栏下的标题栏中，选择 "**新建解决方案**"。

    > [!div class="mx-imgBorder"]
    > ![横幅中的新解决方案选项](./media/add-app-solution/banner-new-solution.png "横幅中的新解决方案选项")

1. 在出现的窗口中，为解决方案指定显示名称、发布者和版本。

    > [!div class="mx-imgBorder"]
    > ![用于新解决方案的选项](./media/add-app-solution/configure-new-solution.png "用于新解决方案的选项")

    将根据你指定的显示名称自动生成名称（不含空格），但你可以根据需要自定义生成的名称。 如果您在这些区域中没有特定的需求，则可以为您的环境指定默认发布服务器，为版本指定**1.0** 。

1. 在左上角附近，选择 "**保存并关闭**"。

    > [!div class="mx-imgBorder"]
    > ![保存新解决方案](./media/add-app-solution/save-new-solution.png "保存新解决方案")

## <a name="create-a-canvas-app-in-a-solution"></a>在解决方案中创建画布应用

可以在解决方案中创建空白画布应用。 不能自动生成三屏应用，或者从解决方案内部自定义模板或示例应用。

1. [登录](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 PowerApps。

1. 如有必要，请切换到包含要在其中创建画布应用的解决方案的环境。

1. 在左侧导航栏中，选择 "**解决方案**"。

    > [!div class="mx-imgBorder"]
    > ![左侧导航栏中的 "解决方案" 选项](./media/add-app-solution/left-nav.png "左侧导航栏中的 "解决方案" 选项")

1. 在解决方案列表中，选择要在其中创建画布应用的解决方案。

1. 在标题栏下的标题栏中，选择 "**新建**" > **应用** > **画布应用**"，然后选择要创建的应用的外观规格（手机或平板电脑）。

    > [!div class="mx-imgBorder"]
    > ![用于在解决方案中创建应用的选项](./media/add-app-solution/new-option.png "用于在解决方案中创建应用的选项")

    Power Apps Studio 会在另一个浏览器选项卡中使用空白画布打开。

1. 创建应用（或至少进行一项更改），然后保存所做的更改。

1. 在选择解决方案的 "浏览器" 选项卡上，选择 "**完成**" 以刷新解决方案中组件的列表。

    > [!div class="mx-imgBorder"]
    > ![完成按钮](./media/add-app-solution/done-button.png "“完成”按钮")

    新应用将出现在该解决方案的组件列表中。 如果保存对应用所做的任何更改，则这些更改将反映在解决方案中的版本中。

## <a name="link-an-existing-canvas-app-to-a-solution"></a>将现有画布应用链接到解决方案

如果要将应用链接到解决方案，两者都必须在相同的环境中，并且必须在解决方案中创建应用。

1. [登录](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 PowerApps。

1. 如有必要，请切换到包含要链接应用的解决方案的环境。

1. 在左侧导航栏中，选择 "**解决方案**"。

    > [!div class="mx-imgBorder"]
    > ![左侧导航栏中的 "解决方案" 选项](./media/add-app-solution/left-nav.png "左侧导航栏中的 "解决方案" 选项")

1. 在解决方案列表中，选择要将应用链接到的解决方案。

1. 在标题栏下的标题栏中，选择 "**添加现有** > **应用** > **画布应用**"。

    > [!div class="mx-imgBorder"]
    > ![链接现有应用的横幅选项](./media/add-app-solution/add-existing.png "链接现有应用的横幅选项")

    在此环境中的解决方案中创建的画布应用列表随即出现。

1. 在应用列表中，选择要链接到解决方案的应用，然后选择 "**添加**"。

    > [!div class="mx-imgBorder"]
    > ![添加按钮](./media/add-app-solution/add-button.png "“添加”按钮")

## <a name="known-limitations"></a>已知的限制

有关已知限制的信息，请参阅[在 PowerApps 中使用解决方案](../common-data-service/use-solution-explorer.md#known-limitations)。 

## <a name="next-steps"></a>后续步骤

- 创建或链接更多应用程序和[其他组件](../common-data-service/use-solution-explorer.md)（如实体、流和仪表板）到你的解决方案。
- [导出解决方案](../common-data-service/import-update-export-solutions.md)，以便可以将其部署到其他环境、AppSource 等。
