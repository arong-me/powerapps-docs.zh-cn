---
title: 将门户连接到 Common Data Service 环境 |MicrosoftDocs
description: 了解如何将门户连接到 Common Data Service 环境以及如何续订身份验证密钥。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 31632f4de1834855c696baa1b4b651ed777c8abd
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72977487"
---
# <a name="connect-to-a-common-data-service-environment-using-a-portal"></a>使用门户连接到 Common Data Service 环境

门户使用 Azure Active Directory 应用程序连接到 Common Data Service 的环境。 在设置门户的同一租户中创建应用程序。 在门户预配过程中，应用程序在 Common Data Service 环境中注册。

![使用 Common Data Service 环境连接门户]与(../media/connect-with-dynamics.png "Common Data Service 环境连接门户")

每个门户都具有与之关联的单独 Azure Active Directory 应用程序，无论该门户是否连接到相同的 Common Data Service 环境。 为门户创建的默认 Azure Active Directory 身份验证提供程序使用同一个 Azure Active Directory 应用程序对门户进行身份验证。 授权由分配给访问门户的用户的 web 角色强制执行。

可以在 Azure Active Directory 中查看关联的门户应用程序。 此应用程序的名称将是 Microsoft CRM 门户，门户 ID 位于 Azure Active Directory 应用程序中的 "**应用程序 ID URI** " 字段。 设置门户的人员拥有此应用程序。 不应删除或修改此应用程序，否则可能会中断门户功能。 你必须是应用程序所有者才能从 PowerApps 门户管理中心管理门户。

## <a name="authentication-key"></a>身份验证密钥

对于使用 Azure Active Directory 应用程序连接到 Common Data Service 的门户，需要一个连接到 Azure Active Directory 应用程序的身份验证密钥。 此密钥是在预配门户时生成的，此密钥的公开部分会自动上载到 Azure Active Directory 应用程序。

> [!IMPORTANT]
> 身份验证密钥将在两年后过期。 必须每两年续订一次，以确保门户将继续连接到 Common Data Service 的环境。 如果不更新密钥，门户将停止工作。  

### <a name="authentication-key-details"></a>身份验证密钥详细信息

在 PowerApps 门户管理中心和门户上显示身份验证密钥的详细信息。

**PowerApps 门户管理中心**

1. 打开[PowerApps 门户管理中心](admin-overview.md)。

2. 选择 "**管理门户身份验证密钥**"。 身份验证密钥连同其到期日期和指纹一起显示。

   > [!div class=mx-imgBorder]
   > Powerapps 门户管理中心中的![身份验证密钥详细信息](../media/manage-auth-key.png "powerapps 门户管理中心中的身份验证密钥详细信息")

**端口**

1. 以管理员身份登录到门户。

2. 导航到 URL < portal_path >/_services/about。 显示身份验证密钥到期日期。 

   > [!div class=mx-imgBorder]
   > ![门户服务页](../media/portal-services-page.png "门户服务页")

> [!NOTE]
> 若要查看身份验证密钥信息，必须在同一浏览器会话中登录到该门户，并且必须具有所有网站访问权限。

### <a name="authentication-key-expiration-notification"></a>身份验证密钥过期通知

身份验证密钥过期之前，你将通过电子邮件、PowerApps 门户管理中心和门户通知你。

**Email**

电子邮件将发送给已注册为连接到其门户的组织的电子邮件通知的用户。 有关注册电子邮件通知的详细信息：[管理向管理员发送电子邮件通知](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-email-notifications)

电子邮件通知按以下间隔发送： 
- 90天 
- 60天 
- 30天 
- 15天 
- 7天 
- 6天 
- 5天 
- 4天 
- 3天 
- 2天 
- 1天 
- 12小时 
- 6小时 
- 3小时

密钥过期后，还会在密钥过期后收到通知。

> [!NOTE]
> - 间隔从密钥到期日期以 UTC 计算。
> - 电子邮件不能保证按以上所列的间隔准确无误。 电子邮件通知可能会延迟或丢失。 务必同时检查密钥到期日期是否联机。

**PowerApps 门户管理中心**

页面顶部会显示一条关于密钥过期的消息。

> [!div class=mx-imgBorder]
> Powerapps 门户管理中心![中的身份验证密钥通知](../media/portal-admin-center-auth-notif.png "powerapps 门户管理中心中的管理员中心身份验证密钥通知")

**端口**

导航到 URL < portal_path >/_services/about "时，将在页面底部显示有关密钥过期的通知。

> [!NOTE]
> 你必须在同一浏览器会话中登录到门户，并且必须分配有 "所有网站" 访问权限。

> [!div class=mx-imgBorder]
> 门户上门户(../media/portal-service-page-auth-notif.png "身份验证密钥通知")![上的身份验证密钥通知]

## <a name="renew-portal-authentication-key"></a>续订门户身份验证密钥

每两年都必须续订密钥，以确保门户可以连接到 Common Data Service 的环境。

> [!NOTE]
> 若要续订密钥，你必须拥有管理门户的权限。

1. 打开[PowerApps 门户管理中心](admin-overview.md)。

2. 选择 "**管理门户身份验证密钥**"。 身份验证密钥连同其到期日期和指纹一起显示。

    > [!div class=mx-imgBorder]
    > ![管理门户身份验证密钥](../media/manage-portal-auth-key.png "管理门户身份验证密钥")

3. 选择 "**更新密钥**"。

4. 在消息中选择 "**更新**"。 将启动更新过程，并显示一条消息。

> [!NOTE]
> - 当此进程在后台运行时，门户将重启一次。
> - 更新密钥时，它将更新两年。
> - 此过程需要5到7分钟。

### <a name="troubleshooting"></a>故障排除

如果密钥更新失败，将显示一条错误消息以及以下操作：

- **重试身份验证密钥更新**。 此操作允许您重新启动门户身份验证密钥更新过程。 如果更新失败多次，请联系 Microsoft 支持部门。

    > [!div class=mx-imgBorder]
    > ![重试门户身份验证密钥更新](../media/retry-auth-key-update.png "重试门户身份验证密钥更新")