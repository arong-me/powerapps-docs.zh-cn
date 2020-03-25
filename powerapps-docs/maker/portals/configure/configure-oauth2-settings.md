---
title: 配置门户的 OAuth2 提供程序设置 | MicrosoftDocs
description: 有关如何添加和配置门户的 OAuth2 提供程序设置的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/17/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 6065c842831aa9aa0c225d12470a4469fe51146d
ms.sourcegitcommit: 629e47c769172e312ae07cb29e66fba8b4f03efc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "3108052"
---
# <a name="configure-oauth2-provider-settings-for-portals"></a>配置门户的 OAuth2 提供程序设置

基于 OAuth 2.0 的外部身份提供程序涉及注册具有第三方服务的“应用程序”以获取“客户端 ID“和“客户端密码”对。 通常此应用程序需要指定允许身份提供程序将用户发送回门户的重定向 URL（信赖方）。 客户端 ID 和客户端密码配置为门户网站设置，以便建立从信赖方到身份提供程序的安全连接。 设置基于 [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]AccountAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.aspx)、[TwitterAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.twitter.twitterauthenticationoptions.aspx)、[FacebookAuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.facebook.facebookauthenticationoptions.aspx) 和 [GoogleOAuth2AuthenticationOptions](https://msdn.microsoft.com//library/microsoft.owin.security.google.googleoauth2authenticationoptions.aspx) 类的属性。  

支持的提供程序是：

- [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 帐户
- Twitter
- Facebook
- Google
- LinkedIn
- Yahoo

## <a name="create-oauth-applications"></a>创建 OAuth 应用程序

一般来说，如果 OAuth 提供程序使用需要重定向 URI 值的应用设置，请根据提供程序如何执行重定向 URI 验证（部分提供程序需要随域名指定完整 URL 路径）指定 <https://portal.contoso.com/or> https://portal.contoso.com/signin-\[provider\]。 将替代重定向 URI 中替代 \[provider\] 的提供程序的名称。

## <a name="google-people-api-settings"></a>Google People API 设置

> [!NOTE]
> 已弃用 [Google+ API](https://developers.google.com/people/legacy)。 我们强烈建议您迁移到 [Google People API](https://developers.google.com/people)。

请执行以下步骤为 Power Apps 门户配置 [Google 的 OAuth 2.0 身份验证] 以执行用户身份验证。

1. 打开 [Google 开发人员控制台](https://console.developers.google.com/)。  
1. 创建 API 项目或打开现有项目。
1. 从 API 和服务仪表板选择**启用 API 和服务**。
1. 搜索并启用 API **Google People API**。
1. 在 **Google APIs** 内，选择左侧导航中的 **Credentials**。

    > [!NOTE]
    > 如果已经为同意屏幕配置了门户顶级域，可以跳过步骤 6 到 14，直接转到步骤 15。 但是，如果已配置了同意屏幕，但是未添加门户顶级域，请在转到步骤 15 之前，执行步骤 11。

1. 选择**配置同意屏幕**。
1. 选择**外部**用户类型。
1. 选择**创建**。
1. 键入**应用程序名称**，需要时，上传徽标的图像。
1. 选择相应的**支持电子邮件**。
1. 在**授权域**中，为顶级域键入 **powerappsportals.com**。 如果尚未[更新您的 Power Apps 门户域名](../admin/update-portal-domain.md)，请使用 **microsoftcrmportals.com**。 如果已经配置了[自定义域名](../admin/add-custom-domain.md)，也可以输入此域名。 
1. 根据需要提供主页、隐私政策和服务条款的链接。 
1. 选择**保存**。
1. 从左侧导航菜单中选择**凭据**。
1. 从**创建凭据**下拉菜单选择 **Oauth 客户端 ID**。
1. 应用程序类型选择 **Web 应用程序**。
1. 键入 Oauth 客户端 ID 的**名称**。
1. 在**授权的 JavaScript 起源**列表中键入您的 Power Apps 门户 URL。
1. **授权重定向 URI** 键入 Power Apps 门户 URL 加 **/signin-google**。 例如，如果门户 URL 为 https://contoso.powerappsportals.com，则授权重定向 URIs 字段应该为 https://contoso.powerappsportals.com/signin-google。
1. 选择**创建**。
1. 复制 **Oauth 客户端**中的**客户端 ID** 和**客户端密码**，然后配置 Power Apps 门户中的 [OAuth2 站点设置](https://docs.microsoft.com/powerapps/maker/portals/configure/configure-oauth2-settings#create-site-settings-by-using-oauth2)。

## <a name="facebook-app-settings"></a>Facebook 应用程序设置

1. 打开 [Facebook 开发人员应用程序仪表板](https://developers.facebook.com/apps)  
2. 选择**添加新应用程序**。
3. 选择**网站**。
4. 选择**跳过并创建应用程序 ID**。
    - 指定**显示名称**。
    - 选择**类别**。
    - 选择**创建应用程序 ID**。

5. 在新应用程序的仪表板中，转至**设置** &gt; **基本**（选项卡），然后添加以下详细信息：
    - 应用程序域（可选）：portal.contoso.com 
    - 联系人电子邮件：*&lt;您选择的电子邮件地址&gt;* 
    - 选择**添加平台**，然后选择**网站**。 
    - 网站 URL：https://portal.contoso.com/ 或 https://portal.contoso.com/signin-facebook

6. 选择**保存更改**。
7. 转至**状态和审查** &gt; **状态**选项卡。
8. 提示将该应用程序及其所有功能提供给公众时，选择**是**。 必须在上面的步骤 5 中填写了有效数据，才能启用此设置。

### <a name="cc-microsoft-application-settings"></a>[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 应用程序设置

1. 打开 [[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)] 帐户开发人员中心](https://account.live.com/developers/applications/index)  
2. 选择**创建应用程序**并指定**应用程序名称**。
3. 选择**我接受**以接受条款和条件。
4. 转到**设置** &gt; **API 设置**，然后将重定向 URL 设置为 https://portal.contoso.com/signin-microsoft 

## <a name="twitter-apps-settings"></a>Twitter 应用程序设置

1. 打开 [Twitter 应用程序管理](https://apps.twitter.com/)。 
2. 选择**新建应用程序**。

    - 指定应用程序的**名称**和**描述**。
    - 将网站 URL 设为 https://portal.contoso.com。
    - 将回调 URL 设置为 https://portal.contoso.com 或 https://portal.contoso.com/signin-twitter。

3. 选择**创建您的 Twitter 应用程序**。

## <a name="linkedin-app-settings"></a>LinkedIn 应用程序设置

1. 打开 [LinkedIn 开发人员网络](https://www.linkedin.com/secure/developer)。  
2. 选择**添加新应用程序**。

    - 指定**应用程序名称**、**说明**等。
    - 将网站 URL 设为 https://portal.contoso.com。
    - 设置 OAuth 用户协议/默认范围：r\_basicprofie 和 r\_emailaddress
    - 设置 OAuth 2.0 重定向 Url：https://portal.contoso.com/signin-linkedin。

3. 选择**添加应用程序**。

## <a name="yahoo-ydn-app-settings"></a>Yahoo! YDN 应用程序设置

> [!NOTE]
> 更新后的 Yahoo YDN OAuth 提供商终结点与 Power Apps 门户之间的现有兼容性问题导致用户暂时不可以通过 Yahoo 身份提供程序的身份验证。

1. 打开 [Yahoo! 开发人员网络](https://developer.yahoo.com/apps)。
2. 选择**创建应用程序**。
    
    - 指定**应用程序名称**。
    - 应用程序类型：**Web 应用程序**。
    - 回调域：portal.contoso.com

3. 选择**创建应用程序**。

## <a name="create-site-settings-by-using-oauth2"></a>使用 OAuth2 创建网站设置

每个提供程序的应用程序仪表板将显示每个应用程序的客户端 ID（应用程序 ID、使用者密钥）和客户端密码（应用程序密码、使用者密码）。 使用这两个值配置门户网站设置。

>[!Note]
> 标准 OAuth2 配置只需要以下设置（以 Facebook 为例）：
> - `Authentication/OpenAuth/Facebook/ClientId`
> - `Authentication/OpenAuth/Facebook/ClientSecret`

替代特定身份提供程序名称为以下名称的网站设置名称的 `[provider]` 标记：Facebook、Google、Yahoo、[!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]、LinkedIn 或 Twitter。

|**网站设置名称**                                           |**说明**                                                                                                                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ExternalLoginEnabled                | 启用或禁用外部帐户登录和注册。 默认：true                                                                                                                                                                                                                                                                         |
| Authentication/OpenAuth/\[provider\]/ClientId                   | 必需。 来自提供程序应用程序的客户端 ID 值。 也可将其称为“应用程序 ID”或“使用者密钥”。  以下设置名称允许向后兼容性：Authentication/OpenAuth/Twitter/ConsumerKey <ul><li>Authentication/OpenAuth/Facebook/AppId</li><li>Authentication/OpenAuth/LinkedIn/ConsumerKey</li> |
| Authentication/OpenAuth/\[provider\]/ClientSecret               | 必需。 来自提供程序应用程序的客户端密码值。 也可将其称为“应用程序密码”或“使用者密码”。  以下设置名称允许向后兼容性：Authentication/OpenAuth/Twitter/ConsumerSecret <ul><li>Authentication/OpenAuth/Facebook/AppSecret</li><li>Authentication/OpenAuth/LinkedIn/ConsumerSecret</li> |
| Authentication/OpenAuth/\[provider\]/AuthenticationType         | OWIN 身份验证中间件类型。 示例：yahoo。 [authenticationoptions.authenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)。                                                                                                                                |  
| Authentication/OpenAuth/\[provider\]/Scope                      | 要请求的权限的逗号分隔的列表。 [microsoftaccountauthenticationoptions.scope](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.scope.aspx)。                                                                                                                |  
| Authentication/OpenAuth/\[provider\]/Caption                    | 用户可以在登录用户界面中显示的文本。 [microsoftaccountauthenticationoptions.caption](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.caption.aspx)。                                                                                              |  
| Authentication/OpenAuth/\[provider\]/BackchannelTimeout         | 反向信道通信的超时值（毫秒）。 [microsoftaccountauthenticationoptions.backchanneltimeout](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.backchanneltimeout.aspx)。                                                                         |  
| Authentication/OpenAuth/\[provider\]/CallbackPath               | 用户代理将返回的应用程序基本路径中的请求路径。 [microsoftaccountauthenticationoptions.callbackpath](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.callbackpath.aspx)。                                                         |  
| Authentication/OpenAuth/\[provider\]/SignInAsAuthenticationType | 将负责实际颁发 **userClaimsIdentity** 的其他身份验证中间件的名称。 [microsoftaccountauthenticationoptions.signinasauthenticationtype](https://msdn.microsoft.com//library/microsoft.owin.security.microsoftaccount.microsoftaccountauthenticationoptions.signinasauthenticationtype.aspx)。 |  
| Authentication/OpenAuth/\[provider\]/AuthenticationMode         | OWIN 身份验证中间件模式。 [security.authenticationoptions.authenticationmode](https://msdn.microsoft.com//library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)。                                                                                                                                       |  

### <a name="see-also"></a>另请参阅

[配置门户身份验证](configure-portal-authentication.md)  
[设置门户的身份验证标识](set-authentication-identity.md)  
[门户的 Open ID Connect 提供程序设置](configure-openid-settings.md)   
[门户的 WS 联合身份验证提供程序设置](configure-ws-federation-settings.md)  
[门户的 SAML 2.0 提供程序设置](configure-saml2-settings.md)
