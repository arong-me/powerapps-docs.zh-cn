---
title: 排查报表中不显示数据的问题 | Microsoft Docs
description: 排查报表中不显示数据的问题
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 06/27/2019
ms.author: mkaur
ms.custom: ''
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 1156aa8fb5fbc3ae51c21b8aa41606df6dbc2e86
ms.sourcegitcommit: e9671e018c1ee4b640528915350a367758991b6a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67420757"
---
# <a name="troubleshoot-problems-with-data-not-displaying-in-a-report"></a>排查报表中不显示数据的问题

报表中不显示数据可能与以下原因有关：  
  
- **没有足够的安全权限**。 如果你无权在 Common Data Service 中查看记录，则报表中将不会显示该记录。  
  
- **未输入数据。** 输入数据的人员可能会将左侧字段留空。  
  
- **数据与报表的条件不匹配。** 许多报表都包含一个只显示活动记录的默认筛选器，或者你可能选择了不包含任何匹配记录的条件。 尝试更改报表筛选器。 有关详细信息，请参阅[编辑报表的默认筛选器](edit-report-filter.md)  
  
- **你可能正在查看报表的缓存副本。** 默认情况下，每次运行报表时，都会从数据库中提取 Common Data Service 报表中的数据。 但是，系统管理员可能已将报表更改为从缓存中运行。 如果报表中未包含最近输入的数据，则可能是缓存中的报表版本较旧。 要刷新报表，请在报表工具栏上，选择“刷新”  按钮。  
  
- **你可能无权读取子报表中的记录。** 如果你无权读取子报表中包含的记录类型，将收到一条错误消息，此消息表示无法显示子报表。  
  
- **Microsoft Internet Explorer 隐私设置可能会阻止所需的 cookie。** 对于图表报表，如果看到的是红色字母 X 而不是图表，则隐私设置可能会阻止图表控件所需的 cookie。 要解决此问题，请在浏览器中为运行 Reporting Services 的服务器启用 cookie。  
  

### <a name="see-also"></a>另请参阅
[处理报表](work-with-reports.md) 

[通过报表向导创建报表](create-report-with-wizard.md)

[添加现有报表](add-existing-report.md)

[编辑报表筛选器](edit-report-filter.md)

