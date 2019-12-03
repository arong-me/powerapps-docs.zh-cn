---
title: 连接到 Common Data Service |Microsoft Docs
description: 了解如何连接到 Common Data Service 并将其用于在 PowerApps 中生成应用程序。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: ''
ms.date: 04/22/2019
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: d9f6e973aa632fe0821db3bcc493174e250afa72
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74679905"
---
# <a name="connect-to-common-data-service"></a>连接到 Common Data Service

你可以在 Common Data Service 中安全地存储你的业务数据，并在 Power Apps 中构建丰富的应用程序，以便用户可以管理该数据。 你还可以将这些数据集成到包含来自 Dynamics 365 的电源自动、Power BI 和数据的解决方案中。

默认情况下，Common Data Service 连接器连接到应用的当前环境中的数据。 如果你的应用程序移动到另一个环境，则连接器将连接到新环境中的数据。 此行为适用于使用单个环境的应用或遵循 ALM 过程的应用，用于从开发迁移到生产。

使用 Common Data Service 连接器添加数据源时，可以更改环境，然后选择一个或多个实体。 默认情况下，该应用程序连接到当前环境中的数据，UI 将在实体列表中显示 " **（当前）** "。

> [!div class="mx-imgBorder"]
> ![默认环境](media/connection-common-data-service/common-data-service-connection-change-environment.png)

如果选择 "**更改**"，则可以指定不同的环境从该环境中提取数据，而不是使用当前环境。

> [!div class="mx-imgBorder"]
> ![其他环境](media/connection-common-data-service/common-data-service-connection-select-environment.png)

所选环境的名称将显示在 "搜索" 框下。

> [!div class="mx-imgBorder"]
> ![新环境](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

Common Data Service 连接器比 Dynamics 365 连接器和接近的特征奇偶校验更可靠。

详细信息：[什么是 Common Data Service？](../../common-data-service/data-platform-intro.md)
