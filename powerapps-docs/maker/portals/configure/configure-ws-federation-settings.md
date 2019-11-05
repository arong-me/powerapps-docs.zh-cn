---
title: 为门户配置 WS 联合身份验证提供程序设置 |MicrosoftDocs
description: 有关为门户添加和配置 WS 联合身份验证提供程序设置的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 2a668f501a54472da0335344997c049794794783
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542702"
---
# <a name="configure-ws-federation-provider-settings-for-portals"></a>为门户配置 WS 联合身份验证提供程序设置

单个 [!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)] 联合身份验证服务服务器可以作为标识提供程序添加（或另一个符合[WS 联合身份验证的](https://msdn.microsoft.com/library/bb498017.aspx)security token service）。 此外，可以将单个[[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ACS](https://azure.microsoft.com/documentation/articles/active-directory-dotnet-how-to-use-access-control/)命名空间配置为一组单独的标识提供者。 AD FS 和 ACS 的设置都基于[wsfederationauthenticationoptions.wtrealm 相](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.aspx)类的属性。

## <a name="create-an-ad-fs-relying-party-trust"></a>创建 AD FS 信赖方信任

使用 AD FS 管理工具，中转到 "**信任关系**" &gt;**信赖方信任**"。

1.  选择 "**添加信赖方信任**"。
2.  欢迎使用：选择 "**启动**"。
3.  选择数据源：选择 **"手动输入信赖方数据**"，然后选择 "**下一步**"。
4.  指定显示名称：输入**名称**，然后选择 "**下一步**"。
    示例： https://portal.contoso.com/
5.  选择 "配置文件"：选择**AD FS 2.0 配置文件**，然后选择 "**下一步**"。
6.  配置证书：选择 "**下一步**"。
7.  配置 URL：选中 "**启用对 WS 联合身份验证被动协议的支持**" 复选框。

信赖方 WS 联合身份验证被动协议 URL：输入 https://portal.contoso.com/signin-federation

-   注意： AD FS 要求门户在**HTTPS**上运行。

    > [!Note]
    > 生成的终结点具有以下设置：终结点类型： **ws-federation**
    > -   绑定： **POST**
    > -   Index：暂缺（0）
    > -   URL： **https://portal.contoso.com/signin-federation**

8.  配置标识：指定 https://portal.contoso.com/ ，选择 "**添加**"，然后选择 "**下一步**"。
    如果适用，则可为每个其他信赖方门户添加更多标识。 用户将可以在任何或所有可用标识之间进行身份验证。
9.  选择 "颁发授权规则"：选择 "**允许所有用户访问此信赖方**"，然后选择 "**下一步**"。
10.  已准备好添加信任：选择 "**下一步**"。
11.  选择“关闭”。

将**名称 ID**声明添加到信赖方信任：

将**帐户名 [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] 转换**为**名称 ID**声明（转换传入声明）：
- 传入声明类型： Windows 帐户名
- 传出声明类型：名称 ID
- 传出名称 ID 格式：未指定
- 传递所有声明值

### <a name="create-ad-fs-site-settings"></a>创建 AD FS 站点设置

应用引用上述 AD FS 信赖方信任的门户网站设置。

> [!Note]
> 标准 AD FS （STS）配置仅使用以下设置（示例值）：
> - Authentication/WsFederation/ADFS/MetadataAddress- https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType- https://adfs.contoso.com/adfs/services/trust
>   - 使用联合元数据的根元素中的**entityID**属性的值（在浏览器中打开**MetadataAddress URL** ，该浏览器是上述站点设置的值）
> - Authentication/WsFederation/ADFS/Wtrealm- https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply- https://portal.contoso.com/signin-federation

可以通过在 AD FS 服务器上运行以下脚本，在 **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** 中检索**WS 联合身份验证元数据**：

```
Import-Module adfs
Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml
```


|                      站点设置名称                      |                                                                                                                                                                                                                                                 描述                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      Authentication/Registration/ExternalLoginEnabled       |                                                                                                                                                                                                                启用或禁用外部帐户登录和注册。 默认值： true                                                                                                                                                                                                                 |
|      Authentication/WsFederation/ADFS/MetadataAddress       | 必填。 AD FS （STS）服务器的[WS 联合身份验证](https://msdn.microsoft.com/library/bb498017.aspx)元数据 URL。 通常以路径：/Federationmetadata.xml/2007-06/Federationmetadata.xml 结束。 示例：<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>。 有关详细信息，请查看： [wsfederationauthenticationoptions.wtrealm 相. MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx)。 |
|     Authentication/WsFederation/ADFS/AuthenticationType     |            必填。 OWIN authentication 中间件类型。 在联合元数据 XML 的根指定[entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata)属性的值。 示例： https://adfs.contoso.com/adfs/services/trust 。 有关详细信息，请查看： [AuthenticationOptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)。             |
|          Authentication/WsFederation/ADFS/Wtrealm           |                                                                                                              必填。 AD FS 信赖方标识符。 示例： `https://portal.contoso.com/`。 有关详细信息，请查看： [wsfederationauthenticationoptions.wtrealm 相. Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)。                                                                                                               |
|           Authentication/WsFederation/ADFS/Wreply           |                                                                                                     必填。 AD FS WS 联合身份验证被动终结点。 示例： https://portal.contoso.com/signin-federation 。 有关详细信息，请查看： [wsfederationauthenticationoptions.wtrealm 相. Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)。                                                                                                     |
|          Authentication/WsFederation/ADFS/Caption           |                                                                                                           您. 用户可在登录用户界面上显示的文本。 默认值： ADFS。 有关详细信息，请查看： [wsfederationauthenticationoptions.wtrealm 相](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)。                                                                                                            |
|        Authentication/WsFederation/ADFS/CallbackPath        |                                                                                                             用于处理身份验证回调的可选约束路径。 有关详细信息，请查看： [wsfederationauthenticationoptions.wtrealm 相. CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)。                                                                                                              |
|       Authentication/WsFederation/ADFS/SignOutWreply        |                                                                                                                               注销过程中使用的 "wreply" 值。有关详细信息，请查看： [wsfederationauthenticationoptions.wtrealm 相. SignOutWreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signoutwreply.aspx)。                                                                                                                               |
|     Authentication/WsFederation/ADFS/BackchannelTimeout     |                                                                                                         反向通道通信的超时值。 示例：00:05:00 （5分钟）。 有关详细信息，请查看： [wsfederationauthenticationoptions.wtrealm 相. BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)。                                                                                                         |
| Authentication/WsFederation/ADFS/RefreshOnIssuerKeyNotFound |                                                                                  确定在 SecurityTokenSignatureKeyNotFoundException 后是否应尝试进行元数据刷新。 有关详细信息，请查看： [wsfederationauthenticationoptions.wtrealm 相. RefreshOnIssuerKeyNotFound](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.refreshonissuerkeynotfound.aspx)。                                                                                  |
|      Authentication/WsFederation/ADFS/UseTokenLifetime      |                                                                                                   指示身份验证会话生存期（如 cookie）应与身份验证令牌的生存期匹配。 [Wsfederationauthenticationoptions.wtrealm 相. UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx)。                                                                                                   |
|     Authentication/WsFederation/ADFS/AuthenticationMode     |                                                                                                                                            OWIN authentication 中间件模式。 有关详细信息，请查看： [AuthenticationOptions. AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)。                                                                                                                                             |
| Authentication/WsFederation/ADFS/SignInAsAuthenticationType |                                                                                            创建 ClaimsIdentity 时使用的 AuthenticationType。 有关详细信息，请查看： [wsfederationauthenticationoptions.wtrealm 相. SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)。                                                                                            |
|       Authentication/WsFederation/ADFS/ValidAudiences       |                                                                                                                                         以逗号分隔的受众 Url 列表。 有关详细信息，请查看： [TokenValidationParameters. AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)。                                                                                                                                          |
|        Authentication/WsFederation/ADFS/ValidIssuers        |                                                                                                                                              以逗号分隔的颁发者 Url 列表。 有关详细信息，请查看： [TokenValidationParameters. ValidIssuers](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.validissuers.aspx)。                                                                                                                                               |
|         Authentication/WsFederation/ADFS/ClockSkew          |                                                                                                                                                                                                                               验证时间时要应用的时钟偏差。                                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/NameClaimType        |                                                                                                                                                                                                                     ClaimsIdentity 用于存储名称声明的声明类型。                                                                                                                                                                                                                      |
|       Authentication/WsFederation/ADFS/RoleClaimType        |                                                                                                                                                                                                                     ClaimsIdentity 用于存储角色声明的声明类型。                                                                                                                                                                                                                      |
|   Authentication/WsFederation/ADFS/RequireExpirationTime    |                                                                                                                                                                                                                     一个值，该值指示令牌是否必须具有 "过期" 值。                                                                                                                                                                                                                      |
|    Authentication/WsFederation/ADFS/RequireSignedTokens     |                                                                                                                                                                       一个值，该值指示 System.identitymodel xmlns =<https://ddue.schemas.microsoft.com/authoring/2003/5> 在未签名时是否有效。                                                                                                                                                                       |
|      Authentication/WsFederation/ADFS/SaveSigninToken       |                                                                                                                                                                                                               用于控制在创建会话时是否保存原始标记的布尔值。                                                                                                                                                                                                                |
|       Authentication/WsFederation/ADFS/ValidateActor        |                                                                                                                                                                                                   一个值，该值指示是否应验证 System.identitymodel. JwtSecurityToken。                                                                                                                                                                                                    |
|      Authentication/WsFederation/ADFS/ValidateAudience      |                                                                                                                                                                                                               用于控制是否将在令牌验证过程中验证受众的布尔值。                                                                                                                                                                                                               |
|       Authentication/WsFederation/ADFS/ValidateIssuer       |                                                                                                                                                                                                                用于控制是否将在令牌验证过程中验证颁发者的布尔值。                                                                                                                                                                                                                |
|      Authentication/WsFederation/ADFS/ValidateLifetime      |                                                                                                                                                                                                               用于控制是否将在令牌验证过程中验证生存期的布尔值。                                                                                                                                                                                                               |
|  Authentication/WsFederation/ADFS/ValidateIssuerSigningKey  |                                                                                                                                                         一个布尔值，控制是否调用对 securityToken xmlns =<https://ddue.schemas.microsoft.com/authoring/2003/5> 进行签名的 System.identitymodel。                                                                                                                                                          |
|            Authentication/WsFederation/ADFS/瓦             |                                                                                                                                       指定标识提供程序重定向 URL 中的 "里瓦" 参数。 有关详细信息，请查看： [wsFederation](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation)。                                                                                                                                       |

## <a name="ws-federation-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] 的 WS 联合身份验证设置

前面描述 AD FS 的部分也可以应用于 [!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] （[[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ad](https://msdn.microsoft.com/library/azure/mt168838.aspx)），因为 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 的行为类似于符合标准[WS 联合身份验证](https://docs.microsoft.com/azure/active-directory/develop/active-directory-developers-guide)的 security token service。 若要开始登录到[[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 管理门户](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal)并创建或选择现有目录。 当目录可用时，请按照说明向目录[添加应用程序](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)。

1.  在目录的 "**应用程序**" 菜单下，选择 "**添加**"。
2.  选择 **"添加我的组织正在开发的应用程序"** 。
3.  为应用程序指定自定义**名称**，然后选择 " **web 应用程序和/或 web API**" 类型。
4.  对于 "**登录 URL** " 和 "**应用 ID URI**"，为 https://portal.contoso.com/ 的两个字段指定门户的 URL。
    - 这对应于**Wtrealm**站点设置值。
5.  此时，将创建一个新的应用程序。 在菜单中，切换到 "**配置**" 部分。
6.  在 "**单一登录**" 部分中，更新第一个 "**答复 url** " 条目，以将路径包含在 URL https://portal.contoso.com/signin-azure-ad 中。
    - 这对应于**Wreply**站点设置值。
7.  选择页脚中的 "**保存**"。
8.  在页脚菜单中，选择 "**查看终结点**"，并记下 "**联合元数据文档**" 字段。

    - 这对应于**MetadataAddress**站点设置值。
    - 在浏览器窗口中粘贴此 URL 以查看联合元数据 XML，并记下根元素的**entityID**属性。
    - 这对应于**AuthenticationType**站点设置值。

> [!Note]
> 标准 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 配置仅使用以下设置（示例值）：
> - Authentication/WsFederation/ADFS/MetadataAddress- https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml
> - Authentication/WsFederation/ADFS/AuthenticationType- https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/
>   - 使用联合元数据的根元素中的**entityID**属性的值（在浏览器中打开**MetadataAddress URL** ，该浏览器是上述站点设置的值）
> - Authentication/WsFederation/ADFS/Wtrealm- https://portal.contoso.com/
> - Authentication/WsFederation/ADFS/Wreply- https://portal.contoso.com/signin-azure-ad

### <a name="see-also"></a>另请参阅

[配置门户身份验证](configure-portal-authentication.md)  
[设置门户的身份验证标识](set-authentication-identity.md)  
[门户的 OAuth2 提供程序设置](configure-oauth2-settings.md)  
[为门户打开 ID 连接提供程序设置](configure-openid-settings.md)  
[门户的 SAML 2.0 提供程序设置](configure-saml2-settings.md)  
