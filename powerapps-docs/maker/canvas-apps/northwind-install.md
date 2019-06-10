---
title: 安装 Northwind Trader 数据库和应用程序 |Microsoft Docs
description: 安装 Northwind 数据库和应用到一个环境，以浏览关系概念。
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 06/06/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 351f9fd4fe369b3073a9edfb0158883140f50693
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66761019"
---
# <a name="install-northwind-traders-database-and-apps"></a>安装 Northwind Trader 数据库和应用程序

按照中的步骤[这一系列的主题](northwind-orders-canvas-part1.md)，在 Common Data Service 中的示例数据库中实现时，可以发现有关关系数据概念。 您还可以查看示例业务应用程序，同时画布和模型驱动的用于管理该数据并通过创建此类应用获得实践经验。 此第一个主题说明如何在您自己的环境中安装 Northwind Trader 数据库并获取访问权限的示例应用，可以打开进行编辑以显示如何生成它们。

Northwind Traders 是虚构的组织管理订单、 产品、 客户、 供应商和小型企业的许多其他方面。 此示例显示使用 Microsoft Access 的第一个版本并仍可用作访问模板。

## <a name="prerequisites"></a>先决条件

- 支持 Common Data Service 中的 PowerApps 许可证。 你可以[使用免费试用版许可证](../signup-for-powerapps.md)30 天。
- 具有 Common Data Service 数据库的环境。 你可以[创建此类环境](https://docs.microsoft.com/power-platform/admin/create-environment)如果您具有相应权限。

## <a name="download-the-solution"></a>下载的解决方案

> [!div class="nextstepaction"]
> [下载 Northwind Traders 解决方案文件](https://pwrappssamples.blob.core.windows.net/samples/NorthwindTraders_1_0_0_6.zip)

这[解决方案](../../developer/common-data-service/introduction-solutions.md)文件 (.zip) 包含的实体、 选项集和业务流程定义; 画布和模型驱动应用; 与一起使用的任何其他部分。

## <a name="install-the-solution"></a>安装解决方案

1. 登录到[PowerApps](https://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，然后确保您正在处理包含 Common Data Service 数据库的环境中。

1. 在左侧的导航窗格中，选择**解决方案**，然后选择**导入**靠近屏幕顶部的工具栏中：

    > [!div class="mx-imgBorder"]
    > ![解决方案视图和导入解决方案入口点](media/northwind-install/solution-import.png)

1. 在中**选择解决方案包**页上，选择**浏览**。

    > [!div class="mx-imgBorder"]
    > ![选择解决方案包页面，然后选择包](media/northwind-install/select-solution2.png)

1. 找到文件下载，并选择**打开**。

    除非选择其他位置，则文件将在下载文件夹中。

1. 如果正确的文件 （版本号可能不同），请选择**下一步**:

    > [!div class="mx-imgBorder"]
    > ![选择包后，选择解决方案包页](media/northwind-install/confirm-solution2.png)

1. 在中**解决方案信息**页上，选择**下一步**解决方案和发布服务器的名称是否正确。

    > [!div class="mx-imgBorder"]
    > ![解决方案信息页](media/northwind-install/confirm-publisher.png)

1. 在中**导入选项**页上，选择**导入**确认 SDK 消息处理，此示例需要：

    > [!div class="mx-imgBorder"]
    > ![导入选项页](media/northwind-install/confirm-sdk.png)

    另一页将出现并显示进度，如在下一步的几分钟内安装解决方案：

    > [!div class="mx-imgBorder"]
    > ![进度栏](media/northwind-install/solution-progress.png)

    在安装完成后，原始页上显示结果：

    > [!div class="mx-imgBorder"]
    > ![导入解决方案页](media/northwind-install/solution-success.png)

1. 选择“关闭”  。

## <a name="load-the-sample-data"></a>加载示例数据

1. 选择**应用程序**，然后选择**Northwind 示例数据**。

    如果在安装解决方案之后立即 Northwind 应用程序不会显示，请等待几分钟：

    > [!div class="mx-imgBorder"]
    > ![Northwind 数据库中的应用列表](media/northwind-install/sample-data-app.png)

1. 当应用程序请求与 Common Data Service 进行交互的权限时，则选择**允许**:

    > [!div class="mx-imgBorder"]
    > ![针对 Common Data Service 同意对话框](media/northwind-install/sample-data-permission.png)

1. 应用程序将加载并显示了示例实体包含任何记录后，选择**将数据加载**来填充实体：

    > [!div class="mx-imgBorder"]
    > ![加载示例数据管理器中的数据按钮](media/northwind-install/sample-data-load.png)

    应用程序加载数据，如跨应用程序中，顶部和数量的记录增加年 3 月点。

    按特定顺序加载实体，以便可以在记录之间建立关系。 例如，**订单详细信息**实体具有多对一关系与**订单**并**订购产品**首先加载的实体。

    可以通过选择在任何时候取消过程**取消**，并可以通过选择在任何时候删除数据**删除数据**:

    > [!div class="mx-imgBorder"]
    > ![加载示例数据管理器作为数据](media/northwind-install/sample-data-progress.png)

    在数据加载完后，最后一行 (**多对多关系**) 显示**完成**，并**加载数据**并**删除数据**再次启用按钮：

    > [!div class="mx-imgBorder"]
    > ![加载数据后，示例数据管理器](media/northwind-install/sample-data-complete.png)

## <a name="sample-apps"></a>应用示例

Northwind 解决方案包括这些应用程序与此数据进行交互：

- Northwind 订单 （画布）
- Northwind 订单 （模型驱动）

打开这些应用程序相同的方式上一个过程中打开该应用程序。

### <a name="canvas"></a>画布

此单屏幕应用提供了简单的母版-详细信息视图的**订单**实体，可以在其中查看并编辑订单和订单的每个行项的摘要。 左边缘附近将显示的订单列表，并可以在该列表以显示摘要和该订单的详细信息中选择一个箭头。 详细信息：[Northwind Traders 的画布应用的概述](northwind-orders-canvas-overview.md)。

> [!div class="mx-imgBorder"]
> ![订单和 Northwind 中的详细信息的列表画布应用](media/northwind-install/orders-canvas.png)

### <a name="model-driven"></a>模型驱动

此应用程序对相同数据 (在**订单**实体) 的画布应用。 在订单列表中，通过选择其数字来显示有关订单的详细信息：

> [!div class="mx-imgBorder"]
> ![Northwind 模型驱动应用中的订单列表](media/northwind-install/orders-model.png)

在单独的窗体上显示订单的摘要：

> [!div class="mx-imgBorder"]
> ![模型驱动应用中的订单详细信息](media/northwind-install/orders-model-2.png)

如果您向窗体下滚动，它显示了相同的行项画布应用一样：

> [!div class="mx-imgBorder"]
> ![模型驱动应用中的多个订单详细信息](media/northwind-install/orders-model-3.png)

## <a name="do-it-yourself"></a>就自己动手

可以按照分步说明来创建画布应用本主题中前面所示。  说明分为三个部分：

1. [创建顺序库](northwind-orders-canvas-part1.md)。
1. [创建摘要的窗体](northwind-orders-canvas-part2.md)。
1. [创建详细信息库](northwind-orders-canvas-part3.md)。

如果你想要跳过一些步骤，该解决方案包含用于每个部分的起始点应用程序。  在应用程序列表中，寻找**Northwind 订单 （画布）-第 1 部分开始**，依此类推。

这[的应用程序概述](northwind-orders-canvas-overview.md)解释了用户界面、 数据源和如何使用关系。

> [!div class="nextstepaction"]
> [首先阅读概述](northwind-orders-canvas-overview.md)
