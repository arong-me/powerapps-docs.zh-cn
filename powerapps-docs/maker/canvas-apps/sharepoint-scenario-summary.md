---
title: SharePoint Online 集成方案的端到端演练 | Microsoft 文档
description: 对我们在本系列教程中生成的方案进行端到端演练。
author: mgblythe
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 06/12/2017
ms.author: mblythe
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: df3c186bb41621e7ec6087a9da55fc037e286b1a
ms.sourcegitcommit: 429b83aaa5a91d5868e1fbc169bed1bac0c709ea
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/24/2018
ms.locfileid: "42850181"
---
# <a name="walk-end-to-end-through-the-completed-sharepoint-online-integration-scenario"></a>对完成的 SharePoint Online 集成方案进行端到端演练
> [!NOTE]
> 本文属于介绍如何将 PowerApps、Microsoft Flow 和 Power BI 与 SharePoint Online 结合使用的系列教程。 请确保已阅读[系列介绍](sharepoint-scenario-intro.md)，了解总体情况以及相关下载内容。

本系列教程涉及大量基础知识，包括生成画布应用和流、创建报表并将其嵌入 SharePoint 中等。 我们由衷希望你已学到很多知识，并且充分了解如何综合运用这些技术，以便可以根据自己的需求将画布应用、流和报表集成到 SharePoint 中。 最后，我们希望对此方案进行端到端演练，以展示各方面的工作是如何完美配合的。

## <a name="step-1-add-a-project-to-the-project-requests-list"></a>第 1 步：向“项目申请”列表添加项目
1. 在“项目申请”列表中，依次单击或点击“所有项”和“项目申请应用”。
   
    ![“项目申请应用”视图](./media/sharepoint-scenario-summary/09-00-01-view-app.png)
2. 单击“打开”，在新的浏览器标签页中打开应用。
   
    ![打开“项目申请应用”](./media/sharepoint-scenario-summary/09-00-02-open-app.png)
3. 在应用中，单击或点击  ![“添加项”图标](./media/sharepoint-scenario-summary/icon-add-item.png) ，创建新项。
4. 在表单中填写以下值：
   
   * “Title”的值为“Mobile devices for design team”

   * “Approved”的值为“Pending”

   * “Description”的值为“The design team will now use Contoso-supplied devices”

   * “EstimatedDays”的值为“30”

   * “ProjectType”的值为“New hardware”

   * “RequestDate”的值为“03/01/2017”

   * “Requestor”的值为“Emily Braun”
     
     ![“项目申请”编辑表单](./media/sharepoint-scenario-summary/09-01-01-app-new.png)
5. 单击或点击右上角的 ![复选标记图标](./media/sharepoint-scenario-summary/icon-check-mark.png)，再关闭浏览器标签页。
6. 返回到“项目申请”列表，依次单击或点击“项目申请应用”和“所有项”。
   
    ![查看所有项](./media/sharepoint-scenario-summary/09-01-01a-view-all.png)
7. 验证列表中的新条目。
   
    ![包含新条目的 SharePoint 列表](./media/sharepoint-scenario-summary/09-01-02-list-new.png)

## <a name="step-2-approve-the-project"></a>第 2 步：审批项目
1. 在第 1 步中添加项后，流应该会运行，并发出审批邮件。 检查审批者的电子邮件帐户的收件箱。
   
    ![“审批申请”电子邮件](./media/sharepoint-scenario-summary/09-02-01-allan-email.png)
2. 单击“批准”。 流运行另一进程，并直接在电子邮件中生成如下反馈。
   
    ![操作完成](./media/sharepoint-scenario-summary/09-02-01a-action-complete.png)
3. 检查申请者的电子邮件帐户的收件箱，应该会看到批准电子邮件。
   
    ![发送给申请者的批准电子邮件](./media/sharepoint-scenario-summary/09-02-02-megan-email.png)
4. 验证列表中更新的条目。
   
    ![条目已更新的 SharePoint 列表](./media/sharepoint-scenario-summary/09-02-03-yes.png)

## <a name="step-3-assign-a-manager-to-the-project"></a>第 3 步：向项目分配经理
1. 首先，我们将查看 SharePoint 中的“项目详细信息”列表。 新项目的“PMAssigned”列的值为“Unassigned”。
   
    ![未分配的 SharePoint 列表项](./media/sharepoint-scenario-summary/09-03-01-unassigned.png)
2. 在 SharePoint 网站的左侧导航窗格中，单击或点击“项目管理应用”。
3. 在第一屏上，单击或点击“分配经理”。
   
    ![向项目分配经理](./media/sharepoint-scenario-summary/09-03-02-intro-screen.png)
4. 在“分配经理”屏幕上，可以看到列表中的两个未分配项目。 选择“设计团队适用的移动设备”项目。
   
    ![应用中选定的未分配项目](./media/sharepoint-scenario-summary/09-03-03-selected.png)
5. 在“经理”文本输入框中，输入“Joni Sherman”，再单击“确定”。
   
    此更改已应用于列表，并且库会进行刷新，因此只会显示剩余未分配的项目。
   
    ![向项目分配的经理](./media/sharepoint-scenario-summary/09-03-04-updated.png)
