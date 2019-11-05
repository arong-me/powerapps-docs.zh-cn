---
title: 为门户配置 OpenID Connect 提供程序设置 |MicrosoftDocs
description: 有关为门户添加和配置 OpenID Connect 提供程序设置的说明。
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
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542790"
---
# <a name="configure-open-id-connect-provider-settings-for-portals"></a>为门户配置打开 ID 连接提供程序设置

[OpenID connect](https://openid.net/connect/)外部标识提供程序是符合 Open ID Connect[规范](https://openid.net/developers/specs/)的服务。 集成提供程序涉及查找与提供程序关联的颁发机构（或颁发者） URL。 可以从提供身份验证工作流过程中所需的元数据的颁发机构确定配置 URL。 提供程序设置基于[OpenIdConnectAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.aspx)类的属性。

颁发机构 Url 的示例如下：

- [Google](https://developers.google.com/identity/protocols/OpenIDConnect)： <https://accounts.google.com/><https://accounts.google.com/.well-known/openid-configuration>
- [[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)]](https://msdn.microsoft.com/library/azure/mt168838.aspx)： [https://login.microsoftonline.com/&lt ;[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 应用程序&gt;/](https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration)

每个 OpenID Connect 提供程序还包括注册应用程序（类似于 OAuth 2.0 提供程序的）以及获取客户端 Id。授权 URL 和生成的应用程序客户端 Id 是在门户和标识提供程序之间启用外部身份验证所需的设置。

> [!Note]
> 当前不支持 Google OpenID Connect 终结点，因为基础库仍处于版本的早期阶段，并且存在兼容性问题。 可以改为使用门户终结点的[OAuth2 提供程序设置](configure-oauth2-settings.md)。

## <a name="openid-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] 的 OpenID 设置

若要开始，请登录到[[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 管理门户](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal)并创建或选择现有目录。 当目录可用时，请按照说明向目录[添加应用程序](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)。  

1. 在目录的 "**应用程序**" 菜单下，选择 "**添加**"。
2. 选择 **"添加我的组织正在开发的应用程序"** 。
3. 指定应用程序的自定义**名称**，然后选择 " **web 应用程序和/或 web API**" 类型。
4. 对于 "**登录 URL** " 和 "**应用 ID URI**"，请为这两个字段指定门户的 URL https://portal.contoso.com/
5. 此时，将创建一个新的应用程序。 导航至菜单中的 "**配置**" 部分。

    在 "**单一登录**" 部分下，更新 "第一个**回复 url** " 条目以在 URL 中包含路径： https://portal.contoso.com/signin-azure-ad 。 这对应于**RedirectUri**站点设置值

6. 在 "**属性**" 部分下，找到 "**客户端 ID** " 字段。 这对应于**ClientId**站点设置值。
7. 在页脚菜单中，选择 "**查看终结点**"，并记下 "**联合元数据文档**" 字段

URL 的左侧部分是**授权**值，采用以下格式之一：

- https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/
- https://login.microsoftonline.com/contoso.onmicrosoft.com/

若要获取服务配置 URL，请将 Federationmetadata.xml/2007-06/Federationmetadata.xml 路径结尾替换为路径。众所周知/openid-配置。 例如，<https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration>

这对应于**MetadataAddress**站点设置值。

### <a name="related-site-settings"></a>相关站点设置

应用引用上述应用程序的门户网站设置。

> [!Note]
> 标准 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 配置仅使用以下设置（示例值）：                                 
> - 身份验证/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/颁发机构-<https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/>                                                    
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ClientId-fedcba98-7654-3210-fedc-ba9876543210                                      
>   客户端 ID 和颁发机构 URL 不包含相同的值，应单独检索。           
> - Authentication/OpenIdConnect/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/RedirectUri- https://portal.contoso.com/signin-azure-ad
 
可以通过使用 \[提供程序的标签\] 标记来配置多个标识提供程序。 每个唯一标签形成一组与标识提供者相关的设置。 示例： [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD、MyIdP


|                          站点设置名称                           |                                                                                                                                                                                                         描述                                                                                                                                                                                                          |
|----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           Authentication/Registration/ExternalLoginEnabled           |                                                                                                                                                                         启用或禁用外部帐户登录和注册。 默认值： true                                                                                                                                                                         |
|         身份验证/OpenIdConnect/\[提供程序\]/Authority          |                                               必填。 进行 OpenIdConnect 调用时要使用的授权。 示例： `https://login.microsoftonline.com/contoso.onmicrosoft.com/`。 有关详细信息：[OpenIdConnectAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.authority.aspx)。                                                |
|      身份验证/OpenIdConnect/\[提供程序\]/MetadataAddress       | 用于获取元数据的发现终结点。 通常以路径：/. well-known/openid-configuration 结束。 示例： `https://login.microsoftonline.com/contoso.onmicrosoft.com/.well-known/openid-configuration`。 有关详细信息，请查看：[OpenIdConnectAuthenticationOptions. MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.metadataaddress.aspx)。 |
|     身份验证/OpenIdConnect/\[提供程序\]/AuthenticationType     |                                   OWIN authentication 中间件类型。 在服务配置元数据中指定颁发者的值。 示例： `https://sts.windows.net/contoso.onmicrosoft.com/`。 有关详细信息，请查看： [AuthenticationOptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)。                                   |
|          身份验证/OpenIdConnect/\[提供程序\]/ClientId          |                                                  必填。 提供程序应用程序中的 "客户端 ID" 值。 它也可能称为 "应用 ID" 或 "使用者密钥"。 有关详细信息，请查看： [OpenIdConnectAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientid.aspx)。                                                   |
|        身份验证/OpenIdConnect/\[提供程序\]/ClientSecret        |                                              提供程序应用程序的客户端机密值。 它也可能称为 "应用密钥" 或 "使用者机密"。 有关详细信息，请查看： [OpenIdConnectAuthenticationOptions. ClientSecret](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.clientsecret.aspx)。                                              |
|        身份验证/OpenIdConnect/\[提供程序\]/RedirectUri         |                                                        您. AD FS WS 联合身份验证被动终结点。 示例： https://portal.contoso.com/signin-saml2 。 有关详细信息，请查看： [OpenIdConnectAuthenticationOptions. RedirectUri](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.redirecturi.aspx)。                                                        |
|          身份验证/OpenIdConnect/\[提供程序\]/Caption           |                                                              您. 用户可在登录用户界面上显示的文本。 默认值： \[提供程序\]。 有关详细信息，请查看： [OpenIdConnectAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.caption.aspx)。                                                               |
|          身份验证/OpenIdConnect/\[提供程序\]/Resource          |                                                                                                       "资源"。 有关详细信息，请查看： [OpenIdConnectAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.resource.aspx)。                                                                                                        |
|        身份验证/OpenIdConnect/\[提供程序\]/ResponseType        |                                                                                                "Response\_类型"。 有关详细信息，请查看： [OpenIdConnectAuthenticationOptions. ResponseType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.responsetype.aspx)。                                                                                                 |
|           身份验证/OpenIdConnect/\[提供程序\]/Scope            |                                                                                要请求的权限的空格分隔列表。 默认值： openid。 有关详细信息，请查看： [OpenIdConnectAuthenticationOptions ](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.scope.aspx)。                                                                                 |
|        身份验证/OpenIdConnect/\[提供程序\]/CallbackPath        |                      用于处理身份验证回调的可选约束路径。 如果未提供并且 RedirectUri 可用，则将从 RedirectUri 生成此值。 有关详细信息，请查看： [OpenIdConnectAuthenticationOptions. CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.callbackpath.aspx)。                      |
|     身份验证/OpenIdConnect/\[提供程序\]/BackchannelTimeout     |                                                                反向通道通信的超时值。 示例：00:05:00 （5分钟）。 有关详细信息，请查看： [OpenIdConnectAuthenticationOptions. BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.backchanneltimeout.aspx)。                                                                |
| 身份验证/OpenIdConnect/\[提供程序\]/RefreshOnIssuerKeyNotFound |                                      确定是否应在 SecurityTokenSignatureKeyNotFoundException 后尝试执行元数据刷新。 有关详细信息，请查看： [OpenIdConnectAuthenticationOptions. RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.refreshonissuerkeynotfound.aspx)。                                       |
|      身份验证/OpenIdConnect/\[提供程序\]/UseTokenLifetime      |                                               指示身份验证会话生存期（如 cookie）应与身份验证令牌的生存期匹配。 有关详细信息，请查看： [OpenIdConnectAuthenticationOptions. UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.usetokenlifetime.aspx)。                                               |
|     身份验证/OpenIdConnect/\[提供程序\]/AuthenticationMode     |                                                                                                     OWIN authentication 中间件模式。 有关详细信息，请查看： [AuthenticationOptions. AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)。                                                                                                     |
| 身份验证/OpenIdConnect/\[提供程序\]/SignInAsAuthenticationType |                                                   创建 ClaimsIdentity 时使用的 AuthenticationType。 有关详细信息，请查看： [OpenIdConnectAuthenticationOptions. SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.signinasauthenticationtype.aspx)。                                                   |
|   身份验证/OpenIdConnect/\[提供程序\]/PostLogoutRedirectUri    |                                                                                 "Post\_注销\_重定向\_uri"。 有关详细信息，请查看： [OpenIdConnectAuthenticationOptions. PostLogoutRedirectUri](https://msdn.microsoft.com/library/microsoft.owin.security.openidconnect.openidconnectauthenticationoptions.postlogoutredirecturi.aspx)。                                                                                 |
|       身份验证/OpenIdConnect/\[提供程序\]/ValidAudiences       |                                                                                                  以逗号分隔的受众 Url 列表。 有关详细信息，请查看： [TokenValidationParameters. AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)。                                                                                                  |
|        身份验证/OpenIdConnect/\[提供程序\]/ValidIssuers        |                                                                                                       以逗号分隔的颁发者 Url 列表。 有关详细信息，请查看： [TokenValidationParameters. ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx)。                                                                                                       |
|         身份验证/OpenIdConnect/\[提供程序\]/ClockSkew          |                                                                                                                                                                                        验证时间时要应用的时钟偏差。                                                                                                                                                                                        |
|       身份验证/OpenIdConnect/\[提供程序\]/NameClaimType        |                                                                                                                                                                              ClaimsIdentity 用于存储名称声明的声明类型。                                                                                                                                                                              |
|       身份验证/OpenIdConnect/\[提供程序\]/RoleClaimType        |                                                                                                                                                                              ClaimsIdentity 用于存储角色声明的声明类型。                                                                                                                                                                              |
|   身份验证/OpenIdConnect/\[提供程序\]/RequireExpirationTime    |                                                                                                                                                                              一个值，该值指示令牌是否必须具有 "过期" 值。                                                                                                                                                                              |
|    身份验证/OpenIdConnect/\[提供程序\]/RequireSignedTokens     |                                                                                                                               一个值，该值指示 System.identitymodel xmlns =<https://ddue.schemas.microsoft.com/authoring/2003/5> 在未签名时是否有效。                                                                                                                                |
|      身份验证/OpenIdConnect/\[提供程序\]/SaveSigninToken       |                                                                                                                                                                        用于控制在创建会话时是否保存原始标记的布尔值。                                                                                                                                                                        |
|       身份验证/OpenIdConnect/\[提供程序\]/ValidateActor        |                                                                                                                                                            一个值，该值指示是否应验证 System.identitymodel. JwtSecurityToken。                                                                                                                                                            |
|      身份验证/OpenIdConnect/\[提供程序\]/ValidateAudience      |                                                                                                                                                                       用于控制是否将在令牌验证过程中验证受众的布尔值。                                                                                                                                                                        |
|       身份验证/OpenIdConnect/\[提供程序\]/ValidateIssuer       |                                                                                                                                                                        用于控制是否将在令牌验证过程中验证颁发者的布尔值。                                                                                                                                                                         |
|      身份验证/OpenIdConnect/\[提供程序\]/ValidateLifetime      |                                                                                                                                                                       用于控制是否将在令牌验证过程中验证生存期的布尔值。                                                                                                                                                                        |
|  身份验证/OpenIdConnect/\[提供程序\]/ValidateIssuerSigningKey  |                                                                                                                  一个布尔值，控制是否调用对 securityToken xmlns =<https://ddue.schemas.microsoft.com/authoring/2003/5> 进行签名的 System.identitymodel。                                                                                                                  |
|                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                              |

## <a name="enable-authentication-using-a-multi-tenant-azure-active-directory-application"></a>使用多租户 Azure Active Directory 应用程序启用身份验证

可以通过使用 [!include[](../../../includes/pn-azure-active-directory.md)]中注册的多租户应用程序，将门户配置为接受来自 [!include[](../../../includes/pn-azure-shortest.md)] 中任何租户的 [!include[](../../../includes/pn-azure-active-directory.md)] 用户，而不仅仅是特定租户。 若要启用多租户，请在 [!include[](../../../includes/pn-azure-active-directory.md)] 应用程序中将**多租户**开关设置为 **"是"** 。

![在 Azure Active Directory 应用程序中启用多租户](../media/enable-multi-tenancy.png "在 Azure Active Directory 应用程序中启用多租户")

### <a name="related-site-settings"></a>相关站点设置

可以通过替换 [provider] 标记的标签来配置多个标识提供程序。 每个唯一标签形成一组与标识提供者相关的设置。 你可以在门户中创建或配置以下站点设置，以支持使用租户应用程序对 [!include[](../../../includes/pn-azure-active-directory.md)] 进行身份验证：

|站点设置名称    |描述   |
|---|---|
|Authentication/OpenIdConnect/[provider]/Authority   |进行 OpenIdConnect 调用时要使用的授权。 例如： `https://login.microsoftonline.com/common`   |
|Authentication/OpenIdConnect/[provider]/ClientId   |提供程序应用程序中的 "客户端 ID" 值。 它也可以称为应用 ID 或使用者密钥。   |
|Authentication/OpenIdConnect/[provider]/ExternalLogoutEnabled   |启用或禁用外部帐户注销和注册。 将此值设置为 True。   |
|Authentication/OpenIdConnect/[provider]/IssuerFilter   |基于通配符的筛选器，与所有租户中的所有颁发者匹配。 在大多数情况下，使用值： `https://sts.windows.net/*/`   |
|Authentication/OpenIdConnect/[provider]/RedirectUri  |提供程序向其发送身份验证响应的回复 URL 位置。例如： `https://portal.contoso.com/signin-oidc` |
|Authentication/OpenIdConnect/[provider]/ValidateIssuer   |用于控制是否将在令牌验证过程中验证颁发者的布尔值。 将此值设置为 False。   |
|||

### <a name="see-also"></a>另请参阅
[配置门户身份验证](configure-portal-authentication.md)  
[设置门户的身份验证标识](set-authentication-identity.md)  
[门户的 OAuth2 提供程序设置](configure-oauth2-settings.md)  
[门户的 WS 联合身份验证提供程序设置](configure-ws-federation-settings.md)  
[门户的 SAML 2.0 提供程序设置](configure-saml2-settings.md)  

