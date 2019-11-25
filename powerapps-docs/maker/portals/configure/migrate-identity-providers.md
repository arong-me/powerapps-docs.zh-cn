---
title: 将身份提供程序迁移到 Azure AD B2C | MicrosoftDocs
description: 了解如何将身份提供程序迁移到 Azure AD B2C。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: a57398d08e190140a3383aef29825f4c08e90363
ms.sourcegitcommit: 8185f87dddf05ee256491feab9873e9143535e02
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "2708867"
---
# <a name="migrate-identity-providers-to-azure-ad-b2c"></a>将身份提供程序迁移到 Azure AD B2C

门户支持允许客户支持多种身份验证系统的可配置安全系统。 除了使用标准协议（如 OIDC、SAML 和 WS 联合身份验证）联合外部身份提供程序外，门户还附带自己的本地凭据。 今后，我们建议您只使用 Azure AD B2C 身份提供程序进行身份验证，弃用其他身份提供程序。 

## <a name="marking-an-identity-provider-as-deprecate"></a>将身份提供程序标记为弃用

您可以将门户配置为将其他身份提供程序标记为已弃用，并允许用户迁移到 Azure AD B2C 身份提供程序。 

以下站点设置用于控制身份提供程序的弃用：

| 姓名  | 说明  |
|--------|--------|
| Authentication/Registration/LocalLoginDeprecated | true 或 false 值。 如果设置为 true，本地帐户将被标记为已弃用。 门户用户需要迁移到未弃用的帐户。 默认情况下，它设置为 false。 |
| Authentication/[protocol]/[provider]/Deprecated  | true 或 false 值。 如果设置为 true，特定帐户将被标记为已弃用。 门户用户需要迁移到未弃用的帐户。 默认情况下，它设置为 false。 |
|||

当门户用户尝试登录时，并且您至少将一个身份提供程序标记为已弃用，则弃用的帐户将在页面上显示。 在以下示例中，Microsoft 帐户被标记为已弃用。

![弃用帐户示例](../media/gdpr-deprecate-account.png "弃用帐户示例")

旧身份验证提供程序屏幕上的文本可以使用以下内容片段进行更改：

| 姓名                                               | Type | 值                         |
|----------------------------------------------------|------|-------------------------------|
| Account/Signin/SignInExternalDeprecatedFormHeading | 文本 | 使用旧帐户登录 |
|||

> [!NOTE]
> 在用户注册或兑现门户的邀请时，弃用的身份验证提供程序不会显示。

## <a name="migrating-a-deprecated-identity-provider-to-a-new-identity-provider"></a>将弃用的身份提供程序迁移到新的身份提供程序

如果门户用户通过弃用的身份提供程序登录，帐户迁移屏幕将显示一条消息提示使用未弃用的身份提供程序登录。 当用户使用未弃用的身份提供程序登录时，用户帐户将与新的提供程序关联。

![帐户迁移示例](../media/gdpr-account-migration.png "帐户迁移示例")

帐户迁移屏幕上的消息可以使用以下内容片段更改：

| 姓名                                         | Type | 值                                                                                                                                                                                                                |
|----------------------------------------------|------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Account/Conversion/PageTitle                 | 文本 | 帐户迁移                                                                                                                                                                                                    |
| Account/Conversion/PageCopy                  | HTML | 您使用了不再受支持的帐户登录。 若要继续使用此门户，您必须迁移到其他帐户。 请选择下方按钮使用新的或现有的受支持帐户登录。 |
| Account/Conversion/SignInExternalFormHeading | 文本 | 使用受支持的帐户登录。                                                                                                                                                                                     |
|||

门户允许多个身份与单个联系人记录关联。 当弃用多个提供程序时，门户用户必须多次同意条款和条件。 每当用户通过弃用的身份提供程序登录时，系统都会为每个弃用的提供程序启动帐户迁移过程，联系人记录将与帐户迁移后的未弃用提供程序关联。

例如：门户支持 Microsoft 帐户 (MSA)、Google 和 Facebook 作为用于身份验证的身份提供程序。 如果您将 Google 和 Facebook 标记为弃用的提供程序，而门户用户只使用 Google 和 Facebook 作为身份验证的身份提供程序，那么用户在尝试使用这两个提供程序中的一个登录时将收到帐户迁移消息。 当用户使用 MSA 登录时，MSA 将被添加到用户的联系人记录中。 用户现在只将 MSA 作为受支持的身份验证身份提供程序。

当门户用户选择新的身份提供程序，且该身份已与其他联系人记录关联时，将显示一条错误消息。 您可以使用以下内容片段配置错误消息：

| 姓名                                                     | Type | 值                                                                                                                               |
|----------------------------------------------------------|------|-------------------------------------------------------------------------------------------------------------------------------------|
| Account/Signin/AccountConversionIdentityUsedErrorHeading | 文本 | 帐户转换错误                                                                                                            |
| Account/Signin/AccountConversionIdentityUsedErrorText    | HTML | 此帐户已存在。 请关闭浏览器，重新启动该流程，并在帐户迁移页面选择其他帐户。 |
|||

## <a name="disabling-local-login"></a>禁用本地登录

您可以使用 `Authentication/Registration/LocalLoginDeprecated` 站点设置将门户配置为禁用本地登录。 如果有人尝试使用本地凭据登录，帐户迁移屏幕将出现并显示通过未弃用的身份提供程序登录的说明。 在帐户迁移后，用户的本地凭据将被禁用。

> [!NOTE]
> 如果您将本地登录标记为已弃用，那么用户将无法注册新帐户。

以下字段被添加到门户联系人记录以指示是否禁用用户的本地登录：
- **已禁用本地登录**：指示联系人无法再使用本地帐户登录到该门户。 默认情况下，它设置为**否**。 如果用户帐户被迁移到未弃用的身份提供程序且本地登录已禁用，此字段将设置为**是**。

    ![已禁用本地登录](../media/local-login-disabled.png "已禁用本地登录")
