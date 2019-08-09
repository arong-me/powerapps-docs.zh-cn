---
title: 将报告添加到模型驱动的应用
ms.custom: ''
ms.date: 06/24/2019
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
  - Dynamics 365 (online)
  - Dynamics 365 Version 9.x
  - PowerApps
author: Mattp123
ms.assetid: b4098c96-bce1-4f57-804f-8694e6254e81
caps.latest.revision: 15
ms.author: matp
manager: kvivek
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---
# <a name="add-reporting-to-your-model-driven-app"></a>将报告添加到模型驱动的应用

PowerApps 应用可能包含可以为用户提供有用业务信息的报表。 这些报表基于 SQL Server Reporting Services，并且提供典型的 SQL Server Reporting Services 报表提供的相同功能集。

> [!div class="mx-imgBorder"] 
> ![](media/progress-against-goals-report.png "“目标进度”标准报表")

系统报表可供所有用户使用。 创建或拥有报表的单个用户既可以将它们与特定的同事或团队共享，也可以将它们提供给组织，供所有用户运行。 这些报表使用 Common Data Service 和 Dynamics 365 for Customer Engagement 应用专用的 FetchXML 查询并检索数据来生成报表。 您在 PowerApps 应用中创建的报表是基于 Fetch 的报表。

> [!NOTE]
> 报表功能不能操作在移动设备上运行的区域应用和模型驱动应用，如平板电脑和手机。 

报表可以采用以下方式之一生成。

- 从模型驱动应用使用报表向导。 详细信息：[使用报表向导创建或编辑报表](/dynamics365/customer-engagement/basics/create-edit-copy-report-wizard) 
<!-- From a model-driven app using an advanced find query. To do this, you build an advanced find query and then select **Download as FetchXML**. Next, from the reports area select **New**, for **Report Type** select **Existing File**, select **Choose File** open the xml file, fill in the required fields, and save the report. More information: [Add a report](/dynamics365/customer-engagement/basics/add-existing-report) -->
- 使用 SQL Server Data Tools 和报表创作扩展创建自定义报表。 详细信息：[报告和分析指南](/dynamics365/customer-engagement/analytics/reporting-analytics-with-dynamics-365)


## <a name="add-reporting-to-a-unified-interface-app"></a>向统一接口应用添加报告
您可以将基于 Fetch 的报告功能添加到您的应用，以便用户能够运行、共享、创建和编辑报表。 为此，需要将报表实体添加到您的应用的站点地图。 

1. 登录 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 并打开现有应用进行编辑。 
2. 在应用程序设计器中，选择**站点地图**旁边的![用于编辑站点地图的铅笔图标](media/ccf-pencil-icon.png)。 
3. 在站点地图设计器中，选择**添加**，然后选择**区域**。 
4. 在**标题**框中，为区域标题输入一个名称，如 *Reports*。 
5. 选择您在上一个步骤命名的区域，选择**添加**，选择**组**，然后在组**标题**框中，为组标题输入一个名称，如 *Reports*。 
6. 选择您在上一个步骤命名的组，选择**添加**，选择**子区域**，然后加入以下属性： 

   - **类型**。 选择**实体**。
   - **实体**。 在实体列表中，选择**报表**实体。  
   - **标题**。 输入描述性标题，如 *Reports*。

      ![将报表实体添加到站点地图](media/report-entity-sitemap.png)

7. 选择**保存并关闭**返回应用程序设计器。 


8. 在应用程序设计器中，选择**保存**，然后选择**发布**。


现在，应用将显示**报表**区域，用户可以在这个区域查看、运行、分派、共享和编辑其有权限的报表，并有权使用使用报表向导创建新报表。 

> [!div class="mx-imgBorder"] 
> ![](media/report-feature-in-app.png "报表视图")

### <a name="see-also"></a>另请参阅
[运行报表](/dynamics365/customer-engagement/basics/run-report)
