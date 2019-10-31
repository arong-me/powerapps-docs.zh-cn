---
title: 常见问题 | Microsoft Docs
description: PowerApps 门户中的常见问题。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 10/02/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="powerapps-portals-faq"></a>PowerApps 门户常见问题解答

我们编译了一个常见问题列表并提供了简短的答案来帮助你快速获得所需信息。

## <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>我收到一个错误，显示只能创建一个门户。

当前，在每种语言的环境中，每种类型只能创建一个门户。 如果您尝试创建多个门户，则会看到如下错误消息：

> [!div class=mx-imgBorder]
> ![最大门户创建错误](media/portal-max-error.png "最大门户创建错误")

要创建更多门户，您必须使用错误消息中的**创建新环境**链接创建一个新环境。 有关创建门户的详细信息，请参阅[创建门户](create-portal.md)。

## <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>我收到无法删除我的门户的错误。

如果权限不足，无法删除门户，您将看到如下错误：

> [!div class=mx-imgBorder]
> ![删除门户错误](media/portal-delete-error.png "删除门户错误")

有关删除门户和所需权限的信息，请参阅[删除门户](manage-existing-portals.md#delete)。

## <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>我收到无法创建门户的错误。

如果权限不足，无法在环境中创建门户，您将看到如下错误：

> [!div class=mx-imgBorder]
> ![创建门户错误](media/portal-create-error.png "创建门户错误")

有关创建门户和所需权限的信息，请参阅[创建门户](create-portal.md)。

## <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>我收到消息：“您的数据还没有准备好”。

有时创建数据库可能会花费一些时间，并且正确的状态可能不会反映在主页上。 在这种情况下，您会看到以下消息：

> [!div class=mx-imgBorder]
> ![数据未准备好](media/data-not-ready.png "数据未准备好")

如果继续出现创建数据库提示或数据尚未准备好的提示，则可以尝试刷新 PowerApps 主页，然后再选择“从空白门户开始(预览)”磁贴。

## <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>我收到错误，显示我没有创建 Azure Active Directory 应用程序所需的权限。

创建门户时，会将门户作为新应用程序注册在与租户关联的 Azure Active Directory 中。 如果您没有足够的权限向 Azure Active Directory 租户注册应用程序，则会看到以下错误：

> [!div class=mx-imgBorder]
> ![Azure Active Directory 错误](media/azure-ad-error.png "Azure Active Directory 错误")

若要在 Azure Active Directory 中创建和注册应用程序，必须与租户管理员联系以打开租户的**应用注册**设置。 有关信息，请参阅[必需权限](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions)。

## <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>我收到一个错误，显示全局管理员在此租户中阻止了门户创建

如果您的全局管理员阻止在租户中创建门户，您将看到以下错误：

> [!div class=mx-imgBorder]
> ![门户创建被阻止错误](media/portal-create-blocked-error.png "门户创建被阻止错误")

您必须与全局管理员联系，以同时允许非管理员创建门户。

如果您是全局管理员，则必须通过 PowerShell 禁用 `disablePortalsCreationByNonAdminUsers` 租户级别设置。 在 PowerShell 窗口中运行以下命令（以管理员身份运行 PowerShell）。

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

详细信息：[在租户中禁用门户创建](create-portal.md#disable-portal-creation-in-a-tenant)
