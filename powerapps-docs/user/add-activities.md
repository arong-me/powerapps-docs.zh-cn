---
title: 在模型驱动的应用中将约会、电子邮件、电话呼叫、备注或任务活动添加到时间线 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 10/03/2019
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 9ba051395e99dc6f2079d033c10a727a2e95da67
ms.sourcegitcommit: 7c1e70e94d75140955518349e6f9130ce3fd094e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "71924570"
---
# <a name="add-an-appointment-email-phone-call-note-or-task-activity-to-the-timeline"></a>将约会、电子邮件、电话呼叫、备注或任务活动添加到时间线 


在“时间线”留言板中添加“活动”以跟踪与客户或联系人的所有通信。 例如，可以进行备注、添加文章、添加任务、发送电子邮件、添加电话呼叫详细信息或设置约会。 系统将自动对每个活动添加时间戳并显示创建者。 你和团队中的其他人可以滚动浏览这些活动，以便在与客户协作时查看历史记录。 

- 从记录中添加的活动显示在记录的“时间线”留言板中。 
- 如果设置了活动的“关于”字段，活动将显示在与其关联的记录中。 
- 此外，还可以选择筛选器窗格，按记录类型和日期筛选活动。 
- 创建新活动时，将在“时间线”留言板中收到“你错过的内容”通知。
- 带有附件的电子邮件将与电子邮件正文一起显示在一起。

  > [!div class="mx-imgBorder"]
  > ![PowerApps 中活动的时间线视图](media/TimelineViewOfActivity.png "PowerApps 中活动的时间线视图")  
 
## <a name="add-an-activity-from-the-nav-bar"></a>从导航栏添加活动
 
最快速添加活动的方法是使用导航栏上的快捷方式，然后将其关联到记录。 例如，可以创建电话呼叫活动，然后使用“关于”字段将其关联到系统中的联系人。

1. 在导航栏上，选择 "**加号**![创建记录" 按钮](media/create-record-button.png "创建记录按钮")，然后选择 "**活动**"。 

   > [!div class="mx-imgBorder"]
   > ![在 PowerApps 中添加活动的快捷方式](media/QuickCreate.png "在 PowerApps 中添加活动的快捷方式")  
 
2. 选择要添加的活动的类型。

3. 填写必填信息。 使用“关于”字段将活动与记录关联。

4. 完成此操作后，选择“保存”。

 
## <a name="add-a-phone-call"></a>添加电话呼叫  
  
1. 打开要向其添加活动的记录。 例如，联系人记录。
  
2. 在“时间线”留言板中，选择“加号” > “电话呼叫”。 


   > [!div class="mx-imgBorder"]
   > ![在 PowerApps 中添加手机活动](media/addphonecall.png "在 PowerApps 中添加手机活动")
  
3. 填写电话的“主题”。

     在“备注”区域，提供与客户的对话的摘要。 
  
     “被叫方”字段会自动填充你添加了电话呼叫活动的记录。 可以视需要选择其他记录。  
  
4. 默认情况下，将方向设置为“拨出”。 可以通过选中“拨出”将其更改为“来电”。 
  
5. 填写完成后，选择“保存”，保存活动。  
  
## <a name="add-a-task"></a>添加任务  
  
1. 打开要向其添加活动的记录。 例如，联系人记录。
  
2. 在“时间线”留言板中，选择“加号” > “任务”。
  
3. “所有者”字段默认设置为当前用户。 如果要重新分配任务，请选择查找图标，然后选择其他用户或团队。  
  
4. 填写完成后，选择“保存”，保存活动。 
  
## <a name="add-an-email"></a>添加电子邮件  

若要将电子邮件活动添加到记录，必须先保存要添加活动的目标记录。  
  
1. 打开要向其添加活动的记录。 例如，联系人记录。
  
2. 在“时间线”留言板中，选择“加号” > “电子邮件”。 

