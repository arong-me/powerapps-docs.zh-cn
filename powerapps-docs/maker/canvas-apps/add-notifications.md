---
title: 发送推送通知 | Microsoft 文档
description: 了解如何在 PowerApps 中向应用发送原生推送通知。
documentationcenter: na
author: jamesol-msft
manager: kfile
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: canvas
ms.date: 08/08/2017
ms.author: jamesol
ms.openlocfilehash: 0792a47db2174dc440488eb854987bca80c8b363
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="send-a-pull-notification-in-powerapps"></a>在 PowerApps 发送推送通知
推送通知用于移动应用中的使用者和业务情形，主要用来与应用用户进行交互，并帮助他们优先处理关键任务。 在 PowerApps 中，可以使用 PowerApps 通知连接器发送通知。 可以将原生推送通知发送到在 PowerApps 中创建的任何应用。 我们计划在今后支持更多通知类型。

![推送通知外观示例](./media/add-notifications/pic1-notification-screenshot.png)

如果出现以下任意情况，请向应用添加推送通知：

* 用户需要立即了解相关信息。
* 用户必须使用应用在预加载的上下文中完成重要任务。
* 希望按特定时间间隔与用户进行交互，或需要用户在特定情况下进入应用。

> [!NOTE]
> 每个用户都必须在 PowerApps Mobile 中打开过一次应用，或在 [Dynamics 365](https://home.dynamics.com/) 中从 AppSource 获取过应用，才能接收推送通知。

## <a name="before-you-start"></a>开始之前
在拥有参与者权限的应用中，添加 PowerApps 通知连接。 如果尚未生成应用，可以[通过模板快速创建一个](get-started-test-drive.md)，默认拥有所需的权限。 上面提及的教程和本教程均使用根据用例管理模板生成的应用。

## <a name="send-a-notification-from-a-flow"></a>通过流发送通知
> [!NOTE]
> 如果通过流触发推送通知，那么目前一次只能向一个用户或安全组发送通知。

1. 在 [Microsoft Flow](https://flow.microsoft.com) 中，创建一个触发器，指定何时发送推送通知。
   
    例如，建议在记录被添加到 Common Data Service 中的“用例”实体时发送通知。
   
    ![创建包含 Common Data Service 触发器的流的屏幕截图](./media/add-notifications/pic4-step1-flowupdated.png)
2. 使用“PowerApps 通知”连接器创建流操作，再输入要向其发送通知的应用的应用 ID。
   
    还可以重命名连接，以反映具体方案。
   
    ![创建用于接收这些推送通知的 PowerApps 连接的屏幕截图](./media/add-notifications/pic5-step2-create-connection.jpg)
3. （可选）在用户点击推送通知后应用打开时，将参数传递给应用。
   
    此示例为选定联系人传递“用例 ID”和“初始所有者”字段。
   
    ![将可选参数传递到推送通知的屏幕截图](./media/add-notifications/pic6-step3-configure-notif.jpg)

## <a name="send-a-notification-from-an-app"></a>通过应用发送通知
可以将推送通知从一个应用发送到另一个应用，也可以发送到同一个应用。

1. 在 [PowerApps](https://web.powerapps.com/) 中，转到要向其发送推送通知的应用。
2. 在“详细信息”选项卡上，复制此应用的“应用 ID”。
   
    ![获取应用 ID](./media/add-notifications/grab-id.png)
3. 在“连接”选项卡上，创建与 PowerApps 通知连接器的连接，并粘贴上一步中复制的应用 ID。
   
    ![创建连接](./media/add-notifications/create-connection.png)
4. 将连接添加到触发器应用。
   
    此示例使用相同的应用作为触发器应用。 如果用户重新分配用例，也会触发向新的用例所有者发送推送通知。
   
    ![添加连接](./media/add-notifications/add-connection.png)
5. 通过推送通知连接，调用 SendPushNotification 方法。
   
    此示例使用窗体中的 OnSuccess 属性触发此通知。
   
    ![PowerApps 公式](./media/add-notifications/powerapps-function.png)

## <a name="load-a-specific-page-and-context-when-a-user-taps-the-notification"></a>在用户点击通知时加载特定页和上下文
### <a name="pass-parameters"></a>传递参数
推送通知可以向应用传递特定参数。 例如，若要读取 CaseID 值，请使用 Param("CaseID")。 若要快速识别此参数，请在应用中添加“标签”控件。 将此控件的 Text 属性设置为 Param("CaseID")。 如果用户从“所有应用”列表打开应用，此值为空。 如果用户从设备上的其他位置打开应用，此值就会填充有 CaseID 值。

### <a name="set-the-start-page"></a>设置起始页
例如，可以将应用设置为打开后显示“用例详情”页：

1. 添加“计时器”控件，并将 OnTimerEnd 属性设置为以下公式：
   <br>**Navigate(EditCase, ScreenTransition.None)**
2. （可选）将 Visible 属性设置为 false，隐藏“计时器”控件。
3. 将屏幕的 OnVisible 属性设置为 Timer.Start()。

> [!TIP]
> 最好在应用中为通知创建专属首页：

>1. 创建应用尚未打开的空页，添加“文本输入”控件，并设置 timer.Duration 值。
>2. 创建应用时，将计时器设置为非零值。 如果已准备好发布应用，请将值设置为 0，以立即触发计时器。

## <a name="syntax"></a>语法
| 名称 | 说明 |
| --- | --- |
| SendPushNotification |向通知连接设置中指定的应用发送推送通知。 |

### <a name="parameters"></a>参数
| 名称 | 类型 | 说明 |
| --- | --- | --- |
| recipients |字符串数组（必需） |列出了： <ul> <li>用户或安全组的电子邮件地址</li> <li>Azure Active Directory 中用户或安全组的对象 ID</li></ul> |
| message |字符串（必需） |推送通知的消息正文。 |
| openApp |布尔值（可选） |是否在用户点击推送通知时打开应用。 |
| params |参数（可选） |与通知一同传递的键值参数。 可以在应用中进一步处理这些参数，以打开特定页并加载特定状态上下文。 |

### <a name="sample-formulas"></a>示例公式
发送基本通知。

```
PowerAppsNotification.SendPushNotification(
{
  recipients: [""f60ccf6f-7579-4f92-967c-2920473c966b", 72f988bf-86f1-41af-91ab-2d7cd011db47],
  message: "A new case was assigned to you."
 }
)
```

发送可打开应用并传递特定参数的通知。

```
PowerAppsNotification.SendPushNotification(
{
  recipients:["email1@contoso.com", "email2@contoso.com"],
  message:"message in the notif toast",
  params:Table({key:"notificationKey", value:"The value for notificationKey"}),
  openApp:true
 }
)
```

## <a name="known-limitations"></a>已知的限制
* 通知暂不显示在适用于 Windows Phone 的 PowerApps Mobile 上。
* 我们暂无法为仅在 Web 浏览器中运行应用的用户提供推送通知。
* 通知显示常规 PowerApps 图标，而不是特定应用图标。
* 使用 Microsoft Flow 时，一次只能向一个接收人发送推送通知。

有关参考信息，请参阅 [PowerApps 通知参考](https://docs.microsoft.com/connectors/powerappsnotification/)。

