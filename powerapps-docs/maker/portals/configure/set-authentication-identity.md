---
title: 设置门户的身份验证标识 | MicrosoftDocs
description: 有关如何设置门户的身份验证标识的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 2faab3a6f41bbcd9a239c52fb00ce27919347879
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980280"
---
# <a name="set-authentication-identity-for-a-portal"></a>设置门户的身份验证身份

门户提供基于 [ASP.NET 身份](https://www.asp.net/identity) API 构建的身份验证功能。 ASP.NET 身份反之基于 [OWIN](https://www.asp.net/aspnet/overview/owin-and-katana) 框架构建，此框架是身份验证系统的重要组件。 提供的服务包括：

- 本地（用户名/密码）用户登录
- 通过第三方身份提供程序的外部（社交提供程序）用户登录
- 使用电子邮件的双因素身份验证
- 电子邮件地址确认
- 密码恢复
- 注册预生成的联系人记录的邀请代码注册

> [!NOTE]
> 联系人实体的门户联系人窗体上的**已确认移动电话号码**当前没有用。 只有当从 Adxstudio Portals 升级时才必须使用此字段。

## <a name="requirements"></a>要求

门户要求：

- 门户基础
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 身份
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 身份工作流解决方案包

## <a name="authentication-overview"></a>身份验证概述

返回门户访问者可以使用本地用户凭据或外部身份提供程序帐户进行身份验证。 新访问者可以通过提供用户名和密码或通过外部提供程序登录来注册新用户帐户。 发送邀请代码（由门户管理员）的访问者可以选择在新用户帐户的注册流程中清除代码。

**相关站点设置：**

- `Authentication/Registration/Enabled`
- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/OpenRegistrationEnabled`
- `Authentication/Registration/InvitationEnabled`
- `Authentication/Registration/RememberMeEnabled`
- `Authentication/Registration/ResetPasswordEnabled`

### <a name="sign-in-by-using-a-local-identity-or-external-identity"></a>使用本地身份或外部身份登录

![使用本地帐户登录](../media/sign-in-local-account.png "使用本地帐户登录")  

### <a name="sign-up-by-using-a-local-identity-or-external-identity"></a>使用本地身份或外部身份注册

![注册新的本地帐户](../media/register-new-local-account.png "注册新的本地帐户")  

### <a name="redeem-an-invitation-code-manually"></a>手动清除邀请代码

![使用邀请码注册](../media/sign-up-invitation-code.png "使用邀请码注册")  

## <a name="forgot-password-or-password-reset"></a>忘记密码或密码重置 

需要密码重置的返回访问者（之前已在用户配置文件中指定了电子邮件地址）可以请求将密码重置令牌发送到他们的电子邮件帐户。 重置令牌允许其所有者选择新密码。 或者，令牌可以丢弃保留用户的原始密码，不修改。

**相关站点设置：**

- `Authentication/Registration/ResetPasswordEnabled`
- `Authentication/Registration/ResetPasswordRequiresConfirmedEmail`

**相关流程：** 将密码重置发送到联系人

1.  根据需要在工作流中自定义电子邮件。
2.  提交电子邮件到调用流程。
3.  提示访问者检查电子邮件。
4.  访问者收到包含说明的密码重置电子邮件。
5.  访问者返回到重置窗体。
6.  密码重置完成。

## <a name="redeem-an-invitation"></a>兑换邀请

清除邀请代码允许注册访问者与专门为该访问者提前准备的现有联系人记录关联。 通常，邀请代码通过电子邮件发送出去，但您可以使用一般代码提交窗体通过其他渠道发送代码。 有效邀请代码提交后，常规用户注册流程开始以设置新的用户帐户。

**相关站点设置：**

`Authentication/Registration/InvitationEnabled`

**相关流程：** 发送邀请

必须在门户中使用清除邀请页面的 URL 自定义此工作流发送的电子邮件：https://portal.contoso.com/register/?returnurl=%2f&invitation={Invitation Code(Invitation)}

1. 创建针对新联系人的邀请。

    ![创建针对新联系人的邀请](../media/create-invitation.png "创建针对新联系人的邀请")  

2. 自定义并保存新邀请。

    ![自定义新邀请](../media/customize-new-invitation.png "自定义新邀请")  

3. 流程：发送邀请
4. 自定义邀请电子邮件。
5. 邀请电子邮件打开兑换页面。
6. 用户使用提交的邀请代码注册。

    ![使用邀请码注册](../media/sign-up-invitation-code.png "使用邀请码注册")  

## <a name="manage-user-accounts-through-profile-pages"></a>通过配置文件页管理用户帐户

通过身份验证的用户通过配置文件页的**安全**导航栏管理其用户帐户。 用户不限于在用户注册时选择的单个本地帐户或单个外部帐户。 具有外部帐户的用户可以选择通过应用用户名和密码创建本地帐户。 从本地帐户开始的用户可以选择将多个外部身份关联到其帐户。 配置文件页也是提示用户请求确认其电子邮件地址的位置，方法是通过请求将确认电子邮件发送到其电子邮件帐户。

**相关站点设置：**

- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/TwoFactorEnabled`

## <a name="set-or-change-a-password"></a>设置或更改密码

具有现有本地帐户的用户可以通过提供原始密码应用新密码。 没有本地帐户的用户可以选择用户名和密码来设置新本地帐户。 用户名设置之后无法更改。

**相关站点设置：**

`Authentication/Registration/LocalLoginEnabled`

**相关流程：**
- 创建用户名和密码。
- 更改现有密码。

## <a name="confirm-an-email-address"></a>确认电子邮件地址

更改电子邮件地址（或首次设置）让其处于未确认的状态。 用户可以请求将确认电子邮件发送到自己的新电子邮件地址，而该电子邮件中将包含有关用户如何完成电子邮件确认流程的说明。

**相关流程：** 将电子邮件确认发送给联系人

1. 根据需要在工作流中自定义电子邮件。 
2. 用户提交新电子邮件，该电子邮件的状态为未确认。
3. 用户检查电子邮件以确认。
4. 流程：将电子邮件确认发送给联系人
5. 自定义确认电子邮件。
6. 用户点击确认链接以完成确认流程。

> [!NOTE]
> 确保为联系人指定主要电子邮件，因为确认电子邮件仅发送给联系人的主要电子邮件 (emailaddress1)。 确认电子邮件将不发送给联系人记录的次要电子邮件 (emailaddress2) 或备用电子邮件 (emailaddress3)。

## <a name="enable-two-factor-authentication"></a>启用双因素身份验证

双因素身份验证功能提高用户帐户的安全性，方法是除标准本地或外部帐户登录之外，还需要证明确认的电子邮件的所有权。 尝试登录启用了双因素身份验证帐户的用户将通过与其帐户关联的确认的电子邮件收到安全代码。 安全代码必须提交才能完成登录流程。 用户可以选择记住成功通过验证的浏览器，这样在后续登录相同浏览器时就不需要提供安全代码。 每个用户帐户单独启用此功能，还需要确认的电子邮件。

> [!WARNING]
> 如果您创建并启用 **Authentication/Registration/MobilePhoneEnabled** 网站设置来启用旧功能，将出现错误。 此站点设置不是现成提供的，门户不支持。

**相关站点设置：**

- `Authentication/Registration/TwoFactorEnabled`
- `Authentication/Registration/RememberBrowserEnabled`

**相关流程：** 发送电子邮件双因素代码给联系人

1. 启用双因素身份验证。
2. 选择通过电子邮件接收安全代码。
3. 等待包含安全代码的电子邮件。
4. 流程：发送电子邮件双因素代码给联系人。
5. 双因素身份验证可禁用。

## <a name="manage-external-accounts"></a>管理外部帐户

通过身份验证的用户可以将多个外部身份连接（注册）到其用户帐户，配置的身份提供程序每个一个。 连接身份后，用户可以选择通过连接的任意身份登录。 只要一个本地身份或外部身份保留，现有身份也可以断开连接。

**相关网站设置：**

- `Authentication/Registration/ExternalLoginEnabled`

**外部身份提供程序网站设置**

1.  选择要连接到用户帐户的提供程序。

    ![管理外部帐户](../media/manage-external-accounts.png "管理外部帐户")  

2.  使用要连接的提供程序登录。

提供程序现在已连接。 也可以断开提供程序。

## <a name="enable-aspnet-identity-authentication"></a>启用 ASP.NET 身份验证

下文介绍了启用和禁用各种身份验证功能和行为的设置：


|                        网站设置名称                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  说明                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          Authentication/Registration/LocalLoginEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     基于用户名（或电子邮件）和密码启用或禁用本地帐户登录。 默认值：false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|          Authentication/Registration/LocalLoginByEmail          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               使用电子邮件地址字段而不是用户名字段启用或禁用本地帐户登录。 默认值：false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|        Authentication/Registration/ExternalLoginEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  启用或禁用外部帐户登录和注册。 默认：true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|          Authentication/Registration/RememberMeEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          本地登录时选中或清除“记住我?”复选框，以便即使 Web 浏览器关闭时也允许通过身份验证的会话仍可以继续。 默认：true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|          Authentication/Registration/TwoFactorEnabled           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        启用或禁止用户可以启用双因素身份验证的选项。 具有确认的电子邮件地址的用户可以选择实现双因素身份验证的增加的安全性。 默认值：false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|       Authentication/Registration/RememberBrowserEnabled        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                执行双因素验证（电子邮件代码）时选中或清除“记住浏览器?”复选框，以便保持当前浏览器的双因素验证。 只要使用同一浏览器，用户在后续登录时就不需要通过双因素验证。 默认：true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|        Authentication/Registration/ResetPasswordEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         启用或禁用密码重置功能。 默认：true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/Registration/ResetPasswordRequiresConfirmedEmail |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               仅为确认的电子邮件地址启用或禁用密码重置。 如果启用，未确认的电子邮件地址不能用于发送密码重置指令。 默认值：false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|   Authentication/Registration/TriggerLockoutOnFailedPassword    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          启用或禁用失败的密码尝试记录。 如果禁用，用户帐户不会锁定。默认值：true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|             Authentication/Registration/IsDemoMode              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                          启用或禁用只在开发或演示环境中使用的演示模式标志。 不要对生产环境启用该设置。 演示模式还需要 Web 浏览器本地运行到 Web 应用程序服务器。 当演示模式启用时，密码重置代码和双因素代码显示给快速访问的用户。 默认值：false                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|    Authentication/Registration/LoginButtonAuthenticationType    | 如果门户只需要一个外部身份提供程序（处理所有身份验证），这允许标题导航栏的**登录**按钮直接链接到外部身份提供程序的登录页（而不是链接到中间本地登录窗体和身份提供程序选择页面）。 只可以为此操作选择一个身份提供程序。 指定提供程序的 [AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx) 值。<br>若要使用 OpenIdConnect（如使用 Azure Active Directory B2C）进行单一登录配置，用户需提供权限。<br>对于基于 OAuth2 的提供程序，可接受的值为：`Facebook, Google, Yahoo, [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn, Yammer,` 或 `Twitter`<br>对于基于 WS 联合身份验证的提供程序，使用为 `Authentication/WsFederation/ADFS/AuthenticationType` 和 `Authentication/WsFederation/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]/\[provider\]/AuthenticationType` 网站设置指定的值。 示例：https://adfs.contoso.com/adfs/services/trust、Facebook-0123456789、Google、Yahoo!，URI：[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)]LiveID。 |
|                                                                 |                                                                                                                                                                                                                                                                                                  |

## <a name="enable-or-disable-user-registration"></a>启用或禁用用户注册

下文介绍了启用和禁用用户注册选项的设置：

| 网站设置名称                                   | 说明                                                                                                                                                                             |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/Enabled                 | 启用或禁用用户注册的所有窗体。 必须为此节中的其他设置启用注册才能生效。 默认：true                                   |
| Authentication/Registration/OpenRegistrationEnabled | 启用或禁用创建新本地用户的注册窗体。 注册窗体允许访问门户的所有匿名访问者创建新用户帐户。 默认：true |
| Authentication/Registration/InvitationEnabled       | 启用或禁用拥有邀请代码的注册用户的邀请代码清除窗体。 默认：true                                                               |
|Authentication/Registration/CaptchaEnabled|启用或禁用用户注册页的 captcha。 默认值：false<br>**注释**：此网站设置默认情况下可能不可用。 若要启用 captcha，您必须同时创建站点设置并将其值设置为 true。 |
||

> [!NOTE]
> 确保为用户指定主要电子邮件，因为注册是使用用户的主要电子邮件 (emailaddress1) 完成的。 不能使用联系人记录的次要电子邮件 (emailaddress2) 或备用电子邮件 (emailaddress3) 注册用户。

## <a name="user-credential-validation"></a>用户凭据验证

下文介绍了调整用户名和密码验证参数的设置： 在用户注册新的本地帐户或更改密码时进行验证。

| 网站设置名称                                                       | 说明                                                                                                                                                                                         |
|-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/PasswordValidator/EnforcePasswordPolicy      | 密码是否包含以下三种类别的字符：<br><ul><li>欧洲语言大写字母（A-Z，使用变音符号，希腊文和西里尔文字字符）</li><li>欧洲语言小写字母（a-z，使用变音符号，ß，希腊文和西里尔文字字符）</li><li>10 位基本数字 (0-9)</li><li>非字母数字字符（特殊字符）（例如，!、$、\#、%）</li></ul>默认值：true。 有关详细信息：[密码策略](https://technet.microsoft.com/library/hh994562(v=ws.10).aspx)。                                                                                                           |  
| Authentication/UserManager/UserValidator/AllowOnlyAlphanumericUserNames | 是否允许用户名仅使用字母数字字符。 默认值：false。 有关详细信息：[UserValidator<TUser, TKey>.AllowOnlyAlphanumericUserNames](https://msdn.microsoft.com/library/dn613211.aspx)。                                                          |  
| Authentication/UserManager/UserValidator/RequireUniqueEmail             | 验证用户是否需要唯一电子邮件地址。 默认值：true。 有关详细信息：[UserValidator<TUser, TKey>.RequireUniqueEmail](https://msdn.microsoft.com/library/dn613213.aspx)。                                                                   |  
| Authentication/UserManager/PasswordValidator/RequiredLength             | 所需密码的最小长度。 默认值：8。 有关详细信息：[PasswordValidator.RequiredLength](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredlength.aspx)。                                       |  
| Authentication/UserManager/PasswordValidator/RequireNonLetterOrDigit    | 密码是否需要非字母或数字字符。 默认值：false。 有关详细信息：[PasswordValidator.RequireNonLetterOrDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirenonletterordigit.aspx)。 |  
| Authentication/UserManager/PasswordValidator/RequireDigit               | 密码是否需要数字（0 到 9）。 默认值：false。 有关详细信息：[PasswordValidator.RequireDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredigit.aspx)。                |  
| Authentication/UserManager/PasswordValidator/RequireLowercase           | 密码是否需要小写字母（a 到 z）。 默认值：false。 有关详细信息：[PasswordValidator.RequireLowercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirelowercase.aspx)。        |  
| Authentication/UserManager/PasswordValidator/RequireUppercase           | 密码是否需要大写字母（A 到 Z）。 默认值：false。 有关详细信息：[PasswordValidator.RequireUppercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requireuppercase.aspx)。       | 
|| 

## <a name="user-account-lockout-settings"></a>用户帐户锁定设置

下文介绍了定义帐户如何以及何时通过身份验证锁定的设置： 当在短暂的时段内检测到一定数量的失败密码尝试时，用户帐户将被锁定一段时间。 锁定期间后用户可以重试。

| 网站设置名称                                               | 说明                                                                                                                                                                                                                                     |
|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/UserLockoutEnabledByDefault          | 指定当用户创建时是否启用用户锁定。 默认值：true。 有关详细信息：[UserManager<TUser, TKey>.UserLockoutEnabledByDefault](https://msdn.microsoft.com/library/dn613214.aspx)。                                                                                                  |  
| Authentication/UserManager/DefaultAccountLockoutTimeSpan        | 达到 Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout 后锁定用户的默认时间量。 默认值：24:00:00（1天）。 有关详细信息：[UserManager<TUser, TKey>.DefaultAccountLockoutTimeSpan](https://msdn.microsoft.com/library/dn613201.aspx)。                 |  
| Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout | 锁定用户前允许的最大访问尝试次数（如果锁定已启用）。 默认值：5。 有关详细信息：[UserManager<TUser, TKey>.MaxFailedAccessAttemptsBeforeLockout](https://msdn.microsoft.com/library/dn613202.aspx)。                                                                        |  
| Authentication/ApplicationCookie/ExpireTimeSpan                 | 默认时间 Cookie 身份验证会话有效。 默认值：24:00:00（1天）。 有关详细信息：[CookieAuthenticationOptions.ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx)。 |
||  

## <a name="cookie-authentication-site-settings"></a>Cookie 身份验证网站设置

修改默认身份验证 Cookie 行为的设置。 由 [CookieAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.aspx) 类定义。

| 网站设置名称   | 说明       |
|----------------------|------------------------------------------------|
| Authentication/ApplicationCookie/AuthenticationType                      | 应用程序身份验证 Cookie 的类型。 默认：ApplicationCookie。 有关详细信息：[AuthenticationOptions::AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx)。  |
| Authentication/ApplicationCookie/CookieName                              | 确定用于保留标识的 Cookie 名称。 默认：.AspNet.Cookies。 有关详细信息：[CookieAuthenticationOptions::CookieName](https://msdn.microsoft.com/library/dn385537.aspx)。  |
| Authentication/ApplicationCookie/CookieDomain                            | 确定用于创建 Cookie 的域。 有关详细信息：[CookieAuthenticationOptions::CookieDomain](https://msdn.microsoft.com/library/dn385536.aspx)。  |
| Authentication/ApplicationCookie/CookiePath                              | 确定用于创建 Cookie 的路径。 默认：/。 有关详细信息：[CookieAuthenticationOptions::CookiePath](https://msdn.microsoft.com/library/dn385539.aspx)。 |
| Authentication/ApplicationCookie/CookieHttpOnly                          | 确定浏览器是否应该允许 Cookie 由客户端 Javascript 访问。 默认值：true。 有关详细信息：[CookieAuthenticationOptions::CookieHttpOnly](https://msdn.microsoft.com/library/dn385540.aspx)。                     |
| Authentication/ApplicationCookie/CookieSecure                            | 确定 Cookie 是否仅应该在 HTTPS 请求中传输。 默认：SameAsRequest。 有关详细信息：[CookieAuthenticationOptions::CookieSecure](https://msdn.microsoft.com/library/dn385538.aspx)。  |
| Authentication/ApplicationCookie/ExpireTimeSpan                          | 控制应用程序 Cookie 从创建开始持续有效的时间。 默认：14 天。 有关详细信息：[CookieAuthenticationOptions::ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx)。  |
| Authentication/ApplicationCookie/SlidingExpiration                       | SlidingExpiration 设置为 true，以指示中间件无论何时处理过期时间过去一半的请求时重新发放具有新过期时间的 Cookie。 默认值：true。 有关详细信息：[CookieAuthenticationOptions::SlidingExpiration](https://msdn.microsoft.com/library/dn385548.aspx)。 |
| Authentication/ApplicationCookie/LoginPath                               | 属性 LoginPath 通知中间件应将传出 401 未经授权状态代码更改为 302 重定向到指定登录路径。 默认：~/signin。 有关详细信息：[CookieAuthenticationOptions::LoginPath](https://msdn.microsoft.com/library/dn385541.aspx)。                                            |
| Authentication/ApplicationCookie/LogoutPath                              | 如果向中间件提供了 LogoutPath，那么该路径的请求将基于 ReturnUrlParameter 重定向。 有关详细信息：[CookieAuthenticationOptions::LogoutPath](https://msdn.microsoft.com/library/dn385545.aspx)。               |
| Authentication/ApplicationCookie/ReturnUrlParameter                      | ReturnUrlParameter 确定查询字符串参数的名称，其由中间件在 401 未经授权状态代码更改为 302 重定向到登录路径时追加。 有关详细信息：[CookieAuthenticationOptions::ReturnUrlParameter](https://msdn.microsoft.com/library/dn385546.aspx)。                           |
| Authentication/ApplicationCookie/SecurityStampValidator/ValidateInterval | 两次安全戳验证之间的时间段。 默认：30 分钟。 有关详细信息：[SecurityStampValidator::OnValidateIdentity](https://msdn.microsoft.com/library/microsoft.aspnet.identity.owin.securitystampvalidator.onvalidateidentity.aspx)。                    |
| Authentication/TwoFactorCookie/AuthenticationType                        | 双重身份验证 Cookie 的类型。 默认：TwoFactorCookie。 有关详细信息：[AuthenticationOptions::AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx)。            |
| Authentication/TwoFactorCookie/ExpireTimeSpan                            | 控制双重 Cookie 从创建开始持续有效的时间。 默认：5 分钟。 有关详细信息：[CookieAuthenticationOptions::ExpireTimeSpan](https://msdn.microsoft.com/library/dn385543.aspx)。     |
|||

### <a name="see-also"></a>另请参阅

[配置门户身份验证](configure-portal-authentication.md)  
[门户的 OAuth2 提供程序设置](configure-oauth2-settings.md)  
[门户的 Open ID Connect 提供程序设置](configure-openid-settings.md)  
[门户的 WS 联合身份验证提供程序设置](configure-ws-federation-settings.md)  
[门户的 SAML 2.0 提供程序设置](configure-saml2-settings.md)  
