---
title: Northwind 商贸的画布应用概述 |Microsoft Docs
description: ''
author: gregli-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/17/2019
ms.author: gregli
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 48966659ca12ada12448543492731fff8431fbde
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/23/2019
ms.locfileid: "71995800"
---
# <a name="overview-of-the-canvas-app-for-northwind-traders"></a>Northwind 商贸的画布应用概述

了解用于管理在您的[环境中安装](northwind-install.md)的 Northwind 商贸数据库中的关系数据的画布应用。 然后按照后续主题中的分步说明操作，从头开始构建此应用程序，从而获得使用关系数据的实践体验。

在本主题中，发现：

- 应用用户在应用中显示和管理关系数据的方式。
- 应用的数据驱动器类型。
- 如何创建这些数据类型之间的关系。

在单个屏幕中，应用用户可以显示、更新、创建和删除订单。

> [!div class="mx-imgBorder"]
> ![Complete 画布应用 ](media/northwind-orders-canvas-part1/orders-finished.png)

## <a name="explore-the-user-interface"></a>浏览用户界面

### <a name="order-gallery"></a>订单库

在应用程序的左边缘，库将显示订单列表，其中包括订单号、状态、客户的名称和订单的总成本。 用户可以滚动浏览列表以查找订单，然后通过选择订单箭头显示其详细信息。 详细信息：[创建订单库](northwind-orders-canvas-part1.md)。

### <a name="summary-form"></a>摘要窗体

在右上角，窗体汇总了用户在订单库中选择的顺序。 摘要包含的信息与库中的信息几乎相同，但该摘要还显示订单创建和支付的日期，以及管理订单的雇员的姓名和照片。 用户可以通过选择标题栏右边缘附近的图标来更改窗体中的数据、保存这些更改、取消这些更改或删除顺序。 详细信息：[创建摘要窗体](northwind-orders-canvas-part2.md)。

### <a name="detail-gallery"></a>详细信息库

在右下角，另一个库会显示有关所选订单中包含的产品及其数量的信息。 此库中的每一项称为订单详细信息。 应用程序用户可以通过使用中的控件或其下的控件，来添加和删除该库中的任何项。 详细信息：[创建详细信息库](northwind-orders-canvas-part3.md)。

> [!div class="mx-imgBorder"]
> 屏幕区域 ![Definition ](media/northwind-orders-canvas-part1/orders-parts.png)

## <a name="explore-the-data-sources"></a>浏览数据源

若要创建此应用，您将显示来自五个实体和一个选项集的数据。 事实上，此应用程序的大多数区域显示来自多个实体的数据。 例如，订单库包含以下信息：

- 订单号是 "**订单**" 实体中的字段。
- 状态是 "**订单**" 实体中的另一个字段，设置了**订单状态**选项中的一个选项。
- "**客户" 实体中**的 "客户名称" 字段。
- 总费用是根据 "**订单详细信息**" 实体中的数据计算的。

摘要包含与订单列表相同的信息，但它还包含管理订单的雇员的姓名和照片。 该信息从**Employees**实体中的字段提取。 详细信息库显示 "**订单详细信息**" 实体中的记录，并且这些详细信息中的每个产品都是 "**订单产品**" 实体中的一条记录。

## <a name="explore-the-relationships"></a>探索关系

您可以在同一个库或窗体中显示不同源（例如，实体）的数据，因为这些实体具有在数据库中为您创建的关系。

### <a name="many-to-one-relationships"></a>多对一关系

例如，有关客户和每个订单的雇员的信息驻留在 "**客户**和**员工**" 实体中。 因此，"**订单**" 实体对这些实体具有多对一关系，因为有多个订单，其中每个订单只能由一个客户放置，并且仅由一个员工管理。

每个订单还具有一个或多个表示订单包含的产品及其数量的行项。 每个行项是 "**订单详细信息**" 实体中的一条记录，它从 "**产品**" 实体中提取有关每个产品的信息。 每个详细信息只标识一个产品，但每个产品可以出现在多个详细信息中。 因此，"**订单详细信息**" 实体与 "**订单产品**" 实体具有多对一关系。

### <a name="one-to-many-relationships"></a>一对多关系

每个订单可包含多个行项，但每个行项仅与一个订单相关。 因此，"**订单**" 实体与 "**订单详细信息**" 实体具有一对多关系。

### <a name="dot-notation-for-relationships"></a>关系的点表示法 

若要根据实体之间的关系显示数据，可以使用点属性选择器跨一个实体之间的关系进行遍历。  例如，"**订单**" 实体中的每个记录将从**Customers**实体中提取信息，以便订单库可以显示客户名称。 在该库中，通过将标签的 " **Text** " 属性设置为此表达式来配置此行为：<br>`ThisItem.Customer.Company`

**ThisItem**指定 "**订单**" 实体中的一条记录，并从**Customers**实体拉取有关下订单的客户的信息。 在这种情况下，表达式指定显示客户的公司名称。 但是，该客户的整个记录会被拉取，因此，您可以轻松地显示该客户的电子邮件地址。

作为另一个示例，您可以根据用户在另一个库中选择的记录以及另一个实体中的记录，指定库应在一个实体中显示记录。 若要显示订单详细信息，请将详细信息库的**Items**属性设置为以下表达式：<br>`Gallery1.Selected.'Order Details'`

在这种情况下， **gallery1.selected**将在**Orders**实体中指定一条记录，**正如前面**的示例中所述。 但是，此表达式并不只提取一条记录，因为上一个表达式已执行。 相反，它将提取整个记录表，以显示每个产品的名称和每个单位的成本（按照**订单产品**实体的反映）和数量（反映在**order Details**实体中）。

## <a name="do-it-yourself"></a>自行完成

可以按照逐步说明创建 Northwind Orders 画布应用。  说明划分为三个部分：

1. [创建订单库](northwind-orders-canvas-part1.md)。
1. [创建摘要窗体](northwind-orders-canvas-part2.md)。
1. [创建详细信息库](northwind-orders-canvas-part3.md)。

如果要跳过，解决方案包含每个部件的启动点应用。  在应用列表中，查找 " **Northwind 订单（画布）-开始第1部分**" 等。

> [!div class="nextstepaction"]
> [继续创建订单库](northwind-orders-canvas-part1.md)
