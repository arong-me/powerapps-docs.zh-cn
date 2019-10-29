---
title: 设置门户的身份验证标识 |MicrosoftDocs
description: 设置门户身份验证标识的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3904de43a8e27ca555545cccdf23532970b02edd
ms.sourcegitcommit: 57b968b542fc43737330596d840d938f566e582a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/22/2019
ms.locfileid: "72978131"
---
# <a name="set-authentication-identity-for-a-portal"></a>设置门户的身份验证标识

门户提供了基于[ASP.NET Identity](http://www.asp.net/identity) API 构建的身份验证功能。 ASP.NET Identity 在[OWIN](http://www.asp.net/aspnet/overview/owin-and-katana)框架的基础上建立，这也是身份验证系统的重要组成部分。 提供的服务包括：

- 本地（用户名/密码）用户登录
- 外部（社交提供商）用户通过第三方标识提供程序登录
- 通过电子邮件进行双重身份验证
- 电子邮件地址确认
- 密码恢复
- 注册预先生成联系人记录的邀请代码

> [!NOTE]
> 联系人实体的门户联系人窗体上的 "**手机确认**" 字段当前不起作用。 仅当从 Adxstudio 门户升级时，才能使用此字段。

## <a name="requirements"></a>要求

门户要求：

- 门户基
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 标识
- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 标识工作流解决方案包

## <a name="authentication-overview"></a>身份验证概述

返回门户访问者可以使用本地用户凭据或外部标识提供者帐户进行身份验证。 新的访问者可以通过提供用户名和密码或通过外部提供商登录来注册新用户帐户。 发送邀请代码（由门户管理员提供）的访问者可以选择兑换注册新用户帐户的过程中的代码。

**相关站点设置：**

- `Authentication/Registration/Enabled`
- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/OpenRegistrationEnabled`
- `Authentication/Registration/InvitationEnabled`
- `Authentication/Registration/RememberMeEnabled`
- `Authentication/Registration/ResetPasswordEnabled`

### <a name="sign-in-by-using-a-local-identity-or-external-identity"></a>使用本地标识或外部标识登录

![使用本地帐户登录](../media/sign-in-local-account.png "使用本地帐户登录")  

### <a name="sign-up-by-using-a-local-identity-or-external-identity"></a>使用本地标识或外部标识注册

![注册新的本地帐户](../media/register-new-local-account.png "注册新的本地帐户")  

### <a name="redeem-an-invitation-code-manually"></a>手动兑换邀请代码

![使用邀请代码注册](../media/sign-up-invitation-code.png "使用邀请代码注册")  

## <a name="forgot-password-or-password-reset"></a>忘记了密码或密码重置 

如果需要重置密码（并且以前在其用户配置文件上指定了电子邮件地址），则可以请求将密码重置令牌发送到其电子邮件帐户。 使用重置令牌，其所有者可以选择新密码。 或者，可以放弃该令牌，使用户的原始密码不受修改。

**相关站点设置：**

- `Authentication/Registration/ResetPasswordEnabled`
- `Authentication/Registration/ResetPasswordRequiresConfirmedEmail`

**相关进程：** 向联系人发送密码重置

1.  根据需要自定义工作流中的电子邮件。
2.  提交电子邮件以调用进程。
3.  系统将提示访问者检查电子邮件。
4.  访问者接收密码重置电子邮件，说明。
5.  访问者返回到重置窗体。
6.  密码重置已完成。

## <a name="redeem-an-invitation"></a>兑换邀请

兑换邀请代码允许注册访问者与专门为该访问者预先准备的现有联系人记录相关联。 通常，邀请代码通过电子邮件发送出去，但你可以使用一般代码提交窗体通过其他渠道发送代码。 提交有效的邀请代码后，将进行普通用户注册（注册）过程以设置新用户帐户。

**相关站点设置：**

`Authentication/Registration/InvitationEnabled`

**相关进程：** 发送邀请

必须使用门户上兑换邀请页面的 URL 自定义此工作流发送的电子邮件： http://portal.contoso.com/register/?returnurl=%2f&invitation={Invitation 代码（邀请）}

1. 为新联系人创建邀请。

    ![为新联系人创建邀请](../media/create-invitation.png "为新联系人创建邀请")  

2. 自定义并保存新邀请。

    ![自定义新邀请](../media/customize-new-invitation.png "自定义新邀请")  

3. 过程：发送邀请
4. 自定义邀请电子邮件。
5. 邀请电子邮件打开兑换页面。
6. 用户使用提交的邀请代码进行注册。

    ![使用邀请代码注册](../media/sign-up-invitation-code.png "使用邀请代码注册")  

## <a name="manage-user-accounts-through-profile-pages"></a>通过配置文件页管理用户帐户

经过身份验证的用户通过配置文件页的**安全**导航栏来管理他们的用户帐户。 用户不限于在用户注册时选择的单个本地帐户或单个外部帐户。 具有外部帐户的用户可以选择通过应用用户名和密码来创建本地帐户。 使用本地帐户启动的用户可以选择将多个外部标识关联到其帐户。 通过请求将确认电子邮件发送到电子邮件帐户，"配置文件" 页也会提醒用户确认其电子邮件地址。

**相关站点设置：**

- `Authentication/Registration/LocalLoginEnabled`
- `Authentication/Registration/ExternalLoginEnabled`
- `Authentication/Registration/TwoFactorEnabled`

## <a name="set-or-change-a-password"></a>设置或更改密码

具有现有本地帐户的用户可以通过提供原始密码来应用新密码。 没有本地帐户的用户可以选择用户名和密码来设置新的本地帐户。 设置用户名后，不能对其进行更改。

**相关站点设置：**

`Authentication/Registration/LocalLoginEnabled`

**相关进程：**
- 创建用户名和密码。
- 更改现有密码。

## <a name="confirm-an-email-address"></a>确认电子邮件地址

更改电子邮件地址（或首次设置它）会将其置于未确认状态。 用户可以请求将确认电子邮件发送到新的电子邮件地址，并且电子邮件将向用户提供完成电子邮件确认过程的说明。

**相关进程：** 向联系人发送电子邮件确认

1. 根据需要自定义工作流中的电子邮件。 
2. 用户提交新的电子邮件，该电子邮件处于未确认状态。
3. 用户检查电子邮件以确认。
4. 处理：向联系人发送电子邮件确认
5. 自定义确认电子邮件。
6. 用户单击确认链接即可完成确认过程。

> [!NOTE]
> 确保为联系人指定了主电子邮件，因为确认电子邮件只发送到联系人的主电子邮件（emailaddress1）。 确认电子邮件不会发送到联系人记录的辅助电子邮件（emailaddress2）或备用电子邮件（emailaddress3）。

## <a name="enable-two-factor-authentication"></a>启用双因素身份验证

双重身份验证功能通过要求对已确认电子邮件的所有权以及标准的本地或外部帐户登录来提高用户帐户的安全性。 如果用户尝试登录到已启用双因素身份验证的帐户，则会将安全代码发送到与其帐户关联的确认电子邮件。 必须提交安全代码才能完成登录过程。 用户可以选择记住成功通过验证的浏览器，这样，从同一浏览器登录的后续登录就不需要使用安全代码。 每个用户帐户单独启用此功能，并需要确认电子邮件。

> [!WARNING]
> 如果创建并启用**Authentication/Registration/MobilePhoneEnabled**站点设置以启用旧功能，则会发生错误。 此站点设置不会现成提供，门户不支持此设置。

**相关站点设置：**

- `Authentication/Registration/TwoFactorEnabled`
- `Authentication/Registration/RememberBrowserEnabled`

**相关进程：** 向联系人发送电子邮件双因素代码

1. 启用双因素身份验证。
2. 选择通过电子邮件接收安全代码。
3. 等待包含安全代码的电子邮件。
4. 处理：向联系人发送电子邮件两个因素代码。
5. 可以禁用双因素身份验证。

## <a name="manage-external-accounts"></a>管理外部帐户

经过身份验证的用户可以将多个外部标识连接（注册）到其用户帐户，每个配置的标识提供程序都有一个。 连接标识后，用户可以选择使用任何连接的标识进行登录。 还可以断开现有标识，只要单个外部标识或本地标识保留。

**相关站点设置：**

- `Authentication/Registration/ExternalLoginEnabled`

**外部标识提供者站点设置**

1.  选择要连接到用户帐户的提供程序。

    ![管理外部帐户](../media/manage-external-accounts.png "管理外部帐户")  

2.  使用要连接的提供者登录。

提供程序现已连接。 该提供程序还可以断开连接。

## <a name="enable-aspnet-identity-authentication"></a>启用 ASP.NET 标识身份验证

下面介绍了启用和禁用各种身份验证功能和行为的设置：


|                        站点设置名称                        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  描述                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          Authentication/Registration/LocalLoginEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     启用或禁用基于用户名（或电子邮件）和密码的本地帐户登录。 默认值： false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|          Authentication/Registration/LocalLoginByEmail          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               使用电子邮件地址字段（而不是用户名字段）启用或禁用本地帐户登录。 默认值： false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|        Authentication/Registration/ExternalLoginEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  启用或禁用外部帐户登录和注册。 默认值： true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|          Authentication/Registration/RememberMeEnabled          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          选择或清除 "记住我"？当 web 浏览器关闭时，本地登录上的复选框允许经过身份验证的会话保持。 默认值： true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|          Authentication/Registration/TwoFactorEnabled           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        启用或禁用用于启用双因素身份验证的用户选项。 具有确认电子邮件地址的用户可以选择添加双重身份验证的安全性。 默认值： false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|       Authentication/Registration/RememberBrowserEnabled        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                选择或清除 "记住浏览器"？用于保留第二因素验证（电子邮件代码）的复选框，以保留当前浏览器的第二重验证。 只要正在使用同一个浏览器，则不会要求用户在后续登录时传递第二因素验证。 默认值： true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|        Authentication/Registration/ResetPasswordEnabled         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         启用或禁用密码重置功能。 默认值： true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/Registration/ResetPasswordRequiresConfirmedEmail |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               仅为已确认的电子邮件地址启用或禁用密码重置。 如果启用，则不能使用未确认的电子邮件地址发送密码重置说明。 默认值： false                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|   Authentication/Registration/TriggerLockoutOnFailedPassword    |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          启用或禁用失败密码尝试的记录。 如果禁用，则不会锁定用户帐户。默认值： true                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|             Authentication/Registration/IsDemoMode              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                          启用或禁用演示模式标志，仅用于开发或演示环境。 不要在生产环境中启用此设置。 演示模式还要求 web 浏览器在本地运行到 web 应用程序服务器。 启用 "演示模式" 后，将向用户显示密码重置代码和第二因素代码，以便快速访问。 默认值： false                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|    Authentication/Registration/LoginButtonAuthenticationType    | 如果门户只需要一个外部标识提供者（用于处理所有身份验证），则允许标题导航栏的 "**登录**" 按钮直接链接到该外部标识提供者的登录页（而不是链接到中间本地登录窗体和标识提供者选择页）。 只能为此操作选择单个标识提供者。 指定提供程序的[AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)值。<br>对于使用 OpenIdConnect 的单一登录配置（如使用 Azure Active Directory B2C），用户需要提供此颁发机构。<br>对于基于 OAuth2 的提供程序，接受的值为： `Facebook, Google, Yahoo, [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)], LinkedIn, Yammer,` 或 `Twitter`<br>对于基于 WS 联合身份验证的提供程序，请使用为 "`Authentication/WsFederation/ADFS/AuthenticationType`" 和 "`Authentication/WsFederation/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]/\[provider\]/AuthenticationType` 网站设置" 指定的值。 示例： http://adfs.contoso.com/adfs/services/trust 、Facebook-0123456789、Google、Yahoo！、uri：[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] LiveID。 |
|                                                                 |                                                                                                                                                                                                                                                                                                  |

## <a name="enable-or-disable-user-registration"></a>启用或禁用用户注册

下面介绍了启用和禁用用户注册（注册）选项的设置：

| 站点设置名称                                   | 描述                                                                                                                                                                             |
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 身份验证/注册/启用                 | 启用或禁用所有形式的用户注册。 必须启用注册，此部分中的其他设置才能生效。 默认值： true                                   |
| Authentication/Registration/OpenRegistrationEnabled | 启用或禁用注册注册窗体以创建新的本地用户。 注册表单允许任何匿名访问者访问门户来创建新的用户帐户。 默认值： true |
| Authentication/Registration/InvitationEnabled       | 启用或禁用邀请代码兑换窗体，用于注册拥有邀请代码的用户。 默认值： true                                                               |
|Authentication/Registration/CaptchaEnabled|启用或禁用用户注册页上的 captcha。 默认值： false<br>**注意**：默认情况下，此站点设置可能不可用。 若要启用 captcha，必须创建站点设置并将其值设置为 true。 |
||

> [!NOTE]
> 确保为用户指定了主电子邮件，因为注册是通过使用用户的主电子邮件（emailaddress1）来完成的。 不能使用联系人记录的辅助电子邮件（emailaddress2）或备用电子邮件（emailaddress3）注册该用户。

## <a name="user-credential-validation"></a>用户凭据验证

下面介绍了调整用户名和密码验证参数的设置。 当用户注册新的本地帐户或更改密码时，将发生验证。

| 站点设置名称                                                       | 描述                                                                                                                                                                                         |
|-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/PasswordValidator/EnforcePasswordPolicy      | 密码是否包含以下三个类别中的字符：<br><ul><li>大写字母，欧洲语言（A 到 Z，带有音调符号标记，希腊语和西里尔字符）</li><li>字母小写字母（a 到 z、带有音调符号标记、希腊语和西里尔字符）</li><li>以10为底的数字（0到9）</li><li>非字母数字字符（特殊字符）（例如！、$、\#、%）</li></ul>默认值： true。 有关详细信息，请执行以下操作：[密码策略](https://technet.microsoft.com/library/hh994562(v=ws.10).aspx)。                                                                                                           |  
| Authentication/UserManager/UserValidator/AllowOnlyAlphanumericUserNames | 是否只为用户名允许字母数字字符。 默认值： false。 有关详细信息[，请： UserValidator < TUser，TKey >。AllowOnlyAlphanumericUserNames](https://msdn.microsoft.com/library/dn613211.aspx)。                                                          |  
| Authentication/UserManager/UserValidator/RequireUniqueEmail             | 验证用户是否需要唯一的电子邮件地址。 默认值： true。 有关详细信息[，请： UserValidator < TUser，TKey >。RequireUniqueEmail](https://msdn.microsoft.com/library/dn613213.aspx)。                                                                   |  
| Authentication/UserManager/PasswordValidator/RequiredLength             | 所需的最短密码长度。 默认值：8。 有关详细信息，请查看： [PasswordValidator. RequiredLength](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredlength.aspx)。                                       |  
| Authentication/UserManager/PasswordValidator/RequireNonLetterOrDigit    | 密码是否需要非字母或数字字符。 默认值： false。 有关详细信息，请查看： [PasswordValidator. RequireNonLetterOrDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirenonletterordigit.aspx)。 |  
| Authentication/UserManager/PasswordValidator/RequireDigit               | 密码是否需要数字（从0到9）。 默认值： false。 有关详细信息，请查看： [PasswordValidator. RequireDigit](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requiredigit.aspx)。                |  
| Authentication/UserManager/PasswordValidator/RequireLowercase           | 密码是否需要小写字母（从 a 到 z）。 默认值： false。 有关详细信息，请查看： [PasswordValidator. RequireLowercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requirelowercase.aspx)。        |  
| Authentication/UserManager/PasswordValidator/RequireUppercase           | 密码是否需要大写字母（从 A 到 Z）。 默认值： false。 有关详细信息，请查看： [PasswordValidator. RequireUppercase](https://msdn.microsoft.com/library/microsoft.aspnet.identity.passwordvalidator.requireuppercase.aspx)。       | 
|| 

## <a name="user-account-lockout-settings"></a>用户帐户锁定设置

下面介绍了定义如何以及何时从身份验证中锁定帐户的设置。 如果在很短的时间内检测到一定次数的失败密码尝试，则该用户帐户会锁定一段时间。 使用可以在锁定期限结束后重试。

| 站点设置名称                                               | 描述                                                                                                                                                                                                                                     |
|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/UserManager/UserLockoutEnabledByDefault          | 指示在创建用户时是否启用用户锁定。 默认值： true。 有关详细信息[，请： UserManager < TUser，TKey >。UserLockoutEnabledByDefault](https://msdn.microsoft.com/library/dn613214.aspx)。                                                                                                  |  
| Authentication/UserManager/DefaultAccountLockoutTimeSpan        | 达到身份验证/UserManager/MaxFailedAccessAttemptsBeforeLockout 后用户被锁定的默认时间长度。 默认值：24:00:00 （1天）。 有关详细信息[，请： UserManager < TUser，TKey >。DefaultAccountLockoutTimeSpan](https://msdn.microsoft.com/library/dn613201.aspx)。                 |  
| Authentication/UserManager/MaxFailedAccessAttemptsBeforeLockout | 锁定用户之前允许的最大访问尝试次数（如果启用了锁定）。 默认值：5。 有关详细信息[，请： UserManager < TUser，TKey >。MaxFailedAccessAttemptsBeforeLockout](https://msdn.microsoft.com/library/dn613202.aspx)。                                                                        |  
| Authentication/ApplicationCookie/ExpireTimeSpan                 | Cookie 身份验证会话的默认时间长度为有效。 默认值：24:00:00 （1天）。 有关详细信息，请查看： [cookieauthenticationoptions.authenticationtype. ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx)。 |
||  

## <a name="cookie-authentication-site-settings"></a>Cookie 身份验证网站设置

用于修改默认身份验证 cookie 行为的设置。 由[cookieauthenticationoptions.authenticationtype](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.aspx)类定义。

| 站点设置名称   | 描述       |
|----------------------|------------------------------------------------|
| Authentication/ApplicationCookie/AuthenticationType                      | 应用程序身份验证 cookie 的类型。 默认值： ApplicationCookie。 有关详细信息，请查看： [AuthenticationOptions：： AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx)。  |
| Authentication/ApplicationCookie/CookieName                              | 确定用于保存标识的 cookie 名称。 默认值：。AspNet. Cookie。 有关详细信息，请查看： [cookieauthenticationoptions.authenticationtype：： CookieName](https://msdn.microsoft.com/library/dn385537.aspx)。  |
| Authentication/ApplicationCookie/CookieDomain                            | 确定用于创建 cookie 的域。 有关详细信息，请查看： [cookieauthenticationoptions.authenticationtype：： CookieDomain](https://msdn.microsoft.com/library/dn385536.aspx)。  |
| Authentication/ApplicationCookie/CookiePath                              | 确定用于创建 cookie 的路径。 默认值：/。 有关详细信息，请查看： [cookieauthenticationoptions.authenticationtype：： CookiePath](https://msdn.microsoft.com/library/dn385539.aspx)。 |
| Authentication/ApplicationCookie/CookieHttpOnly                          | 确定浏览器是否应允许客户端 javascript 访问 cookie。 默认值： true。 有关详细信息，请查看： [cookieauthenticationoptions.authenticationtype：： CookieHttpOnly](https://msdn.microsoft.com/library/dn385540.aspx)。                     |
| Authentication/ApplicationCookie/CookieSecure                            | 确定 cookie 是否应该只在 HTTPS 请求上传输。 默认值： SameAsRequest。 有关详细信息，请查看： [cookieauthenticationoptions.authenticationtype：： CookieSecure](https://msdn.microsoft.com/library/dn385538.aspx)。  |
| Authentication/ApplicationCookie/ExpireTimeSpan                          | 控制应用程序 cookie 从创建的点保持有效的时间。 默认值：14天。 有关详细信息，请查看： [cookieauthenticationoptions.authenticationtype：： ExpireTimeSpan](https://msdn.microsoft.com/library/microsoft.owin.security.cookies.cookieauthenticationoptions.expiretimespan(v=vs.113).aspx)。  |
| Authentication/ApplicationCookie/SlidingExpiration                       | SlidingExpiration 设置为 true，以指示中间件在每次处理超过过期时段一半的请求时，使用新的过期时间重新发出新的 cookie。 默认值： true。 有关详细信息，请查看： [cookieauthenticationoptions.authenticationtype：： SlidingExpiration](https://msdn.microsoft.com/library/dn385548.aspx)。 |
| Authentication/ApplicationCookie/LoginPath                               | LoginPath 属性通知中间件，应将传出401未经授权的状态代码更改为302重定向到给定的登录路径。 默认值： ~/signin。 有关详细信息，请查看： [cookieauthenticationoptions.authenticationtype：： LoginPath](https://msdn.microsoft.com/library/dn385541.aspx)。                                            |
| Authentication/ApplicationCookie/LogoutPath                              | 如果 LogoutPath 提供了中间件，则对该路径的请求将基于 ReturnUrlParameter 进行重定向。 有关详细信息，请查看： [cookieauthenticationoptions.authenticationtype：： LogoutPath](https://msdn.microsoft.com/library/dn385545.aspx)。               |
| Authentication/ApplicationCookie/ReturnUrlParameter                      | ReturnUrlParameter 确定在401未授权状态代码更改为302重定向到登录路径时，中间件追加的查询字符串参数的名称。 有关详细信息，请查看： [cookieauthenticationoptions.authenticationtype：： ReturnUrlParameter](https://msdn.microsoft.com/library/dn385546.aspx)。                           |
| Authentication/ApplicationCookie/SecurityStampValidator/ValidateInterval | 安全戳验证之间的时间段。 默认值：30分钟。 有关详细信息，请查看： [SecurityStampValidator：： OnValidateIdentity](https://msdn.microsoft.com/library/microsoft.aspnet.identity.owin.securitystampvalidator.onvalidateidentity.aspx)。                    |
| Authentication/TwoFactorCookie/AuthenticationType                        | 双因素身份验证 cookie 的类型。 默认值： TwoFactorCookie。 有关详细信息，请查看： [AuthenticationOptions：： AuthenticationType](https://msdn.microsoft.com/library/dn300391.aspx)。            |
| Authentication/TwoFactorCookie/ExpireTimeSpan                            | 控制两个系数 cookie 从创建的点保持有效的时间。 默认值：5分钟。 有关详细信息，请查看： [cookieauthenticationoptions.authenticationtype：： ExpireTimeSpan](https://msdn.microsoft.com/library/dn385543.aspx)。     |
|||

### <a name="see-also"></a>另请参阅

[配置门户身份验证](configure-portal-authentication.md)  
[门户的 OAuth2 提供程序设置](configure-oauth2-settings.md)  
[为门户打开 ID 连接提供程序设置](configure-openid-settings.md)  
[门户的 WS 联合身份验证提供程序设置](configure-ws-federation-settings.md)  
[门户的 SAML 2.0 提供程序设置](configure-saml2-settings.md)  
