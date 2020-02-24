---
title: 配置门户的 WS 联合身份验证提供程序 | MicrosoftDocs
description: 有关如何添加和配置门户的 WS-Federation 提供程序设置的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: f210a5c806ce3ac894e647fc882a4e3d8f4c0167
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977653"
---
# <a name="configure-ws-federation-provider-settings-for-portals"></a>配置门户的 WS 联合身份验证提供程序设置

单个  [!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)] 联合身份验证服务服务器可作为身份提供程序（或又一个遵守 [WS 联合身份验证](https://msdn.microsoft.com/library/bb498017.aspx)的安全令牌服务）添加。 此外，单个 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ACS](https://azure.microsoft.com/documentation/articles/active-directory-dotnet-how-to-use-access-control/) 命名空间可作为一组单独的身份提供程序配置。 AD FS 和 ACS 的设置均基于 [WsFederationAuthenticationOptions](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.aspx) 类的属性。

## <a name="create-an-ad-fs-relying-party-trust"></a>创建 AD FS 信赖方信任

使用 AD FS 管理工具，转至**信任关系** &gt; **信赖方信任**。

1.  选择**添加信赖方信任**。
2.  欢迎：选择**开始**。
3.  选择数据源：选择**手动输入有关信赖方的数据**，然后选择**下一步**。
4.  指定显示名称：输入**名称**，然后选择**下一步**。
    示例: https://portal.contoso.com/
5.  选择配置文件：选择 **AD FS 2.0 配置文件**，然后选择**下一步**。
6.  配置证书：选择**下一步**。
7.  配置 URL：选中**启用 WS 联合身份验证被动协议的支持**复选框。

信赖方 WS 联合身份验证被动协议 URL：输入 https://portal.contoso.com/signin-federation

-   注意：AD FS 要求门户在 **HTTPS** 上运行。

    > [!Note]
    > 出现的终结点具有下列设置：终结点类型：**WS 联合身份验证**
    > -   绑定：**POST**
    > -   索引：n/a (0)
    > -   URL：**https://portal.contoso.com/signin-federation**

8.  配置标识：指定 https://portal.contoso.com/，选择**添加**，然后选择**下一步**。
    如果适用，可以为每个其他信赖方门户添加更多身份。 用户可以跨任何或所有可用身份进行身份验证。
9.  选择颁发授权规则：选择**允许所有用户访问此信赖方**，然后选择**下一步**。
10.  准备添加信任：选择**下一步**。
11.  选择**关闭**。

添加**名称 ID** 声明到信赖方信任：

**将 [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] 帐户名**转换为**名称 ID** 声明（转换传入声明）：
- 传入声明类型：Windows 帐户名
- 传出声明类型：名称 ID
- 传出名称 ID 格式：未指定
- 传递所有声明值

### <a name="create-ad-fs-site-settings"></a>创建 AD FS 网站设置

应用引用上面的 AD FS 信赖方信任的门户网站设置。

> [!Note]
> 标准 AD FS (STS) 配置仅使用以下设置（包含示例值）：
> - Authentication/WsFederation/ADFS/MetadataAddress - https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType - https://adfs.contoso.com/adfs/services/trust
>   - 使用联合元数据的根元素中的 **entityID** 属性值（在是上方网站设置的浏览器中打开 **MetadataAddress URL**）
> - Authentication/WsFederation/ADFS/Wtrealm - https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply - https://portal.contoso.com/signin-federation

**WS 联合身份验证元数据**可以通过在 AD FS 服务器上运行以下脚本在 **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** 中进行检索：

```
Import-Module adfs
Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml
```


|                      网站设置名称                      |                                                                                                                                                                                                                                                 说明                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Authentication/Registration/ExternalLoginEnabled       |                                                                                                                                                                                                                启用或禁用外部帐户登录和注册。 默认：true                                                                                                                                                                                                                 |
|      Authentication/WsFederation/ADFS/MetadataAddress       | 必需。 AD FS (STS) 服务器的 [WS 联合身份验证](https://msdn.microsoft.com/library/bb498017.aspx)元数据 URL。 通常以此路径结尾：/FederationMetadata/2007-06/FederationMetadata.xml。 示例：<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>。 有关详细信息：[WsFederationAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx)。 |
|     Authentication/WsFederation/ADFS/AuthenticationType     |            必需。 OWIN 身份验证中间件类型。 在联合元数据 XML 的根指定 [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) 属性的值。 示例：https://adfs.contoso.com/adfs/services/trust。 有关详细信息：[AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)。             |
|          Authentication/WsFederation/ADFS/Wtrealm           |                                                                                                              必需。 AD FS 信赖方标识符。 示例：`https://portal.contoso.com/`。 有关详细信息：[WsFederationAuthenticationOptions.Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)。                                                                                                               |
|           Authentication/WsFederation/ADFS/Wreply           |                                                                                                     必需。 AD FS WS 联合身份验证被动终结点。 示例：https://portal.contoso.com/signin-federation。 有关详细信息：[WsFederationAuthenticationOptions.Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)。                                                                                                     |
|          Authentication/WsFederation/ADFS/Caption           |                                                                                                           推荐。 用户可以在登录用户界面中显示的文本。 默认：ADFS。 有关详细信息：[WsFederationAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)。                                                                                                            |
|        Authentication/WsFederation/ADFS/CallbackPath        |                                                                                                             在其中处理身份验证回调的可选约束路径。 有关详细信息：[WsFederationAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)。                                                                                                              |
|       Authentication/WsFederation/ADFS/SignOutWreply        |                                                                                                                               注销期间应使用“wreply”值。有关详细信息：[WsFederationAuthenticationOptions.SignOutWreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signoutwreply.aspx)。                                                                                                                               |
|     Authentication/WsFederation/ADFS/BackchannelTimeout     |                                                                                                         反向信道通信的超时值。 示例：00:05:00（5 分钟）。 有关详细信息：[WsFederationAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)。                                                                                                         |
| Authentication/WsFederation/ADFS/RefreshOnIssuerKeyNotFound |                                                                                  确定是否应在 SecurityTokenSignatureKeyNotFoundException 后尝试刷新元数据。 有关详细信息：[WsFederationAuthenticationOptions.RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.refreshonissuerkeynotfound.aspx)。                                                                                  |
|      Authentication/WsFederation/ADFS/UseTokenLifetime      |                                                                                                   指示身份验证会话生存期（例如，Cookie）应与身份验证令牌匹配。 [WsFederationAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx)。                                                                                                   |
|     Authentication/WsFederation/ADFS/AuthenticationMode     |                                                                                                                                            OWIN 身份验证中间件模式。 有关详细信息：[AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)。                                                                                                                                             |
| Authentication/WsFederation/ADFS/SignInAsAuthenticationType |                                                                                            在创建 System.Security.Claims.ClaimsIdentity 时使用的 AuthenticationType。 有关详细信息：[WsFederationAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)。                                                                                            |
|       Authentication/WsFederation/ADFS/ValidAudiences       |                                                                                                                                         逗号分隔访问群体 URL 的列表。 有关详细信息：[TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)。                                                                                                                                          |
|        Authentication/WsFederation/ADFS/ValidIssuers        |                                                                                                                                              逗号分隔颁发者 URL 的列表。 有关详细信息：[TokenValidationParameters.ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx)。                                                                                                                                               |
|         Authentication/WsFederation/ADFS/ClockSkew          |                                                                                                                                                                                                                               验证时间时要应用的时钟偏移。                                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/NameClaimType        |                                                                                                                                                                                                                     ClaimsIdentity 用于存储名称声明的声明类型。                                                                                                                                                                                                                      |
|       Authentication/WsFederation/ADFS/RoleClaimType        |                                                                                                                                                                                                                     ClaimsIdentity 用于存储角色声明的声明类型。                                                                                                                                                                                                                      |
|   Authentication/WsFederation/ADFS/RequireExpirationTime    |                                                                                                                                                                                                                     指示令牌是否必须具有“到期”值的值。                                                                                                                                                                                                                      |
|    Authentication/WsFederation/ADFS/RequireSignedTokens     |                                                                                                                                                                       指示如果未签名 System.IdentityModel.Tokens.SecurityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5> 是否可以有效的值。                                                                                                                                                                       |
|      Authentication/WsFederation/ADFS/SaveSigninToken       |                                                                                                                                                                                                               控制在创建会话时是否保存原始令牌的布尔值。                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/ValidateActor        |                                                                                                                                                                                                   指示是否应验证 System.IdentityModel.Tokens.JwtSecurityToken.Actor 的值。                                                                                                                                                                                                    |
|      Authentication/WsFederation/ADFS/ValidateAudience      |                                                                                                                                                                                                               控制是否在验证令牌时验证访问群体的布尔值。                                                                                                                                                                                                               |
|       Authentication/WsFederation/ADFS/ValidateIssuer       |                                                                                                                                                                                                                控制是否在验证令牌时验证颁发者的布尔值。                                                                                                                                                                                                                |
|      Authentication/WsFederation/ADFS/ValidateLifetime      |                                                                                                                                                                                                               控制是否在验证令牌时验证生存期的布尔值。                                                                                                                                                                                                               |
|  Authentication/WsFederation/ADFS/ValidateIssuerSigningKey  |                                                                                                                                                         控制签署 securityToken xmlns=<https://ddue.schemas.microsoft.com/authoring/2003/5> 的 System.IdentityModel.Tokens.SecurityKey 的验证是否调用的布尔值。                                                                                                                                                          |
|            Authentication/WsFederation/ADFS/Whr             |                                                                                                                                       在身份提供程序重定向 URL 中指定“whr”参数。 有关详细信息：[wsFederation](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation)。                                                                                                                                       |

## <a name="ws-federation-settings-for-pn-azure-active-directory"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] 的 WS 联合身份验证设置

介绍 AD FS 的上一章节也可以适用于 [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] ([[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx))，因为 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 行为与遵守标准 [WS 联合身份验证](https://docs.microsoft.com/azure/active-directory/develop/active-directory-developers-guide) 的安全令牌服务相似。 开始登录到 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 管理门户](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal)并创建或选择现有目录。 提供目录时，按照说明[将应用程序添加](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)到目录。

1.  在目录的**应用程序**菜单下，选择**添加**。
2.  选择**添加我的组织正在开发的应用程序**。
3.  为应用程序指定自定义**名称**，然后选择类型 **Web 应用程序和/或 Web API**。
4.  对于**登录 URL** 和**应用程序 ID URI**，指定两个字段的门户的 URLhttps://portal.contoso.com/。
    - 这对应于 **Wtrealm** 网站设置值。
5.  此时，新应用程序创建。 在菜单中转至**配置**部分。
6.  在**单一登录**部分中，更新第一个**响应 URL** 条目以在 URL 中包含路径 https://portal.contoso.com/signin-azure-ad。
    - 这对应于 **Wreply** 网站设置值。
7.  在脚注中，选择**保存**。
8.  在脚注菜单上，选择**查看终结点**并注意**联合元数据文档**字段。

    - 这对应于 **MetadataAddress** 网站设置值。
    - 在浏览器窗口中粘贴此 URL 以查看联合元数据 XML 并注释根元素的 **entityID** 属性。
    - 这对应于 **AuthenticationType** 网站设置值。

> [!Note]
> 标准 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 配置仅使用以下设置（包含示例值）：
> - Authentication/WsFederation/ADFS/MetadataAddress - https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType - https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/
>   - 使用联合元数据的根元素中的 **entityID** 属性值（在是上方网站设置的浏览器中打开 **MetadataAddress URL**）
> - Authentication/WsFederation/ADFS/Wtrealm - https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply - https://portal.contoso.com/signin-azure-ad

### <a name="see-also"></a>另请参阅

[配置门户身份验证](configure-portal-authentication.md)  
[设置门户的身份验证标识](set-authentication-identity.md)  
[门户的 OAuth2 提供程序设置](configure-oauth2-settings.md)  
[门户的 Open ID Connect 提供程序设置](configure-openid-settings.md)  
[门户的 SAML 2.0 提供程序设置](configure-saml2-settings.md)  
