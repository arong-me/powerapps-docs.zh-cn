---
title: 管理画布应用的本地数据网关 | Microsoft Docs
description: 管理本地数据网关及其连接
author: arthiriyer
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 04/14/2020
ms.author: arthii
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 0956668fa3576dca58c728396d0c4c08473df73f
ms.sourcegitcommit: c0508e233a03ac4846c04d5caae79eccca3e2843
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385203"
---
# <a name="manage-an-on-premises-data-gateway-in-power-apps"></a>在 Power Apps 中管理本地数据网关

安装本地数据网关，以在 Power Apps 内置的画布应用和不在云中的数据源（例如本地 SQL Server 数据库或本地 SharePoint 站点）之间快速、安全地传输数据。 查看拥有管理权限的所有网关，并管理这些网关的权限和连接。

借助网关，可以通过这些连接来连接到本地数据：

* SharePoint
* SQL Server
* Oracle
* Informix
* Filesystem
* DB2

## <a name="prerequisites"></a>先决条件

* 用于[注册](../signup-for-powerapps.md)Power Apps 的用户名和密码。
* 网关的管理权限。 （安装每个网关时，用户默认获得这些权限，而其他网关的管理员也可以将其网关的这些权限授予用户。）
* 支持使用本地网关访问本地数据的许可证。 有关详细信息，请参阅[定价页](https://powerapps.microsoft.com/pricing/)的“连接性”部分。
* 网关和本地连接只能在用户的[默认环境](working-with-environments.md)中创建和使用。

## <a name="install-a-gateway"></a>安装网关

若要安装网关，请按照[安装本地数据网关](/data-integration/gateway/service-gateway-install)中的步骤进行操作。 在标准模式下安装网关，因为“本地数据网关（个人模式）”仅适用于 Power BI。

## <a name="view-and-manage-gateway-permissions"></a>查看和管理网关权限

1. 在 [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 的左侧导航栏中，依次单击或点击“**网关**”和一个网关。

2. 通过单击或点击“**用户**”，指定用户或组，然后指定权限级别来将用户添加到网关：

   * **可使用**：用户可以在网关上创建用于应用和流的连接，但不能共享网关。 对运行应用但不共享应用的用户使用此权限。
   * **可使用和共享**：用户可以在网关上创建用于应用和流的连接，并可在共享应用时自动共享网关。 对需要与其他用户或组织共享应用的用户使用此权限。
   * **管理员**：管理员可以完全控制网关，包括添加用户、设置权限、创建与所有可用数据源的连接和删除网关。

对于“可使用”和“可使用和共享”权限级别，请选择用户可以通过网关连接的数据源。

> [!NOTE]
> **可以使用**和**可以使用 + share**不适用于自定义连接器。

## <a name="view-and-manage-gateway-connections"></a>查看和管理网关连接

1. 在 [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 的左侧导航栏中，依次单击或点击“**网关**”和一个网关。

2. 依次单击或点击“连接”和一个连接，查看连接的详细信息、编辑设置或删除连接。

3. 要共享连接，请单击或点击“**共享**”，然后添加或删除用户。

    > [!NOTE]
   > 可以仅共享某些类型的连接（如 SQL Server）。 有关详细信息，请参阅 [共享应用资源](share-app-resources.md)。

若要详细了解如何管理连接，请参阅[管理连接](add-manage-connections.md)。

## <a name="troubleshooting-and-advanced-configuration"></a>疑难解答和高级配置

有关解决网关问题的详细信息，请参阅[对本地数据网关进行故障排除](/data-integration/gateway/service-gateway-tshoot)。 有关配置的详细信息，请参阅[使用本地数据网关应用](/data-integration/gateway/service-gateway-app)。

## <a name="next-steps"></a>后续步骤

* [安装本地数据网关](/data-integration/gateway/service-gateway-install)。
* 创建连接到本地数据源的应用，例如 [SQL Server](connections/connection-azure-sqldatabase.md) 或 [SharePoint](connections/connection-sharepoint-online.md)。
* [共享连接到本地数据源的应用](share-app.md)。
