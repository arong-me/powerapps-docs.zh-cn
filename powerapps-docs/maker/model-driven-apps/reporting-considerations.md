---
title: 报告注意事项 | MicrosoftDocs
ms.custom: ''
ms.date: 09/27/2019
ms.reviewer: ''
ms.service: crm-online
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 for Customer Engagement (online)
- powerapps
ms.assetid: cb1bb002-8300-43bb-ab75-99e7a9c9c35d
caps.latest.revision: 11
author: Mattp123
ms.author: matp
manager: kvivek
tags:
- MigrationHO
search.audienceType:
- customizer
search.app:
- D365CE
ms.openlocfilehash: d3600ad3c1f0953ff3aef5786c62afebca43b4c4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755035"
---
# <a name="reporting-considerations"></a>报告注意事项

模型驱动应用程序具有很多允许客户显示业务数据的功能，可帮助客户推进决策过程，与其客户更有效地互动。  提供的功能包括视图、图表、仪表板和 SQL Server Reporting Services 报表。 并且包括允许用户使用 Power BI 功能 [PowerView](https://support.office.com/article/power-view-overview-and-learning-5380e429-3ee0-4be2-97b7-64d7930020b6)、[PowerPivot](https://support.office.com/article/power-pivot-overview-and-learning-f9001958-7901-4caa-ad80-028a6d2432ed) 和 [PowerQuery](https://support.office.com/article/power-query-overview-and-learning-ed614c81-4b00-4291-bd3a-55d80767f81d) 轻松构建自助报表的 Microsoft Excel 集成。 随着应用程序数据库中持有的数据量规模不断增长，考虑您的 BI 战略并确定最有效的报告和可视化大型数据集的机制变得空前重要。  
  
 在环境中，报告基础结构被共享，并与数据库相互分开。 在此架构下，虽然客户共享运行报表所需的资源，但每个报表根据客户的单个数据库实例运行。  此外，不论用户何时需要实现业务目标，都能够运行所需数量的报表。  我们不限制报表时间。  
  
 内置到 Common Data Service 报表功能旨在使用户能够运行跨度时间较短的数据集的报表。 鉴于此， 请注意以下固定设置：  
  
- 报表和查询最长执行五分钟。 达到最大期限时，报表将超时，并向用户返回消息。 在五分钟持续时间内，报表和查询允许跨 50,000 条记录以上的大型数据集，这提供了很大的灵活性，可以满足大多数运行报告的需求。  
  
- 若要改善查询响应，建议最大程度地减少详细报告显示的大量记录。 为此，应用相应筛选减少返回的记录数目。 在创建聚合或汇总报表时，查询应该将聚合推送到查询而不是 Fetch 详细记录以在报表中执行聚合。  这可以通过使用 Fetch XML 聚合来实现。 <!-- More information: [Use FetchXML aggregation](../developer/use-fetchxml-aggregation.md)  -->
  
- 对于在仪表板中显示的图表和网格， 您的应用允许用户运行数据集在 50,000 行以下的查询。 如果用户运行跨 50,000 或更多行数据集的仪表板查询，将返回消息“超出最大记录限制。 减少要同步的记录数”。  数据集的实际设置将帮助确保应用程序具有最佳性能。  
 
  
<a name="BKMK_ReportTips"></a>   
## <a name="tips-and-solutions-for-reporting"></a>报告相关建议和解决方案  
 通常，对于大多数组织的报告需求，这些设置已经足够。 一般来说，为了确保您的用户不超出这些设置，同时为改进报表查询性能，请考虑以下最佳实践。  
  
- 在创建自定义报表或仪表板时，可以将其设计为，通过在报表中添加基于时间的筛选器（例如当前月份或季度）限制结果查询来在更短的时段内查询更小的数据集。  
  
- 建议您限制返回结果所需的实体数。 这可帮助减少运行查询和返回结果集所需的时间。  
  
- 建议您减少在详细报表中显示的记录数。 适当筛选可用于减少查询返回的记录数量以减少超时。  
  
- 对于聚合或汇总报表，查询必须用于将聚合推送到数据库而不是 Fetch 详细记录，并在 SQL Server Reporting Services 报表中执行聚合。  
  
- 如果适合您的业务，用户应运行默认（现成）报表和仪表板。 这些报表和仪表板通常设计为每个用户数据集查询，那么在大多数情况下不会超出数据集限制。  
  
  如果用户必须运行超出这些设置的报表，建议您查看以下选项，获取可满足复杂报表需求的帮助。 通过使用数据集成解决方案，这两个选项有效地从 Common Data Service 将报告工作负载卸载到其他数据存储。  
  
- [适配器](reporting-considerations.md#BKMK_ThirdPartyAdapt)与 SQL Server Integration Services (SSIS) 结合用于扩展与您的应用程序数据集成的功能。  
  
- 提取转换加载 [(ETL) 工具](reporting-considerations.md#BKMK_ETL)为创建数据分析提供了一组新工具，方法是通过合并多个数据源，或在未使用 SSIS 的情况下将数据提取到数据仓库解决方案。 ETL 工具为连接 Common Data Service 以移动数据提供了综合的解决方案。  
  
> [!IMPORTANT]
>  在使用这些工具时，建议在非商业时间移动或同步数据。  
  
 如果需要，有许多 Microsoft 合作伙伴可针对您的特定报告需求提供解决方案，如创建专门用于运行大报表的数据的脱机副本。  这些合作伙伴熟知可用的数据集成工具。 详细信息：[查找 Dynamics 365 合作伙伴](https://dynamics.microsoft.com/partners/find-a-partner/)  
  
<a name="BKMK_ThirdPartyAdapt"></a>   
## <a name="third-party-adapters-for-ssis"></a>SSIS 第三方适配器  
  
-   [适用于 Dynamics 365/CRM 的 CozyRoc SSIS+ 组件](https://www.cozyroc.com/ssis/dynamics-crm)  
  
-   [适用于 Dynamics 365 的 KingswaySoft SSIS 集成工具包](https://www.kingswaysoft.com/products/ssis-integration-toolkit-for-microsoft-dynamics-365)  
  
-   [适用于 Dynamics 365 的 CData SSIS 组件](https://www.cdata.com/ssis/components/)  
  
-   [适用于 Dynamics 365 的 Team4 SSIS 连接器](https://www.team4.de/microsoft-dynamics-365-crm/)  
  
<!--    [PragmaticWorks TaskFactory SSIS Source/Destination for Dynamics CRM](https://pragmaticworks.com/Products/Task-Factory/Features/DynamicsCRMSource.aspx)  -->
  
<a name="BKMK_ETL"></a>   
## <a name="etl-tools"></a>ETL 工具  
  
-   [TIBCO Dynamics 365 集成](https://www.tibco.com/solutions/microsoft-dynamics-365-integration)  <br />
  
<!--   [Productivity tools from Informatica](https://community.informatica.com/community/search.jspa?peopleEnabled=true&userID=&containerType=14&container=2002&spotlight=true&resultTypes=solution&q=dynamics+CRM)  -->
  
### <a name="see-also"></a>另请参阅  
 [Report Authoring Extension（带 SQL Server Data Tools 支持）](https://www.microsoft.com/download/details.aspx?id=45013) <br />
  
 [Microsoft Power Query for Excel 简介](https://office.microsoft.com/en-ca/excel-help/introduction-to-microsoft-power-query-for-excel-HA104003940.aspx?CTT=5&origin=HA104003813)   <br />
 [Dynamics 365 for Customer Engagement OData Feeds 和 Power 查询：什么是 [记录]？](https://community.dynamics.com/crm/b/survivingcrm/archive/2014/02/16/dynamics-crm-odata-feeds-and-power-query-what-s-the-record.aspx)   <br />
 

