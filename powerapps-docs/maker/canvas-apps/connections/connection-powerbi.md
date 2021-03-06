---
title: Power BI 连接概述 | Microsoft 文档
description: 参阅可用的 Power BI 连接
author: lancedMicrosoft
manager: kvivek
ms.service: powerapps
ms.topic: reference
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 10/12/2016
ms.author: lanced
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 40741bbaaba75f6cb1312057d5bba8c02ea15835
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74723618"
---
# <a name="connect-to-power-bi-from-power-apps"></a>从 Power Apps 连接到 Power BI
![Power BI](./media/connection-powerbi/powerbiicon.png)

Power BI 是一套用于分析数据和共享见解的业务分析工具。 通过每个设备上提供的丰富的仪表板来监视业务并快速获取答案。 可以在应用中检查在 Power BI 服务中设置的数据警报的状态。 有关 Power BI 中数据警报的详细信息，请转到[文档页](https://docs.microsoft.com/power-bi/service-set-data-alerts)。

本主题演示如何在应用中使用 Power BI 连接，并列出可用的函数。

## <a name="prerequisites"></a>必备组件
* [注册](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)
* 添加 Power BI [连接](https://powerapps.microsoft.com/tutorials/add-manage-connections/)
* 通过[模板](https://powerapps.microsoft.com/tutorials/get-started-test-drive/)、[数据](https://powerapps.microsoft.com/tutorials/get-started-create-from-data/)或[从头开始](https://powerapps.microsoft.com/tutorials/get-started-create-from-blank/)创建应用

## <a name="use-the-power-bi-connection-in-your-app"></a>在应用中使用 Power BI 连接
### <a name="list-the-alerts-that-youve-set-up-in-the-power-bi-service"></a>列出在 Power BI 服务中设置的警报
1. 在“**插入**”菜单上，选择“**库**”，并添加任意“**文本库**”。
2. 若要显示当前用户的警报，将库的 [Items](../controls/properties-core.md) 属性设置为以下公式：

   `PowerBI.GetAlerts()`

库中将会更新警报列表。 对于每条警报，都将收到警报的名称、警报的 ID 号，以及配置警报的组工作区的 ID。 通过警报 ID，可以获取有关该警报的更多信息。

### <a name="view-the-status-of-an-alert"></a>查看警报状态
若要查看警报状态，可使用从以上步骤获取的警报 ID 调用 CheckAlertStatus 函数。

可以将警报 ID 作为文本字符串（例如 "1234"）传递，也可以作为对使用 GetAlerts （）调用（例如 Gallery1.selected alertId）进行填充的库部分的引用。

若要继续，请添加一个标签，然后将[“Text”](../controls/properties-core.md)属性设置为以下公式之一：

* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).alertTitle`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).currentTileValue`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).alertThreshold`
* `PowerBI.CheckAlertStatus( /* alert ID that you received from GetAlert */ ).isAlertTriggered`

此时，标签会更新显示警报的当前状态。

## <a name="view-the-available-functions"></a>查看可用函数
此连接包括以下函数：

| 函数名称 | 描述 |
| --- | --- |
| GetAlerts |列出在 Power BI 服务中设置的警报 |
| CheckAlertStatus |检查特定警报的状态 |

## <a name="getalerts"></a>GetAlerts
列出在 Power BI 服务中设置的警报。

#### <a name="input-properties"></a>输入属性
无。

#### <a name="output-properties"></a>输出属性

| 属性名称 | 数据类型 | 需要 | 描述 |
| --- | --- | --- | --- |
| 值 |数组 |否 |在 Power BI 服务中设置的数据警报的数组。 每个数组中的元素将包括： <ul><li>alertTitle：警报的标题</li><li>alertId：警报的 ID</li><li>groupId：创建警报的组的 ID</li></ul> |

## <a name="checkalertstatus"></a>CheckAlertStatus
检查警报状态。

> [!NOTE]
> 如果调用过于频繁，将会在每次发出警报时限制对此终结点的请求。

#### <a name="input-properties"></a>输入属性

| 属性名称 | 数据类型 | 需要 | 描述 |
| --- | --- | --- | --- |
| alertId |整数 |是 |由 GetAlerts 返回的警报的 ID |

#### <a name="output-properties"></a>输出属性

| 属性名称 | 数据类型 | 需要 | 描述 |
| --- | --- | --- | --- |
| tileValue |number |否 |触发警报时的磁贴值 |
| tileUrl |字符串 |否 |具有警报的磁贴的 URL |
| alertTitle |字符串 |否 |警报名称 |
| isAlertTriggered |布尔值 |否 |当前是否触发了警报 |
| alertThreshold |number |否 |触发警报的阈值 |

## <a name="helpful-links"></a>有用链接
查看所有[可用连接](../connections-list.md)。  
了解如何向你的应用[添加连接](../add-manage-connections.md)。

