---
title: 将报告功能添加到模型驱动应用
ms.custom: ''
ms.date: 08/16/2019
ms.reviewer: ''
ms.service: powerapps
ms.topic: article
author: Mattp123
ms.assetid: b4098c96-bce1-4f57-804f-8694e6254e81
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: aba6196680d674b8ee42096e340a105b19ac8d07
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2752324"
---
# <a name="add-reporting-features-to-your-model-driven-app"></a>将报告功能添加到模型驱动应用

PowerApps 应用可以包含可以为用户提供有用业务信息的报表。 这些报表基于 SQL Server Reporting Services，并且提供典型的 SQL Server Reporting Services 报表提供的相同功能集。

> [!div class="mx-imgBorder"] 
> ![](media/progress-against-goals-report.png "Progress against goals standard report")

系统报表可供所有用户使用。 创建或拥有报表的单个用户既可以将它们与特定的同事或团队共享，也可以将它们提供给组织，供所有用户运行。 这些报表使用 Common Data Service 专有的 FetchXML 查询并检索数据来生成报表。 您在 PowerApps 应用中创建的报表是基于 Fetch 的报表。

> [!NOTE]
> 报表功能不能操作在移动设备上运行的区域应用和模型驱动应用，如平板电脑和手机。 

<!-- Reports can be built in either of the following ways.

- From a model-driven app using the report wizard. More information: [Create or edit a report using the Report Wizard](/dynamics365/customer-engagement/basics/create-edit-copy-report-wizard) 
- Create custom reports using SQL Server Data Tools and Report Authoring Extensions. More information: [Reporting and Analytics Guide](/dynamics365/customer-engagement/analytics/reporting-analytics-with-dynamics-365)  -->


## <a name="add-reporting-to-a-unified-interface-app"></a>向统一接口应用添加报告
您可以将基于 Fetch 的报告功能添加到您的应用，以便用户能够运行、共享、创建和编辑报表。 为此，需要将报表实体添加到您的应用的站点地图。 

1. 登录 [PowerApps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 并打开现有应用进行编辑。 
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
> ![](media/report-feature-in-app.png "Report view")

## <a name="options-for-creating-new-reports"></a>新建报表所用的选项
您可以通过两种方式之一创建新报表：
- 使用“报表向导”。 打开已启用报告功能的模型驱动应用，然后运行“报表向导”以创建新报表。 报表向导可以创建表和图表报表，包括钻取报表和前 N 个报表。 详细信息：[使用“报表向导”创建报表](../../user/create-report-with-wizard.md) 
- 使用 Report Authoring Extension。 您可以使用 Visual Studio、SQL Server Data Tools 和 Report Authoring Extension 来编写新的或自定义现有的基于 Fetch 的 Reporting Services 报表。 详细信息：[使用 SQL Server Data Tools 新建报表](/dynamics365/customer-engagement/analytics/create-a-new-report-using-sql-server-data-tools)

## <a name="report-visibility"></a>报表可见性
标准实体报表（例如客户实体的“客户摘要”报表）可供所有应用用户使用。 负责报表的用户可以与特定的同事或团队共享它们。 系统管理员和系统定制员可以使报表具有组织范围内的可见性，以便所有用户都可以使用它们。 有关如何共享报表的信息，请参阅[与其他用户和团队共享报表](../../user/work-with-reports.md#share-a-report-with-other-users-or-teams)。 

## <a name="reports-in-solutions"></a>解决方案中的报表
报表可识别解决方案。 如果将报表作为组件添加到解决方案，则可使其成为一套单独的软件，可用于扩展 PowerApps 功能和用户界面。 唯有对组织可见的报表才能添加到解决方案中。

若要验证某个报表可否可被组织查看：在报表列表中，打开一个模型驱动应用，选择报表，然后选择**编辑**。 在**管理**选项卡上，查看是否将**查看者**设置为**组织**。 

> [!div class="mx-imgBorder"] 
> ![](media/report-scope.png "Organization level report visibility")

您可以将报表快照作为解决方案的一部分进行添加、导入或导出。 在模型驱动应用中，报表、子报表、报表类别、报表显示区域和报表相关记录类型都会被视为报表集的组件。 在非覆盖模式下导入解决方案更新时，如果已自定义报表集的任何组件，则会忽略对报表做出的任何解决方案更新。

## <a name="related-topics"></a>相关主题
[使用报表](/powerapps/user/work-with-reports)<br/>
[使用报表向导创建报表](/powerapps/user/create-report-with-wizard)<br/>
[从 PowerApps 外部添加报表](/powerapps/user/add-existing-report)<br/>
[编辑报表的默认筛选器](/powerapps/user/edit-report-filter)<br/>
[对报表进行故障排除](/powerapps/user/troubleshoot-reports)
