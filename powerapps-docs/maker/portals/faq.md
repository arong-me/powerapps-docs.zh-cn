---
title: 常见问题 | Microsoft Docs
description: Power Apps 门户中的常见问题。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 12/27/2019
ms.author: shjais
ms.reviewer: tapanm
ms.openlocfilehash: 35f68ef861ac8908e1eb9227df6768b7a2c2c9f3
ms.sourcegitcommit: 5ec7c7f04fe41896dec966706a3b3d295648726f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/06/2020
ms.locfileid: "2934094"
---
# <a name="power-apps-portals-faq"></a>Power Apps 门户常见问题解答

我们编译了一个常见问题列表并提供了简短的答案来帮助你快速获得所需信息。

## <a name="general"></a>常规

### <a name="when-is-an-add-on-portal-in-suspended-state"></a>附加产品门户何时处于暂挂状态？

到期后，[使用之前购买的门户附加产品计划预配的](provision-portal-add-on.md)门户将暂挂。 对于试用门户，到期期间为 30 天，但是，生产中已购买许可证的附加产品门户可能有所不同。 7 天后将删除暂挂试用门户，但是，生产门户的暂挂期可能不同。 有关更多详细信息，请参阅附加产品门户的[门户生命周期](./admin/portal-lifecycle.md#considerations-for-add-on-portals)。

### <a name="how-do-i-redirect-a-user-to-a-default-page-after-signing-in"></a>如何在用户登录后将用户重定向到默认页面？

您可以将门户配置为在用户登录后将用户重定向到默认页面。 若要实现此功能，您可以在主页 Web 模板中包含 JavaScript 代码。

例如，如果要将所有用户在登录后重定向到论坛页面，您可以在主页 Web 模板内包含 JavaScript 代码，如下所示：

```xml
{% if user %}
//if any user logs in
<script>
  window.location.href='./forums/'
</script>
{% else %}
//Home web page code, if you don't want to display the page when the user is being redirected
{% endif %}
//Home web page code, if you want to display the page when the user is being redirected
```

有关使用 Liquid 模板的详细信息，请参阅[使用 Liquid 模板](liquid/liquid-overview.md)。

### <a name="im-getting-an-error-that-only-one-portal-can-be-created"></a>我收到一个错误，显示只能创建一个门户。

当前，在每种语言的环境中，每种类型只能创建一个门户。 如果您尝试创建多个门户，则会看到如下错误消息：

> [!div class=mx-imgBorder]
> ![最大门户创建错误](media/portal-max-error.png "最大门户创建错误")

要创建更多门户，您必须使用错误消息中的**创建新环境**链接创建一个新环境。 有关创建门户的详细信息，请参阅[创建门户](create-portal.md)。

### <a name="im-getting-an-error-that-i-cant-delete-my-portal"></a>我收到无法删除我的门户的错误。

如果权限不足，无法删除门户，您将看到如下错误：

> [!div class=mx-imgBorder]
> ![删除门户错误](media/portal-delete-error.png "删除门户错误")

有关删除门户和所需权限的信息，请参阅[删除门户](manage-existing-portals.md#delete)。

### <a name="im-getting-an-error-that-i-cant-create-a-portal"></a>我收到无法创建门户的错误。

如果权限不足，无法在环境中创建门户，您将看到如下错误：

> [!div class=mx-imgBorder]
> ![创建门户错误](media/portal-create-error.png "创建门户错误")

有关创建门户和所需权限的信息，请参阅[创建门户](create-portal.md)。

### <a name="im-getting-the-message-your-data-isnt-quite-ready"></a>我收到消息：“您的数据还没有准备好”。

有时创建数据库可能会花费一些时间，并且正确的状态可能不会反映在主页上。 在这种情况下，您会看到以下消息：

> [!div class=mx-imgBorder]
> ![数据尚未准备好](media/data-not-ready.png "数据尚未准备好")

如果继续出现创建数据库提示或数据尚未准备好的提示，则可以尝试刷新 Power Apps 主页，然后再选择**从空白门户开始**磁贴。

### <a name="im-getting-an-error-that-i-dont-have-required-permissions-to-create-azure-active-directory-applications"></a>我收到错误，显示我没有创建 Azure Active Directory 应用程序所需的权限。

创建门户时，会将门户作为新应用程序注册在与租户关联的 Azure Active Directory 中。 如果您没有足够的权限向 Azure Active Directory 租户注册应用程序，则会看到以下错误：

> [!div class=mx-imgBorder]
> ![Azure Active Directory 错误](media/azure-ad-error.png "Azure Active Directory 错误")

若要在 Azure Active Directory 中创建和注册应用程序，必须与租户管理员联系以打开租户的**应用注册**设置。 有关信息，请参阅[必需权限](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions)。

### <a name="im-getting-an-error-that-portal-creation-is-blocked-in-this-tenant-by-global-administrator"></a>我收到一个错误，显示全局管理员在此租户中阻止了门户创建

如果您的全局管理员阻止在租户中创建门户，您将看到以下错误：

> [!div class=mx-imgBorder]
> ![门户创建被阻止错误](media/portal-create-blocked-error.png "门户创建被阻止错误")

您必须与全局管理员联系，以同时允许非管理员创建门户。

如果您是全局管理员，则必须通过 PowerShell 禁用 `disablePortalsCreationByNonAdminUsers` 租户级别设置。 在 PowerShell 窗口中运行以下命令（以管理员身份运行 PowerShell）。

```
Set-TenantSettings -RequestBody @{ "disablePortalsCreationByNonAdminUsers" = $false }
```

详细信息：[在租户中禁用门户创建](create-portal.md#disable-portal-creation-in-a-tenant)

### <a name="im-getting-an-error-that-i-dont-have-appropriate-license-to-access-this-website"></a>我收到一个错误消息，显示我没有适当的许可证来访问该网站。

使用门户访问经过身份验证的页面的组织的内部用户需要将许可证分配给门户所连接的环境。 您可以在[此处](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-clarify-the-use-rights-to-portals-for-internal-users)阅读有关内部用户的门户用户权限的更多信息。 当环境未分配许可证时，内部用户将收到如下错误：

> [!div class=mx-imgBorder]
> ![门户登录错误](media/portal-login-error.png "门户登录错误")

## <a name="licensing-and-provisioning"></a>许可和设置

### <a name="how-do-i-get-a-portal-subscription"></a>如何获取门户订阅？

[Power Apps 门户](overview.md) 现在在 Power Apps 中完全独立存在。 不再需要许可证即可预配门户。 用户对门户的访问需要许可证，具体取决于角色类型。 有关更多详细信息，请参阅 [Power Apps 门户许可常见问题](https://docs.microsoft.com/power-platform/admin/powerapps-flow-licensing-faq#can-you-share-more-details-regarding-the-new-power-apps-portals-licensing)。

### <a name="how-do-i-change-the-audience-and-type-of-a-portal-after-it-is-provisioned"></a>如何在设置门户后更改门户的访问群体和类型？

在设置门户后，将禁用更改门户访问群体的选项。

但是，您可以在门户设置后更改门户的访问群体和类型，可按照[更改门户的 Dynamics 365 实例、访问群体或类型](admin/change-dynamics-instance.md)中的步骤操作。

> [!NOTE]
> - 建议重置和再次预配门户，以便更改受众、门户类型、组织等。 详细信息：[重置门户](admin/reset-portal.md)
> - 更改 Dynamics 365 实例仅适用于使用较低版本门户加载项预配的门户。

### <a name="how-do-i-change-the-base-url-of-a-portal-after-it-is-provisioned"></a>如何在配置门户后更改门户的基础 URL？

您可以在设置门户后更改门户的基础 URL，按照[更改门户的基础 URL](admin/change-base-url.md) 中的步骤操作。

### <a name="how-do-i-delete-a-portal-completely-after-it-is-provisioned"></a>如何在设置门户后将其完全删除？

门户由下列组件构成：

- **门户网站主机**：门户网站主机是建立实际网站的门户代码。

- **门户解决方案**：在 Common Data Service 环境中安装以及包含任何门户的元数据实体的解决方案。

要完全删除门户，需要删除门户网站主机并从您的 Common Data Service 环境中卸载门户解决方案。

若要重置门户主机，请执行[重置门户](admin/reset-portal.md)中的步骤。 请务必注意，重置门户主机不会影响在您的 Common Data Service 环境中完成的配置。

要删除门户解决方案，必须从 Dynamics 365 解决方案资源管理器 UI 删除解决方案。 门户解决方案卸载的顺序在[卸载门户解决方案](https://community.dynamics.com/365/b/dynamics365portalssupport/archive/2017/02/27/portal-troubleshooting-part-three-uninstalling-portal-solutions)中提供。

## <a name="common-data-service-environment-lifecycle"></a>Common Data Service 环境生命周期

### <a name="we-recently-moved-our-common-data-service-environment-from-one-geolocation-or-tenant-to-another-how-do-we-handle-portals-connected-to-our-organization"></a>我们近期将 Common Data Service 环境从一个地理位置或租户移至了另一个地理位置或租户。 我们如何处理连接到我们的组织的门户？

在将 Common Data Service 环境从一个地理位置或租户移至另一个地理位置或租户时，与该组织关联的门户不会自动移动。 而且，由于您的组织已经移动，与该组织关联的任何门户都不会工作，并会在启动时引发错误。

再次将您的门户关联到相关组织：

1. 按照[重置门户](admin/reset-portal.md)中的步骤从现有地理位置或租户重置现有门户主机。 这将会删除您的关联的门户资源，在操作完成后，门户 URL 将无法访问。

2. 在重置现有门户后，转到新租户（或现有门户的新地理位置）并设置其中的可用门户。

### <a name="after-restoring-a-common-data-service-environment-from-an-old-backup-the-portal-connected-to-the-organization-is-not-working-how-do-we-fix-it"></a>从旧备份还原 Common Data Service 环境后，连接到组织的门户将不工作。 我们如何解决？

从备份还原 Common Data Service 环境后，您的组织中的各种更改将完成，这可能断开您的门户与组织的连接。 若要解决此问题，请执行以下操作：

- 如果组织 ID 在还原操作后相同，门户解决方案仍然可用：

1. 打开 [Power Apps 门户管理中心](admin/admin-overview.md)。
2. 转到**门户详细信息**选项卡。
3. 在**门户状态**下拉列表中，选择**关**。
4. 选择**更新**。 
5. 更新操作完成后，将**门户状态**下拉列表设置为**开**，然后选择**更新**。

  您的门户将重新启动，与组织的连接将再次创建。

- 如果组织 ID 在还原操作后不同或门户解决方案被从您的组织中删除：

  - 在这种情况下，最好按照[重置门户](admin/reset-portal.md)中的步骤重置门户，然后重新设置它。

### <a name="we-recently-changed-the-url-of-our-common-data-service-environment-and-our-portal-stopped-working-how-do-we-fix-it"></a>我们近期更改了我们的 Common Data Service 环境的 URL，我们的门户已停止工作。 我们如何解决？

在更改您的 Common Data Service 环境的 URL 后，您的门户将停止工作，因为它无法再识别 Common Data Service 环境 URL。 若要解决此问题，请执行以下操作：

1. 打开 [Power Apps 门户管理中心](admin/admin-overview.md)。
2. 转到**门户操作** > **更新 Dynamics 365 URL**。
3. 请按照向导内的说明操作。

您的门户将重新启动并重新开始工作。

## <a name="debugging-and-fixing-problems"></a>调试和修复问题

### <a name="when-accessing-my-portal-i-see-a-generic-error-page-how-can-i-see-the-actual-error"></a>在访问我的门户时，我看到常规错误页。 我如何才能看到实际错误？

在尝试呈现门户时不论何时发生服务器错误，常规错误页都会显示给最终用户，并包含错误的时间戳和活动 ID。 门户管理员可以将门户配置为获取实际错误详细信息，这在调试和修复问题时很有帮助。 若要看到实际错误：

- **在门户上禁用自定义错误页**：这将关闭自定义错误页，并会允许您在导航到该页面时看到任何错误的完整堆栈跟踪。 您可以按照[禁用自定义错误](admin/view-portal-error-log.md#disable-custom-error)中的步骤禁用自定义错误。

只有当您开发门户时比较适合使用此方法。 在您的门户可供您的用户使用时，您应重新启用自定义错误。 详细信息：[查看门户错误日志](admin/view-portal-error-log.md)

- **启用诊断日志记录**：这将允许您在 Azure Blob 存储帐户中获取所有门户错误。 您可以按照[访问门户错误日志](admin/view-portal-error-log.md#access-portal-error-logs)中的步骤启用诊断日志记录。

在启用诊断日志记录时，可通过使用常规错误页上显示的活动 ID 搜索用户报告的特定错误。 活动 ID 随错误详细信息一起记录，对于查找实际问题很有用。

## <a name="portal-administration-and-management"></a>门户管理

### <a name="how-do-i-use-a-custom-login-provider-on-my-portal"></a>如何在我的门户中使用自定义登录提供程序？

门户支持为标准身份验证协议提供支持的任何自定义登录提供程序。 我们支持任何自定义 IDP 的 OpenIdConnect、SAML2 和 WS 联合身份验证协议。 OAuth 2 仅支持一组固定的已知 IDP。 有关如何设置 IDP 配置的详细信息，请参阅[配置门户身份验证](configure/configure-portal-authentication.md)。

### <a name="how-do-i-get-new-portal-releases-in-my-sandbox-portal-first-before-it-gets-applied-to-production"></a>如何在应用于生产前在我的沙盒门户中获取新的门户版本？

任何门户发布都经过两个阶段：早期升级和公开上市 (GA)。 在早期升级阶段，仅升级标记为早期升级的门户。 若要在沙盒（开发或测试）环境中获取新的门户版本，可以为您的门户启用早期升级。 有关如何为门户启用早期升级的信息，请参阅[升级门户](https://docs.microsoft.com/dynamics365/customer-engagement/portals/upgrade-portal)。

### <a name="how-do-i-use-a-custom-domain-name-for-my-portal"></a>如何为我的门户使用自定义域名？

您可以使您的门户使用自定义域名来替代标准 `microsoftcrmportals.com` 域名。 详细信息：[将您的门户链接到自定义域](admin/add-custom-domain.md)

## <a name="portal-checker"></a>门户检查器

### <a name="portal-does-not-load-and-displays-a-generic-error-page-server-error-in--application"></a>门户无法加载，并显示常规错误页（“/”应用程序中发生了服务器错误） 

此问题可能是多种原因造成的，如门户无法连接到基础 Common Data Service 环境，Common Data Service 环境不存在或其 URL 已更改，请求 Common Data Service 环境超时等。 运行门户检查器工具时，将尝试确定确切原因，并提供正确的缓解方法。 

下面是最常见原因的列表及其相应的缓解步骤：

#### <a name="url-of-the-connected-common-data-service-environment-has-changed"></a>连接的 Common Data Service 环境的 URL 发生了更改 

针对组织设置了门户后，用户更改 Common Data Service 环境的 URL 时会发生此问题。 若要修复此问题，请更新 Dynamics 365 URL：

1. 打开 [Power Apps 门户管理中心](admin/admin-overview.md)。
2. 转到**门户操作** > **更新 Dynamics 365 URL**。 成功执行此操作之后，将更新 Common Data Service 环境 URL，而门户将开始工作。

#### <a name="common-data-service-environment-connected-to-your-portal-is-in-administration-mode"></a>连接到您的门户的 Common Data Service 环境处于管理员模式

将组织从生产模式更改为沙盒模式期间，或者在组织管理员手动更改组织期间，该 Common Data Service 环境进入管理模式时，将发生此问题。

如果是这种原因，可通过执行[此处](https://docs.microsoft.com/dynamics365/admin/manage-sandbox-instances#administration-mode)列出的操作禁用管理模式。 禁用管理模式之后，门户将正常工作。

#### <a name="authentication-connection-between-common-data-service-environment-and-portal-is-broken"></a>Common Data Service 环境与门户之间的身份验证连接已断开

当因为 Common Data Service 环境已从备份恢复或已删除并通过备份重新创建而导致 Dynamic 365 组织与门户之间的身份验证连接断开时，将发生此问题。 若要解决此问题，请执行以下操作：

1. 打开 [Power Apps 门户管理中心](admin/admin-overview.md)。
2. 在**门户详细信息**选项卡中，选择**门户状态**列表中的**关闭**。
3. 选择**更新**。
4. 选择**门户状态**列表中的**打开**。
5. 选择**更新**。 门户将重新启动，并且可以建立身份验证连接。

但是，在某些情况下，特别是恢复操作（或重新设置了组织）后组织 ID 已更改，这些缓解步骤无效。 在这些情况下，可以重置门户并针对同一个实例重新设置门户。 有关如何重置门户的信息，请参阅[重置门户](admin/reset-portal.md)。

#### <a name="request-to-common-data-service-environment-has-timed-out"></a>对 Common Data Service 环境的请求已超时

此问题通常是暂时性问题，如果对 Common Data Service 环境的 API 请求超时，可能发生此问题。API 请求开始工作后，此问题将自行缓解。 若要缓解此问题，也可以重新启动门户：

1. 打开 [Power Apps 门户管理中心](admin/admin-overview.md)。
2. 转到**门户操作** > **重新启动**。

如果重新启动门户无效，并且此问题长期出现，请联系 Microsoft 支持获取帮助。

#### <a name="website-binding-not-found"></a>未找到网站绑定

从基础 Common Data Service 环境删除了门户的网站绑定记录，并且门户无法自动创建绑定时，将发生此问题。 若要解决此问题，请执行以下操作：

1. 打开[“门户管理”应用](configure/configure-portal.md)。
2. 转到**门户** > **网站绑定**。
3. 删除指向您的门户的所有网站绑定记录。 **站点名称**字段可以帮助您确定门户的网站绑定记录。
4. 删除了所有网站绑定记录之后，请重新启动门户。

完成上面的步骤之后，您的门户将重新启动，并自动重新创建网站绑定记录。

但是，当您的实例中的可用网站记录的 GUID 与默认安装门户期间创建的不同时，门户将无法自动重新创建网站绑定记录。 在此情况下，请执行以下步骤：

1. 删除与您的门户有关的所有网站绑定记录。
2. 使用以下值手动创建网站绑定记录：
  - **名称**：可以是任意字符串
  - **网站**：选择要在门户中呈现的网站记录
  - **站点名称**：键入门户的主机名，即 开头无 https:// 的门户 URL。 如果您的门户在使用自定义域名，此处请使用自定义域名。
  - 让其他所有字段保留为空。
3. 重新创建网站绑定记录之后，从 Power Apps 门户管理中心重新启动门户。

#### <a name="an-unexpected-error-has-occurred-while-trying-to-connect-to-your-common-data-service-environment"></a>尝试连接到您的 Common Data Service 环境时发生了意外错误

此情况可能是某个意外问题导致的。 若要缓解此情况，可以尝试重置门户或重新设置门户。 有关如何重置门户的信息，请参阅[重置门户](admin/reset-portal.md)。

如果重置门户和重新设置无法解决此问题，请联系 Microsoft 支持获取帮助。

### <a name="portal-is-not-displaying-updated-data-from-common-data-service-environment"></a>门户不显示来自 Common Data Service 环境的更新数据

门户中显示的任何数据都是从门户高速缓存呈现的。 只要更新 Common Data Service 环境中的数据，都将更新此高速缓存。 但是，此过程为异步过程，可能需要最多 15 分钟。 如果在门户的元数据实体（如网页、Web 文件、内容片段、站点设置等）中进行更改，建议手动清除高速缓存或从 Power Apps 门户管理中心重新启动门户。 有关如何清除缓存的信息，请参阅[清除门户的服务器端高速缓存](admin/clear-server-side-cache.md)。 

但是，如果发现非门户元数据实体中长期存在过时数据，可能是下面列出的各种问题造成的：

#### <a name="entities-not-enabled-for-cache-invalidation"></a>未对实体启用高速缓存无效

如果仅看到特定实体的过时数据，而不是看到所有实体过时数据，可能是因为未对整个特定实体启用“更改跟踪”元数据。

如果运行门户检查器（自助诊断）工具，将在实体列表或实体窗体和 Web 窗体中列出门户中引用，但未启用更改跟踪的所有实体的“对象类型”代码。 请通过使用[浏览组织的元数据](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/browse-your-metadata)中介绍的步骤浏览您的元数据

如果在这些实体中的任何一个内遇到过时数据问题，可通过使用 Power Apps 门户管理中心启用更改跟踪。 UI 或 Dynamics 365 API。 详细信息：[为实体启用更改跟踪](https://docs.microsoft.com/dynamics365/customerengagement/on-premises/developer/use-change-tracking-synchronize-data-external-systems#enable-change-tracking-for-an-entity)

#### <a name="organization-not-enabled-for-change-tracking"></a>尚未为组织启用更改跟踪

除了为每个实体启用更改跟踪，还必须为整个组织启用更改跟踪。 提交门户设置请求时，将为组织启用更改跟踪。 但是，如果从旧数据库恢复组织或重置组织，更改跟踪可能中断。 若要解决此问题，请执行以下操作：

1. 打开 [Power Apps 门户管理中心](admin/admin-overview.md)。
2. 在**门户详细信息**选项卡中，选择**门户状态**列表中的**关闭**。
3. 选择**更新**。
4. 选择**门户状态**列表中的**打开**。
5. 选择**更新**。 门户将重新启动，并且可以建立身份验证连接。

### <a name="performance-best-practices"></a>性能最佳实践

多种配置问题可能导致门户中发生性能问题。 所有自带门户模板均已针对各种可能影响门户性能的负载情况和配置进行了测试，而下面是可能导致门户中发生性能问题的常见门户配置的列表。

门户检查器（自助诊断）工具还将通过查看您的门户配置来指出这些问题。

#### <a name="web-page-tracking-enabled"></a>已启用网页跟踪

为门户网页启用页面跟踪可能导致门户中发生性能问题。 从 Dynamics 365 门户的 2018 年 1 月版本开始，已弃用此功能。 详细信息：[Dynamics 365 门户：已弃用的功能](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

门户检查器工具将列出已启用了页面跟踪的所有网页（根网页和内容网页）。 应通过执行以下步骤禁用这些页面：

1. 打开[“门户管理”应用](configure/configure-portal.md)。
2. 转到“高级查找”。
3. 搜索已启用了**启用跟踪（已弃用）** 字段（值为“是”）的所有网页。
4. 批量编辑所有这些页面，并将该字段设置为**否**。

也可以转至门户检查器结果中列出的每个页面，然后将**启用跟踪（已弃用）** 字段的值设置为**否**。 请务必了解如果在使用 Dynamics 365 门户解决方案版本 9.x，则窗体中将不显示该字段，您可能需要首先将其添加到窗体中。 

#### <a name="web-file-tracking-enabled"></a>已启用 Web 文件跟踪

为门户 Web 文件启用页面跟踪可能导致门户中发生性能问题。 从 Dynamics 365 门户的 2018 年 1 月版本开始，已弃用此功能。 详细信息：[Dynamics 365 门户：已弃用的功能](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

门户检查器工具将列出已启用了页面跟踪的所有 Web 文件。 应通过执行以下步骤禁用这些文件：

1. 打开[“门户管理”应用](configure/configure-portal.md)。
2. 转到“高级查找”。
3. 搜索已启用了**启用跟踪（已弃用）** 字段（值为“是”）的所有 Web 文件。
4. 批量编辑所有这些记录，并将该字段设置为**否**。

也可以转至门户检查器结果中列出的每个文件，然后将**启用跟踪（已弃用）** 字段的值设置为**否**。 请务必了解如果在使用门户解决方案版本 9.x，则窗体中将不显示该字段，您可能需要首先将其添加到窗体中。 

#### <a name="login-tracking-enabled"></a>已启用登录跟踪

启用门户登录跟踪可能导致门户中发生性能问题。 从 Dynamics 365 门户的 2018 年 1 月版本开始，已弃用此功能。 详细信息：[Dynamics 365 门户：已弃用的功能](https://blogs.msdn.microsoft.com/crm/2018/03/20/portal-capabilities-for-dynamics-365-deprecated-features/)

门户检查器工具将检查是否为门户启用了登录跟踪，如果已启用，将显示检查失败。 应通过执行以下步骤禁用登录跟踪：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  转到**门户** > **站点设置**。
3.  搜索名称为 `Authentication/LoginTrackingEnabled` 的站点设置。
4.  将此站点设置的值更改为 **False**，或删除此站点设置。
5.  重新启动门户。 

#### <a name="header-output-cache-is-disabled"></a>已禁用页眉输出高速缓存

在您的门户中禁用页眉输出高速缓存可能会导致高负载情况下门户中出现性能问题。 下面提供了有关此功能的更多详细信息：[在门户上启用页眉和页脚输出高速缓存](configure/enable-header-footer-output-caching.md)

门户检查器工具将检查门户中是否已禁用了页眉输出高速缓存，如果已禁用，将显示检查失败。 若要启用：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  转到**门户** > **站点设置**。
3.  搜索名称为 `Header/OutputCache/Enabled` 的站点设置。
4.  如果此站点设置可用，请将“站点”设置的值更改为 **True**。 如果此站点设置不可用，请使用此名称创建一个新的站点设置，并将其值设置为 **True**。
5.  重新启动门户。 

#### <a name="footer-output-cache-is-disabled"></a>已禁用页脚输出高速缓存

在您的门户中禁用页脚输出高速缓存可能会导致高负载情况下门户中出现性能问题。 下面提供了有关此功能的更多详细信息：[在门户上启用页眉和页脚输出高速缓存](configure/enable-header-footer-output-caching.md)

门户检查器工具将检查门户中是否已禁用了页脚输出高速缓存，如果已禁用，将显示检查失败。 若要启用：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  转到**门户** > **站点设置**。
3.  搜索名称为 `Footer/OutputCache/Enabled` 的站点设置。
4.  如果此站点设置可用，请将“站点”设置的值更改为 **True**。 如果此站点设置不可用，请使用此名称创建一个新的站点设置，并将其值设置为 **True**。
5.  重新启动门户。 

#### <a name="large-number-of-web-file-records"></a>大量的 Web 文件记录

门户使用 Web 文件实体存储要在门户中使用的任何静态文件。 此实体的主要用例是存储网站的静态内容，如 CSS、JavaScript、图像文件等。 但是，此类文件过多可能导致门户的启动速度太慢。

门户检查器工具将检查这种情况，并且在门户中的活动 Web 文件超过 500 个时提供指示。 如果所有这些文件中都包含静态内容，如 CSS、JavaScript、图像文件等，可以采取下面的操作缓解此问题。

- 使用 Azure blob 存储或 CDN 之类外部文件服务器存储这些文件，然后在门户内或基础模板中的相应页面上引用这些文件。

- 如果不能将文件移到外部，请确保加载主页时不加载所有这些文件。 如果 Web 文件的父页面设置为主页，将随主页加载该文件。 若要避免这种情况，可以执行以下步骤：

  1. 创建无内容且模板为空的假网页。 此页面将用于创建 Web 文件的定向路径。 
  2. 对于主页上不需要的所有 Web 文件，将父页面更改为这个假网页。 完成后，Web 文件的完整路径为 `Portal URL/{dummy_webpage}/{web file}`
  3. 直接在要引用这个 Web 文件的页面的页面模板或 Web 模板的 HTML 中引用该文件。 这将在该页面中根据需要加载您的文件。 

#### <a name="loading-static-resources-cssjs-asynchronously"></a>异步加载静态资源 (css/js)

处理门户实施时，务必了解您将完全管理页面的 HTML，这意味着应遵守标准 Web 部署实践，以确保网页的客户端性能不受影响。 

网页中的性能问题的其中一个最常见的原因是，加载页面时同步加载大量静态资源 (css/js)。 同步加载大量 css/js 文件可能导致客户端长时间处理网页。 

对于门户，只要将某个 Web 文件直接关联到主页，都会在生成的 HTML 中创建一个依赖项，这意味着该 Web 文件将始终与主页一起加载。 如果该 Web 文件为 css/js 文件，可能同步加载，并且可能导致客户端处理时间变慢。 

若要避免这种情况，可以执行以下步骤： 

1. 如果主页上不需要某个 Web 文件，请确保不将该文件的父页面设置为主页，并重用上面介绍的机制根据需要加载该文件。
2. 根据需要在任何页面中加载 JavaScript 文件时，使用 `<async>` 或 `<defer>` HTML 属性异步加载该文件。
3. 根据需要加载 CSS 文件时，可使用 `<preload>` HTML 属性 (https://www.w3.org/TR/preload/) 或基于 JavaScript 的方法，因为所有浏览器中现在还不支持预加载。

#### <a name="entity-form-lookup-configuration"></a>实体窗体查找配置 

如果下拉列表中显示的记录量超过 200，并且经常改变，则让查找在实体窗体或 Web 窗体中显示为下拉模式可能非常占用性能。 此选项仅应用于静态查找，如国家/地区列表和省/直辖市/自治区列表，从而生成数量有限的记录。

如果为可能有大量记录的查找启用此选项，将导致有实体窗体的网页的加载时间变慢。 如果此页由大量用户使用，并多次加载，可能会导致整个网站变慢，并且将把网站资源用于呈现此页面。 对于这些情况，应该使用完整的查找体验，否则应该为所需外观生成调用（使用 Web 模板创建的）AJAX 终结点的自定义 HTML 控件。

#### <a name="number-of-web-roles"></a>Web 角色数目

Web 角色在门户中用于启用基于角色的访问控制。 通常会限制门户中的 Web 角色数量，因为也会限制权限的不同组合数量。 如果门户中的 Web 角色数量超过 100，可能导致影响门户所有页面的性能问题。

### <a name="an-active-home-site-marker-is-not-available-for-this-portal"></a>可用的“主页”站点标记不适用于此门户

当**主页**站点标记在门户配置中不可用时，发生此问题。 若要解决此问题，请执行以下操作：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  在左侧窗格中，选择**站点标记**。
3.  使用以下值创建一个新的站点标记： 
  - **名称**：主页
  - **网站**：选择门户主机的网站。
  - **页面**：选择设置为门户主页的网页记录。

### <a name="the-home-site-marker-is-not-pointing-to-any-webpage"></a>“主页”站点标记未指向任何网页

当**主页**站点标记可用，但是不指向任何网页时，发生此问题。 若要解决此问题，请执行以下操作：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  在左侧窗格中，选择**站点标记**。
3.  找到**主页**站点标记记录。
4.  将**页面**字段更新为指向门户的活动主页。

### <a name="the-home-site-marker-is-pointing-to-a-deactivated-web-page"></a>“主页”站点标记指向的是已停用的网页

当**主页**站点标记可用，但是指向已停用网页时，发生此问题。 若要解决此问题，请执行以下操作：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  在左侧窗格中，选择**站点标记**。
3.  找到**主页**站点标记记录。
4.  将**页面**字段更新为指向门户的活动主页。

### <a name="the-home-site-marker-is-not-pointing-to-home-page-of-the-portal"></a>“主页”站点标记未指向门户的主页

当**主页**站点标记可用，但是指向门户的非主页网页时，发生此问题。 若要解决此问题，请执行以下操作：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  在左侧窗格中，选择**站点标记**。
3.  找到**主页**站点标记记录。
4.  将**页面**字段更新为指向门户的活动主页。

### <a name="an-active-profile-site-marker-is-not-available-for-this-portal"></a>可用的“个人资料”站点标记不适用于此门户

当**个人资料**站点标记在门户配置中不可用时，发生此问题。 若要解决此问题，请执行以下操作：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  在左侧窗格中，选择**站点标记**。
3.  使用以下值创建一个新的站点标记： 
  - **名称**：个人资料
  - **网站**：选择门户主机的网站。
  - **页面**：选择设置为门户个人资料页的网页记录。

### <a name="the-profile-site-marker-is-not-pointing-to-any-webpage"></a>“个人资料”站点标记未指向任何网页

当**个人资料**站点标记可用，但是不指向任何网页时，发生此问题。 若要解决此问题，请执行以下操作：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  在左侧窗格中，选择**站点标记**。
3.  找到**个人资料**站点标记记录。
4.  将**页面**字段更新为指向门户的活动个人资料页。

### <a name="the-profile-site-marker-is-pointing-to-a-deactivated-web-page"></a>“个人资料”站点标记指向的是已停用的网页

当**个人资料**站点标记可用，但是指向已停用网页时，发生此问题。 若要解决此问题，请执行以下操作：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  在左侧窗格中，选择**站点标记**。
3.  找到**个人资料**站点标记记录。
4.  将**页面**字段更新为指向门户的活动个人资料页。

### <a name="an-active-page-not-found-site-marker-is-not-available-for-this-portal"></a>可用的“找不到页面”站点标记不适用于此门户

当**找不到页面**站点标记在门户配置中不可用时，发生此问题。 若要解决此问题，请执行以下操作：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  在左侧窗格中，选择**站点标记**。
3.  使用以下值创建一个新的站点标记： 
  - **名称**：找不到页面
  - **网站**：选择门户主机的网站。
  - **页面**：选择设置为门户“找不到页面”页的网页记录。

### <a name="the-page-not-found-site-marker-is-not-pointing-to-any-webpage"></a>“找不到页面”站点标记未指向任何网页

当**找不到页面**站点标记可用，但是不指向任何网页时，发生此问题。 若要解决此问题，请执行以下操作：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  在左侧窗格中，选择**站点标记**。
3.  找到**找不到页面**站点标记记录。
4.  将**页面**字段更新为指向门户的活动“找不到页面”页。

### <a name="the-page-not-found-site-marker-is-pointing-to-a-deactivated-web-page"></a>“找不到页面”站点标记指向的是已停用的网页

当**找不到页面**站点标记可用，但是指向已停用网页时，发生此问题。 若要解决此问题，请执行以下操作：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  在左侧窗格中，选择**站点标记**。
3.  找到**找不到页面**站点标记记录。
4.  将**页面**字段更新为指向门户的活动“找不到页面”页。

### <a name="an-active-access-denied-site-marker-is-not-available-for-this-portal"></a>可用的“拒绝访问”站点标记不适用于此门户

当**拒绝访问**站点标记在门户配置中不可用时，发生此问题。 若要解决此问题，请执行以下操作：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  在左侧窗格中，选择**站点标记**。
3.  使用以下值创建一个新的站点标记： 
  - **名称**：拒绝访问
  - **网站**：选择门户主机的网站。
  - **页面**：选择设置为门户“拒绝访问”页的网页记录。

### <a name="the-access-denied-site-marker-is-not-pointing-to-any-webpage"></a>“拒绝访问”站点标记未指向任何网页

当**拒绝访问**站点标记可用，但是不指向任何网页时，发生此问题。 若要解决此问题，请执行以下操作：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  在左侧窗格中，选择**站点标记**。
3.  找到**拒绝访问**站点标记记录。
4.  将**页面**字段更新为指向门户的“拒绝访问”页。

### <a name="the-access-denied-site-marker-is-pointing-to-a-deactivated-web-page"></a>“拒绝访问”站点标记指向的是已停用的网页

当**拒绝访问**站点标记可用，但是指向已停用网页（不能停用根页或内容页）时，发生此问题。 若要解决此问题，请执行以下操作：

1.  打开[“门户管理”应用](configure/configure-portal.md)。
2.  在左侧窗格中，选择**站点标记**。
3.  找到**拒绝访问**站点标记记录。
4.  将**页面**字段更新为指向门户的“拒绝访问”页。

### <a name="profile-web-form-is-not-available-for-contact-entity"></a>配置文件 Web 窗体不可用于联系人实体

“个人资料”页是门户中用于与个人资料有关的所有问题的一个常见页面。 此页显示用户可用于更新其个人资料的窗体。 此页中所用窗体来自联系人实体中的可用**个人资料网页**主窗体。 此窗体是在预配门户时，在 Common Data Service 环境中创建的。 在门户中删除或禁用**个人资料** Web 窗体时，显示此错误。 此窗体是必需窗体，删除或禁用此窗体可能会损坏门户中显示运行时错误的整个网站。 这是不可修复的状态，需要在环境中重新安装门户。

### <a name="published-state-is-not-available-for-this-website"></a>已发布状态不适用于此网站

若要解决此问题，请确保发布状态实体**已发布**可用且处于活动状态。

### <a name="published-state-is-not-visible"></a>已发布状态不可见

若要解决此问题，请确保发布状态实体**已发布**的 **isVisible** 复选框已选中。

### <a name="list-of-entities-with-search-result-having-invalid-url"></a>搜索结果中包含无效 URL 的实体列表 

若要解决此问题，请确保您的实体具有相应的安全权限。

### <a name="list-of-entities-with-cms-security-check-failed"></a>CMS 安全检查失败的实体列表 

若要解决此问题，请确保您的实体具有正确的搜索页面。

### <a name="web-file-is-not-active"></a>Web 文件处于停用状态

若要解决此问题，请确保 Web 文件处于可用状态。

### <a name="the-partial-url-of-web-file-is-misconfigured"></a>Web 文件的部分 URL 配置错误

若要解决此问题，请确保部分 URL 是以主页作为根页的文件名。

### <a name="web-file-doesnt-have-a-file-attachment"></a>Web 文件不含文件附件

若要解决此问题，请在 Web 文件的注释部分中添加相应的 CSS 文件。

### <a name="file-attachment-doesnt-have-content"></a>文件附件不含任何内容

若要解决此问题，请在 Web 文件的注释部分中添加包含完整内容的 CSS 文件。

### <a name="mime-type-of-file-is-not-textcss"></a>文件的 MIME 类型不是文本/css

若要解决此问题，请确保无任何插件或流会替代 MIME 类型的 CSS 文件。