---
title: "共享应用中使用的资源 | Microsoft 文档"
description: "了解在共享应用时如何共享应用中使用的资源"
services: 
suite: powerapps
documentationcenter: na
author: archnair
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/28/2016
ms.author: archanan
ms.openlocfilehash: 75cd4137babde948ea70d8ee48a938c9acc092cc
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="share-app-resources"></a>共享应用资源
[共享应用](share-app.md)前，先考虑应用依赖的资源类型，如以下一个或多个资源类型：

* 到数据源的连接
* 本地数据网关
* 自定义连接器
* Excel 工作簿或其他服务
* 流

其中的某些资源会在共享应用时自动共享。 而其他资源需要你或与你共享应用的人执行额外操作，以使应用按预期的方式运行。

还可以与整个组织共享连接、自定义连接器和本地数据网关。

## <a name="connections"></a>连接
某些类型的连接（如 SQL Server）会自动共享，而其他类型的连接则需用户自行创建到应用中的数据源或源的连接。

在 [powerapps.com](https://web.powerapps.com) 上，可以确定某个连接是否会自动共享，并可更新共享权限。 在左侧导航栏中，依次单击或点击“**管理**”、“**连接**”，然后单击或点击一个连接。 如果出现“**共享**”选项卡，则连接将自动共享。

  ![连接详细信息页中的“共享”选项卡](./media/share-app-resources/shared-connections.png)

## <a name="on-premises-data-gateways"></a>本地数据网关
如果创建和共享的应用包含本地源的数据，则[本地数据网关](gateway-management.md)本身及该网关的某些类型的连接将自动共享。 对于任何没有自动共享的连接，可以手动将其共享（如之前部分所述），或让应用提示用户创建其自己的连接。 若要显示已配置网关的连接：

1. 打开 [powerapps.com](https://web.powerapps.com)，在左侧导航栏中单击或点击“**管理**”，然后单击或点击“**网关**”。
2. 单击或点击一个网关，然后单击或点击“**连接**”选项卡。

**注意**：如果手动共享了一个或多个连接，则需在下列情况下重新对其共享：

* 向已共享的应用添加本地数据网关。
* 更改与你共享应用（该应用具有本地数据网关）的用户或组的设置。

## <a name="custom-connectors"></a>自定义连接器
共享使用自定义连接器的应用时，自定义连接器会自动共享，但用户必须自行创建与它的连接。

在 [powerapps.com](https://web.powerapps.com) 上，可以查看或更新自定义连接器的权限。 在左侧导航栏中，依次单击或点击“**管理**”、“**连接**”、“**新建连接**”（位于右上角）。 依次单击或点击“自定义”和自定义连接器，查看它的详细信息。

## <a name="excel-workbooks"></a>Excel 工作簿
如果共享的应用所使用的数据并非所有用户都能访问（如云存储帐户中的 Excel 工作簿），则[共享数据](share-app-data.md)。

## <a name="flows"></a>流
如果共享包含流的应用，则系统将提示运行该应用的用户确认或更新流所依赖的任何连接。 此外，只有创建该流的用户能自定义其参数。 例如，可以创建一个向指定地址发送电子邮件的流，但其他用户不能更改该地址。

