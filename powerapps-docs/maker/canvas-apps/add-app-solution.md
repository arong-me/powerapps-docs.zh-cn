---
title: 在解决方案中创建画布应用 |Microsoft Docs
description: 在 PowerApps 中，创建一个解决方案中的画布应用，以便可以将应用部署到另一个环境
author: AFTOwen
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: ''
ms.date: 10/23/2018
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: dcb6a9c69e602b739d58afde2242d18b60e6f477
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61540365"
---
# <a name="create-a-canvas-app-from-within-a-solution"></a>创建画布应用从解决方案中

如果，例如，想要将应用部署到不同的环境，请创建从解决方案中的应用。 解决方案可以包含不仅应用，但还自定义的实体、 选项集和其他组件。 ： 创建应用程序和从解决方案中的其他组件，导出解决方案，然后将其导入另一个环境，您可以快速自定义的环境中不同的方式。

解决方案是基于客户的参与，与 Dynamics 365 相同的平台。 有关详细信息，请参阅[解决方案概述](../common-data-service/solutions-overview.md)。

## <a name="prerequisite"></a>先决条件

若要按照本主题中的步骤，必须切换到包含 Common Data Service 数据库的环境。

## <a name="create-a-solution"></a>创建解决方案

如果你已有想要创建应用，或者对于想要链接的应用程序的解决方案，则可以跳过此过程。

1. [登录](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 PowerApps，然后 （如果有必要） 切换到相应的环境：

    - 如果你想要创建从应用的解决方案中，切换到包含 Common Data Service 数据库的任何环境。
    - 如果你想要将现有应用程序链接到一个解决方案，切换到包含该应用的环境。

1. 在左侧的导航栏中，选择**解决方案**。

    > [!div class="mx-imgBorder"]
    > ![解决方案选项中的左侧的导航栏](./media/add-app-solution/left-nav.png "左侧的导航栏中的解决方案选项")

1. 在标题栏下方的标题中，选择**新的解决方案**。

    > [!div class="mx-imgBorder"]
    > ![标题栏中的新建解决方案选项](./media/add-app-solution/banner-new-solution.png "标题栏中的新建解决方案选项")

1. 在出现的窗口中，指定显示名称、 发布者和你的解决方案的版本。

    > [!div class="mx-imgBorder"]
    > ![新的解决方案的选项](./media/add-app-solution/configure-new-solution.png "新解决方案的选项")

    将根据你指定的显示名称自动生成的名称 （不含空格），但如果你想，您可以自定义生成的名称。 你可以为您的环境指定默认发布服务器和**1.0**如果这些区域中没有特定需求的版本。

1. 左上角附近，选择**保存并关闭**。

    > [!div class="mx-imgBorder"]
    > ![保存新的解决方案](./media/add-app-solution/save-new-solution.png "保存新的解决方案")

## <a name="create-a-canvas-app-in-a-solution"></a>在解决方案中创建画布应用

可以创建从解决方案中的空白画布应用。 无法自动生成三屏应用或自定义模板或示例应用中，解决方案中。

1. [登录](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 PowerApps。

1. 如有必要，切换到包含想要创建画布应用的解决方案的环境。

1. 在左侧的导航栏中，选择**解决方案**。

    > [!div class="mx-imgBorder"]
    > ![解决方案选项中的左侧的导航栏](./media/add-app-solution/left-nav.png "左侧的导航栏中的解决方案选项")

1. 在解决方案的列表中，选择要在其中创建画布应用的解决方案。

1. 在标题栏下方的标题中，选择**新建** > **应用** > **画布应用**，然后选择应用程序的窗体因素 （手机或平板电脑），你想要创建。

    > [!div class="mx-imgBorder"]
    > ![在解决方案中创建应用程序的选项](./media/add-app-solution/new-option.png "选项在解决方案中创建的应用")

    PowerApps Studio 打开，并在另一个浏览器选项卡的空白画布。

1. 创建您的应用程序 （或进行至少一次更改），然后保存所做的更改。

1. 在其中选择你的解决方案浏览器选项卡上，选择**完成**以刷新你的解决方案中的组件列表。

    > [!div class="mx-imgBorder"]
    > ![完成按钮](./media/add-app-solution/done-button.png "完成按钮")

    新的应用显示为该解决方案的组件的列表中。 如果将保存到您的应用程序的任何更改，它们将反映在解决方案中的版本。

## <a name="link-an-existing-canvas-app-to-a-solution"></a>将现有的画布应用链接到一个解决方案

如果你想要将应用链接到一个解决方案，两者都必须在相同环境中，并且应用程序必须已创建从解决方案中。

1. [登录](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 PowerApps。

1. 如有必要，切换到包含你想要链接的应用程序的解决方案的环境。

1. 在左侧的导航栏中，选择**解决方案**。

    > [!div class="mx-imgBorder"]
    > ![解决方案选项中的左侧的导航栏](./media/add-app-solution/left-nav.png "左侧的导航栏中的解决方案选项")

1. 在解决方案的列表中，选择你想要链接的应用程序的解决方案。

1. 在标题栏下方的标题中，选择**添加现有项** > **应用** > **画布应用**。

    > [!div class="mx-imgBorder"]
    > ![横幅选项链接现有的应用程序](./media/add-app-solution/add-existing.png "横幅选项链接现有的应用程序")

    将显示在此环境中的解决方案中创建的画布应用的列表。

1. 在应用程序列表中，选择你想要链接到该解决方案，然后选择的应用**添加**。

    > [!div class="mx-imgBorder"]
    > ![添加按钮](./media/add-app-solution/add-button.png "添加按钮")

## <a name="known-limitations"></a>已知的限制

有关已知限制的信息，请参阅[在 PowerApps 中使用解决方案](../common-data-service/use-solution-explorer.md#known-limitations)。 

## <a name="next-steps"></a>后续步骤

- 创建或链接更多应用和[其他组件](../common-data-service/use-solution-explorer.md)，例如实体、 流和仪表板，你的解决方案。
- [导出你的解决方案](../common-data-service/import-update-export-solutions.md)，以便您可以将其部署到另一个环境中，在 AppSource，等等。
