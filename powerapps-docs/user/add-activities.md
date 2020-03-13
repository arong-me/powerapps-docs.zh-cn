---
title: 在模型驱动的应用中将约会、电子邮件、电话呼叫、备注或任务活动添加到时间线 | MicrosoftDocs
ms.custom: ''
author: mduelae
manager: kvivek
ms.service: powerapps
ms.component: pa-user
ms.topic: conceptual
ms.date: 03/10/2020
ms.author: mduelae
ms.reviewer: ''
ms.assetid: ''
search.audienceType:
- enduser
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 58e64d275a7d1380cd580a86f9899053b140b99e
ms.sourcegitcommit: a02b20113164acb11955d27ef4ffa421ee0fba9d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/10/2020
ms.locfileid: "78970947"
---
# <a name="add-an-appointment-email-phone-call-note-or-task-activity-to-the-timeline"></a>将约会、电子邮件、电话呼叫、备注或任务活动添加到时间线 


在“时间线”  留言板中添加“活动”  以跟踪与客户或联系人的所有通信。 例如，可以进行备注、添加文章、添加任务、发送电子邮件、添加电话呼叫详细信息或设置约会。 系统将自动对每个活动添加时间戳并显示创建者。 你和团队中的其他人可以滚动浏览这些活动，以便在与客户协作时查看历史记录。 

- 从记录中添加的活动显示在记录的“时间线”  留言板中。 
- 如果设置了活动的“关于”  字段，活动将显示在与其关联的记录中。 
- 此外，还可以选择筛选器窗格，按记录类型和日期筛选活动。 
- 创建新活动时，将在“时间线”  留言板中收到“你错过的内容”  通知。
- 带有附件图像的电子邮件将与电子邮件正文一起内联显示。

  > [!div class="mx-imgBorder"]
  > ![Power Apps 中的活动的时间线视图](media/TimelineViewOfActivity.png "Power Apps 中的活动的时间线视图")


图例：

  1. 搜索记录
  2. 备注
  3. 添加信息和活动
  4. 筛选
  5. 更多命令
  6. 活动状态
  7. 活动图标
  8. 日期和时间
 
## <a name="add-an-activity-from-the-nav-bar"></a>从导航栏添加活动
 
最快速添加活动的方法是使用导航栏上的快捷方式，然后将其关联到记录。 例如，可以创建电话呼叫活动，然后使用“关于”  字段将其关联到系统中的联系人。

1. 在顶部导航栏上，选择“新建”![“创建记录”按钮](media/create-record-button.png "“创建记录”按钮") > 活动”，然后选择要添加的活动类型   。

   > [!div class="mx-imgBorder"]
   > ![在 Power Apps 中添加活动的快捷方式](media/add_new_activity_from_nav.gif "在 Power Apps 中添加活动的快捷方式")  
 
3. 填写必填信息。 使用“关于”  字段将活动与记录关联。

4. 完成后，选择“保存并关闭”或“保存并新建”   。 

## <a name="add-an-activity-from-within-a-record"></a>从记录内部添加活动

还可以打开记录，然后向记录添加活动。 

   > [!div class="mx-imgBorder"]
   > ![在 Power Apps 中添加活动的快捷方式](media/add_new_activity_from_record.gif "在 Power Apps 中添加活动的快捷方式") 


### <a name="add-a-phone-call"></a>添加电话呼叫  
  
1. 打开要向其添加活动的记录。 例如，打开联系人记录。
  
2. 在“时间线”部分，选择“添加信息和活动”![添加活动](media/add-activity-button.png "“添加活动”按钮") > “电话呼叫”    。 


   > [!div class="mx-imgBorder"]
   > ![在 Power Apps 中添加电话活动](media/addphonecall.png "在 Power Apps 中添加电话活动")
  
3. 填写电话的“主题”  。

     在“说明”区域，提供与客户的对话的摘要  。 
  
     “被叫方”  字段会自动填充你添加了电话呼叫活动的记录。 可以视需要选择其他记录。  
  
4. 默认情况下，将方向设置为“拨出”  。 可以通过选中“拨出”  将其更改为“来电”  。
  
5. 填完表单后，选择“保存并关闭”以保存电话呼叫活动  。  
  
### <a name="add-a-task"></a>添加任务  
  
1. 打开要向其添加活动的记录。 例如，打开联系人记录。
  
2. 在“时间线”部分，选择“添加信息和活动”![添加活动](media/add-activity-button.png "“添加活动”按钮") > “任务”    。
  
3. “所有者”  字段默认设置为当前用户。 如果要重新分配任务，请选择查找图标，然后选择其他用户或团队。  
  
4. 填完任务后，选择“保存并关闭”进行保存  。 
  
### <a name="add-an-email"></a>添加电子邮件  

若要将电子邮件活动添加到记录，必须先保存要添加活动的目标记录。  
  
1. 打开要向其添加活动的记录。 例如，打开联系人记录。
  
2. 在“时间线”部分，选择“添加信息和活动”![添加活动](media/add-activity-button.png "“添加活动”按钮") > “电子邮件”    。 

3. 填写电子邮件的主题，并使用提供的空白区域来撰写电子邮件。
  
4. 若要向电子邮件添加附件，请保存电子邮件。 然后，在命令栏上选择“附加文件” > “选择文件”，然后选择要附加到电子邮件的文件   。

   > [!NOTE]
   > 带有附件图像的电子邮件将与电子邮件正文一起内联显示。
  
5. 要在电子邮件正文中使用模板，请在命令栏上，选择“插入模板”，然后选择该模板  。 如需详细了解如何插入电子邮件模板，请参阅[插入电子邮件模板](insert-email-template.md)。 
  
