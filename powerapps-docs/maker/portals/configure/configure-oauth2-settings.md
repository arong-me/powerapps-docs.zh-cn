---
title: 为门户配置 OAuth2 提供程序设置 |MicrosoftDocs
description: 有关为门户添加和配置 OAuth2 提供程序设置的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: be576425067079549d3174e6d6306814a6ddb13a
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542800"
---
# <a name="configure-oauth2-provider-settings-for-portals"></a>为门户配置 OAuth2 提供程序设置

基于 OAuth 2.0 的外部标识提供程序涉及向第三方服务注册 "应用程序"，以获取 "客户端 ID" 和 "客户端密码" 对。 通常，此应用程序需要指定允许标识提供者将用户发送回门户（依赖方）的重定向 URL。 将客户端 ID 和客户端密码配置为门户网站设置，以便建立从信赖方到标识提供程序的安全连接。 这些设置基于[[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]AccountAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.aspx)、 [TwitterAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.twitter.twitterauthenticationoptions.aspx)、 [FacebookAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.facebook.facebookauthenticationoptions.aspx)和[GoogleOAuth2AuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.google.googleoauth2authenticationoptions.aspx)类的属性。  

支持的提供程序包括：

- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 帐户
- Twitter
- Facebook
- Google
- LinkedIn
- Yahoo

## <a name="create-oauth-applications"></a>创建 OAuth 应用程序

通常，如果 OAuth 提供程序使用需要重定向 URI 值的应用设置，请指定 <https://portal.contoso.com/or> https://portal.contoso.com/signin-\[提供程序\]，具体取决于提供程序执行重定向 URI 验证的方式（某些提供程序需要与域名一起指定完整 URL 路径）。 用提供程序的名称替换 "重定向 URI" 中\] 的 \[提供程序。

### <a name="google"></a>Google

