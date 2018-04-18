---
title: 安装和配置技术支持 PowerApps 示例 | Microsoft Docs
description: 安装和配置技术支持 PowerApps 示例的分步说明。
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
ms.date: 02/20/2018
ms.author: caburk
ms.openlocfilehash: 97ff0c781933fa8d2896a35f0bd507bfb0b75ea9
ms.sourcegitcommit: eac8ad7b54a0b0eba6444a38a952dbfd17bc64b5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2018
---
# <a name="install-and-configure-the-help-desk-powerapps-sample"></a>安装和配置技术支持 PowerApps 示例

安装和配置技术支持 PowerApps 示例的分步说明。

完成以下步骤的估计时间：10-15 分钟

如果希望查看此流程的演示，请观看此视频。

[![技术支持安装视频](./media/help-desk-install/help-desk-install-video.png)](https://youtu.be/z4cdtD6hB_4 )

## <a name="help-desk-powerapps-sample-overview"></a>技术支持 PowerApps 示例概述
技术支持提供用户友好体验，方便最终用户与支持专业人员交流。 快速找到最重要问题的答案，跟踪开放票证的进度，并查看之前的请求的详细信息。 要拥有此应用，需完成少量设置。

![技术支持 PowerApp 的打开屏幕](./media/help-desk-install/Login-screen.png)

观看此视频，了解如何使用技术支持 PowerApp 示例。

[![技术支持演示视频](./media/help-desk-install/help-desk-demo-video.png)](https://youtu.be/sl5fXwwnvzI)

## <a name="prerequisites"></a>先决条件

- [注册](https://web.powerapps.com/) PowerApps。

## <a name="create-the-helpdesk-sharepoint-list"></a>创建技术支持 SharePoint 列表

此列表存储技术支持票证。

1. 打开 Web 浏览器并导航到 https://portal.office.com。
2. 用具有列表创建权限的帐户登录。
3. 导航到要在其中存放技术支持列表的站点集合。
4. 单击网页右上角的齿轮图标。
5. 单击“添加应用”。
6. 在“查找应用”文本框中，输入“自定义”。
7. 单击搜索图标。
8. 单击“自定义列表”应用。
9. 在“名称”文本框中，输入“技术支持”。

    > [!IMPORTANT]
    > 如果为列表选择其他名称，请务必将其记下，因为需要将安装和配置流程期间出现的所有“技术支持”替换为此名称。

10. 单击“创建”。

### <a name="create-description-column"></a>创建“说明”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“说明”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“多行文本”。
4. 在“要求此列包含信息”单选按钮列表中，选择“是”。
5. 在“指定允许的文本类型”单选按钮列表中，选择“纯文本”。
6. 单击“确定”。

### <a name="create-category-column"></a>创建“类别”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“类别”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“选项”。
4. 在“在单独行上输入每个选项”文本框中，输入以下值，每个值单独占一行： 
    - 笔记本电脑/电脑设备问题
    - 笔记本电脑/电脑软件问题
5. 在“强制使用唯一值”单选按钮列表中，选择“否”。
6. 在“选项显示方式”单选按钮列表中，选择“下拉菜单”。
7. 在“默认值”文本框中，输入“笔记本电脑/电脑设备问题”。
8. 单击“确定”。

### <a name="create--complete-column"></a>创建“完成百分比”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“完成百分比”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“数字 (1, 10, 100)”。
4. 在“要求此列包含信息”单选按钮列表中，选择“否”。
5. 单击“确定”。

### <a name="create-priority-column"></a>创建“优先级”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“优先级”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“选项”。
4. 在“在单独行上输入每个选项”文本框中，输入以下值，每个值单独占一行： 
    - 高
    - 中型
    - 低
5. 在“强制使用唯一值”单选按钮列表中，选择“否”。
6. 在“选项显示方式”单选按钮列表中，选择“下拉菜单”。
7. 在“默认值”文本框中，输入“低”。
8. 单击“确定”。

### <a name="create-taskstatus-column"></a>创建“任务状态”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“任务状态”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“选项”。
4. 在“在单独行上输入每个选项”文本框中，输入以下值，每个值单独占一行： 
    - 未启动
    - 进行中
    - 已完成
    - 已推迟
    - 等待 CSR
5. 在“强制使用唯一值”单选按钮列表中，选择“否”。
6. 在“选项显示方式”单选按钮列表中，选择“下拉菜单”。
7. 在“默认值”文本框中，输入“未启动”。
8. 单击“确定”。

### <a name="create-assignedto-column"></a>创建“分配对象”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“分配对象”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“用户或用户组”。
4. 在“要求此列包含信息”单选按钮列表中，选择“否”。
5. 在“允许多选”单选按钮列表中，选择“否”。
6. 单击“确定”。

### <a name="edit-title-column"></a>编辑“标题”列

1. 单击“标题”列链接。
2. 在“要求此列包含信息”单选按钮列表中，选择“否”。
3. 单击“确定”。

## <a name="download-the-help-desk-powerapp"></a>下载技术支持 PowerApp

1.  在 Web 浏览器中，导航到 http://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/helpdesk/docs/HelpDesk(SP_List).zip。
2.  下载 PowerApps 包并将其保存到计算机。

## <a name="create-connections"></a>创建连接

1.  在 Web 浏览器中，导航到 https://web.powerapps.com。
2.  使用注册所用的同一凭据登录。
3.  在左侧菜单中，选择“连接”。
    
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

### <a name="create-office-365-users-connection"></a>创建 Office 365 用户连接

1.  单击“+ 新建连接”。
2.  在“搜索”文本框中，输入“Office 365 用户”。
3.  从列表中选择“Office 365 用户”。
4.  单击“创建”。
5.  在弹出窗口中，选择登录所用的帐户。

## <a name="import-the-help-desk-powerapp"></a>导入技术支持 PowerApp

1.  在 Web 浏览器中，导航到 https://web.powerapps.com。
2.  使用注册所用的同一凭据登录。
3.  在左侧菜单中，选择“应用”。 
4.  单击“导入包(预览)”。
    
    ![“导入包”屏幕](./media/help-desk-install/import-package.png)

5.  单击“上传”按钮，选择前面步骤中下载的 PowerApp 包。
6.  对于“应用”和“流”资源类型，将“导入设置”设置为“新建”。
7.  对于“SharePoint”和“Outlook”连接，将“导入设置”设置为“在导入期间选择”。
    
    ![“导入设置”屏幕](./media/help-desk-install/import-settings.png)

8.  单击“SharePoint 连接”对应的“红色图标”。
9.  在连接列表中，单击带有用户名的项。

    ![“导入设置”屏幕](./media/help-desk-install/import-settings-sharepoint.png)

10. 单击“保存”。
11.  单击“Office 365 Outlook 连接”对应的“红色图标”。
12.  在连接列表中，单击带有用户名的项。

    ![“导入设置”屏幕](./media/help-desk-install/import-settings-office365outlook.png)

13. 单击“保存”。

    > [!TIP] 
    > 完成后，屏幕显示如下。

    ![“导入设置”屏幕](./media/help-desk-install/import-settings-done.png)

14. 单击“导入”并等待，直到流程完成。

    ![“导入设置”屏幕](./media/help-desk-install/import-done.png)

## <a name="configure-the-powerapp-to-use-the-sharepoint-list"></a>配置 PowerApp 以使用 SharePoint 列表

1. 在 Web 浏览器中，单击“应用”。
2. 单击“技术支持 PowerApp”旁的省略号。
3. 单击“在 Web 上编辑”。
4. 单击“允许”。

### <a name="delete-connections"></a>删除连接

1. 单击“查看”。
2. 单击“数据源”。
3. 在“数据”窗格，单击“技术支持”旁的省略号。
4. 单击“删除”。

### <a name="helpdesk-list"></a>技术支持列表

1. 单击“查看”。
2. 单击“数据源”。
3. 在“数据”窗格中，单击“+ 添加数据源”。
4. 选择“SharePoint”。
5. 单击“创建”。
6. 在“最近使用的站点”列表中，选择在其中创建技术支持列表的 SharePoint 站点。

    > [!TIP] 
    > 如果列表中未显示此站点，请在文本框中输入该 SharePoint 站点的 URL，然后单击“前往”。

7. 在列表顶部的“搜索”框中，输入“技术支持”。
8. 选中“技术支持”列表旁的复选框。
9. 单击“连接”。

### <a name="update-admin-list"></a>更新管理员列表

1. 选择“登录屏幕”。
2. 从下拉列表中选择“OnStart”。
3. 展开公式窗口，查找“AdminList”集合。
4. 将“user@microsoft.com”替换为你的技术支持管理员。

    ![更新管理员列表](./media/help-desk-install/Change-admin.png)
    
    > [!TIP] 
    > 如果有多个管理员，请使用逗号分隔。示例："admin1@microsoft.com","admin2@microsoft.com"。

5. 单击“文件”。
6. 单击“保存”。
7. 单击“发布”。
8. 单击“发布此版本”。

## <a name="modify-the-flow"></a>修改流

1.  在左侧菜单中，单击“流”。
2.  如果提示登录，请使用注册所用的同一凭据登录。
3.  从顶部菜单选择“我的流”。
4.  单击“技术支持流”旁的铅笔图标。 
 
    ![“编辑流”屏幕](./media/help-desk-install/edit-flow.png)

5.  展开“获取项”操作。 
6.  更改“站点地址”和“列表名称”，使其与创建的技术支持 SharePoint 列表匹配。
    
    ![“编辑流”屏幕](./media/help-desk-install/edit-flow-getitems.png)

    > [!TIP] 
    > 无需手动键入，可从下拉列表选择。

7.  展开“切换”。
8.  展开“未启动”用例。
9.  展开“发送电子邮件”操作。
10. 将“收件人”更改为技术支持管理员的电子邮件。

    ![“编辑流”屏幕](./media/help-desk-install/edit-flow-condition-send-email.png) 

11. 单击“更新流”。

## <a name="play-the-powerapp"></a>播放 PowerApp

1. 在 Web 浏览器中，单击“应用”。
2. 单击“技术支持 PowerApp”旁的省略号。
3. 单击“打开”。 

观看此视频，了解如何使用技术支持 PowerApp 示例。

[![技术支持演示视频](./media/help-desk-install/help-desk-demo-video.png)](https://youtu.be/sl5fXwwnvzI)