6. 关闭应用，再返回到 SharePoint 列表。 可以看到，项目条目现已更新为包含项目经理姓名。
   
    ![已分配的 SharePoint 列表项](./media/sharepoint-scenario-summary/09-03-05-assigned.png)

## <a name="step-4-add-time-estimates-for-the-project"></a>第 4 步：添加项目估计时间
1. 单击或点击 ![“返回”图标](./media/sharepoint-scenario-summary/icon-back.png)，返回到第一屏，再单击或点击“更新详细信息”。
   
    ![更新项目详细信息](./media/sharepoint-scenario-summary/09-04-00-intro-screen.png)
2. 在“查看项目”屏幕上的搜索框中输入“移动”。
   
    ![在应用中搜索](./media/sharepoint-scenario-summary/09-04-01-search-mobile.png)
3. 单击“设计团队适用的移动设备”项的 ![“详细信息箭头”图标](./media/sharepoint-scenario-summary/icon-details-arrow.png)。
   
    ![选择要更新的项目](./media/sharepoint-scenario-summary/09-04-02-select-project.png)
4. 在“更新详细信息”屏幕上，设置以下值：
   
   * “Status”字段的值为“Not started”

   * “ProjectedStartDate”字段的值为“3/6/2017”

   * “ProjectedEndDate”字段的值为“3/24/2017”

   * “ProjectedDays”字段的值为“15”
     
     ![更新项目详细信息](./media/sharepoint-scenario-summary/09-04-03-update.png)
5. 单击或点击右上角的 ![复选标记图标](./media/sharepoint-scenario-summary/icon-check-mark.png) ，将更改应用于 SharePoint 列表。
6. 关闭应用，再返回到列表。 可以看到，项目条目现已更新为包含更改后的日期和天数。
   
   ![SharePoint 列表中更新的详细信息](./media/sharepoint-scenario-summary/09-04-04-updated-list.png)

## <a name="step-5-review-report-data-for-existing-projects"></a>第 5 步：查看现有项目的报表数据
1. 在 SharePoint Online 中，依次单击或点击“网站内容”和“网页”。
2. 打开我们之前创建的“项目分析”页。
   
    ![嵌入的项目分析报表](./media/sharepoint-scenario-summary/09-05-01-report-complete.png)
3. 查看显示差异的可视化效果。
   
    ![显示差异的图表](./media/sharepoint-scenario-summary/09-05-02-chart-variance.png)
   
    正如我们在创建此可视化效果时所指出的一样，Irvin Sayers 所负责项目的实际天数与预计天数差异比 Joni Sherman 多得多。
4. 向下钻取此可视化效果，可以看出，差异主要来自实际天数比预计多得多的两个项目。
   
    ![显示差异详细信息的图表](./media/sharepoint-scenario-summary/09-05-03-chart-variance-drill.png)
5. 查看显示项目获准日期与预计开始日期的时间跨度的表。
   
    ![显示开始日期差异的表](./media/sharepoint-scenario-summary/09-05-04-chart-diff-completed.png)
   
    正如我们在创建此可视化效果时所指出的一样，分配给 Irvin Sayers 的项目会延期启动，其中两个项目的延期启动时间跨度要比其他项目长得多。

## <a name="step-6-respond-to-pending-project-delays"></a>第 6 步：响应待审批项目延迟
1. 在 Power BI 服务中，依次单击或点击“project-analysis”数据集和“立即刷新”。 刷新操作会触发我们为待审批项目创建的警报。
   
    ![立即刷新数据集](./media/sharepoint-scenario-summary/09-06-01-refresh.png)
2. 刷新完成后，右上角的“通知中心”会显示“新通知”图标。
   
    ![Power BI 通知中心](./media/sharepoint-scenario-summary/09-06-02-alert.png)
   
    此图标可能需要一段时间才能显示。因此，如果没有立马看到它，请过一段时间再回来看看。
3. 打开“通知中心”，查看所触发警报的详细信息。
   
    ![数据警报通知](./media/sharepoint-scenario-summary/09-06-03-notification.png)
4. 检查警报创建者（在此示例中，为 Megan Bowen）的收件箱。
   
    ![来自 Power BI 的警报电子邮件](./media/sharepoint-scenario-summary/09-06-04-email-powerbi.png)
5. 检查在数据警报流中添加的人员（在此示例中，为 Allan DeYoung）的收件箱。
   
    ![来自 Microsoft Flow 的警报电子邮件](./media/sharepoint-scenario-summary/09-06-05-email-flow.png)
6. 至此，已获取待审批项目的相关信息，可以返回并审批所有待审批事项。

我们的端到端演练和本系列教程到此结束。 建议继续访问以下网站：

* [PowerApps](http://www.powerapps.com/)
* [Microsoft Flow](http://flow.microsoft.com)
* [Power BI](http://www.powerbi.com)
* [Power User 社区](https://powerusers.microsoft.com/)
* [SharePoint](http://sharepoint.microsoft.com)
* [Microsoft 技术社区](https://techcommunity.microsoft.com/)

若对本系列教程有任何反馈、补充内容建议，或希望了解其他内容以便使用我们介绍的技术，请通过评论的形式告知我们。

