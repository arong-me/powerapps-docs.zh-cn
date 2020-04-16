---
title: 邀请联系人访问门户 | MicrosoftDocs
description: 有关如何在门户中创建和配置邀请的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 03/16/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: f6e6989e1005f12fd3e9d3a02222a8cd95226cca
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136209"
---
# <a name="invite-contacts-to-your-portals"></a>为门户邀请联系人

可使用门户邀请功能，通过在 Common Data Service 中创建的自动电子邮件邀请联系人访问门户。 受邀者将收到一封可由您完全自定义的电子邮件，其中包括门户链接和邀请代码。 此代码可用于获取您配置的特定访问权限。 使用此功能，您可以：

- 发送单个邀请或组邀请
-   如有必要指定到期日期
-   如有必要指定用户或门户联系人作为邀请者
-   收兑邀请时自动将受邀联系人分配到帐户
-   收兑邀请时自动执行工作流
-   收兑时将受邀联系人自动分配到 Web 角色

邀请收兑可以使用任何身份验证选项来完成。 有关门户身份验证的文档，请参阅[设置门户的身份验证标识](set-authentication-identity.md)并选择适用于您的门户版本和配置的模型。 用户将在收兑时采用管理员提供的任何设置。 将为邀请和联系人创建邀请收兑活动。

邀请通过**发送邀请**工作流进行发送。 默认情况下，该工作流将创建包含常规消息的电子邮件并将其发送到受邀联系人的主要电子邮件地址。 “抄送”和“密件抄送”字段中的电子邮件地址将被忽略，以确保通信的安全。 **发送邀请**工作流包含需要编辑的电子邮件模板，以包含门户的特定消息和门户的**邀请收兑页面**的正确超链接。

若要编辑**发送邀请**工作流电子邮件模板，请找到该模板并停用。 停用之后，编辑电子邮件模板，以发送所需邮件并提供门户的**邀请收兑页面**的链接。

> [!NOTE]
> 将把邀请仅发送给联系人的主要电子邮件 (emailaddress1)。 邀请将不发送给联系人记录的次要电子邮件 (emailaddress2) 或备用电子邮件 (emailaddress3)。

## <a name="create-invitations-from-portal-management-app"></a>通过门户管理应用创建邀请

1.  打开[“门户管理”应用](configure-portal.md)。

2.  转至**门户** > **联系人**。
    或者，您还可以从[共享](../manage-existing-portals.md#share)窗格打开**联系人**页面。 

3.  选择联系人或打开要邀请的联系人记录。

4.  在命令栏上，选择**创建邀请**。

5.  在**邀请**页面上，在该字段中输入适当的值。 详细信息：[邀请属性](#invitation-attributes)

6.  选择**保存**。

7.  在命令栏上，选择**流** > **发送邀请**。

    > [!div class="mx-imgBorder"]
    > ![发送邀请工作流](../media/send-invitation-portal-app.png "发送邀请工作流")

8.  在确认窗口中选择**确定**。 将把邀请发送给所选联系人。

    > [!div class="mx-imgBorder"]
    > ![有关发送邀请的确认](../media/confirm-invitation-portal-app.png "有关发送邀请的确认")

### <a name="send-multiple-invitations"></a>发送多份邀请

可为联系人创建邀请，然后一次性发送全部邀请。

1.  为所需联系人创建邀请，然后转至**门户** > **邀请**。

2.  选择创建的邀请。

3.  在命令栏上，选择**流** > **发送邀请**。

    > [!div class="mx-imgBorder"]
    > ![发送邀请工作流](../media/send-invitation-portal-app.png "发送邀请工作流")

4.  在确认窗口中选择**确定**。 将把邀请发送给所选联系人。

    > [!div class="mx-imgBorder"]
    > ![有关发送多份邀请的确认](../media/confirm-multiple-invites-portal-app.png "有关发送多份邀请的确认")

## <a name="invitation-attributes"></a>邀请属性

下面介绍**邀请**页面的属性：


|  姓名    |    说明    |
|-------|------------|
|                 姓名                  |                                                                                                      帮助识别邀请的描述性名称。                                                                                                      |
|                 Type                  |                                             **单个**或**组**。 “单个”仅允许邀请一个联系人并且只有一个收兑。 “组”允许邀请多个联系人并且具有多个收兑。                                              |
|             负责人/发件人              | 发送邀请时，用户将作为电子邮件发件人。 如果创建的电子邮件已在“发件人”字段中包含某人，则可在**发送邀请**工作流中将其覆盖。 |
|            邀请代码            |                                                                 只有受邀者知道的唯一邀请代码。 创建新邀请时，将自动生成邀请代码。                                                                  |
|              到期日期              |                                                                                     表示邀请收兑变得无效的日期。 （可选）                                                                                     |
|                邀请者                |                                                                                               可在联系人作为邀请发送者时使用。 （可选）                                                                                                |
|          受邀联系人           |                                                                                                             门户的受邀联系人。                                                                                                              |
|           分派给帐户           |                                                                        在收兑邀请时作为收兑联系人的上级客户关联的帐户记录。 （可选）                                                                        |
| 在收兑联系人时执行工作流 |                                                         在收兑邀请时执行的工作流程。 将向工作流传递收兑联系人作为主要实体。 （可选）                                                          |
|          分派 Web 角色          |                                                                               在收兑邀请时与收兑联系人关联的一组 Web 角色。 （可选）                                                                                |
|          收兑的联系人          |                                                                                                   已成功收兑邀请的联系人。                                                                                                   |
|      允许的最大收兑数      |                                                                                   可以收兑邀请的最大次数。 仅适用于组类型邀请。                                                                                   |
|                                       |                                                                                                                                                                                                                                                                    |

### <a name="see-also"></a>另请参见

[配置在门户中使用的联系人](configure-contacts.md)  
[设置门户的身份验证标识](set-authentication-identity.md)  