6. 在电子邮件中撰写完毕后，在命令栏上选择“发送”  。 


#### <a name="list-emails-in-a-conversation-view"></a>在对话视图中列出电子邮件

1. 要在对话视图中列出电子邮件，请转到“设置” > “个性化设置”   。

   > [!div class="mx-imgBorder"]
   > ![设置个人选项](media/emailsettings1.png "设置个人选项")

2. 在“电子邮件”选项卡上，选择“将电子邮件限制为时间线上的对话”   。 有关个人设置的详细信息，请参阅[设置个人选项](https://docs.microsoft.com/powerapps/user/set-personal-options#email-tab-options)。 启用后，可以打开具有时间线的任何窗体，并且电子邮件将分组到对话线程中，最新的电子邮件显示在最上方。
   
   > [!div class="mx-imgBorder"]
   > ![设置个人选项电子邮件](media/emailsettings2.png "设置电子邮件的个人选项")

  
### <a name="add-an-appointment"></a>添加约会  

要向记录添加约会活动，必须先保存要向其添加约会活动的记录。  

> [!NOTE]
> Dynamics 365 App for Outlook、适用于手机的 Dynamics 365 的应用以及在移动电话 Web 浏览器上运行模型驱动应用 Web 客户端时，不支持定期约会。
  
1. 打开要向其添加活动的记录。 例如，打开联系人记录。
  
2.  在“时间线”部分，选择“添加信息和活动”![添加活动](media/add-activity-button.png "“添加活动”按钮") > “约会”    。  
  
3. 填写约会的“主题”，并设置“开始时间”和“结束时间”    。
  
4. 填完约会详细信息后，选择“保存并关闭”以保存约会  。

### <a name="add-notes"></a>添加注释

也可以在活动区域轻松添加备注。
  
1. 打开要向其添加活动的记录。 例如，打开联系人记录。
  
2. 在“时间线”部分，选择“输入备注”区域   。

3. 添加备注的标题并添加备注详细信息。

4. 要向备注添加附件，请选择“添加附件”  。

3. 完成后，选择“添加备注”进行保存  。

   > [!div class="mx-imgBorder"]
   > ![添加备注](media/addnote.png "添加备注")

> [!NOTE]
> 还可通过选择“添加信息和活动”![添加活动](media/add-activity-button.png "“添加活动”按钮") > “说明”来添加备注   。

#### <a name="edit-or-delete-a-note"></a>编辑或删除备注

- 要在创建备注后立即编辑或删除此备注，请选择该备注，然后选择“编辑此备注”或“删除备注”   。 

  > [!div class="mx-imgBorder"]
  > ![更新备注](media/addnote2.png "更新备注")

### <a name="add-a-post"></a>添加文章 

1. 打开想要向其添加文章的记录。 例如，打开联系人记录。

2. 在“时间线”部分，选择“添加信息和活动”![添加活动](media/add-activity-button.png "“添加活动”按钮") > “文章”    。 

3. 在文本字段中输入文章详细信息。

4. 完成后，选择“添加”以保存文章  。

   > [!div class="mx-imgBorder"]
   > ![更新文章](media/post.png "添加文章")
  
  保存文章后，它将显示在时间线留言板的顶部。
  
## <a name="refresh-the-timeline"></a>刷新时间线 

可以刷新时间留言板以查看最新信息。

在“时间线”部分，选择![“更多”按钮](media/MoreButton.png "“更多”按钮")，然后选择“刷新时间线”   。

  > [!div class="mx-imgBorder"]
  > ![刷新时间线](media/refresh.png "刷新时间线")


## <a name="use-the-filter-pane"></a>使用筛选器窗格

使用筛选器窗格按记录类型或活动类型和日期快速筛选时间线留言板中的活动、备注或文章。 可以同时选择多个筛选器和筛选器选项。 可以筛选和查看活动截止日期、修改日期或活动状态。

- 在“时间线”部分，选择“打开筛选器窗格”，然后选择要筛选活动的方式   。

 > [!Note]
 > 当你在浏览器中缩小时，“筛选器”窗格和时间线记录显示在两列中。 当时间线在多列中显示时，“筛选器”窗格显示为与时间线记录并排的列。 若要了解详细信息，请参阅[“筛选器”窗格以两列模式显示](../maker/model-driven-apps/faqs-timeline-control.md#why-my-agents-see-the-filter-pane-even-when-the-expand-filter-pane-by-default-check-box-is-cleared)。 

  > [!div class="mx-imgBorder"]
  > ![时间线中的“筛选器”窗格](media/timeline-filter2.png "时间线中的“筛选器”窗格") ![时间线中的“筛选器”窗格](media/timeline-filter5.png "时间线中的“筛选器”窗格")


## <a name="manage-activities"></a>管理活动
从时间线留言板中直接管理活动，包括向其他用户分配活动、删除或关闭活动、向队列添加活动、打开关联的记录或编辑备注和文章。

  ![时间线命令栏选项](media/timeline-options1.png "时间线命令栏选项") ![时间线命令栏选项](media/timeline-options2.png "时间线命令栏选项") ![时间线命令栏选项](media/timeline-options3.png "时间线命令栏选项") ![时间线命令栏选项](media/timeline-options4.png "时间线命令栏选项")

## <a name="see-also"></a>另请参阅

[设置时间线控件](../maker/model-driven-apps/set-up-timeline-control.md)

[有关时间线控件的常见问题解答](../maker/model-driven-apps/faqs-timeline-control.md)

[有关活动和时间线留言板的常见问题](faq-for-timeline-and-activity.md)

[客户服务中心应用中的时间线部分](https://docs.microsoft.com/dynamics365/customer-service/customer-service-hub-user-guide-basics#timeline)
