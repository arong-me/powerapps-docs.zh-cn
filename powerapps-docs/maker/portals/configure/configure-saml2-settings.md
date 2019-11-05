---
title: 为门户配置 SAML 2.0 提供程序设置 |MicrosoftDocs
description: 有关为门户添加和配置 SAML 2.0 提供程序设置的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: af5b0ae8eddb68127c7271fccb4696a23fedfc60
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542748"
---
# <a name="configure-saml-20-provider-settings-for-portals"></a>为门户配置 SAML 2.0 提供程序设置

若要提供外部身份验证，可以添加一个或多个符合[SAML 2.0](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html)的标识提供者（IdP）。 本文档介绍如何设置各种标识提供者，使其与充当服务提供商的门户集成。  

## <a name="ad-fs-idp"></a>AD FS （IdP）

标识提供程序的设置，例如 [!include[](../../../includes/pn-active-dir-fed-svcs-ad-fs.md)]。

### <a name="create-an-ad-fs-relying-party-trust"></a>创建 AD FS 信赖方信任

> [!Note]
> 有关如何在 [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] 脚本中执行这些步骤的信息，请参阅下面的[使用 PowerShell 配置 AD FS](#configure-ad-fs-by-using-powershell)。

使用 [!include[](../../../includes/pn-adfs-short.md)] 管理工具，请参阅**服务** > **声明说明**。

1.  选择 "**添加声明说明**"。
2.  指定声明：

    -  显示名称：**永久性标识符**

    -  声明标识符： **urn： oasis：名称： tc： SAML：2.0： nameid 格式：持久性**

    -  为以下项**启用**复选框：在联合元数据中发布此声明说明作为此联合身份验证服务可以接受的声明类型

    -  为以下项**启用**复选框：在联合元数据中发布此声明说明作为此联合身份验证服务可以发送的声明类型

3.  选择“确定”。

使用 [!include[](../../../includes/pn-adfs-short.md)] 管理工具选择 "**信任关系**" >**信赖方信任**"。

1. 选择 "**添加信赖方信任**"。
2. 欢迎使用：选择 "**启动**"。
3. 选择数据源：选择 **"手动输入信赖方数据**"，然后选择 "**下一步**"。
4. 指定显示名称：输入名称，然后选择 "**下一步**"。
   示例： https://portal.contoso.com/
5. 选择 "配置文件"：选择**AD FS 2.0 配置文件**，然后选择 "**下一步**"。
6. 配置证书：选择 "**下一步**"。
7. 配置 URL：选中 "**启用对 SAML 2.0 WebSSO 协议的支持"** 复选框。
   信赖方 SAML 2.0 SSO 服务 URL：输入 https://portal.contoso.com/signin-saml2
   - 注意： [!include[](../../../includes/pn-adfs-short.md)] 要求门户在 HTTPS 上运行。

   > [!Note] 
   > 生成的终结点具有以下设置： 
   > - 终结点类型： **SAML 断言使用终结点**             
   > - 绑定： **POST**                                            
   > - Index：暂缺（0）                                              
   > - URL： **https://portal.contoso.com/signin-saml2**

8. 配置标识：指定 https://portal.contoso.com/ ，选择 "**添加**"，然后选择 "**下一步**"。
   如果适用，你可以为每个其他信赖方门户添加更多标识。 用户将可以在任何或所有可用标识之间进行身份验证。
9. 选择 "颁发授权规则"：选择 "**允许所有用户访问此信赖方**"，然后选择 "**下一步**"。
10. 已准备好添加信任：选择 "**下一步**"。
11. 选择“关闭”。

将**名称 ID**声明添加到信赖方信任：

将**帐户名[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] 转换**为**名称 ID**声明（转换传入声明）：

- 传入声明类型： **[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] 帐户名称**

- 传出声明类型：**名称 ID**

- 传出名称 ID 格式：**永久性标识符**

- 传递所有声明值

### <a name="create-site-settings"></a>创建站点设置

应用引用上述 [!include[](../../../includes/pn-adfs-short.md)] 信赖方信任的门户网站设置。

> [!Note]
> 标准 [!include[](../../../includes/pn-adfs-short.md)] （IdP）配置仅使用以下设置（示例值）： Authentication/SAML2/ADFS/MetadataAddress-<https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>  
> - Authentication/SAML2/ADFS/AuthenticationType- https://adfs.contoso.com/adfs/services/trust    
>   -   使用联合元数据的根元素中的**entityID**属性的值（在浏览器中打开**MetadataAddress URL** ，该浏览器是上述站点设置的值） 
> - Authentication/SAML2/ADFS/ServiceProviderRealm- https://portal.contoso.com/  
> - Authentication/SAML2/ADFS/AssertionConsumerServiceUrl- https://portal.contoso.com/signin-saml2  
>   可以通过在 [!include[](../../../includes/pn-adfs-short.md)] 服务器上运行以下脚本来检索**联合元数据** **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** ： `Import-Module adfs`
>   `Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml`

可以通过替换 [provider] 标记的标签来配置多个 IdP 服务。 每个唯一标签形成一组与 IdP 相关的设置。 示例： ADFS、[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD、MyIdP


| 站点设置名称                                             | 描述                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ExternalLoginEnabled              | 启用或禁用外部帐户登录和注册。 默认值： true                                                                                                                                                                                                                                                                                                                                                            |
| Authentication/SAML2/[provider]/MetadataAddress             | 必填。 [!include[](../../../includes/pn-adfs-short.md)] （STS）服务器的[WS 联合身份验证](https://msdn.microsoft.com/library/bb498017.aspx)元数据 URL。 它通常以路径：/Federationmetadata.xml/2007-06/Federationmetadata.xml 结束。 示例： `https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml`。 [!include[](../../../includes/proc-more-information.md)] [wsfederationauthenticationoptions.wtrealm 相. MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx) |  
| Authentication/SAML2/[provider]/AuthenticationType          | 必填。 OWIN authentication 中间件类型。 在联合元数据 XML 的根指定[entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata)属性的值。 示例： `https://adfs.contoso.com/adfs/services/trust`。 [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions. AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)                                                            |  
| Authentication/SAML2/[provider]/ServiceProviderRealm<br>或 <br>Authentication/SAML2/[provider]/Wtrealm                      | 必填。 [!include[](../../../includes/pn-adfs-short.md)] 信赖方标识符。 示例： `https://portal.contoso.com/`。 [!include[](../../../includes/proc-more-information.md)] [wsfederationauthenticationoptions.wtrealm 相. Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)                       |  
| Authentication/SAML2/[provider]/AssertionConsumerServiceUrl<br>或<br>Authentication/SAML2/[provider]/Wreply                       | 必填。 [!include[](../../../includes/pn-adfs-short.md)] SAML 使用者断言终结点。 示例： https://portal.contoso.com/signin-saml2 。 [!include[](../../../includes/proc-more-information.md)] [wsfederationauthenticationoptions.wtrealm 相. Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)                                                                                                                                                                                                  |  
| Authentication/SAML2/[provider]/Caption                     | 您. 用户可在登录用户界面上显示的文本。 默认值： [提供程序]。 [!include[](../../../includes/proc-more-information.md)] [wsfederationauthenticationoptions.wtrealm 相](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)                |  
| Authentication/SAML2/[provider]/CallbackPath                | 用于处理身份验证回调的可选约束路径。 [!include[](../../../includes/proc-more-information.md)] [wsfederationauthenticationoptions.wtrealm 相. CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)                                                                                                                                                                                                                      |  
| Authentication/SAML2/[provider]/BackchannelTimeout          | 反通道通信的超时值。 示例：00:05:00 （5分钟）。 [!include[](../../../includes/proc-more-information.md)] [wsfederationauthenticationoptions.wtrealm 相. BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)                                                                                                                                                                                                                   |  
| Authentication/SAML2/[provider]/UseTokenLifetime            | 指示身份验证会话生存期（例如，cookie）应与身份验证令牌的生存期匹配。 [Wsfederationauthenticationoptions.wtrealm 相. UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx)。                                                                                                                                                                               |  
| Authentication/SAML2/[provider]/AuthenticationMode          | OWIN authentication 中间件模式。 [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions. AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)                                                                                                                                                                                                                                                                              |  
| Authentication/SAML2/[provider]/SignInAsAuthenticationType  | 创建 ClaimsIdentity 时使用的 AuthenticationType。 [!include[](../../../includes/proc-more-information.md)] [wsfederationauthenticationoptions.wtrealm 相. SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)                                                                                                                                                                                                 |  
| Authentication/SAML2/[provider]/ValidAudiences              | 以逗号分隔的受众 Url 列表。 [!include[](../../../includes/proc-more-information.md)] [TokenValidationParameters. AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)                                                                                                                                                                                                                                                                          |  
| Authentication/SAML2/[provider]/ClockSkew                   | 验证时间时要应用的时钟偏差。                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/SAML2/[provider]/RequireExpirationTime       | 一个值，该值指示令牌是否必须具有到期值。                                                                                                                                                                                                                                                                                                                                                                      |
| Authentication/SAML2/[provider]/ValidateAudience            | 用于控制是否将在令牌验证过程中验证受众的布尔值。                                                                                                                                                                                                                                                                                                                                                         |

### <a name="idp-initiated-sign-in"></a>IdP-启动的登录

[!include[](../../../includes/pn-adfs-short.md)] 支持 SAML 2.0[规范](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline)的[IdP 启动的单一登录（SSO）](https://technet.microsoft.com/library/jj127245.aspx)配置文件。 为了使门户（服务提供程序）能够正确响应 IdP 启动的 SAML 请求，必须正确编码[RelayState](https://blogs.technet.com/b/askds/archive/2012/09/27/ad-fs-2-0-relaystate.aspx)参数。  

要编码到 SAML RelayState 参数中的基本字符串值必须采用格式**ReturnUrl =/content/sub-content/** ，其中 **/content/sub-content/** 是你要在门户中访问的网页的路径（服务提供商）。 该路径可以替换为门户上的任何有效网页。 编码字符串值，并将其置于格式为**RPID =&lt;url 编码 RPID&gt;& RelayState =&lt;url 编码 RelayState&gt;** 的容器字符串中。 这会再次将整个字符串编码并添加到 **<https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=&lt;URL> 编码 RPID/RelayState&gt;** 格式的另一个容器。

例如，如果提供服务提供程序路径 **/content/sub-content/** 和信赖方 ID **https://portal.contoso.com/** ，则会用以下步骤构造 URL：

对值进行编码 ReturnUrl =/content/sub-content/

-   获取 ReturnUrl% 3D% 2Fcontent% 2Fsub-content% 2F

<!-- -->

-   对值进行编码 https://portal.contoso.com/

<!-- -->

-   获取 https %3 %2 F %2 f 门户。 contoso. .com% 2F

<!-- -->

-   对值进行编码 RPID = https %3 A %2 F %2 F 门户。 contoso. .com% 2F & RelayState = ReturnUrl% 3D% 2Fcontent% 2Fsub-content% 2F

<!-- -->

-   若要获取 RPID %3 D https %2 5 3A %2 5 2F %2 5 2Fportal% 252F% 26RelayState% 3DReturnUrl% 253D% 252Fcontent% 252Fsub-content% 252F

<!-- -->

-   预置 AD FS IdP 启动的 SSO 路径以获取最终 URL

<!-- -->

-   https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

以下 [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] 脚本可用于构造 URL （保存到名为 Get-IdPInitiatedUrl 的文件）。

```
<#

.SYNOPSIS 

Constructs an IdP-initiated SSO URL to access a portal page on the service provider.

.PARAMETER path

The path to the portal page.

.PARAMETER rpid

The relying party identifier.

.PARAMETER adfsPath

The AD FS IdP initiated SSO page.

.EXAMPLE

PS C:\\> .\\Get-IdPInitiatedUrl.ps1 -path "/content/sub-content/" -rpid "https://portal.contoso.com/" -adfsPath "https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx"

#>

param

(

[parameter(mandatory=$true,position=0)]

$path,

[parameter(mandatory=$true,position=1)]

$rpid,

[parameter(position=2)]

$adfsPath = https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx

)

$state = ReturnUrl=$path

$encodedPath = [uri]::EscapeDataString($state)

$encodedRpid = [uri]::EscapeDataString($rpid)

$encodedPathRpid = [uri]::EscapeDataString("RPID=$encodedRpid&RelayState=$encodedPath")

$idpInitiatedUrl = {0}?RelayState={1} -f $adfsPath, $encodedPathRpid

Write-Output $idpInitiatedUrl
```

## <a name="saml-20-settings-for-includepn-azure-active-directoryincludespn-azure-active-directorymd"></a>[!INCLUDE[pn-azure-active-directory](../../../includes/pn-azure-active-directory.md)] 的 SAML 2.0 设置

前面描述 [!include[](../../../includes/pn-adfs-short.md)] 的部分也可以应用于[[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 广告](https://msdn.microsoft.com/library/azure/mt168838.aspx)，因为 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] ad 的行为类似于标准[SAML 2.0](https://msdn.microsoft.com/library/azure/dn195591.aspx)&ndash;兼容 IdP。 若要开始，请登录到[[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 管理门户](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal)并创建或选择现有目录。 当目录可用时，请按照说明向目录[添加应用程序](https://msdn.microsoft.com/library/azure/dn132599.aspx)。  

1.  在目录的 "**应用程序**" 菜单下，选择 "**添加**"。
2.  选择 **"添加我的组织正在开发的应用程序"** 。
3.  为应用程序指定自定义名称，然后选择 " **web 应用程序和/或 WEB API**" 类型。
4.  对于 "**登录 URL** " 和 "**应用 ID URI**"，为 https://portal.contoso.com/ 的两个字段指定门户的 URL。
    这对应于**ServiceProviderRealm** （Wtrealm）站点设置值。
5. 此时，将创建一个新的应用程序。 在菜单中，切换到 "**配置**" 部分。

    在 "**单一登录**" 部分下，更新 "第一个**回复 url** " 条目，以将路径包含在 URL https://portal.contoso.com/signin-azure-ad 中。

    这对应于**AssertionConsumerServiceUrl** （Wreply）站点设置值。

6. 在页脚菜单中，选择 "**查看终结点**"，并记下 "**联合元数据文档**" 字段。

这对应于**MetadataAddress**站点设置值。

-   在浏览器窗口中粘贴此 URL 以查看联合元数据 XML，并记下根元素的**entityID**属性。
-   这对应于**AuthenticationType**站点设置值。

> [!Note]
> 标准 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 配置仅使用以下设置（示例值）： Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/MetadataAddress-<https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml> 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AuthenticationType-<https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/>  
> - 使用联合元数据的根元素中的**entityID**属性的值（在浏览器中打开**MetadataAddress URL** ，该浏览器是上述站点设置的值） 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ServiceProviderRealm-<https://portal.contoso.com/>  
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AssertionConsumerServiceUrl-<https://portal.contoso.com/signin-azure-ad>                                                                                   |

## <a name="shibboleth-identity-provider-3"></a>Shibboleth 标识提供程序3

使用以下准则正确地将[Shibboleth 标识提供程序](https://wiki.shibboleth.net/confluence/display/IDP30/Home)配置为 IdP 服务。 下面的示例假定 IdP 托管在域 https://idp.contoso.com 上。  

联合元数据 URL 是 https://idp.contoso.com/idp/shibboleth

-   必须配置 IdP 以生成或提供永久性标识符。 按照说明启用[永久标识符生成](https://wiki.shibboleth.net/confluence/display/IDP30/NameIDGenerationConfiguration)。  

-   必须将 IdP 联合元数据（&lt;IDPSSODescriptor&gt;）配置为包含[SSO 重定向绑定](https://shibboleth.net/about/advanced.html)。 [示例](https://wiki.shibboleth.net/confluence/display/SHIB2/MetadataExample)。  

```
<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect"

Location=https://idp.contoso.com/idp/profile/SAML2/Redirect/SSO/>
```

通过设置[metadata-providers](https://wiki.shibboleth.net/confluence/display/IDP30/MetadataConfiguration)来配置服务提供程序（信赖方）。  

-   每个服务提供者联合元数据（&lt;SPSSODescriptor&gt;）都必须包含一个断言使用者服务 post 绑定。 一种选择是使用[FilesystemMetadataProvider](https://wiki.shibboleth.net/confluence/display/IDP30/FilesystemMetadataProvider)并引用包含以下内容的配置文件：  

```
<AssertionConsumerService index=1 isDefault=true

Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"

Location=https://portal.contoso.com/signin-saml2/>
```

Location 特性对应于**AssertionConsumerServiceUrl** （Wreply）设置。

-   服务提供程序联合元数据应为与**AuthenticationType**设置对应的 EntityDescriptor 指定**entityID**属性。

**&lt;EntityDescriptor entityID =<https://portal.local.contoso.com/&gt>; .。。**

> [!Note] 
> 标准 Shibboleth 配置仅使用以下设置（示例值）：   
> Authentication/SAML2/Shibboleth/MetadataAddress- https://idp.contoso.com/idp/shibboleth   
> -   Authentication/SAML2/Shibboleth/AuthenticationType- https://idp.contoso.com/idp/shibboleth 
> -   使用联合元数据的根元素中的**entityID**属性的值（在浏览器中打开**MetadataAddress URL** ，该浏览器是上述站点设置的值）  
> -   Authentication/SAML2/Shibboleth/ServiceProviderRealm- https://portal.contoso.com/ 
> -   Authentication/SAML2/Shibboleth/AssertionConsumerServiceUrl- https://portal.contoso.com/signin-saml2 

### <a name="idp-initiated-sign-in"></a>IdP-启动的登录

Shibboleth 支持 SAML 2.0[规范](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline)的[IDP 启动的 SSO](https://wiki.shibboleth.net/confluence/display/SHIB2/IdPUnsolicitedSSO)配置文件。 要使门户（服务提供程序）能够正确响应 IdP 启动的 SAML 请求，必须正确编码 RelayState 参数。  

要编码到 SAML RelayState 参数中的基本字符串值必须采用格式**ReturnUrl =/content/sub-content/** ，其中 **/content/sub-content/** 是你要在门户中访问的网页的路径（服务提供商）。 该路径可以替换为门户上的任何有效网页。 完整的 IdP 启动的 SSO URL 的格式应 <https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=&lt;URL> 编码的提供程序 ID&gt;& target =&lt;URL 编码的返回路径&gt;。

例如，如果服务提供商路径 **/content/sub-content/** 和信赖方 ID **https://portal.contoso.com/** ，最终 URL 将 https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=https%3A%2F%2Fportal.contoso.com%2F&target=ReturnUrl%3D%2Fcontent%2Fsub-content%2F

以下 [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] 脚本可用于构造 URL （保存到名为 Get-ShibbolethIdPInitiatedUrl 的文件）。

```
<# 

.SYNOPSIS

Constructs an IdP initiated SSO URL to access a portal page on the service provider.

.PARAMETER path

The path to the portal page.

.PARAMETER providerId

The relying party identifier.

.PARAMETER shibbolethPath

The Shibboleth IdP-initiated SSO page.

.EXAMPLE

PS C:\\> .\\Get-ShibbolethIdPInitiatedUrl.ps1 -path "/content/sub-content/" -providerId "https://portal.contoso.com/" -shibbolethPath "https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO"

#>

param

(

[parameter(mandatory=$true,position=0)]

$path,

[parameter(mandatory=$true,position=1)]

$providerId,

[parameter(position=2)]

$shibbolethPath = https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO

)

$state = ReturnUrl=$path

$encodedPath = [uri]::EscapeDataString($state)

$encodedRpid = [uri]::EscapeDataString($providerId)

$idpInitiatedUrl = {0}?providerId={1}&target={2} -f $shibbolethPath, $encodedRpid, $encodedPath

Write-Output $idpInitiatedUrl
```

## <a name="configure-ad-fs-by-using-powershell"></a>使用 PowerShell 配置 AD FS

还可以通过在 [!include[](../../../includes/pn-adfs-short.md)] 服务器上运行以下 [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] 脚本（将内容保存到名为 Add-AdxPortalRelyingPartyTrustForSaml 的文件）来执行在 [!include[](../../../includes/pn-adfs-short.md)] 中添加信赖方信任的过程。 运行该脚本后，请继续配置门户网站设置。

```
<# 

.SYNOPSIS

Adds a SAML 2.0 relying party trust entry for a website.

.PARAMETER domain

The domain name of the portal.

.EXAMPLE

PS C:\\> .\\Add-AdxPortalRelyingPartyTrustForSaml.ps1 -domain portal.contoso.com

#>

param

(

[parameter(Mandatory=$true,Position=0)]

$domain,

[parameter(Position=1)]

$callbackPath = /signin-saml2

)

$VerbosePreference = Continue

$ErrorActionPreference = Stop

Import-Module adfs

Function Add-CrmRelyingPartyTrust

{

param (

[parameter(Mandatory=$true,Position=0)]

$name

)

$identifier = https://{0}/ -f $name

$samlEndpoint = New-ADFSSamlEndpoint -Binding POST -Protocol SAMLAssertionConsumer -Uri (https://{0}{1} -f $name, $callbackPath)

$identityProviderValue = Get-ADFSProperties | % { $_.Identifier.AbsoluteUri }

$issuanceTransformRules = @'

@RuleTemplate = MapClaims

@RuleName = Transform [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] Account Name to Name ID claim

c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname"]

=> issue(Type = "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier", Issuer = c.Issuer, OriginalIssuer = c.OriginalIssuer, Value = c.Value, ValueType = c.ValueType, Properties["https://schemas.xmlsoap.org/ws/2005/05/identity/claimproperties/format"] = "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent");

@RuleTemplate = LdapClaims

@RuleName = Send LDAP Claims

c:[Type == "https://schemas.microsoft.com/ws/2008/06/identity/claims/windowsaccountname", Issuer == "AD AUTHORITY"]

=> issue(store = "[!INCLUDE[pn-active-directory](../../../includes/pn-active-directory.md)]", types = ("https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname", "https://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress"), query = ";givenName,sn,mail;{{0}}", param = c.Value);

'@ -f $identityProviderValue

$issuanceAuthorizationRules = @'

@RuleTemplate = AllowAllAuthzRule

=> issue(Type = https://schemas.microsoft.com/authorization/claims/permit, Value = true);

'@

Add-ADFSRelyingPartyTrust -Name $name -Identifier $identifier -SamlEndpoint $samlEndpoint -IssuanceTransformRules $issuanceTransformRules -IssuanceAuthorizationRules $issuanceAuthorizationRules

}

# add the 'Identity Provider' claim description if it is missing

if (-not (Get-ADFSClaimDescription | ? { $_.Name -eq Persistent Identifier })) {

Add-ADFSClaimDescription -name "Persistent Identifier" -ClaimType "urn:oasis:names:tc:SAML:2.0:nameid-format:persistent" -IsOffered:$true -IsAccepted:$true

}

# add the portal relying party trust

Add-CrmRelyingPartyTrust $domain
```

### <a name="see-also"></a>另请参阅

[配置门户身份验证](configure-portal-authentication.md)  
[设置门户的身份验证标识](set-authentication-identity.md)  
[门户的 OAuth2 提供程序设置](configure-oauth2-settings.md)  
[为门户打开 ID 连接提供程序设置](configure-openid-settings.md)  
[门户的 WS 联合身份验证提供程序设置](configure-ws-federation-settings.md)  
