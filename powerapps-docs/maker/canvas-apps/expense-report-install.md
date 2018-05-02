---
title: 安装和配置支出报表 PowerApps 示例 | Microsoft Docs
description: 安装和配置支出报表 PowerApps 示例的分步说明。
services: ''
suite: powerapps
documentationcenter: na
author: caburk
manager: ''
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 04/08/2018
ms.author: caburk
ms.openlocfilehash: a63504b0438f50584da6739b9f397300e36d4ce6
ms.sourcegitcommit: 4710a56d308efe67fe60a7688143e61f5e5f2b44
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="install-and-configure-the-expense-report-powerapps-sample"></a>安装和配置支出报表 PowerApps 示例

安装和配置支出报表 PowerApps 示例的分步说明。

完成以下步骤的估计时间：10-15 分钟

如果希望查看此流程的演示，请观看此视频。

[![支出报表安装视频](./media/expense-report-install/expense-report-install-video.png)](https://youtu.be/DOR28V5kCkw)

## <a name="expense-report-powerapps-sample-overview"></a>支出报表 PowerApps 示例概述
跟踪费用报销单从提交到审批的整个过程。 将行项统计为应计个人支出，并在准备就绪后提交审批。 要拥有此应用，需完成少量设置。

![支出报表 PowerApp 的打开屏幕](./media/expense-report-install/expense-report-powerapp.png)

观看此视频，了解如何使用支出报表 PowerApp 示例。

[![支出报表安装视频](./media/expense-report-install/expense-report-demo-video.png)](https://youtu.be/h6E9cdrOvMU)

## <a name="prerequisites"></a>先决条件

- [注册](../signup-for-powerapps.md) PowerApps。

## <a name="create-the-expenses-sharepoint-list"></a>创建支出 SharePoint 列表

此列表存储支出报表。

1. 打开 Web 浏览器并导航到 https://portal.office.com。
2. 用具有列表创建权限的帐户登录。
3. 导航到支出列表要驻留的站点集合。
4. 单击网页右上角的齿轮图标。
5. 单击“添加应用”。
6. 在“查找应用”文本框中，输入“自定义”。
7. 单击搜索图标。
8. 单击“自定义列表”应用。
9. 在“名称”文本框中，输入“开支”。

    > [!IMPORTANT]
    > 如果为列表选择其他名称，请务必将其记下，因为需要将安装和配置流程期间出现的所有“支出”替换为此名称。

10. 单击“创建”。

### <a name="create-costcenter-column"></a>创建“成本中心”列

1. 单击“支出”列表。
2. 单击网页右上角的齿轮图标。
3. 选择“列表设置”。
4. 单击“创建列”。
5. 在“列名”文本框中，输入“成本中心”。
6. 在“此列中的信息类型为”单选按钮列表中，选择“选项”。
7. 在“在单独行上输入每个选项”文本框中，输入以下值，每个值单独占一行： 
    - Microsoft
    - Contoso
8. 在“默认值”文本框中，输入“Microsoft”。
9. 单击“确定”。

### <a name="create-comments-column"></a>创建“注释”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“注释”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“多行文本”。
4. 单击“确定”。

### <a name="create-status-column"></a>创建“状态”列

1. 单击“支出”列表。
2. 单击网页右上角的齿轮图标。
3. 选择“列表设置”。
4. 单击“创建列”。
5. 在“列名”文本框中，输入“状态”。
6. 在“此列中的信息类型为”单选按钮列表中，选择“选项”。
7. 在“在单独行上输入每个选项”文本框中，输入以下值，每个值单独占一行： 
    - 开放
    - Pending
    - Approved
8. 在“默认值”文本框中，输入“打开”。
9. 单击“确定”。

### <a name="create-approvername-column"></a>创建“审批者姓名”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“审批者姓名”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“用户或用户组”。
4. 在“要求此列包含信息”单选按钮列表中，选择“是”。
5. 单击“确定”。

### <a name="create-datesubmitted-column"></a>创建“提交日期”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“提交日期”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“日期和时间”。
4. 在“要求此列包含信息”单选按钮列表中，选择“是”。
5. 单击“确定”。

### <a name="create-startdate-column"></a>创建“开始日期”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“开始日期”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“日期和时间”。
4. 在“要求此列包含信息”单选按钮列表中，选择“是”。
5. 单击“确定”。

### <a name="create-enddate-column"></a>创建“结束日期”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“结束日期”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“日期和时间”。
4. 在“要求此列包含信息”单选按钮列表中，选择“是”。
5. 单击“确定”。

## <a name="create-the-line-items-sharepoint-list"></a>创建行项 SharePoint 列表

此列表存储与支出报表相关的行项。

1. 导航到创建了支出列表的站点集合。
2. 单击网页右上角的齿轮图标。
3. 单击“添加应用”。
4. 在“查找应用”文本框中，输入“自定义”。
5. 单击搜索图标。
6. 单击“自定义列表”应用。
7. 在“名称”文本框中，输入“行项”。

    > [!IMPORTANT] 
    > 如果为列表选择其他名称，请务必将其记下，因为需要将安装和配置流程期间出现的所有“支出”替换为此名称。

8. 单击“创建”。
 
### <a name="create-category-column"></a>创建“类别”列

1. 单击“行项”列表。
2. 单击网页右上角的齿轮图标。
3. 选择“列表设置”。
4. 单击“创建列”。
5. 在“列名”文本框中，输入“类别”。
6. 在“此列中的信息类型为”单选按钮列表中，选择“选项”。
7. 在“在单独行上输入每个选项”文本框中，输入以下值，每个值单独占一行： 
    - 食品和饮料
    - 运输
    - 业务需求
8. 在“默认值”文本框中，输入“食品和饮料”。
9. 单击“确定”。

### <a name="create-cost-column"></a>创建“成本”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“成本”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“数字 (1, 10, 100)”。
4. 在“要求此列包含信息”单选按钮列表中，选择“是”。
5. 单击“确定”。

### <a name="create-date-column"></a>创建“日期”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“日期”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“日期和时间”。
4. 在“要求此列包含信息”单选按钮列表中，选择“是”。
5. 单击“确定”。

### <a name="create-description-column"></a>创建“说明”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“说明”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“多行文本”。
4. 在“要求此列包含信息”单选按钮列表中，选择“是”。
5. 在“指定允许的文本类型”单选按钮列表中，选择“纯文本”。
6. 单击“确定”。

### <a name="create-reportid-column"></a>创建“报表 ID”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“报表 ID”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“查找 (此站点已存在的信息)”。
4. 在“要求此列包含信息”单选按钮列表中，选择“是”。
5. 在“信息获取位置”下拉列表中，选择创建的“支出”列表。
6. 在“在此列”下拉列表中，选择“ID”。
7. 单击“确定”。

### <a name="edit-title-column"></a>编辑“标题”列

1. 单击“标题”列链接。
2. 在“要求此列包含信息”单选按钮列表中，选择“否”。
3. 单击“确定”。

## <a name="download-the-expense-report-powerapp"></a>下载支出报表 PowerApp

1.  在 Web 浏览器中，导航到以下链接：

    http://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/myexpenses/docs/MyExpenses(SP_List).zip。

2.  下载支出报表 PowerApps 示例包，并将其保存到计算机。

## <a name="create-connections"></a>创建连接

1.  在 Web 浏览器中，导航到 https://web.powerapps.com。
2.  使用注册所用的同一凭据登录。
3.  在左侧菜单中，选择“连接”。

### <a name="create-approvals-connection"></a>创建“审批”连接

1.  单击“+ 新建连接”。
2.  在“搜索”文本框中，输入“审批”。
3.  从列表中选择“审批”。
4.  单击“创建”。
    
### <a name="create-office-365-outlook-connection"></a>创建 Office 365 Outlook 连接

1.  单击“+ 新建连接”。
2.  在“搜索”文本框中，输入“Office 365 Outlook”。
3.  从列表中选择“Office 365 Outlook”。
4.  单击“创建”。
5.  在弹出窗口中，选择登录所用的帐户。

### <a name="create-sharepoint-connection"></a>创建 SharePoint 连接

1.  单击“+ 新建连接”。
2.  在“搜索”文本框中，输入“Outlook”。
3.  从列表中选择“SharePoint”。
4.  单击“创建”。
5.  在弹出窗口中，选择登录所用的帐户。

## <a name="import-the-expense-report-powerapp"></a>导入支出报表 PowerApp

1.  在 Web 浏览器中，导航到 https://web.powerapps.com。
2.  使用注册所用的同一凭据登录。
3.  在左侧菜单中，选择“应用”。 
4.  单击“导入包(预览)”。
    
    ![“导入包”屏幕](./media/expense-report-install/import-package.png)

5.  单击“上传”按钮，选择前面步骤中下载的 PowerApp 包。
6.  对于“应用”和“流”资源类型，将“导入设置”设置为“新建”。
7.  对于“SharePoint”和“Outlook”连接，将“导入设置”设置为“在导入期间选择”。
    
    ![“导入设置”屏幕](./media/expense-report-install/import-settings.png)

8.  单击“SharePoint 连接”对应的“红色图标”。
9.  在连接列表中，单击带有用户名的项。

    ![“导入设置”屏幕](./media/expense-report-install/import-settings-sharepoint.png)

10. 单击“保存”。
11. 单击“SharePoint 连接”对应的“红色图标”。
12. 在连接列表中，单击带有用户名的项。

    ![“导入设置”屏幕](./media/expense-report-install/import-settings-approvals.png)

13.  单击“保存”。
14.  单击“Office 365 Outlook 连接”对应的“红色图标”。
15.  在连接列表中，单击带有用户名的项。

    ![“导入设置”屏幕](./media/expense-report-install/import-settings-office365outlook.png)

16. 单击“保存”。

    > [!TIP] 
    > 完成后，屏幕显示如下：

    ![“导入设置”屏幕](./media/expense-report-install/import-settings-done.png)

17. 单击“导入”并等待，直到流程完成。

    ![“导入设置”屏幕](./media/expense-report-install/import-done.png)

## <a name="configure-the-powerapp-to-use-the-sharepoint-lists"></a>配置 PowerApp 以使用 SharePoint 列表

1. 在 Web 浏览器中，单击“应用”。
2. 单击“支出报表 PowerApp”旁的省略号。
3. 单击“在 Web 上编辑”。
4. 单击“允许”。

### <a name="delete-connections"></a>删除连接
1. 单击“查看”。
2. 单击“数据源”。
3. 在“数据”窗格，单击“支出”旁的省略号。
4. 单击“删除”。
5. 在“数据”窗格中，单击“行项”旁的省略号。
6. 单击“删除”。

### <a name="expenses-list"></a>支出列表

1. 单击“查看”。
2. 单击“数据源”。
3. 在“数据”窗格中，单击“+ 添加数据源”。
4. 单击“+ 新建连接”。
5. 选择“SharePoint”。
6. 单击“创建”。
7. 在“最近使用的站点”列表中，选择在其中创建支出列表的 SharePoint 站点。

    > [!TIP] 
    > 如果列表中未显示此站点，请在文本框中输入该 SharePoint 站点的 URL，然后单击“前往”。

8. 在列表顶部的“搜索”文本框中，输入“支出”。
9. 选中“支出”列表旁的复选框。
10. 单击“连接”。

### <a name="lineitems-list"></a>行项列表

1. 单击“查看”。
2. 单击“数据源”。
3. 在“数据”窗格中，单击“+ 添加数据源”。
4. 单击“+ 新建连接”。
5. 选择“SharePoint”。
6. 单击“创建”。
7. 在“最近使用的站点”列表中，选择在其中创建行项列表的 SharePoint 站点。

    > [!TIP] 
    > 如果列表中未显示此站点，请在文本框中输入该 SharePoint 站点的 URL，然后单击“前往”。

8. 在列表顶部的“搜索”文本框中，输入“行项”。
9. 选中“行项”列表旁的复选框。
10. 单击“连接”。
11. 单击“文件”。
12. 单击“保存”。
13. 单击“发布”。
14. 单击“发布此版本”。

## <a name="modify-the-flow"></a>修改流

1.  在左侧菜单中，单击“流”。
2.  如果提示登录，请使用注册所用的同一凭据登录。
3.  从顶部菜单选择“我的流”。
4.  单击“审批支出”流旁的铅笔图标。
 
    ![“编辑流”屏幕](./media/expense-report-install/edit-flow.png)

5.  展开“获取项”操作。 
6.  更改“站点地址”和“列表名称”，使其与创建的支出 SharePoint 列表匹配。
    
    ![“编辑流”屏幕](./media/expense-report-install/edit-flow-getitems.png)

    > [!TIP] 
    > 无需手动键入，可从下拉列表选择。

7.  展开“条件”。
8.  展开“如果是”部分。
9.  展开“将项状态更改为‘已批准’”操作。
10. 更改“站点地址”和“列表名称”，使其与创建的支出 SharePoint 列表匹配。

    ![“编辑流”屏幕](./media/expense-report-install/edit-flow-condition-ifyes.png) 

    > [!TIP] 
    > 无需手动键入，可从下拉列表选择。

11. 展开“如果不是”部分。
12. 展开“将项状态更改为‘开放’”操作。
13. 更改“站点地址”和“列表名称”，使其与创建的支出 SharePoint 列表匹配。 

    ![“编辑流”屏幕](./media/expense-report-install/edit-flow-condition-ifno.png)

    > [!TIP] 
    > 无需手动键入，可从下拉列表选择。

14. 单击“更新流”。

## <a name="play-the-powerapp"></a>播放 PowerApp

1. 在 Web 浏览器中，单击“应用”。
2. 单击“支出报表 PowerApp”旁的省略号。
3. 单击“打开”。

观看此视频，了解如何使用支出报表 PowerApp 示例。

[![支出报表安装视频](./media/expense-report-install/expense-report-demo-video.png)](https://youtu.be/h6E9cdrOvMU)

##<a name="next-steps"></a>后续步骤
- [自定义 SharePoint 列表窗体](https://docs.microsoft.com/en-us/powerapps/maker/canvas-apps/customize-list-form)
- [添加并配置控件](https://docs.microsoft.com/en-us/powerapps/maker/canvas-apps/add-configure-controls)
- [编辑和管理 SharePoint 列表或库的权限](https://support.office.com/en-us/article/edit-and-manage-permissions-for-a-sharepoint-list-or-library-02d770f3-59eb-4910-a608-5f84cc297782)



