---
title: 连接到 Common Data Service |Microsoft Docs
description: 了解如何连接到 Common Data Service 并将其用于在 Power Apps 中构建应用。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 03/04/2020
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 227482b383acd3117cc78eddf97698ffa9146698
ms.sourcegitcommit: 56c8c7cc64695ccb00e0d021c9f98cf70b69b4a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78845161"
---
# <a name="connect-to-common-data-service"></a>连接到 Common Data Service

## <a name="overview"></a>概述

你可以在 Common Data Service 中安全地存储你的业务数据，并在 Power Apps 中构建丰富的应用程序，以便用户可以管理该数据。 你还可以将这些数据集成到包含来自 Dynamics 365 的电源自动、Power BI 和数据的解决方案中。

默认情况下，Common Data Service 连接器连接到应用的当前环境中的数据。 如果你的应用程序移动到另一个环境，则连接器将连接到新环境中的数据。 此行为适用于使用单个环境的应用或遵循 ALM 过程的应用，用于从开发迁移到生产。

使用 Common Data Service 连接器添加数据源时，可以更改环境，然后选择一个或多个实体。 默认情况下，应用程序连接到当前环境中的数据。

![默认环境](media/connection-common-data-service/common-data-service-connection-change-environment.png)

如果选择 "**更改**"，则可以指定不同的环境从该环境中提取数据，而不是使用当前环境。

![其他环境](media/connection-common-data-service/common-data-service-connection-select-environment.png)

所选环境的名称将显示在 "实体" 列表下。

![新环境](media/connection-common-data-service/common-data-service-connection-after-change-environment.png)

Common Data Service 连接器比 Dynamics 365 连接器和接近的特征奇偶校验更可靠。

### <a name="common-data-service-and-the-improved-data-source-experience"></a>Common Data Service 和改进的数据源体验

如果在2019年11月之前创建了一个带有 Common Data Service 连接器的画布应用，则可能没有 Common Data Service 的最新版本的权益。 有关更多详细信息以及升级连接，请阅读[Common Data Service 连接改进](../use-native-cds-connector.md)。