[Google OAuth2 API 凭据说明](https://developers.google.com/accounts/docs/OpenIDConnect#appsetup)  

1. 打开[Google 开发人员控制台](https://console.developers.google.com/)  
2. 创建 API 项目或打开现有项目
3. 中转到**api &** Authentication &gt;**api**，然后在 "**社交 Api**" 下选择 "**Google + API**"，并选择 "**启用 API** "
4. 请参阅**api & auth** &gt;**同意屏幕**。
    - 指定**电子邮件地址**。
    - 指定自定义**产品名称**。
    - 选择 "**保存**"。
5. 请参阅**api & auth** &gt;**凭据**，并创建新的客户端 ID。
   - 应用程序类型：**Web 应用程序**
   - 授权 [!INCLUDE[pn-javascript](../../../includes/pn-javascript.md)] 起源： https://portal.contoso.com
   - 授权重定向 Uri： https://portal.contoso.com/signin-google 
   - 选择 "**创建客户端 ID**"。

### <a name="facebook-app-settings"></a>Facebook 应用设置

1. 打开[Facebook 开发人员应用仪表板](https://developers.facebook.com/apps)  
2. 选择 "**添加新应用**"。
3. 选择 "**网站**"。
4. 选择 "**跳过并创建应用 ID**"。
    - 指定**显示名称**。
    - 选择**类别**。
    - 选择 "**创建应用 ID**"。

5. 在新应用的 "仪表板" 上，请参阅 "**设置**" &gt;"**基本**" （选项卡），并添加以下详细信息：
    - 应用域（可选）： portal.contoso.com 
    - 联系人电子邮件：*所选&lt;电子邮件地址&gt;* 
    - 选择 "**添加平台**"，然后选择 "**网站**"。 
    - 网站 URL： https://portal.contoso.com/ 或 https://portal.contoso.com/signin-facebook

6. 选择 "**保存更改**"。
7. 请参阅**状态 & 查看**&gt;**状态**"选项卡。
8. 系统提示时，请选择 **"是**"，以使应用及其所有功能可供一般公共使用。 您必须填写上述步骤5中的有效数据，才能启用此设置。

### <a name="includecc-microsoftincludescc-microsoftmd-application-settings"></a>[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 应用程序设置

1. 打开[[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 帐户开发人员中心](https://account.live.com/developers/applications/index)  
2. 选择 "**创建应用程序**"，并指定**应用程序名称**。
3. 选择 "**我接受**" 以接受条款和条件。
4. 转到 "**设置**" &gt;" **API 设置**"，然后将 "重定向 URL" 设置为 "https://portal.contoso.com/signin-microsoft 

### <a name="twitter-apps-settings"></a>Twitter 应用设置

1. 打开[Twitter 应用程序管理](https://apps.twitter.com/)。 
2. 选择 "**创建新应用**"。

    - 指定应用的**名称**和**描述**。
    - 将网站 URL 设置为 https://portal.contoso.com。
    - 将回叫 URL 设置为 https://portal.contoso.com 或 https://portal.contoso.com/signin-twitter。

3. 选择 "**创建 Twitter 应用程序**"。

### <a name="linkedin-app-settings"></a>LinkedIn 应用设置

1. 打开[LinkedIn 开发人员网络](https://www.linkedin.com/secure/developer)。  
2. 选择 "**添加新应用程序**"。

    - 指定**应用程序名称**、**说明**等。
    - 将 "网站 URL" 设置为 https://portal.contoso.com。
    - 设置 OAuth 用户协议/默认作用域： r\_basicprofie 和 r\_emailaddress
    - 设置 OAuth 2.0 重定向 url： https://portal.contoso.com/signin-linkedin。

3. 选择 "**添加应用程序**"。

### <a name="yahoo-ydn-app-settings"></a>Yahoo！ YDN 应用设置

1. 打开[Yahoo！ Developer Network](https://developer.yahoo.com/apps)。
2. 选择 "**创建应用**"。
    
    - 指定**应用程序名称**。
    - 应用程序类型： **Web 应用程序**。
    - 回拨域： portal.contoso.com

3. 选择 "**创建应用**"。

## <a name="create-site-settings-by-using-oauth2"></a>使用 OAuth2 创建站点设置

每个提供程序的应用程序仪表板将显示每个应用程序的客户端 ID （应用程序 ID、使用者密钥）和客户端密钥（应用程序密钥、使用者机密）。 使用这两个值来配置门户网站设置。

>[!Note]
> 标准 OAuth2 配置只需要以下设置（使用 Facebook 作为示例）：
> - `Authentication/OpenAuth/Facebook/ClientId`
> - `Authentication/OpenAuth/Facebook/ClientSecret`

用特定的标识提供程序名称替换站点设置名称中的 `[provider]` 标记： Facebook、Google、Yahoo、[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]、LinkedIn 或 Twitter。

|**站点设置名称**                                           |**Description**                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ExternalLoginEnabled                | 启用或禁用外部帐户登录和注册。 默认值： true                                                                                                                                                                                                                                                                         |
| 身份验证/OpenAuth/\[提供程序\]/ClientId                   | 必填。 提供程序应用程序中的 "客户端 ID" 值。 它也可以称为应用 ID 或使用者密钥。  允许使用以下设置名称进行向后兼容： Authentication/OpenAuth/Twitter/ConsumerKey <ul><li>Authentication/OpenAuth/Facebook/AppId</li><li>Authentication/OpenAuth/LinkedIn/ConsumerKey</li> |
| 身份验证/OpenAuth/\[提供程序\]/ClientSecret               | 必填。 提供程序应用程序的客户端机密值。 它也可以称为应用密钥或使用者机密。  允许使用以下设置名称进行向后兼容： Authentication/OpenAuth/Twitter/ConsumerSecret <ul><li>Authentication/OpenAuth/Facebook/AppSecret</li><li>Authentication/OpenAuth/LinkedIn/ConsumerSecret</li> |
| 身份验证/OpenAuth/\[提供程序\]/AuthenticationType         | OWIN authentication 中间件类型。 示例： yahoo。 [authenticationoptions. authenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)。                                                                                                                                |  
| 身份验证/OpenAuth/\[提供程序\]/Scope                      | 要请求的权限的逗号分隔列表。 [microsoftaccountauthenticationoptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.scope.aspx)。                                                                                                                |  
| 身份验证/OpenAuth/\[提供程序\]/Caption                    | 用户可在登录用户界面上显示的文本。 [microsoftaccountauthenticationoptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.caption.aspx)。                                                                                              |  
| 身份验证/OpenAuth/\[提供程序\]/BackchannelTimeout         | 反向通道通信的超时值（以毫秒为单位）。 [microsoftaccountauthenticationoptions. backchanneltimeout](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.backchanneltimeout.aspx)。                                                                         |  
| 身份验证/OpenAuth/\[提供程序\]/CallbackPath               | 应用程序的基路径中将返回用户代理的请求路径。 [microsoftaccountauthenticationoptions. callbackpath](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.callbackpath.aspx)。                                                         |  
| 身份验证/OpenAuth/\[提供程序\]/SignInAsAuthenticationType | 将负责实际发出**userClaimsIdentity**的另一个身份验证中间件的名称。 [microsoftaccountauthenticationoptions. signinasauthenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.signinasauthenticationtype.aspx)。 |  
| 身份验证/OpenAuth/\[提供程序\]/AuthenticationMode         | OWIN authentication 中间件模式。 [authenticationoptions. authenticationmode](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)。                                                                                                                                       |  

### <a name="see-also"></a>另请参阅

[配置门户身份验证](configure-portal-authentication.md)  
[设置门户的身份验证标识](set-authentication-identity.md)  
[为门户  打开 ID 连接提供程序设置](configure-openid-settings.md)  
[门户的 WS 联合身份验证提供程序设置](configure-ws-federation-settings.md)  
[门户的 SAML 2.0 提供程序设置](configure-saml2-settings.md)
