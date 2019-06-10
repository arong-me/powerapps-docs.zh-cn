---
title: Northwind Traders 的画布应用的概述 |Microsoft Docs
description: ''
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: e2f28b07f53646e6fbf5afc0b1510bd37e3262b8
ms.sourcegitcommit: e85072f7a80da308c4caabe20adbf2509588ca57
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66761042"
---
# <a name="overview-of-the-canvas-app-for-northwind-traders"></a>Northwind Traders 的画布应用的概述

了解有关画布应用，用于管理关系数据在 Northwind Traders 数据库[环境中安装](northwind-install.md)。 然后按照后续主题中的分步说明来生成此应用程序中的从零开始，从而获得亲身体验使用关系数据。

在本主题中，发现：

- 如何应用用户显示和管理应用程序中的关系数据。
- 哪些类型的数据驱动应用程序。
- 如何创建这些类型的数据之间的关系。

在单个屏幕中，应用程序用户可以显示、 更新、 创建和删除订单。

> [!div class="mx-imgBorder"]
> ![完整的画布应用](media/northwind-orders-canvas-part1/orders-finished.png)

## <a name="explore-the-user-interface"></a>浏览用户界面

### <a name="order-gallery"></a>顺序库

在应用程序的左边缘，库显示订单的列表，包括订单号、 状态、 客户的名称和顺序的总成本。 用户可以滚动浏览列表以查找订单，然后通过选择订单的箭头显示有关它的详细信息。 详细信息：[创建顺序库](northwind-orders-canvas-part1.md)。

### <a name="summary-form"></a>摘要窗体

在右上角中，窗体总结了用户选择顺序库中的顺序。 摘要包括很多相同的信息如库，而且摘要也显示创建顺序和付费，以及名称和托管订单的员工的图片时的日期。 用户可以更改窗体中的数据，保存这些更改、 取消它们，或通过选择标题栏右侧旁边的图标来删除订单。 详细信息：[创建摘要窗体](northwind-orders-canvas-part2.md)。

### <a name="detail-gallery"></a>详细信息库

在右下角中，另一个库将显示有关所选的订单包含哪些产品以及哪些数量中的信息。 此库中的每一项称为订单详细信息。 应用程序用户可以添加和使用控件中和其下删除库中的任何项。 详细信息：[创建详细信息库](northwind-orders-canvas-part3.md)。

> [!div class="mx-imgBorder"]
> ![屏幕区域的定义](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="explore-the-data-sources"></a>浏览数据源

若要创建此应用，将显示从五个实体和选项集的数据。 实际上，此应用程序的大多数区域显示多个实体中的数据。 例如，订单库包含此信息：

- 订单号是中的字段**订单**实体。
- 状态是中的另一个字段**订单**实体，则从选项**订单状态**选项集。
- 客户名称是中的字段**客户**实体。
- 根据中的数据来计算总成本**订单详细信息**实体。

摘要包含一些相同的信息的列表的订单，但它还包含姓名和托管订单的员工的照片。 从字段中提取信息**员工**实体。 详细信息库将显示中的记录**订单详细信息**实体，并且这些详细信息中的每个产品是中的记录**订购产品**实体。

## <a name="explore-the-relationships"></a>浏览的关系

可以在同一个库或窗体中显示来自不同源 （例如，实体） 的数据，因为这些实体具有在数据库中为你创建关系。

### <a name="many-to-one-relationships"></a>多对一的关系

例如，客户和每个订单的员工有关的信息位于**客户**并**员工**实体。 因此，**订单**实体具有与这些实体的多对一关系，因为有很多订单，其中每个可以只有一个客户和只能有一个员工管理。

每个订单还具有一个或多个行项表示包含订单的产品和数量。 每个行项是中的记录**订单详细信息**实体，并从每个产品的信息**订购产品**实体。 每个详细信息标识只能有一个产品，但每个产品可以出现在多个详细信息。 因此，**订单详细信息**实体具有多对一关系与**订购产品**实体。

### <a name="one-to-many-relationships"></a>一个对多关系

每个订单可以包含多个行项，但每个行项仅与一个订单相关。 因此，**订单**实体具有一个对多关系与**订单详细信息**实体。

### <a name="dot-notation-for-relationships"></a>点表示法的关系 

若要显示基于实体之间的关系数据，可以使用圆点属性选择器以从一个实体跨关系遍历到另一个。  例如，在每个记录**订单**实体中提取信息从**客户**实体以便顺序库可以显示客户名称。 在此库中，配置此行为通过设置**文本**此表达式将标签的属性：<br>`ThisItem.Customer.Company`

**ThisItem**指定在记录**订单**中的实体和提取信息**客户**有关该客户下订单的实体。 在这种情况下，该表达式指定出现在客户的公司名称。 但是，该客户的整个记录提取，因此可以轻松地显示，例如，该客户的电子邮件地址改为。

作为从一个实体到另一个引导另一个示例中，您可以指定库应在一个实体中基于用户在另一个库中选择和另一个实体中的记录显示记录。 若要显示的订单详细信息，请将设置详细信息库**项**属性设置为此表达式：<br>`Gallery1.Selected.'Order Details'`

在这种情况下， **Gallery1.Selected**指定中的记录**订单**实体，就像**ThisItem**未在前面的示例。 但是，此表达式不会提取只是一条记录，与上一个表达式。 相反，它提取整个表的记录，以显示每个产品的名称和每个单位成本 (中反映**订购产品**实体) 和数量 (具体体现在**订单详细信息**实体)。

## <a name="do-it-yourself"></a>就自己动手

可以按照分步说明来创建 Northwind 订单画布应用。  说明分为三个部分：

1. [创建顺序库](northwind-orders-canvas-part1.md)。
1. [创建摘要的窗体](northwind-orders-canvas-part2.md)。
1. [创建详细信息库](northwind-orders-canvas-part3.md)。

如果你想要跳过一些步骤，该解决方案包含用于每个部分的起始点应用程序。  在应用程序列表中，寻找**Northwind 订单 （画布）-第 1 部分开始**，依此类推。

> [!div class="nextstepaction"]
> [继续创建顺序库](northwind-orders-canvas-part1.md)
