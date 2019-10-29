---
title: 将标识提供者迁移到 Azure AD B2C |MicrosoftDocs
description: 了解如何将标识提供程序迁移到 Azure AD B2C。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: a57398d08e190140a3383aef29825f4c08e90363
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978292"
---
# <a name="migrate-identity-providers-to-azure-ad-b2c"></a>将标识提供者迁移到 Azure AD B2C

门户支持一个可配置的安全系统，可让客户支持多个身份验证系统。 门户除了包含其自身的本地凭据外，还可以使用标准协议（如 OIDC、SAML 和 WS 联合身份验证）与外部标识提供者进行联合。 接下来，我们建议你仅使用 Azure AD B2C 标识提供程序进行身份验证，并且弃用其他标识提供者。 

## <a name="marking-an-identity-provider-as-deprecate"></a>将标识提供程序标记为弃用

你可以配置门户将其他标识提供程序标记为已弃用，并允许用户迁移到 Azure AD B2C 标识提供者。 

以下站点设置用于控制标识提供者的弃用：

| 名称  | 描述  |
|--------|--------|
| Authentication/Registration/LocalLoginDeprecated | True 或 false 值。 如果设置为 true，则本地帐户将被标记为已弃用。 门户用户将需要迁移到不推荐使用的帐户。 默认情况下，它设置为 false。 |
| Authentication/[协议]/[provider]/Deprecated  | True 或 false 值。 如果设置为 true，则特定帐户将标记为已弃用。 门户用户将需要迁移到不推荐使用的帐户。 默认情况下，它设置为 false。 |
|||

当门户用户尝试登录时，如果已将至少一个标识提供者标记为已弃用，则页面上将显示不推荐使用的帐户。 在下面的示例中，将 Microsoft 帐户标记为已弃用。

![弃用的帐户示例](../media/gdpr-deprecate-account.png "弃用的帐户示例")

旧身份验证提供程序的屏幕上的文本可通过使用以下内容片段进行更改：

| 名称                                               | 类型 | Value                         |
|----------------------------------------------------|------|-------------------------------|
| 帐户/登录/SignInExternalDeprecatedFormHeading | Text | 使用旧帐户登录 |
|||

> [!NOTE]
> 当用户注册或兑换门户邀请时，不会显示不推荐使用的标识提供者。

## <a name="migrating-a-deprecated-identity-provider-to-a-new-identity-provider"></a>将弃用的标识提供程序迁移到新的标识提供程序

如果门户用户使用已弃用的标识提供者登录，则 "帐户迁移" 屏幕将显示一条消息，用于使用不推荐使用的标识提供者登录。 如果用户使用不推荐使用的标识提供者登录，则该用户帐户与新的提供程序相关联。

![帐户迁移示例](../media/gdpr-account-migration.png "帐户迁移示例")

可使用以下内容段更改用于帐户迁移的屏幕上的消息：

| 名称                                         | 类型 | Value                                                                                                                                                                                                                |
|----------------------------------------------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 帐户/转换/PageTitle                 | Text | 帐户迁移                                                                                                                                                                                                    |
| 帐户/转换/PageCopy                  | .HTML | 你使用了不再受支持的帐户登录。 若要继续使用此门户，必须迁移到不同的帐户。 选择下面的按钮以使用新的或现有的受支持帐户登录。 |
| 帐户/转换/SignInExternalFormHeading | Text | 使用受支持的帐户登录。                                                                                                                                                                                     |
|||

门户允许多个标识与一个联系人记录相关联。 当不推荐使用多个提供程序时，门户用户必须多次同意条款和条件。 每当用户使用已弃用的标识提供者登录时，将为每个不推荐使用的提供程序启动帐户迁移过程，并且在帐户迁移后，联系人记录将与不推荐使用的访问接口相关联。

例如：门户支持 Microsoft 帐户（MSA）、Google 和 Facebook 作为标识提供程序进行身份验证。 如果将 Google 和 Facebook 标记为不推荐使用的提供程序，并且门户用户仅将 Google 和 Facebook 作为标识提供程序进行身份验证，则当用户尝试使用这两个提供程序中的任一提供程序登录时，将收到帐户迁移消息。 当用户使用 MSA 登录时，将在用户的联系人记录中添加 MSA。 现在，用户只有 MSA 作为受支持的身份验证标识提供者。

当门户用户选择新的标识提供者并且标识已经与另一个联系人记录相关联时，将显示一条错误消息。 你可以使用以下内容片段配置错误消息：

| 名称                                                     | 类型 | Value                                                                                                                               |
|----------------------------------------------------------|------|-------------------------------------------------------------------------------------------------------------------------------------|
| 帐户/登录/AccountConversionIdentityUsedErrorHeading | Text | 帐户转换错误                                                                                                            |
| 帐户/登录/AccountConversionIdentityUsedErrorText    | .HTML | 此帐户已存在。 关闭浏览器，重新启动此过程，然后在 "帐户迁移" 页上选择其他帐户。 |
|||

## <a name="disabling-local-login"></a>禁用本地登录

你可以使用 `Authentication/Registration/LocalLoginDeprecated` 站点设置来配置门户以禁用本地登录。 如果有人尝试使用本地凭据登录，将显示 "帐户迁移" 屏幕，并显示使用不推荐使用的标识提供者登录的指令。 迁移帐户时，将禁用该用户的本地凭据。

> [!NOTE]
> 如果将本地登录名标记为已弃用，用户将无法注册新帐户。

以下字段将添加到门户联系人记录中，以指示是否为用户禁用了本地登录名：
- **禁用本地登录**：表示联系人无法再使用本地帐户登录到门户。 默认情况下，它设置为 "**否**"。 如果用户的帐户迁移到不推荐使用的标识提供者并且禁用了本地登录，则此字段设置为 **"是"** 。

    ![已禁用本地登录](../media/local-login-disabled.png "已禁用本地登录")
