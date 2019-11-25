---
title: 配置门户的 OpenID Connect 提供程序设置 | MicrosoftDocs
description: 有关如何添加和配置门户的 OpenID Connect 提供程序设置的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 2b4d31165ccd12b2cb5c8c2a4c8ec6f9dd04a7c7
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755343"
---
# <a name="configure-open-id-connect-provider-settings-for-portals"></a>配置门户的 Open ID Connect 提供程序设置

[OpenID Connect](https://openid.net/connect/) 外部身份提供程序是符合 Open ID Connect [规范](https://openid.net/developers/specs/)的服务。 集成提供程序涉及查找与提供程序关联的监管机构（或 发行机构）URL。 配置 URL 可以从在身份验证工作流期间提供所需元数据的监管机构确定。 提供程序设置基于 [OpenIdConnectAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.aspx) 类的属性。

监管机构 URL 的示例：

- [Google](https://developers.google.com/identity/protocols/OpenIDConnect)：<https://accounts.google.com/><https://accounts.google.com/.well-known/openid-configuration>
- [[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]](https://msdn.microsoft.com/library/azure/mt168838.aspx)：[https://login.microsoftonline.com/&lt;[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 应用程序&gt;/](https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration)

各 OpenID Connect 提供程序还涉及注册应用程序（类似 OAuth 2.0 提供程序）和获取客户端 ID。颁发机构 URL 和生成的客户端 ID 是在门户与身份提供程序之间实现外部身份验证所需设置。

> [!Note]
> Google OpenID Connect 终结点目前不支持，因为基础库仍然处于版本的早期阶段，存在要解决的兼容性问题。 可以改用[门户的 OAuth2 提供程序设置](configure-oauth2-settings.md)终结点。

## <a name="openid-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] 的 OpenID 设置

开始登录到 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 管理门户](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal)并创建或选择现有目录。 提供目录时，按照说明[将应用程序添加](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)到目录。  

1. 在目录的**应用程序**菜单下，选择**添加**。
2. 选择**添加我的组织正在开发的应用程序**。
3. 为应用程序指定自定义**名称**并选择类型 **Web 应用程序和/或 Web API**。
4. 对于**登录 URL** 和**应用程序 ID URI**，指定两个字段的门户的 URLhttps://portal.contoso.com/
5. 此时，新应用程序创建。 在菜单中导航到**配置**部分。

    在**单一登录**部分下，更新第一个**响应 URL** 条目以在 URL 中包含路径：https://portal.contoso.com/signin-azure-ad。 这对应 **RedirectUri** 网站设置值

6. 在**属性**部分下，找到**客户端 ID** 字段。 对应 **ClientId** 网站设置值。
7. 在脚注菜单上，选择**查看终结点**并注意**联合元数据文档**字段

URL 的剩余部分是**监管机构**值，使用以下格式之一：

- https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/
- https://login.microsoftonline.com/contoso.onmicrosoft.com/

若要获取服务配置 URL，请将 FederationMetadata/2007-06/FederationMetadata.xml 路径尾替换为路径 .well-known/openid-configuration。 例如，<https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration>

这对应于 **MetadataAddress** 网站设置值。

### <a name="related-site-settings"></a>相关站点设置

应用引用上述应用程序的门户网站设置

> [!Note]
> 标准 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 配置仅使用以下设置（包含示例值）：                                 
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/Authority - <https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/>                                                    
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ClientId - fedcba98-7654-3210-fedc-ba9876543210                                      
>   客户端 ID 和监管机构 URL 不包含相同值，应该单独检索。           
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/RedirectUri - https://portal.contoso.com/signin-azure-ad
 
多个身份提供程序可以通过替代 \[provider\] 标记的标签配置。 每个唯一标签建立与身份提供程序相关的一组设置。 示例：[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD、MyIdP


|                          网站设置名称                           |                                                                                                                                                                                                         说明                                                                                                                                                                                                          |
|----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Authentication/Registration/ExternalLoginEnabled           |                                                                                                                                                                         启用或禁用外部帐户登录和注册。 默认：true                                                                                                                                                                         |
|         Authentication/OpenIdConnect/\[provider\]/Authority          |                                               必需。 进行 OpenIdConnect 调用时要使用的监管机构。 示例：`https://login.microsoftonline.com/contoso.onmicrosoft.com/`。 有关详细信息：[OpenIdConnectAuthenticationOptions.Authority](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.authority.aspx)。                                                |
|      Authentication/OpenIdConnect/\[provider\]/MetadataAddress       | 获取元数据的发现终结点。 通常结尾为以下路径：/.well-known/openid-configuration。 示例：`https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration`。 有关详细信息：[OpenIdConnectAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.metadataaddress.aspx)。 |
|     Authentication/OpenIdConnect/\[provider\]/AuthenticationType     |                                   OWIN 身份验证中间件类型。 指定服务配置元数据中的发行机构值。 示例：`https://sts.windows.net/contoso.onmicrosoft.com/`。 有关详细信息：[AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)。                                   |
|          Authentication/OpenIdConnect/\[provider\]/ClientId          |                                                  必需。 来自提供程序应用程序的客户端 ID 值。 也可将其称为“应用程序 ID”或“使用者密钥”。 有关详细信息：[OpenIdConnectAuthenticationOptions.ClientId](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientid.aspx)。                                                   |
|        Authentication/OpenIdConnect/\[provider\]/ClientSecret        |                                              来自提供程序应用程序的客户端密码值。 也可将其称为“应用程序密码”或“使用者密码”。 有关详细信息：[OpenIdConnectAuthenticationOptions.ClientSecret](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientsecret.aspx)。                                              |
|        Authentication/OpenIdConnect/\[provider\]/RedirectUri         |                                                        推荐。 AD FS WS 联合身份验证被动终结点。 示例：https://portal.contoso.com/signin-saml2。 有关详细信息：[OpenIdConnectAuthenticationOptions.RedirectUri](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.redirecturi.aspx)。                                                        |
|          Authentication/OpenIdConnect/\[provider\]/Caption           |                                                              推荐。 用户可以在登录用户界面中显示的文本。 默认值：\[provider\]。 有关详细信息：[OpenIdConnectAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.caption.aspx)。                                                               |
|          Authentication/OpenIdConnect/\[provider\]/Resource          |                                                                                                       'resource'。 有关详细信息：[OpenIdConnectAuthenticationOptions.Resource](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.resource.aspx)。                                                                                                        |
|        Authentication/OpenIdConnect/\[provider\]/ResponseType        |                                                                                                “response\_type”。 有关详细信息：[OpenIdConnectAuthenticationOptions.ResponseType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.responsetype.aspx)。                                                                                                 |
|           Authentication/OpenIdConnect/\[provider\]/Scope            |                                                                                以空格分隔的要请求的权限的列表。 默认值：openid。 有关详细信息：[OpenIdConnectAuthenticationOptions.Scope](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.scope.aspx)。                                                                                 |
|        Authentication/OpenIdConnect/\[provider\]/CallbackPath        |                      在其中处理身份验证回调的可选约束路径。 如果未提供且 RedirectUri 可用，此值将从 RedirectUri 生成。 有关详细信息：[OpenIdConnectAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.callbackpath.aspx)。                      |
|     Authentication/OpenIdConnect/\[provider\]/BackchannelTimeout     |                                                                反向信道通信的超时值。 示例：00:05:00（5 分钟）。 有关详细信息：[OpenIdConnectAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.backchanneltimeout.aspx)。                                                                |
| Authentication/OpenIdConnect/\[provider\]/RefreshOnIssuerKeyNotFound |                                      确定是否应在 SecurityTokenSignatureKeyNotFoundException 后尝试刷新元数据。 有关详细信息：[OpenIdConnectAuthenticationOptions.RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.refreshonissuerkeynotfound.aspx)。                                       |
|      Authentication/OpenIdConnect/\[provider\]/UseTokenLifetime      |                                               指示身份验证会话生存期（例如，Cookie）应与身份验证令牌匹配。 有关详细信息：[OpenIdConnectAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.usetokenlifetime.aspx)。                                               |
|     Authentication/OpenIdConnect/\[provider\]/AuthenticationMode     |                                                                                                     OWIN 身份验证中间件模式。 有关详细信息：[AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)。                                                                                                     |
| Authentication/OpenIdConnect/\[provider\]/SignInAsAuthenticationType |                                                   在创建 System.Security.Claims.ClaimsIdentity 时使用的 AuthenticationType。 有关详细信息：[OpenIdConnectAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.signinasauthenticationtype.aspx)。                                                   |
|   Authentication/OpenIdConnect/\[provider\]/PostLogoutRedirectUri    |                                                                                 |post\_logout\_redirect\_uri“。 有关详细信息：[OpenIdConnectAuthenticationOptions.PostLogoutRedirectUri](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.postlogoutredirecturi.aspx)。                                                                                 |
|       Authentication/OpenIdConnect/\[provider\]/ValidAudiences       |                                                                                                  逗号分隔访问群体 URL 的列表。 有关详细信息：[TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)。                                                                                                  |
|        Authentication/OpenIdConnect/\[provider\]/ValidIssuers        |                                                                                                       逗号分隔颁发者 URL 的列表。 有关详细信息：[TokenValidationParameters.ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx)。                                                                                                       |
|         Authentication/OpenIdConnect/\[provider\]/ClockSkew          |                                                                                                                                                                                        验证时间时要应用的时钟偏移。                                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[provider\]/NameClaimType        |                                                                                                                                                                              ClaimsIdentity 用于存储名称声明的声明类型。                                                                                                                                                                              |
|       Authentication/OpenIdConnect/\[provider\]/RoleClaimType        |                                                                                                                                                                              ClaimsIdentity 用于存储角色声明的声明类型。                                                                                                                                                                              |
|   Authentication/OpenIdConnect/\[provider\]/RequireExpirationTime    |                                                                                                                                                                              指示令牌是否必须具有“到期”值的值。                                                                                                                                                                              |
|    Authentication/OpenIdConnect/\[provider\]/RequireSignedTokens     |                                                                                                                               指示如果未签名 System.IdentityModel.Tokens.SecurityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5> 是否可以有效的值。                                                                                                                                |
|      Authentication/OpenIdConnect/\[provider\]/SaveSigninToken       |                                                                                                                                                                        控制在创建会话时是否保存原始令牌的布尔值。                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[provider\]/ValidateActor        |                                                                                                                                                            指示是否应验证 System.IdentityModel.Tokens.JwtSecurityToken.Actor 的值。                                                                                                                                                            |
|      Authentication/OpenIdConnect/\[provider\]/ValidateAudience      |                                                                                                                                                                       控制是否在验证令牌时验证访问群体的布尔值。                                                                                                                                                                        |
|       Authentication/OpenIdConnect/\[provider\]/ValidateIssuer       |                                                                                                                                                                        控制是否在验证令牌时验证颁发者的布尔值。                                                                                                                                                                         |
|      Authentication/OpenIdConnect/\[provider\]/ValidateLifetime      |                                                                                                                                                                       控制是否在验证令牌时验证生存期的布尔值。                                                                                                                                                                        |
|  Authentication/OpenIdConnect/\[provider\]/ValidateIssuerSigningKey  |                                                                                                                  控制签署 securityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5> 的 System.IdentityModel.Tokens.SecurityKey 的验证是否调用的布尔值。                                                                                                                  |
|                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                              |

## <a name="enable-authentication-using-a-multi-tenant-azure-active-directory-application"></a>使用多租户 Azure Active Directory 应用程序启用身份验证

您可以使用在 [!include[](../../../includes/pn-azure-active-directory.md)] 中注册的多租户应用程序将门户配置为接受来自 [!include[](../../../includes/pn-azure-shortest.md)] 中任何租户而不只是特定租户的 [!include[](../../../includes/pn-azure-active-directory.md)] 用户。 若要启用多组织，在 [!include[](../../../includes/pn-azure-active-directory.md)] 应用程序中将**多租户**切换为**是**。

![在 Azure Active Directory 应用程序中启用多组织](../media/enable-multi-tenancy.png "在 Azure Active Directory 应用程序中启用多组织")

### <a name="related-site-settings"></a>相关站点设置

可以通过用标签代替 [provider] 标记来配置多个标识提供者。 每个唯一标签建立与身份提供程序相关的一组设置。 您可以使用多租户应用程序在门户中创建或配置以下站点来支持对 [!include[](../../../includes/pn-azure-active-directory.md)] 的身份验证：

|网站设置名称    |说明   |
|---|---|
|Authentication/OpenIdConnect/[provider]/Authority   |进行 OpenIdConnect 调用时要使用的监管机构。 例如：`https://login.microsoftonline.com/common`   |
|Authentication/OpenIdConnect/[provider]/ClientId   |来自提供程序应用程序的客户端 ID 值。 也可将其称为“应用程序 ID”或“使用者密钥”。   |
|Authentication/OpenIdConnect/[provider]/ExternalLogoutEnabled   |启用或禁用外部帐户注销和注册。 将此值设置为 True。   |
|Authentication/OpenIdConnect/[provider]/IssuerFilter   |在跨所有租户的所有颁发者中匹配的基于通配符的筛选器。 在多数情况下，请使用值：`https://sts.windows.net/*/`   |
|Authentication/OpenIdConnect/[provider]/RedirectUri  |提供程序发送身份验证响应的回复 URL 位置。例如：`https://portal.contoso.com/signin-oidc` |
|Authentication/OpenIdConnect/[provider]/ValidateIssuer   |控制是否在验证令牌时验证颁发者的布尔值。 将此值设置为 False。   |
|||

### <a name="see-also"></a>另请参阅
[配置门户身份验证](configure-portal-authentication.md)  
[设置门户的身份验证标识](set-authentication-identity.md)  
[门户的 OAuth2 提供程序设置](configure-oauth2-settings.md)  
[门户的 WS 联合身份验证提供程序设置](configure-ws-federation-settings.md)  
[门户的 SAML 2.0 提供程序设置](configure-saml2-settings.md)  

