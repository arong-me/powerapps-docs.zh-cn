---
title: 在门户中将 Power BI 报表或仪表板添加到网页 |MicrosoftDocs
description: 说明如何将 Power BI 报表或仪表板添加到门户中的网页。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3735a0ef1a26fdd19b7bfb7f6db717cf9bd07861
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976153"
---
# <a name="add-a-power-bi-report-or-dashboard-to-a-web-page-in-portal"></a>将 Power BI 报表或仪表板添加到门户中的网页

您可以使用[powerbi](../liquid/portals-entity-tags.md#powerbi)液体标记将 Power BI 报表或仪表板添加到门户中的网页。 您可以在网页上的 "**复制**" 字段中或在 web 模板的 "**源**" 字段中添加标记。 如果添加在 Power BI 的新工作区中创建的 Power BI 报表或仪表板，则必须在 powerbi 液体标记中将身份验证类型指定为 powerbiembedded。

例如： 

```
{% powerbi path:"https://app.powerbi.com/groups/00000000-0000-0000-0000-000000000000/reports/00000000-0000-0000-0000-000000000001/ReportSection01" %}
```

> [!NOTE]
> 如果已指定 AAD 作为 powerbi 液体标记中的身份验证类型，则必须在将安全 Power BI 报表或仪表板添加到门户中的网页之前，将其与所需的用户共享。 详细信息：[共享 Power BI 工作区](https://docs.microsoft.com/power-bi/service-how-to-collaborate-distribute-dashboards-reports#collaborate-with-coworkers-in-an-app-workspace)并[共享 Power BI 仪表板和报表](https://docs.microsoft.com/power-bi/service-share-dashboards)。

## <a name="get-the-path-of-a-dashboard-or-report"></a>获取仪表板或报表的路径

1.  登录到[Power BI](https://powerbi.microsoft.com/)。

2.  打开要嵌入到门户中的仪表板或报表。

3.  从地址栏复制 URL。

    > [!div class=mx-imgBorder]
    > ![获取 Power BI 面板的路径](../media/powerbi-dashboard-url.png "获取 Power BI 仪表板的路径")

## <a name="get-the-id-of-a-dashboard-tile"></a>获取仪表板磁贴的 ID

1.  登录到[Power BI](https://powerbi.microsoft.com/)。

2.  打开要将磁贴嵌入门户的仪表板。

3.  指向磁贴，选择 "**更多选项**"，然后选择 "**以焦点模式打开**"。

    > [!div class=mx-imgBorder]
    > ![以焦点模式打开 Power BI 仪表板磁贴]在(../media/powerbi-dashboard-tile-focus.png "焦点模式下打开 Power BI 仪表板磁贴")

4.  从地址栏中的 URL 复制磁贴 ID。 磁贴 ID 是/tiles/. 之后的值。

    > [!div class=mx-imgBorder]
    > ![Power BI 仪表板磁贴 id](../media/powerbi-dashboard-tile-id.png "Power BI 仪表板磁贴 id")


### <a name="see-also"></a>另请参阅


[powerbi 液体标记](../liquid/portals-entity-tags.md#powerbi)<br> 
[设置 Power BI 集成](set-up-power-bi-integration.md)
