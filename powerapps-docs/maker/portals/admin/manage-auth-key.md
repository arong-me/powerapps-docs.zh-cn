---
title: 将门户连接到 Common Data Service 环境 | MicrosoftDocs
description: 了解如何将门户连接到 Common Data Service 环境以及如何续订身份验证密钥。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 75d633c13b3d15888115e2e42a47e4f9da15e56f
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2978401"
---
# <a name="connect-to-a-common-data-service-environment-using-a-portal"></a>使用门户连接到 Common Data Service 环境

门户使用 Azure Active Directory 应用程序连接到 Common Data Service 环境。 此应用程序在配置门户的同一个租户内创建。 在门户配置过程中，应用程序注册到 Common Data Service 环境。

![使用 Common Data Service 环境连接门户](../media/connect-with-dynamics.png "使用 Common Data Service 环境连接门户")

每一个门户都有一个单独的 Azure Active Directory 应用程序与其关联，不论它是否连接到同一个 Common Data Service 环境。 为门户创建的默认 Azure Active Directory 身份验证提供程序使用同一个 Azure Active Directory 应用程序来验证门户。 授权由分派给访问门户的用户的 Web 角色强制执行。

您可在 Azure Active Directory 中查看关联的门户应用程序。 此应用程序的名称将是 Microsoft CRM 门户，门户 ID 位于 Azure Active Directory 应用程序的**应用 ID URI** 字段中。 配置门户的人员负责该应用程序。 您不应删除或修改此应用程序，或者您可能中断门户功能。 您必须是应用程序的负责人才能从 Power Apps 门户管理中心管理门户。

## <a name="authentication-key"></a>身份验证密钥

若要使用 Azure Active Directory 应用程序将门户连接到 Common Data Service，需要一个身份验证密钥连接到 Azure Active Directory 应用程序。 此密钥在您配置门户时生成，此密钥的公共部分将自动上载到 Azure Active Directory 应用程序。

> [!IMPORTANT]
> 身份验证密钥将在两年后过期。 密钥必须每两年续订一次，以确保您的门户可以继续连接到 Common Data Service 环境。 如果您不更新密钥，门户将停止工作。  

### <a name="authentication-key-details"></a>身份验证密钥详细信息

身份验证密钥的详细信息显示在 Power Apps 门户管理中心和门户中。

**Power Apps 门户管理中心**

1. 打开 [Power Apps 门户管理中心](admin-overview.md)。

2. 选择**管理门户身份验证密钥**。 身份验证密钥及其到期日期和指纹将显示。

   > [!div class=mx-imgBorder]
   > ![Power Apps 门户管理中心内的身份验证密钥详细信息](../media/manage-auth-key.png "Power Apps 门户管理中心内的身份验证密钥详细信息")

**门户**

1. 以管理员身份登录到门户。

2. 导航到 URL <portal_path>/_services/about。 身份验证密钥的到期日期将显示。 

   > [!div class=mx-imgBorder]
   > ![门户服务页面](../media/portal-services-page.png "门户服务页面")

> [!NOTE]
> 若要查看身份验证密钥的信息，您必须在同一个浏览器会话中登录到门户，且您必须拥有所有网站访问权限。

### <a name="authentication-key-expiration-notification"></a>身份验证密钥到期通知

在身份验证密钥到期前，您会收到电子邮件、Power Apps 门户管理中心和门户发来的通知。

**Email**

电子邮件将发送给已注册接收连接到其门户的组织的电子邮件通知的用户。 有关注册接收电子邮件通知的详细信息：[管理发给管理员的电子邮件通知](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-email-notifications)

电子邮件通知按照下列时间间隔发送： 
- 90 天 
- 60 天 
- 30 天 
- 15 天 
- 7 天 
- 6 天 
- 5 天 
- 4 天 
- 3 天 
- 2 天 
- 1 天 
- 12 小时 
- 6 小时 
- 3 小时

密钥过期后的每一天您都会收到通知，直到密钥过期一周。

> [!NOTE]
> - 时间间隔使用 UTC 时间从密钥到期之日起计算。
> - 电子邮件不保证严格按照上述间隔时间发送。 电子邮件通知可能会延迟或漏掉。 请务必另外在线检查密钥到期日期。

**Power Apps 门户管理中心**

密钥到期消息显示在页面顶部。

> [!div class=mx-imgBorder]
> ![Power Apps 门户管理中心内的身份验证密钥通知](../media/portal-admin-center-auth-notif.png "Power Apps 门户管理中心内的身份验证密钥通知")

**门户**

在导航到 URL <portal_path>/_services/about 时，有关密钥到期的通知将显示在页面底部。

> [!NOTE]
> 您必须在同一个浏览器会话中登录到您的门户，且您必须被分派了所有网站访问权限。

> [!div class=mx-imgBorder]
> ![门户中的身份验证密钥通知](../media/portal-service-page-auth-notif.png "门户中的身份验证密钥通知")

## <a name="renew-portal-authentication-key"></a>续订门户身份验证密钥

您必须每两年续订一次密钥，以确保您的门户可以连接到 Common Data Service 环境。

> [!NOTE]
> 若要续订密钥，您必须具有管理您的门户的权限。

1. 打开 [Power Apps 门户管理中心](admin-overview.md)。

2. 选择**管理门户身份验证密钥**。 身份验证密钥及其到期日期和指纹将显示。

    > [!div class=mx-imgBorder]
    > ![管理门户身份验证密钥](../media/manage-portal-auth-key.png "管理门户身份验证密钥")

3. 选择**更新密钥**。

4. 在消息中选择**更新**。 更新过程将启动，消息将显示。

> [!NOTE]
> - 当此过程在后台运行的同时，门户将重新启动一次。
> - 更新密钥后，它的有效期是两年。
> - 此过程需要五到七分钟时间。

### <a name="troubleshooting"></a>疑难解答​​

如果密钥更新失败，将出现错误消息并提示执行以下操作：

- **重试身份验证密钥更新**。 此操作允许您重新开始门户的身份验证密钥更新过程。 如果更新多次失败，请与 Microsoft 支持联系。

    > [!div class=mx-imgBorder]
    > ![重试门户身份验证密钥更新](../media/retry-auth-key-update.png "重试门户身份验证密钥更新")