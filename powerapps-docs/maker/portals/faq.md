---
title: 常见问题 |Microsoft Docs
description: PowerApps 门户中的常见问题。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: eb7228f669fe8c36e25a18f4db0c7e4c4964a42d
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72976682"
---
# <a name="powerapps-portals-faq"></a>PowerApps 门户常见问题解答

我们已经编译了常见问题列表，并提供了一些简短答案来帮助你快速访问你的信息。

## <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>我收到一个错误，指出只能创建一个门户。

目前，你只能在环境中为每种语言创建一个门户。 如果尝试创建多个门户，你将看到一条错误消息，如下所示：

> [!div class=mx-imgBorder]
> ![最大门户创建错误](media/portal-max-error.png "最大门户创建错误")

若要创建更多门户网站，必须使用错误消息中的 "**创建新环境**" 链接创建新环境。 有关创建门户的详细信息，请参阅[创建门户](create-portal.md)。

## <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>我遇到了错误，无法删除门户。

如果你没有足够的权限删除门户，你将看到如下错误：

> [!div class=mx-imgBorder]
> ![删除门户错误](media/portal-delete-error.png "删除门户错误")

有关删除门户和所需权限的信息，请参阅[删除门户](manage-existing-portals.md#delete)。

## <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>我遇到了错误，无法创建门户。

如果你没有足够的权限在环境中创建门户，你将看到如下错误：

> [!div class=mx-imgBorder]
> ![创建门户错误](media/portal-create-error.png "创建门户错误")

有关创建门户和所需权限的信息，请参阅[创建门户](create-portal.md)。

## <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>我收到消息： "您的数据没有准备就绪"。

有时，数据库创建可能需要一些时间，并且在主页上可能不会反映正确的状态。 在这种情况下，你将看到以下消息：

> [!div class=mx-imgBorder]
> ![数据未就绪](media/data-not-ready.png "数据未就绪")

如果你继续获取 "创建数据库" 提示或数据未就绪，则可以尝试在**从空白**磁贴中选择门户之前刷新 PowerApps 主页。

## <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>我收到一个错误消息，指出没有必要的权限来创建 Azure Active Directory 应用程序。

创建门户时，门户会在与租户关联 Azure Active Directory 中注册为新的应用程序。 如果你没有足够的权限向 Azure Active Directory 租户注册应用程序，你将看到如下错误：

> [!div class=mx-imgBorder]
> ![Azure Active Directory 错误](media/azure-ad-error.png "Azure Active Directory 错误")

若要在 Azure Active Directory 中创建和注册应用程序，必须与租户管理员联系，以便为租户启用**应用注册**设置。 有关信息，请参阅[所需权限](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions)。

## <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>我收到错误，由全局管理员在此租户中阻止门户创建

如果全局管理员在租户中阻止创建门户，你将看到一个错误，如下所示：

> [!div class=mx-imgBorder]
> ![门户创建已阻止错误](media/portal-create-blocked-error.png "门户创建已阻止错误")

还必须与全局管理员联系，以允许非管理员创建门户。

如果你是全局管理员，则必须通过 PowerShell 禁用 `disablePortalsCreationByNonAdminUsers` 租户级别设置。 在 PowerShell 窗口中运行以下命令（以管理员身份运行 PowerShell）。

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

详细信息：[禁用在租户中创建门户](create-portal.md#disable-portal-creation-in-a-tenant)

## <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>我收到了一个错误，指出我没有适当的许可证来访问此网站。

使用门户访问经过身份验证的页面的组织的内部用户需要将许可证分配到门户连接到的环境。 可在[此处](https://docs.microsoft.com/en-us/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users)阅读有关内部用户的门户用户权限的详细信息。 如果环境未分配许可证，则内部用户将收到如下错误：

> [!div class=mx-imgBorder]
> ![门户登录错误](media/portal-login-error.png "门户登录错误")

