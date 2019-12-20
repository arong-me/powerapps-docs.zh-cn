---
title: 在 Power Platform 数据流中使用本地数据网关 | MicrosoftDocs
description: 了解如何在 Power Platform 数据流中使用本地数据网关
ms.custom: ''
ms.date: 08/05/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
caps.latest.revision: ''
ms.author: matp
manager: kvivek
tags: ''
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0b534e3c4a7aae36d38901b75b34cc87fd7f511e
ms.sourcegitcommit: 64d816a759c5cc6343928d56a673812c3ea066c2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/06/2019
ms.locfileid: "2895228"
---
# <a name="using-an-on-premises-data-gateway-in-power-platform-dataflows"></a>在 Power Platform 数据流中使用本地数据网关

可安装本地数据网关，以便在 Power Platform 数据流和非云中数据源（如本地 SQL Server 数据库或本地 SharePoint 站点）之间快速、安全地传输数据。
可查看您拥有其管理权限的所有网关，以及管理这些网关的权限和连接。

使用网关，可以通过以下连接连接到本地数据：

-   SharePoint

-   SQL Server

-   Oracle

-   Informix

-   Filesystem

-   DB2

## <a name="prerequisites"></a>必备条件

-   Power Apps 帐户。 还没有？ [注册 30 天的免费试用](https://docs.microsoft.com/powerapps/maker/signup-for-powerapps)。

-   网关的管理权限。 默认为您安装的网关提供这些权限。 管理员可以为其他人授予网关的权限。 

-   一份支持使用本地网关访问本地数据的许可证。 有关详细信息，请参阅[查找适合的 Power Apps 计划页](https://powerapps.microsoft.com/pricing/)中的“连接到数据和系统”部分。

-   只能在用户的默认环境中创建和使用网关和本地连接。 详细信息：[使用环境和 Microsoft Power Apps](../canvas-apps/working-with-environments.md)。

## <a name="install-a-gateway"></a>安装网关
1.  在 [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 的左侧导航窗格中，选择**网关**。

    ![左侧导航栏中的“网关”](media/nav-pane-gateways.png)

2.  从列表中选择一个网关。 如果您没有网关的管理权限，请选择[立即安装网关](https://go.microsoft.com/fwlink/?LinkID=820931)，然后按照向导中的提示操作。

     ![网关安装](media/install-gateway-now.png)

     有关如何安装网关的详细信息，请参阅[了解本地数据网关](../canvas-apps/gateway-reference.md)。

## <a name="use-an-on-premises-data-source-in-a-dataflow"></a>在数据流中使用本地数据源
1. 从数据源列表选择一个本地数据源。

   ![选择本地数据源](media/on-premises-data-sources.png)

2. 提供将用于访问本地数据的企业网关的连接详细信息。 必须选择网关本身，并提供所选网关的凭据。 只有您是其管理员的网关才会在列表中显示。

    ![提供连接详细信息](media/connection-creds.png)

可更改用于指定数据流的企业网关，也可以使用数据流制作工具更改为您的所有查询分配的网关。

> [!NOTE]
> 数据流将尝试使用新网关查找或创建所需数据源。 如果失败，则所选网关中提供需要的所有数据流之前，您不能更改网关。


## <a name="view-and-manage-gateway-permissions"></a>查看和管理网关权限
1.  在 [powerapps.com](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 的左侧导航窗格中，选择**网关**，然后选择所需网关。

2.  若要向网关添加用户，请选择**用户**，指定用户或组，然后指定权限级别：

    -   **可以使用**。 具有此权限的用户可以为网关创建要用于应用程序和流的连接，但是不能共享网关。 请将此选项用于要运行应用，但是不共享应用的用户。

    -   **可以使用 + 共享**。 具有此权限的用户可以为网关创建要用于应用程序和流的连接，并在共享应用程序时自动共享该网关。 请将此权限用于需要与其他用户或组织共享应用程序的用户。

    -   **管理员**。管理员拥有网关的完全控制权，包括添加用户，设置权限，创建与所有可用数据源之间的连接和删除网关。

      对于**可以使用**和**可以使用 + 共享**权限级别，选择用户可通过网关连接的数据源。

## <a name="view-and-manage-gateway-connections"></a>查看和管理网关连接
1.  在 *powerapps.com* 的左侧导航栏中，选择**网关**，然后选择所需网关。

2.  执行所需操作： 
    - 若要查看详细信息，编辑设置或删除网关，请选择**连接**，然后选择一个连接。
    - 若要共享连接，请选择**共享**，然后添加或删除用户。

      > [!NOTE]
      > 只能共享某些类型的连接，如 SQL Server 连接。 有关详细信息，请参阅[在 Power Apps 中共享区域应用程序资源](../canvas-apps/share-app-resources.md)。 <br />
      >
      > 有关如何管理连接的详细信息，请参阅[在 Power Apps 中管理区域应用程序连接](../canvas-apps/add-manage-connections.md)。


## <a name="limitations"></a>限制
使用企业网关和数据流时有一些已知限制。

-   每个数据流只能使用一个网关。 因此，应使用同一个网关配置所有查询。

-   更改网关会影响整个数据流。

-   如果需要多个网关，最好是构建多个数据流（每个网关一个），并使用计算或实体引用功能来统一数据。

-   只有在使用企业网关时才支持数据流。 不能在下拉列表和设置屏幕中选择个人网关。

有关网关问题故障诊断的信息，或有关为网络配置网关服务的信息，请参阅[了解本地数据网关](../canvas-apps/gateway-reference.md)。

## <a name="next-steps"></a>后续步骤

- [在 Power Apps 中创建和使用数据流](create-and-use-dataflows.md)

- [使用 Power Query 将数据添加到 Common Data Service 中的实体](data-platform-cds-newentity-pq.md)

- [连接 Azure Data Lake Storage Gen2 以存储数据流](/power-bi/service-dataflows-connect-azure-data-lake-storage-gen2)


