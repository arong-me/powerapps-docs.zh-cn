---
title: 邀请联系人到门户 |MicrosoftDocs
description: 在门户中创建和配置邀请的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 631f17d9764fbfc209fd193ddabe4882f8ad8042
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73552212"
---
# <a name="invite-contacts-to-your-portals"></a>邀请联系人加入门户

使用门户的邀请功能，通过在 Common Data Service 中创建的自动电子邮件邀请联系人加入门户。 你邀请的人员会收到一封电子邮件，其中包含你的门户的链接和邀请代码。 此代码可用于获取您配置的特殊访问权限。 利用此功能，您可以：

- 发送单邀请或组邀请
-   如果需要，请指定到期日期
-   将用户或门户联系人指定为邀请者（如果需要）
-   邀请兑换时自动将邀请的联系人分配给帐户
-   邀请兑换时自动执行工作流
-   在兑换时自动将邀请的联系人分配给 Web 角色

可以使用我们的众多身份验证选项中的任意一个来完成邀请兑换。 有关门户身份验证的文档，请参阅为[门户设置身份验证标识](set-authentication-identity.md)和选择适用于你的门户版本和配置的模型。 用户在兑换后将采用管理员提供的任何设置。 将为邀请和联系人创建邀请兑换活动。

邀请通过**发送邀请**工作流发送。 默认情况下，工作流使用一般邮件创建一封电子邮件，并将其发送到受邀联系人的主要电子邮件地址。 **发送邀请**工作流包含一个电子邮件模板，需要对其进行编辑，使其包含门户的特定邮件和门户**邀请兑换页面**的正确超链接。

若要编辑**发送邀请**工作流电子邮件模板，请找到该模板并将其停用。 停用后，编辑电子邮件模板以发送所需的邮件，并提供指向门户的**邀请兑换页面**的链接。

> [!NOTE]
> 邀请只发送到联系人的主要电子邮件（emailaddress1）。 邀请将不会发送到联系人记录的辅助电子邮件（emailaddress2）或备用电子邮件（emailaddress3）。

## <a name="create-invitations-from-portal-management-app"></a>从门户管理应用创建邀请

1.  打开[门户管理应用](configure-portal.md)。

2.  中转到 "**门户**" > **联系人**"。
    或者，也可以从 "[共享](../manage-existing-portals.md#share)" 窗格打开 "**联系人**" 页。 

3.  选择联系人或打开要邀请的联系人记录。

4.  在命令栏上，选择 "**创建邀请**"。

5.  在 "**邀请**" 页上，在字段中输入相应的值。 详细信息：[邀请属性](#invitation-attributes)

6.  选择“保存”。

7.  在命令栏上，选择 " **Flow** > **发送邀请**"。

    > [!div class="mx-imgBorder"]
    > ![发送邀请工作流](../media/send-invitation-portal-app.png "发送邀请工作流")

8.  在确认窗口中，选择 **"确定"** 。 邀请将发送到所选联系人。

    > [!div class="mx-imgBorder"]
    > ![确认发送邀请](../media/confirm-invitation-portal-app.png "确认发送邀请")

### <a name="send-multiple-invitations"></a>发送多个邀请

您可以为联系人创建邀请，然后一次发送所有邀请。

1.  创建所需联系人的邀请，然后 > **邀请**中转到**门户**。

2.  选择创建的邀请。

3.  在命令栏上，选择 " **Flow** > **发送邀请**"。

    > [!div class="mx-imgBorder"]
    > ![发送邀请工作流](../media/send-invitation-portal-app.png "发送邀请工作流")

4.  在确认窗口中，选择 **"确定"** 。 邀请将发送到所选联系人。

    > [!div class="mx-imgBorder"]
    > ![确认发送多个邀请](../media/confirm-multiple-invites-portal-app.png "确认发送多个邀请")

## <a name="invitation-attributes"></a>邀请属性

下表说明了**邀请**页的属性：


|  名称    |    描述    |
|-------|------------|
|                 名称                  |                                                                                                      有助于识别邀请的描述性名称。                                                                                                      |
|                 类型                  |                                             **单个**或**组**。 单个将仅邀请一个联系人，并只允许一个兑换。 组允许邀请多个联系人和多个兑换次数。                                              |
|             所有者/发件人              | 发送邀请时将作为电子邮件的发件人的用户。 如果创建的电子邮件中的 "发件人" 字段中已包含某人，则可以在**发送邀请**工作流中覆盖此项。 |
|            邀请代码            |                                                                 只有被邀请者知道的邀请的唯一代码。 这是在创建新邀请时自动生成的。                                                                  |
|              到期日期              |                                                                                     表示邀请将对兑换无效的时间的日期。 可选。                                                                                     |
|                邀请者                |                                                                                               当联系人为邀请的发件人时，可以使用。 可选。                                                                                                |
|          受邀联系人           |                                                                                                             要邀请到门户的联系人。                                                                                                              |
|           分配给帐户           |                                                                        兑换邀请时，将与兑换联系人的父客户关联的帐户记录。 可选。                                                                        |
| 对兑换联系人执行工作流 |                                                         要在兑换邀请时执行的工作流进程。 该工作流将作为主要实体传递给兑换联系人。 可选。                                                          |
|          分配到 Web 角色          |                                                                               兑换邀请时，要与兑换联系人关联的一组 web 角色。 可选。                                                                                |
|          兑换的联系人          |                                                                                                   已成功兑换邀请的联系人。                                                                                                   |
|      允许的最大兑换次数      |                                                                                   邀请可兑换的次数。 仅适用于组类型邀请。                                                                                   |
|                                       |                                                                                                                                                                                                                                                                    |

### <a name="see-also"></a>另请参阅

[配置联系人以在门户上使用](configure-contacts.md)  
[设置门户的身份验证标识](set-authentication-identity.md)  
