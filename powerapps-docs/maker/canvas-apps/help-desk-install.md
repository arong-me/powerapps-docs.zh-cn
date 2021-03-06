---
title: 安装和配置画布应用的技术支持示例 | Microsoft Docs
description: 用于在 Power Apps 中安装和配置画布应用的技术支持示例的分步说明。
author: matthewbolanos
manager: kvivek
ms.service: powerapps
ms.topic: sample
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 01/15/2020
ms.author: mabolan
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4eafe6aaafb2fe461a98212a64d3858ebf5f5f0f
ms.sourcegitcommit: 1c4ab1859febccf79a835bd2f168e7e12a953a18
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2020
ms.locfileid: "76111107"
---
# <a name="install-and-configure-the-help-desk-sample-in-power-apps"></a>在 Power Apps 中安装和配置技术支持示例

用于在 Power Apps 中安装和配置画布应用的技术支持示例的分步说明。

完成以下步骤的估计时间：10-15 分钟

> [!TIP]
> 有关此过程的演示，请观看此[视频](https://youtu.be/z4cdtD6hB_4)。

## <a name="overview-of-the-sample"></a>示例概述

技术支持提供用户友好体验，方便最终用户与支持专业人员交流。 快速找到最重要问题的答案，跟踪开放票证的进度，并查看之前的请求的详细信息。 要拥有此应用，需完成少量设置。

![技术支持 PowerApp 的打开屏幕](./media/help-desk-install/Login-screen.png)

> [!TIP]
> 观看此[视频](https://youtu.be/sl5fXwwnvzI)，了解如何使用技术支持 PowerApp 示例。

## <a name="prerequisites"></a>必备组件

- [注册](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)Power Apps。
- 必须具有有效的 SharePoint Online 许可证和创建列表的权限。

## <a name="create-the-helpdesk-sharepoint-list"></a>创建技术支持 SharePoint 列表

此列表存储技术支持票证。

1. 打开 Web 浏览器并导航到 [https://portal.office.com](https://admin.microsoft.com ) 。
2. 用具有创建 SharePoint 列表权限的帐户登录。
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

1. 选择技术支持列表旁的省略号，单击“设置”。
2. 单击“创建列”。
3. 在“列名”文本框中，输入“说明”。
4. 在“此列中的信息类型为”单选按钮列表中，选择“多行文本”。
5. 在“要求此列包含信息”单选按钮列表中，选择“是”。
6. 在“指定允许的文本类型”单选按钮列表中，选择“纯文本”。
7. 单击**确定**。

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
8. 单击**确定**。

### <a name="create-percentcomplete-column"></a>创建 PercentComplete 列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“PercentComplete”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“数字 (1, 10, 100)”。
4. 在“要求此列包含信息”单选按钮列表中，选择“否”。
5. 单击**确定**。

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
8. 单击**确定**。

### <a name="create-taskstatus-column"></a>创建“任务状态”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“任务状态”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“选项”。
4. 在“在单独行上输入每个选项”文本框中，输入以下值，每个值单独占一行： 
    - 未启动
    - 进行中
    - COMPLETED
    - 已推迟
    - 等待 CSR
5. 在“强制使用唯一值”单选按钮列表中，选择“否”。
6. 在“选项显示方式”单选按钮列表中，选择“下拉菜单”。
7. 在“默认值”文本框中，输入“未启动”。
8. 单击**确定**。

### <a name="create-assignedto-column"></a>创建“分配对象”列

1. 单击“创建列”。
2. 在“列名”文本框中，输入“分配对象”。
3. 在“此列中的信息类型为”单选按钮列表中，选择“用户或用户组”。
4. 在“要求此列包含信息”单选按钮列表中，选择“否”。
5. 在“允许多选”单选按钮列表中，选择“否”。
6. 单击**确定**。

### <a name="edit-title-column"></a>编辑“标题”列

1. 单击“标题”列链接。
2. 在“要求此列包含信息”单选按钮列表中，选择“否”。
3. 单击**确定**。

## <a name="download-the-app"></a>下载应用

1.  [下载](https://pappsfeprodwestuscontent.blob.core.windows.net/sampleapps/helpdesk/docs/HelpDesk(SP_List).zip)Power Apps 包并将其保存到计算机。

## <a name="create-connections"></a>创建连接

1.  在 web 浏览器中，导航到[make.powerapps.com](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。
2.  使用注册所用的同一凭据登录。
3.  在左侧菜单，依次选择“数据”和“连接”。
    
### <a name="create-office-365-outlook-connection"></a>创建 Office 365 Outlook 连接

1.  单击“+ 新建连接”。
2.  在“搜索”文本框中，输入“Office 365 Outlook”。
3.  从列表中选择“Office 365 Outlook”。
4.  单击“创建”。
5.  在弹出窗口中，选择登录所用的帐户。

### <a name="create-sharepoint-connection"></a>创建 SharePoint 连接

1.  单击“+ 新建连接”。
2.  在“搜索”文本框中，输入“SharePoint”。
3.  从列表中选择“SharePoint”。
4.  单击“创建”。
5.  在弹出窗口中，选择登录所用的帐户。

### <a name="create-office-365-users-connection"></a>创建 Office 365 用户连接

1.  单击“+ 新建连接”。
2.  在“搜索”文本框中，输入“Office 365 用户”。
3.  从列表中选择“Office 365 用户”。
4.  单击“创建”。
5.  在弹出窗口中，选择登录所用的帐户。

## <a name="import-the-app"></a>导入应用

1. 在 Web 浏览器中，导航到 [https://web.powerapps.com](https://make.powerapps.com )。
2. 使用注册所用的同一凭据登录。
3. 在左侧菜单中，选择“应用”。 
4. 单击“导入包(预览)”。
    
   ![“导入包”屏幕](./media/help-desk-install/import-package.png)

5. 单击“上传”按钮，选择前面步骤中下载的 PowerApp 包。
6. 对于“应用”和“流”资源类型，将“导入设置”设置为“新建”。
7. 对于“SharePoint”和“Outlook”连接，将“导入设置”设置为“在导入期间选择”。
    
   ![“导入设置”屏幕](./media/help-desk-install/import-settings.png)

8. 单击“SharePoint 连接”对应的“红色图标”。
9. 在连接列表中，单击带有用户名的项。

   ![“导入设置”屏幕](./media/help-desk-install/import-settings-sharepoint.png)

10. 单击“保存”。
11. 单击“Office 365 Outlook 连接”对应的“红色图标”。
12. 在连接列表中，单击带有用户名的项。

    ![“导入设置”屏幕](./media/help-desk-install/import-settings-office365outlook.png)

13. 单击“保存”。

    > [!TIP] 
    > 完成后，屏幕显示如下。

    ![“导入设置”屏幕](./media/help-desk-install/import-settings-done.png)

14. 单击“导入”并等待，直到流程完成。

    ![“导入设置”屏幕](./media/help-desk-install/import-done.png)

## <a name="configure-the-app-to-use-the-sharepoint-list"></a>将应用配置为使用 SharePoint 列表

1. 在“后续步骤”下，单击“打开应用”。
2. 在出现权限提示时，选择“允许”。

### <a name="delete-connections"></a>删除连接

1. 在“视图”选项卡上，选择“数据源”。
1. 在 "**数据**" 窗格中，选择 "**支持人员**" 旁边的省略号（...），然后选择 "**删除**"。

### <a name="helpdesk-list"></a>技术支持列表

1. 在“视图”选项卡上，选择“数据源”。
1. 在“数据”窗格中，选择“添加数据源” > “新建连接” > “SharePoint” > “创建”。
1. 在“最近使用的站点”列表中，选择在其中创建技术支持列表的 SharePoint 站点。

    > [!TIP] 
    > 如果列表中未出现该站点，在文本框中键入或粘贴 SharePoint 站点的 URL，然后选择“转到”。

1. 在列表顶部的 "**搜索**" 框中，键入或粘贴 "**支持人员**"。
1. 选择 "**支持人员**" 旁边的复选框，然后选择 "**连接**"。

### <a name="update-admin-list"></a>更新管理员列表

1. 选择**应用**。
2. 从下拉列表中选择“OnStart”。
3. 展开公式窗口，查找“AdminList”集合。
4. 将“user@microsoft.com”替换为你的技术支持管理员。

    ![更新管理员列表](./media/help-desk-install/Change-admin.png)
    
   > [!TIP]
   > 如果有多个管理员，请使用逗号分隔管理员列表。 示例："admin1@microsoft.com","admin2@microsoft.com"。
   > 若要确保 AdminList 中的地址与 Power Apps 所需的格式相匹配，请选择 "查看 > Global > MyProfile > 变量"，并查看 "Mail" 列以查看预期的电子邮件格式。

1. 选择“文件” > “保存” > “发布” > “发布此版本”。

## <a name="modify-the-flow"></a>修改流

1.  在左侧菜单中，单击“流”。
2.  如果提示登录，请使用注册所用的同一凭据登录。
3.  从顶部菜单选择“我的流”。
4.  单击 " **HelpDeskFlow** Flow" 旁边的铅笔图标。 
 
    ![“编辑流”屏幕](./media/help-desk-install/edit-flow.png)

5.  展开“获取项”操作。 
6.  更改“站点地址”和“列表名称”，使其与创建的技术支持 SharePoint 列表匹配。
    
    ![“编辑流”屏幕](./media/help-desk-install/edit-flow-getitems.png)

    > [!TIP] 
    > 无需手动键入，可从下拉列表选择。

7.  展开“切换”。
8.  展开“未启动”用例。
9.  展开“未启动用例”操作。
10. 将“收件人”更改为技术支持管理员的电子邮件。

    ![“编辑流”屏幕](./media/help-desk-install/edit-flow-condition-send-email.png) 

11. 单击“更新流”。

## <a name="play-the-app"></a>播放应用

1. 在 Web 浏览器中，单击“应用”。
2. 单击 "技术支持" 应用旁边的省略号（...）。
3. 单击“打开”。 

> [!TIP]
> 观看此[视频](https://youtu.be/sl5fXwwnvzI)，了解如何使用技术支持 PowerApp 示例。

## <a name="next-steps"></a>后续步骤
- [自定义 SharePoint 列表窗体](https://docs.microsoft.com/powerapps/maker/canvas-apps/customize-list-form)
- [添加并配置控件](https://docs.microsoft.com/powerapps/maker/canvas-apps/add-configure-controls)
- [编辑和管理 SharePoint 列表或库的权限](https://support.office.com/article/edit-and-manage-permissions-for-a-sharepoint-list-or-library-02d770f3-59eb-4910-a608-5f84cc297782)
