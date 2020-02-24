---
title: 向门户内的网页添加 Power BI 报表或仪表板 | MicrosoftDocs
description: 有关向门户内的网页添加 Power BI 报表或仪表板的简介。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/22/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: babd35989529b66f0c32cdd6e61ba2ef77e8c601
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977609"
---
# <a name="add-a-power-bi-report-or-dashboard-to-a-web-page-in-portal"></a>向门户内的网页添加 Power BI 报表或仪表板

可通过使用 [powerbi](../liquid/portals-entity-tags.md#powerbi) Liquid 标记向门户内的网页添加 Power BI 报表或仪表板。 可在网页中的**复制**字段内或 Web 模板中的**源**字段内添加该标记。 如果添加在 Power BI 中的新工作区创建的 Power BI 报表或仪表板，您必须在 powerbi Liquid 标记中将身份验证类型指定为 **powerbiembedded**。

例如： 

```
{% powerbi authentication_type:"powerbiembedded" path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

> [!NOTE]
> 如果您已在 powerbi Liquid 标记中将 AAD 指定为身份验证类型，您必须在将安全的 Power BI 报表或仪表板添加到门户中的网页之前将它与所需用户共享。 更多信息：[共享 Power BI 工作区](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports#collaborate-with-coworkers-in-an-app-workspace)和[共享 Power BI 仪表板和报表](https://docs.microsoft.com/power-bi/service-share-dashboards)。

## <a name="get-the-path-of-a-dashboard-or-report"></a>获取仪表板或报表的路径

1.  登录到 [Power BI](https://powerbi.microsoft.com/)。

2.  打开要嵌入门户的仪表板或报表。

3.  从地址栏复制 URL。

    > [!div class=mx-imgBorder]
    > ![获取 Power BI 仪表板的路径](../media/powerbi-dashboard-url.png "获取 Power BI 仪表板的路径")

## <a name="get-the-id-of-a-dashboard-tile"></a>获取仪表板磁贴的 ID

1.  登录到 [Power BI](https://powerbi.microsoft.com/)。

2.  打开要从中将磁贴嵌入门户的仪表板。

3.  指向磁贴，选择**其他选项**，然后选择**在焦点模式下打开**。

    > [!div class=mx-imgBorder]
    > ![在焦点模式下打开 Power BI 仪表板磁贴](../media/powerbi-dashboard-tile-focus.png "在焦点模式下打开 Power BI 仪表板磁贴")

4.  从地址栏中的 URL 复制磁贴 ID。 磁贴 ID 是 /tiles/ 后的值。

    > [!div class=mx-imgBorder]
    > ![Power BI 仪表板磁贴 ID](../media/powerbi-dashboard-tile-id.png "Power BI 仪表板磁贴 ID")


### <a name="see-also"></a>另请参阅


[powerbi Liquid 标记](../liquid/portals-entity-tags.md#powerbi)<br> 
[设置 Power BI 集成](set-up-power-bi-integration.md)
