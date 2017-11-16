---
title: "创建列表以便将 SharePoint Online 与 PowerApps、Microsoft Flow 和 Power BI 集成 | Microsoft 文档"
description: "在此任务中，我们将创建 SharePoint 列表，以用作应用、流、报表和仪表板的数据源。"
services: 
suite: powerapps
documentationcenter: na
author: mgblythe
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 06/12/2017
ms.author: mblythe
ms.openlocfilehash: 35c6e2b7ddadc0ff907ce34986accdd11a794dd4
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="set-up-lists-for-sharepoint-online-integration-with-powerapps-microsoft-flow-and-power-bi"></a>创建列表以便将 SharePoint Online 与 PowerApps、Microsoft Flow 和 Power BI 集成
注意：本文属于将 PowerApps、Microsoft Flow 和 Power BI 与 SharePoint Online 结合使用的系列教程。 请确保已阅读[系列介绍](sharepoint-scenario-intro.md)，了解总体情况以及相关下载内容。

SharePoint 具有大量共享和协作功能，但对于此方案，我们将重点关注其中一种功能，即 [SharePoint 列表](https://support.office.com/article/Introduction-to-lists-0A1C3ACE-DEF0-44AF-B225-CFA8D92C52D7)。 列表就是一系列可以与团队成员和其他网站用户共享的数据。 我们将回顾一下用于此方案的列表，以便你可以在自己的 SharePoint Online 网站中创建列表。

## <a name="step-1-understand-the-lists"></a>第 1 步：了解列表
第一个列表是便于项目申请者添加申请的“项目申请”列表。 然后，项目审批者可以审查申请，并决定是批准还是拒绝。

| **列表列** | **数据类型** | **备注** |
| --- | --- | --- |
| 标题 |单行文本 |默认列，用于项目名称 |
| 说明 |单行文本 | |
| ProjectType |单行文本 |值：new hardware、upgraded hardware、new software、upgraded software |
| RequestDate |Date | |
| Requestor |单行文本 | |
| EstimatedDays |Number |将申请者的预计天数与项目经理的预计天数以及实际天数进行比较 |
| Approved |单行文本 |值：pending、yes、no |

注意：我们还使用“ID”列，此列由 SharePoint 生成，并且默认隐藏。 为简单起见，我们使用基本的数据类型，但实际应用可能会使用更为复杂的类型，如“Requestor”列的“Person or Group”类型。 若要了解 PowerApps 支持的数据类型，请参阅[从 Microsoft PowerApps 到 SharePoint 的连接](https://powerapps.microsoft.com/tutorials/connection-sharepoint-online/#known-issues)。

第二个列表是“项目详细信息”列表，用于跟踪所有已获准项目的详细信息，如已分配的项目经理。

| **列表列** | **数据类型** | **备注** |
| --- | --- | --- |
| 标题 |单行文本 |默认列，用于项目名称 |
| RequestID |Number |与“项目申请”列表中“ID”列的值一致 |
| ApprovedDate |Date | |
| 状态 |单行文本 |值：not started、in progress、completed |
| ProjectedStartDate |Date |项目经理预计的项目开始时间 |
| ProjectedEndDate |Date |项目经理预计的项目结束时间 |
| ProjectedDays |Number |工作天数；通常会进行计算，但此方案例外 |
| ActualDays |Number |对于已完成的项目 |
| PMAssigned |单行文本 |项目经理 |

## <a name="step-2-create-and-review-the-lists"></a>第 2 步：创建并检查列表
若要继续完成此方案，需要创建两个 SharePoint 列表，并在其中填充示例数据。 为此，我们将介绍如何创建列表，并在其中粘贴示例数据。 请确保已从[下载包](https://aka.ms/o4ia0f)获取 Excel 文件。

注意：在这一步中，使用 Internet Explorer。

### <a name="create-the-lists"></a>创建列表
1. 在 Internet Explorer 中，依次单击或点击 SharePoint 网站上的“新建”和“列表”。
   
    ![新建 SharePoint 列表](./media/sharepoint-scenario-setup/01-01-01-new-list.png)
2. 输入名称“项目申请”，再单击或点击“创建”。
   
    ![指定新列表的名称](./media/sharepoint-scenario-setup/01-01-02-create-list.png)
   
    此时，将创建“项目申请”列表，其中包含默认“Title”字段。
   
    ![“项目申请”列表](./media/sharepoint-scenario-setup/01-01-03-initial-list.png)

### <a name="add-columns-to-the-list"></a>向列表添加列
1. 依次单击或点击 ![“新建项”图标](./media/sharepoint-scenario-setup/icon-new.png) 和“单行文本”。
   
    ![添加单行文本字段](./media/sharepoint-scenario-setup/01-01-04-add-column.png)
2. 输入名称“Description”，再单击或点击“创建”。
   
    ![创建“Description”列](./media/sharepoint-scenario-setup/01-01-05-description-column.png)
3. 对列表中的其他列重复执行第 1 步 和第 2 步 ：
   
   1. “Single line of text”>“ProjectType”
   2. “Date”>“RequestDate”
   3. “Single line of text”>“Requestor”
   4. “Number”>“EstimatedDays”
   5. “Single line of text”>“Approved”

### <a name="copy-data-into-the-list"></a>将数据复制到列表中
1. 单击或点击“快速编辑”。
   
    ![适用于列表的“快速编辑”](./media/sharepoint-scenario-setup/01-01-06-quick-edit.png)
2. 选择网格中的单元格。
   
    ![包含所有列的列表](./media/sharepoint-scenario-setup/01-01-07-empty-grid.png)
3. 打开 project-requests.xlsx 工作簿，并选择所有数据（不含标题）。
   
    ![“项目申请”Excel 表](./media/sharepoint-scenario-setup/01-01-08-excel-table.png)
4. 将数据复制并粘贴到 SharePoint 内的网格中，再单击或点击“完成”。
   
    ![包含数据的已完成列表](./media/sharepoint-scenario-setup/01-01-09-full-grid.png)
5. 使用 project-details.xlsx 工作簿，对“项目详细信息”列表重复执行列表创建和复制过程。 请参阅[第 1 步：了解列表](#step-1-understand-the-lists)中的“项目详细信息”表，了解列名称和数据类型。

## <a name="step-3-update-connections-to-samples---optional"></a>第 3 步：为示例内容更新连接 - 可选
正如本系列教程简介部分中所述，我们在[下载包](https://aka.ms/o4ia0f)中添加了两个示例应用和一个报表。 可以在不使用这些示例的情况下完成此方案，但若要使用示例，必须更新与 SharePoint 列表的连接。 更新为使用你自己的列表（而不是我们的列表）作为数据源。

### <a name="update-connections-for-the-sample-apps"></a>为示例应用更新连接
1. 在 PowerApps Studio 中打开“project-management-app.msapp”。
2. 单击或点击“允许”，以便 PowerApps 可以使用 SharePoint。
3. 在功能区中的“视图”选项卡上，单击或点击“数据源”。
   
    ![PowerApps 数据源](./media/sharepoint-scenario-setup/01-03-01-data-sources.png)
4. 在右侧窗格中，依次单击或点击“项目详细信息”旁边的省略号 (...) 和“删除”。
   
    ![删除“项目详细信息”数据源](./media/sharepoint-scenario-setup/01-03-02-remove.png)
5. 在右侧窗格中，单击或点击“添加数据源”。
   
    ![添加数据源](./media/sharepoint-scenario-setup/01-03-03-add.png)
6. 单击或点击“新建连接”。
   
    ![新建连接](./media/sharepoint-scenario-setup/01-03-03a-new-connection.png)
7. 依次单击或点击“SharePoint”和“连接”。
   
    ![SharePoint 连接](./media/sharepoint-scenario-setup/01-03-03b-sharepoint.png)
8. 输入包含你创建的列表的 SharePoint Online 网站 URL，再单击或点击“前往”。
   
    ![SharePoint URL](./media/sharepoint-scenario-setup/01-03-03c-sharepoint-url.png)
9. 选择“项目详细信息”列表，再单击或点击“连接”。
   
    ![“项目详细信息”列表](./media/sharepoint-scenario-setup/01-03-03d-project-details.png)
   
    此时，右侧窗格中的“数据源”选项卡显示你创建的连接。
   
    ![数据源](./media/sharepoint-scenario-setup/01-03-03e-data-sources.png)
10. 在右侧窗格中，依次单击或点击“项目详细信息”旁边的省略号 (...) 和“刷新”。
    
    ![刷新“项目详细信息”数据源](./media/sharepoint-scenario-setup/01-03-02-remove.png)
11. 单击右上角的  ![“运行应用”图标](./media/sharepoint-scenario-setup/icon-run-arrow.png) ，以运行应用并确保连接能够正常工作。
12. 使用“项目申请”列表，对“project-requests-app.msapp”重复执行此部分中的步骤。

### <a name="update-connections-for-the-sample-report"></a>为示例报表更新连接
1. 在 Power BI Desktop 中打开“project-analysis.pbix”。
2. 在功能区的“开始”选项卡上，依次单击或点击“编辑查询”和“数据源设置”。
   
    ![编辑查询](./media/sharepoint-scenario-setup/01-03-04-edit-queries.png)
3. 单击或点击“更改源”。
   
    ![数据源设置](./media/sharepoint-scenario-setup/01-03-05-settings.png)
4. 输入你的 SharePoint Online 网站 URL，再单击或点击“确定”。
   
    ![SharePoint 列表 URL](./media/sharepoint-scenario-setup/01-03-06-list-url.png)
5. 此时，Power BI Desktop 在功能区下显示横幅，以便可以应用更改并导入新源中的数据。 单击或点击“应用更改”。
   
    ![应用查询更改](./media/sharepoint-scenario-setup/01-03-07-apply.png)
6. 使用组织帐户（用于访问 SharePoint Online 的帐户）登录，再单击或点击“连接”。
   
    ![连接 SharePoint Online](./media/sharepoint-scenario-setup/01-03-08-connect.png)

## <a name="next-steps"></a>后续步骤
本系列教程的下一步是[生成用于处理项目申请的应用](sharepoint-scenario-generate-app.md)。
