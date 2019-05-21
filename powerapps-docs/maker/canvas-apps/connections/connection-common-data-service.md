---
title: 连接到 Common Data Service |Microsoft Docs
description: 了解如何连接到 Common Data Service，并将其用于在 PowerApps 中生成应用。
author: aftowen
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/22/2019
ms.author: anneta
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ede2736711fbb79250e1ca4b8e735f7fbd19b78d
ms.sourcegitcommit: be110258910aa097b0065da1ee4ea1c40b7e1334
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/20/2019
ms.locfileid: "65922485"
---
# <a name="connect-to-common-data-service"></a>连接到 Common Data Service

可以安全地将业务数据存储在 Common Data Service 并构建丰富的应用在 PowerApps 中，以便用户可以管理该数据。 您还可以将该数据集成到解决方案，其中包括 Microsoft Flow、 Power BI 和数据从 Dynamics 365。

默认情况下，Common Data Service 连接器连接到你的应用的当前环境中的数据。 如果您的应用程序移动到另一个环境，连接器将连接到新环境中的数据。 这适用于使用单一环境或遵循 ALM 过程将从开发移至测试到生产环境的应用的应用。

添加带有 Common Data Service 连接器的数据源时，您可以更改环境，然后选择一个或多个实体。  默认情况下，应用程序连接到当前环境中的数据和 UI 会显示 **（当前）** 对实体的列表。 如果选择**更改**，可以指定不同的环境将数据提取从它而非或除了当前环境。 

![通用数据服务更改环境](media/connection-common-data-service/common-data-service-connection-change-environment.png)

Common Data Service 连接器是比 Dynamics 365 连接器和接近功能奇偶校验更可靠。

详细信息：[什么是 Common Data Service？](../../common-data-service/data-platform-intro.md)
