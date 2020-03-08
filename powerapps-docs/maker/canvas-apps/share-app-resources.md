---
title: 共享画布应用中使用的资源 | Microsoft Docs
description: 了解如何共享 canvas 应用在 Power Apps 中使用的资源
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 02/03/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 77ccf02395c4d697a6d2054dd1a6dedda26d6e6e
ms.sourcegitcommit: 56c8c7cc64695ccb00e0d021c9f98cf70b69b4a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78845162"
---
# <a name="share-canvas-app-resources-in-power-apps"></a>共享画布-Power Apps 中的应用资源

[共享画布应用](share-app.md)前，先考虑应用依赖的资源类型，例如以下一个或多个资源类型：

* Common Data Service 中的实体

    有关向用户授予此数据访问权限的信息，请参阅[管理实体权限](share-app.md#manage-entity-permissions)。
    
* 到数据源的连接
* 本地数据网关
* 自定义连接器
* Excel 工作簿或其他服务
* 流

其中的某些资源会在共享应用时自动共享。 而其他资源需要你或与你共享应用的人执行额外操作，以使应用按预期的方式运行。

还可以与整个组织共享连接、自定义连接器和本地数据网关。

## <a name="connections"></a>连接

与其他用户共享应用时，某些连接（例如，通过 SQL 或 Windows 身份验证 SQL Server）会与应用进行[隐式共享](share-app-resources.md#implicit-sharing)。 其他连接要求用户创建自己的连接，并显式 grant security 权限（例如 Common Data Service、OneDrive for business 的安全角色、SQL Server 与 Azure AD 身份验证）。

当你与其他用户共享应用时，你可以确定是否自动将连接作为应用的一部分进行共享;允许您更新共享权限。 为此，请在 make.powerapps.com 中选择 "**数据**"，并从左侧导航 -> **连接**"。 然后选择所需的连接。 如果 "**共享**" 按钮出现在顶部导航栏上，或者如果选择 "*更多命令*（...）" 时显示 "**共享**" 选项，则所选连接可与其他用户共享。

  ![OneDrive for business 不共享](./media/share-app-resources/shared-connections-odb.png)

  ![与 SQL Server 共享 SQL 身份验证连接](./media/share-app-resources/shared-connections-sqlauth.png)

### <a name="implicit-sharing"></a>隐式共享

共享使用可共享的连接的应用时，应用连接会与应用一起**隐式共享**。 例如，当你跳到 make.powerapps.com，选择 "**应用**"，选择使用此连接的应用，选择 "*更多命令*（...）"，然后选择 "**共享**" 时，将显示以下消息：

  ![隐式权限警告](./media/share-app-resources/share-app-implicit-permission.png)

如果选择 "**确认**"，并与其他用户共享选定的应用，则应用连接将与应用一起隐式共享。

## <a name="on-premises-data-gateways"></a>本地数据网关
如果创建和共享的应用包含本地源的数据，则[本地数据网关](gateway-management.md)本身及该网关的某些类型的连接将自动共享。 对于任何没有自动共享的连接，可以手动将其共享（如之前部分所述），或让应用提示用户创建其自己的连接。 若要显示已配置网关的连接：

1. 打开 [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，在左侧导航栏中单击或点击“**管理**”，然后单击或点击“**网关**”。
2. 单击或点击一个网关，然后单击或点击“**连接**”选项卡。

> [!NOTE]
> 如果手动共享一个或多个连接，可能需要在下列情况下重新共享：

* 向已共享的应用添加本地数据网关。
* 更改与你共享应用（该应用具有本地数据网关）的用户或组的设置。

## <a name="custom-connectors"></a>自定义连接器
共享使用自定义连接器的应用时，自定义连接器会自动共享，但用户必须自行创建与它的连接。

在 [powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，可以查看或更新自定义连接器的权限。 在左侧导航栏中，依次单击或点击“**管理**”、“**连接**”、“**新建连接**”（位于右上角）。 依次单击或点击“自定义”和自定义连接器，查看它的详细信息。

## <a name="excel-workbooks"></a>Excel 工作簿
如果共享的应用所使用的数据并非所有用户都能访问（如云存储帐户中的 Excel 工作簿），则[共享数据](share-app-data.md)。

## <a name="flows"></a>流
如果共享包含流的应用，则系统将提示运行该应用的用户确认或更新流所依赖的任何连接。 此外，只有创建该流的用户能自定义其参数。 例如，可以创建一个向指定地址发送电子邮件的流，但其他用户不能更改该地址。

