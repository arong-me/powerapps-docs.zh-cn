---
title: Power Apps 中的时间线控件（部分）的常见问题解答 | MicrosoftDocs
description: Power Apps 中的时间线控件（部分）的常见问题解答
ms.date: 02/03/2020
ms.service: powerapps
author: kabala123
ms.assetid: 7F495EE1-1208-49DA-9B02-17855CEB2FDF
ms.author: kabala
manager: shujoshi
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 6556ee415f2ee3340f6e36f417a25299871c1860
ms.sourcegitcommit: c5b9bdf820c7d60f00bf1b16d9e9f7d046fd7252
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2020
ms.locfileid: "3013045"
---
# <a name="faqs-for-timeline-control"></a>时间线控件的常见问题解答

## <a name="why-do-i-receive-the-message-records-could-not-be-loaded-because-of-unexpected-error"></a>为什么会收到消息“由于出现意外错误，无法加载记录”？

**时间线**部分检索相关数据并在窗体卡中显示。 默认情况下，时间线检索 10 个标准活动实体的数据，分别是：

-   电子邮件
-   任务
-   事件解决方法
-   传真
-   商机结束
-   信件
-   约会
-   电话联络

当您以管理员身份执行以下过程时，在运行时用户将看到错误：

**过程**
-   再创建一些自定义活动
-   为移动设备启用自定义活动
-   为所有自定义活动选择**卡窗体** 

**错误：** 由于出现意外错误，无法加载记录。

   > [!div class=mx-imgBorder] 
   > ![由于出现意外错误，无法加载记录。](media/timeline-error1.png "由于出现意外错误，无法加载记录。")

因为用于检索数据的活动实体数超过了最大限制 10，所以发生此错误。

   > [!div class=mx-imgBorder] 
   > ![查询中的链接实体数量已超过最大限制](media/timeline-error2.png "[查询中的链接实体数量已超过最大限制")

### <a name="workaround"></a>解决办法

若要解决此问题，必须将实体数量减少到 10 或更少。 若要完成此操作，请执行以下步骤。

1.  登录到您的 `https://<YourOrgURL>.dynamics.com/apps` 环境。

2.  打开模型驱动应用，然后在命令栏上，选择**设置** ![设置](../model-driven-apps/media/powerapps-gear.png) > **高级设置**。

3.  转到**设置** > **自定义** > **自定义系统**。 将在新浏览器窗口中打开解决方案资源管理器页面。

4.  展开默认解决方案窗格中**组件**下的**实体**。

5.  选择实体，然后选择**窗体**。 例如，选择**客户**实体。

6.  选择窗体类型为**主**的**交互式体验的客户**记录。 将在新浏览器窗口中打开**交互式体验的客户**窗体。

   > [!div class=mx-imgBorder] 
   > ![选择名称中具有交互式体验的实体窗体](media/account-interactive-experience.png "选择名称中具有交互式体验的实体窗体")

   对于统一接口，需要使用包含 `<Entity> for Interactive experience`的窗体名称。

7.  双击**时间线**部分中的**对话选项卡**字段。 将显示**活动选项卡属性**对话框。

    > [!div class=mx-imgBorder] 
    > ![双击社交窗格中的字段](media/timeline-conversation-tabs-field.png "双击社交窗格中的字段")  

8.  为**筛选条件**容器中的**显示这些活动**字段选择**显示选定项**选项。

9.  选择要对用户显示的活动。

10. 选择**确定**，然后选择**保存**。

11. 选择**发布**发布自定义项。


## <a name="why-i-cant-assign-or-delete-an-activity-from-the-timeline"></a>为什么不能在时间线中分派或删除活动？

如果使用 **HideCustomActions** 规则隐藏功能区命令栏定义中的按钮（如**分派**和**删除**），这些按钮将在时间线控件中显示，但是不起作用。 命令栏中的按钮与时间线控件中的按钮相同，因此，当用户在时间线控件中选择**分派**或**删除**按钮时，将显示错误消息。

**您没有权限执行此操作。请与您的系统管理员联系。**

若要缓解此问题，请在命令栏定义中取消隐藏这些按钮。


## <a name="why-my-users-see-different-activities-and-records-in-their-my-activities-stream-in-the-dashboard"></a>为什么我的用户在仪表板中“我的活动”流中看到的活动和记录不同？

仪表板中的**我的活动**流显示特定用户负责的记录和活动。 例如，用户 **A** 看到的是 **A** 负责的记录和活动，而用户 **B** 看到的则是 **B** 负责的记录和活动。

## <a name="see-also"></a>另请参阅

[设置时间线控件](set-up-timeline-control.md)

[客户服务中心应用中的时间线部分](https://docs.microsoft.com/dynamics365/customer-service/customer-service-hub-user-guide-basics#timeline)

[向时间线添加约会、电子邮件、电话联络、注释或任务活动](../../user/add-activities.md)