3. 填写电子邮件的主题，并使用提供的空白区域来撰写电子邮件。
  
4. 若要向电子邮件添加附件，请保存电子邮件。 然后，在“附件”部分，选择“+”以添加附件。  
  
5. 若要在电子邮件正文中使用模板，在命令栏上，单击“插入模板”，然后选择该模板。   
  
6. 填写完成后，选择“发送”。 


    > [!NOTE]
    > 若要列出会话视图中的电子邮件，请参阅 "**设置**" > "**个性化设置**" > **电子邮件**"选项卡，然后选择 **" 在时间线上显示电子邮件 "** 。 有关个人设置的详细信息，请参阅[设置个人选项](https://docs.microsoft.com/en-us/powerapps/user/set-personal-options#email-tab-options)。 启用后，可以打开任何具有时间线的窗体，电子邮件将按最新的最新电子邮件分组到会话线程中。

   > [!div class="mx-imgBorder"]
   > ![设置个人选项](media/emailsettings1.png "设置个人选项")
   
    > [!div class="mx-imgBorder"]
    > ![设置个人选项电子邮件](media/emailsettings2.png "设置电子邮件的个人选项")

  
## <a name="add-an-appointment"></a>添加约会  

若要向记录添加约会活动，必须先保存要向其添加活动的记录。  
  
1. 打开要向其添加活动的记录。 例如，联系人记录。
  
2. 在“时间线”留言板中，选择“加号” > “约会”。  
  
3. 使用工具提示填写必填信息。
  
4. 填写完成后，选择“保存”，保存约会。

## <a name="add-notes"></a>添加注释

也可以在活动区域轻松添加备注。
  
1. 打开要向其添加活动的记录。 例如，联系人记录。
  
2. 在“时间线”留言板中，开始输入备注。 使用“添加附件”向备注添加任何附件。

3. 填写完成后，选择“添加备注”保存备注。


> [!NOTE]
> 也可以使用“时间线”留言板上部的“加号”来添加备注。

   > [!div class="mx-imgBorder"]
   > ![添加备注](media/addnote.png "添加备注")

添加备注后，可以删除或编辑备注。


> [!div class="mx-imgBorder"]
> ![更新注释](media/addnote2.png "更新注释")

## <a name="add-a-post"></a>添加文章 

1. 打开想要向其添加文章的记录。 例如，联系人记录。

2. 在“时间线”留言板中，选择“加号” > “文章”。 

3. 在文本字段中输入文章 

4. 填写完成后，选择“添加”保存文章。

> [!div class="mx-imgBorder"]
> ![更新帖子](media/post.png "添加文章")
  
  保存文章后，它将显示在时间线留言板的顶部。
  
## <a name="refresh-the-timeline"></a>刷新时间线 

可以刷新时间留言板以查看最新信息。

在**时间线**背景中，选择 "![更多" 按钮](media/MoreButton.png "更多按钮")，然后选择 "**刷新时间线**"。

> [!div class="mx-imgBorder"]
> ![刷新时间线](media/refresh.png "刷新时间线")


## <a name="use-the-filter-pane"></a>使用筛选器窗格

使用筛选器窗格按记录类型或活动类型和日期快速筛选时间线留言板中的活动、备注或文章。 可以同时选择多个筛选器和筛选器选项。 可以筛选和查看活动截止日期、修改日期或活动状态。

- 在**时间线**背景中，选择 "**打开筛选器窗格**漏斗图标"。

> [!div class="mx-imgBorder"]
> ![时间线中的筛选器窗格](media/filterpane.png "时间线中的筛选器窗格")


## <a name="manage-activities"></a>管理活动
从时间线留言板中直接管理活动，包括向其他用户分配活动、删除或关闭活动、向队列添加活动、打开关联的记录或编辑备注和文章。


> [!div class="mx-imgBorder"]
> ![管理活动 .png](media/ManageActivities.png "ManageActivities .png")



