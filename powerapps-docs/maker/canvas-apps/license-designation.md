---
title: 应用的许可证指定 |Microsoft Docs
description: 说明如何检查选定应用的许可证指定
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 03/24/2020
ms.author: alaug
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 95478501e6ca5af36ef993637b3612cdf1ea0196
ms.sourcegitcommit: 77e00640a59a7db9d67d3ac52f74d264cbe3a494
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2020
ms.locfileid: "80328769"
---
# <a name="how-to-check-license-designation-for-an-app"></a>如何检查应用的许可证指定

从10月2019开始，多个连接器从标准重新分类为高级。

[Power Apps 许可常见问题](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#office-365) 概述重新分类的连接器。 重新分类之前使用这些连接器的应用已被授予延长时间范围，允许没有高级版许可证的用户访问这些应用。

下表概述了这些标识以及最终用户访问应用时必须具有的许可证。

| **指** | **定义**
|-|-|
| 标准 | 仅使用标准连接器的应用。 最终用户必须具有适用于 Office 365 计划、每个应用计划或每个用户计划的 Power Apps 才能访问此应用。
| 扩展 | 允许在2019年10月1日使用升级到高级版连接器的应用。 最终用户必须具有适用于 Office 365 计划、按应用计划或按用户计划的 Power Apps。 [Power Apps 许可常见问题](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#office-365) 概述了2019年10月1日升级到高级版的连接器。
| 高级 | 至少使用一个高级连接器的应用。 最终用户必须具有每个应用计划或每个用户计划才能访问。

## <a name="check-app-license-designation-from-app-settings"></a>检查应用设置中的应用许可证指定

1. 登录到 [Power Apps](https://make.powerapps.com)。

1. 选择左侧的 "**应用**"。

1. 从应用列表中选择应用。 您可以使用 top 或的 "**设置**" 选项，然后使用下拉菜单中的 "**更多命令**（**...**）" 和 "**设置**"：

    ![Settings 选项](media/license-designation/app-settings.png)

1. 选择 "**设置**" 以查看许可证指定信息：

    ![设置中的许可证指定](media/license-designation/settings-license-designation.png)

## <a name="check-app-license-designation-from-app-details"></a>检查应用详细信息中的应用许可证指定

1. 登录到 [Power Apps](https://make.powerapps.com)。

1. 选择左侧的 "**应用**"。

1. 从应用列表中选择应用。 您可以使用 top 或的 "**详细信息**" 选项，然后使用下拉菜单中的 "**更多命令**（**...**）"，然后选择**详细信息**：

    ![应用详细信息](media/license-designation/app-details.png)

1. 选择**详细信息**：

    ![详细信息中的应用指定](media/license-designation/app-details-page.png)

## <a name="pass-assignment"></a>传递分配

有关传递分配的详细信息，请参阅[每个应用计划的 Power Apps](https://docs.microsoft.com/power-platform/admin/about-powerapps-perapp#step-three-set-up-apps-to-use-per-app-plans)。

## <a name="next-steps"></a>后续步骤

- [Power Apps 许可常见问题](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq)

### <a name="see-also"></a>另请参阅

- [编辑应用](edit-app.md)
- [删除应用](delete-app.md)
