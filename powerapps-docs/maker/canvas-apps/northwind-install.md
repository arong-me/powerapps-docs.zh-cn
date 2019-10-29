---
title: 安装 Northwind 商贸数据库和应用 |Microsoft Docs
description: 将 Northwind 数据库和应用安装到环境中，以探索关系概念。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 06/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 3a2c3b468c7ccc09c49221c65113e66b562f5ed1
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "71990863"
---
# <a name="install-northwind-traders-database-and-apps"></a>安装 Northwind 商贸数据库和应用

按照[此系列主题](northwind-orders-canvas-part1.md)中的步骤，您可以发现有关在 Common Data Service 中的示例数据库中实现的关系数据的概念。 你还可以浏览示例业务应用（画布和模型驱动）来管理该数据，并通过创建此类应用来获得切实可行的经验。 本主题介绍如何在自己的环境中安装 Northwind 商贸数据库并获取对示例应用的访问权限，你可以打开这些应用进行编辑，以显示它们的生成方式。

Northwind 商贸是一家虚构的组织，负责管理企业的订单、产品、客户、供应商和其他许多方面。 此示例与第一个版本的 Microsoft Access 一起显示，仍可用作访问模板。

## <a name="prerequisites"></a>必备组件

- 支持 Common Data Service 的 PowerApps 许可证。 你可以[使用免费试用版许可证](../signup-for-powerapps.md)30 天。
- 具有 Common Data Service 数据库的环境。 如果你具有相应的权限，则可以[创建此类环境](https://docs.microsoft.com/power-platform/admin/create-environment)。

## <a name="download-the-solution"></a>下载解决方案

> [!div class="nextstepaction"]
> [下载 Northwind 商贸解决方案文件](https://pwrappssamples.blob.core.windows.net/samples/NorthwindTraders_1_0_0_6.zip)

此[解决方案](../../developer/common-data-service/introduction-solutions.md)文件（.zip）包含实体、选项集和业务流程的定义;画布和模型驱动应用;以及一起使用的任何其他部分。

## <a name="install-the-solution"></a>安装解决方案

1. 登录到[PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后确保你在包含 Common Data Service 数据库的环境中工作。

1. 在左侧导航窗格中，选择 "**解决方案**"，然后在屏幕顶部附近的工具栏中选择 "**导入**"：

    > [!div class="mx-imgBorder"]
    > ![解决方案 "视图和导入-解决方案入口点](media/northwind-install/solution-import.png)

1. 在 "**选择解决方案包**" 页中，选择 "**浏览**"。

    > [!div class="mx-imgBorder"]
    > 选择 "包之前 ![选择解决方案包" 页面](media/northwind-install/select-solution2.png)

1. 找到下载的文件，然后选择 "**打开**"。

    除非您选择了其他位置，否则该文件将位于 "下载" 文件夹中。

1. 如果有正确的文件（版本号可能不同），请选择 "**下一步**"：

    > [!div class="mx-imgBorder"]
    > 选择包后 ![选择解决方案包页](media/northwind-install/confirm-solution2.png)

1. 如果解决方案的名称正确，请在 "**解决方案信息**" 页中选择 "**下一步**"。

    > [!div class="mx-imgBorder"]
    > ![解决方案信息 "页面](media/northwind-install/confirm-publisher.png)

1. 在 "**导入选项**" 页上，选择 "**导入**" 以确认 SDK 消息处理，示例要求：

    > [!div class="mx-imgBorder"]
    > ![导入选项 "页](media/northwind-install/confirm-sdk.png)

    在接下来的几分钟内安装解决方案时，将显示另一页，并显示进度：

    > [!div class="mx-imgBorder"]
    > ![进度栏](media/northwind-install/solution-progress.png)

    安装完成后，原始页面将显示结果：

    > [!div class="mx-imgBorder"]
    > ![导入解决方案页](media/northwind-install/solution-success.png)

1. 选择“关闭”。

## <a name="load-the-sample-data"></a>加载示例数据

1. 选择 "**应用**"，然后选择 " **Northwind 示例数据**"。

    如果在安装解决方案后未立即出现 Northwind 应用，请等待几分钟：

    > [!div class="mx-imgBorder"]
    > 在应用列表中 ![Northwind 数据库](media/northwind-install/sample-data-app.png)

1. 当应用请求与 Common Data Service 交互的权限时，请选择 "**允许**"：

    > [!div class="mx-imgBorder"]
    > Common Data Service 的 ![许可对话框](media/northwind-install/sample-data-permission.png)

1. 在应用程序加载并显示示例实体不包含任何记录后，请选择 "**加载数据**" 以填充实体：

    > [!div class="mx-imgBorder"]
    > 示例数据管理器中 !["加载数据" 按钮](media/northwind-install/sample-data-load.png)

    当应用程序加载数据时，将在应用程序的顶部的第3号点和记录数增加。

    实体按特定顺序加载，以便可以在记录之间建立关系。 例如，"**订单详细信息**" 实体与 "**订单**" 和 "**订单" 产品**实体具有多对一关系，它们首先加载。

    您可以通过选择 "**取消**" 随时取消该过程，并且可以通过选择 "**删除数据**" 随时删除数据：

    > [!div class="mx-imgBorder"]
    > 加载数据时数据管理器 ![示例](media/northwind-install/sample-data-progress.png)

    数据完成加载后，最后一行（**多对多关系**）将显示**完成**，并再次启用 "**加载数据**" 和 "**删除数据**" 按钮：

    > [!div class="mx-imgBorder"]
    > 加载数据后 ![示例数据管理器](media/northwind-install/sample-data-complete.png)

## <a name="sample-apps"></a>应用示例

Northwind 解决方案包含以下用于与此数据交互的应用：

- Northwind 订单（画布）
- Northwind 订单（模型驱动）

打开这些应用的方式与你在上一过程中打开应用的方式相同。

### <a name="canvas"></a>画布

此单屏幕应用提供**Orders**实体的简单的主-详细视图，您可以在其中查看和编辑订单的订单和每个行项的汇总。 订单列表显示在左边缘附近，您可以选择该列表中的箭头，以显示该订单的摘要和详细信息。 详细信息：[有关 Northwind 商贸的画布应用的概述](northwind-orders-canvas-overview.md)。

> [!div class="mx-imgBorder"]
> Northwind 画布应用中订单和详细信息的 ![列表](media/northwind-install/orders-canvas.png)

### <a name="model-driven"></a>模型驱动

此应用对与画布应用相同的数据（在**Orders**实体中）进行操作。 在订单列表中，通过选择订单号来显示有关订单的详细信息：

> [!div class="mx-imgBorder"]
> Northwind 模型驱动应用中的订单 ![列表](media/northwind-install/orders-model.png)

订单摘要以单独的形式显示：

> [!div class="mx-imgBorder"]
> 模型驱动应用中 ![订单详细信息](media/northwind-install/orders-model-2.png)

如果向下滚动窗体，它会显示与画布应用相同的行项：

> [!div class="mx-imgBorder"]
> 在模型驱动的应用中 ![更多订单详细信息](media/northwind-install/orders-model-3.png)

## <a name="do-it-yourself"></a>自行完成

可以按照分步说明创建本主题前面部分中所示的画布应用。  说明划分为三个部分：

1. [创建订单库](northwind-orders-canvas-part1.md)。
1. [创建摘要窗体](northwind-orders-canvas-part2.md)。
1. [创建详细信息库](northwind-orders-canvas-part3.md)。

如果要跳过，解决方案包含每个部件的启动点应用。  在应用列表中，查找 " **Northwind 订单（画布）-开始第1部分**" 等。

此[应用概述](northwind-orders-canvas-overview.md)介绍了用户界面、数据源以及如何使用关系。

> [!div class="nextstepaction"]
> [首先阅读概述](northwind-orders-canvas-overview.md)
