---
title: 配置门户的 SAML 2.0 提供程序设置 | MicrosoftDocs
description: 有关如何添加和配置门户的 SAML 2.0 提供程序设置的说明。
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
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2759632"
---
# <a name="configure-saml-20-provider-settings-for-portals"></a>配置门户的 SAML 2.0 提供程序设置

要提供外部身份验证，可添加一个或多个符合 [SAML 2.0](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html) 的身份提供程序 (IdP)。 本文说明了如何设置各种身份提供程序以便与充当服务提供程序的门户集成。  

## <a name="ad-fs-idp"></a>AD FS (IdP)

身份提供程序（如 [!include[](../../../includes/pn-active-dir-fed-svcs-ad-fs.md)]）的设置。

### <a name="create-an-ad-fs-relying-party-trust"></a>创建 AD FS 信赖方信任

> [!Note]
> 有关如何通过 [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] 脚本执行这些步骤的信息，请参阅下面的[使用 PowerShell 配置 AD FS](#configure-ad-fs-by-using-powershell)。

使用 [!include[](../../../includes/pn-adfs-short.md)] 管理工具，转至**服务** > **声明说明**。

1.  选择**添加声明说明**。
2.  指定声明：

    -  显示名称：**持久标识符**

    -  声明标识符：**urn:oasis:names:tc:SAML:2.0:nameid-format:persistent**

    -  **启用**复选框以：以此联合服务能接受的声明类型在联合元数据中发布此声明说明

    -  **启用**复选框以：以此联合服务能发送的声明类型在联合元数据中发布此声明说明

3.  选择**确定**。

使用 [!include[](../../../includes/pn-adfs-short.md)] 管理工具，选择**信任关系** >**信赖方信任**。

1. 选择**添加信赖方信任**。
2. 欢迎：选择**开始**。
3. 选择数据源：选择**手动输入有关信赖方的数据**，然后选择**下一步**。
4. 指定显示名称：输入名称，然后选择**下一步**。
   示例: https://portal.contoso.com/
5. 选择配置文件：选择 **AD FS 2.0 配置文件**，然后选择**下一步**。
6. 配置证书：选择**下一步**。
7. 配置 URL：选中**启用 SAML 2.0 WebSSO 协议的支持**复选框。
   信赖方 SAML 2.0 SSO 服务 URL：输入 https://portal.contoso.com/signin-saml2
   - 注意：[!include[](../../../includes/pn-adfs-short.md)] 要求门户在 HTTPS 上运行。

   > [!Note] 
   > 出现的终结点具有以下设置： 
   > - 终结点类型：**SAML 声明使用终结点**             
   > - 绑定：**POST**                                            
   > - 索引：n/a (0)                                              
   > - URL：**https://portal.contoso.com/signin-saml2**

8. 配置标识：指定 https://portal.contoso.com/，选择**添加**，然后选择**下一步**。
   如果适用，可以为每个其他信赖方门户添加更多身份。 用户可以跨任何或所有可用身份进行身份验证。
9. 选择颁发授权规则：选择**允许所有用户访问此信赖方**，然后选择**下一步**。
10. 准备添加信任：选择**下一步**。
11. 选择**关闭**。

添加**名称 ID** 声明到信赖方信任：

**将 [!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] 帐户名**转换为**名称 ID** 声明（转换传入声明）：

- 传入声明类型：**[!INCLUDE[pn-ms-windows-short](../../../includes/pn-ms-windows-short.md)] 帐户名**

- 传出声明类型：**名称 ID**

- 传出名称 ID 格式：**持久标识符**

- 传递所有声明值

### <a name="create-site-settings"></a>创建网站设置

应用引用上面的 [!include[](../../../includes/pn-adfs-short.md)] 信赖方信任的门户网站设置。

> [!Note]
> 标准 [!include[](../../../includes/pn-adfs-short.md)] (IdP) 配置只使用以下设置（使用示例值）：Authentication/SAML2/ADFS/MetadataAddress - <https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml>  
> - Authentication/SAML2/ADFS/AuthenticationType - https://adfs.contoso.com/adfs/services/trust    
>   -   使用联合元数据的根元素中的 **entityID** 属性值（在是上方网站设置的浏览器中打开 **MetadataAddress URL**） 
> - Authentication/SAML2/ADFS/ServiceProviderRealm - https://portal.contoso.com/  
> - Authentication/SAML2/ADFS/AssertionConsumerServiceUrl - https://portal.contoso.com/signin-saml2  
>   **联合元数据**可以通过在 [!include[](../../../includes/pn-adfs-short.md)] 服务器上运行以下脚本在 **[!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)]** 中进行检索：`Import-Module adfs`
>   `Get-ADFSEndpoint -AddressPath /FederationMetadata/2007-06/FederationMetadata.xml`

可以通过用标签代替 [provider] 标记来配置多个 IdP 服务。 每个唯一标签窗体设定与 IdP 相关的一组设置。 示例：ADFS、[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD、MyIdP


| 网站设置名称                                             | 说明                                                                                                                                                                                                                                                                                                                                                                                                                             |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ExternalLoginEnabled              | 启用或禁用外部帐户登录和注册。 默认：true                                                                                                                                                                                                                                                                                                                                                            |
| Authentication/SAML2/[provider]/MetadataAddress             | 必需。 [!include[](../../../includes/pn-adfs-short.md)] (STS) 服务器的 [WS 联合身份验证](https://msdn.microsoft.com/library/bb498017.aspx)元数据 URL。 通常以此路径结尾：/FederationMetadata/2007-06/FederationMetadata.xml。 示例：`https://adfs.contoso.com/FederationMetadata/2007-06/FederationMetadata.xml`。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.MetadataAddress](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.metadataaddress.aspx) |  
| Authentication/SAML2/[provider]/AuthenticationType          | 必需。 OWIN 身份验证中间件类型。 在联合元数据 XML 的根指定 [entityID](https://docs.microsoft.com/azure/active-directory/develop/active-directory-federation-metadata) 属性的值。 示例：`https://adfs.contoso.com/adfs/services/trust`。 [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions.AuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationtype.aspx)                                                            |  
| Authentication/SAML2/[provider]/ServiceProviderRealm<br>或 <br>Authentication/SAML2/[provider]/Wtrealm                      | 必需。 [!include[](../../../includes/pn-adfs-short.md)] 信赖方标识符。 示例：`https://portal.contoso.com/`。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Wtrealm](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wtrealm.aspx)                       |  
| Authentication/SAML2/[provider]/AssertionConsumerServiceUrl<br>或<br>Authentication/SAML2/[provider]/Wreply                       | 必需。 [!include[](../../../includes/pn-adfs-short.md)] SAML 使用者声明终结点。 示例：https://portal.contoso.com/signin-saml2。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Wreply](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.wreply.aspx)                                                                                                                                                                                                  |  
| Authentication/SAML2/[provider]/Caption                     | 推荐。 用户可以在登录用户界面中显示的文本。 默认值：[provider]。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.Caption](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.caption.aspx)                |  
| Authentication/SAML2/[provider]/CallbackPath                | 在其中处理身份验证回调的可选约束路径。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.CallbackPath](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.callbackpath.aspx)                                                                                                                                                                                                                      |  
| Authentication/SAML2/[provider]/BackchannelTimeout          | 反向信道通信的超时值。 示例：00:05:00（5 分钟）。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.BackchannelTimeout](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.backchanneltimeout.aspx)                                                                                                                                                                                                                   |  
| Authentication/SAML2/[provider]/UseTokenLifetime            | 指示身份验证会话生存期（例如，Cookie）应与身份验证令牌匹配。 [WsFederationAuthenticationOptions.UseTokenLifetime](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.usetokenlifetime.aspx)。                                                                                                                                                                               |  
| Authentication/SAML2/[provider]/AuthenticationMode          | OWIN 身份验证中间件模式。 [!include[](../../../includes/proc-more-information.md)] [AuthenticationOptions.AuthenticationMode](https://msdn.microsoft.com/library/microsoft.owin.security.authenticationoptions.authenticationmode.aspx)                                                                                                                                                                                                                                                                              |  
| Authentication/SAML2/[provider]/SignInAsAuthenticationType  | 在创建 System.Security.Claims.ClaimsIdentity 时使用的 AuthenticationType。 [!include[](../../../includes/proc-more-information.md)] [WsFederationAuthenticationOptions.SignInAsAuthenticationType](https://msdn.microsoft.com/library/microsoft.owin.security.wsfederation.wsfederationauthenticationoptions.signinasauthenticationtype.aspx)                                                                                                                                                                                                 |  
| Authentication/SAML2/[provider]/ValidAudiences              | 逗号分隔访问群体 URL 的列表。 [!include[](../../../includes/proc-more-information.md)] [TokenValidationParameters.AllowedAudiences](https://msdn.microsoft.com/library/system.identitymodel.tokens.tokenvalidationparameters.allowedaudiences.aspx)                                                                                                                                                                                                                                                                          |  
| Authentication/SAML2/[provider]/ClockSkew                   | 验证时间时要应用的时钟偏移。                                                                                                                                                                                                                                                                                                                                                                                          |
| Authentication/SAML2/[provider]/RequireExpirationTime       | 指示令牌是否必须具有到期值的值。                                                                                                                                                                                                                                                                                                                                                                      |
| Authentication/SAML2/[provider]/ValidateAudience            | 控制是否在验证令牌时验证访问群体的布尔值。                                                                                                                                                                                                                                                                                                                                                         |

### <a name="idp-initiated-sign-in"></a>IdP 启动登录

[!include[](../../../includes/pn-adfs-short.md)] 支持 SAML 2.0 [规范](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline)的 [IdP 启动单一登录 (SSO) 配置文件](https://technet.microsoft.com/library/jj127245.aspx)。 为使门户（服务提供商）正确响应 IdP 启动的 SAML 请求，必须将 [RelayState](https://blogs.technet.com/b/askds/archive/2012/09/27/ad-fs-2-0-relaystate.aspx) 参数正确编码。  

将编码到 SAML RelayState 参数的基本字符串值必须采用格式：**ReturnUrl=/content/sub-content/**，其中 **/content/sub-content/** 是在门户（服务提供商）中要访问的网页的路径。 路径可以由门户中的任何有效网页替换。 字符串值编码并放在到格式的容器字符串中：**RPID=&lt;URL 编码的 RPID&gt;&RelayState=&lt;URL 编码的 RelayState&gt;**。 整个字符串将又一次编码并添加到其他格式的容器 **<https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=&lt;URL> 编码的 RPID/RelayState&gt;**。

例如，指定服务提供商路径 **/content/sub-content/** 和信赖方 ID **https://portal.contoso.com/**，使用以下步骤构建 URL：

为 ReturnUrl=/content/sub-content/ 编码

-   以获取 ReturnUrl%3D%2Fcontent%2Fsub-content%2F

<!-- -->

-   编码值 https://portal.contoso.com/ 

<!-- -->

-   以获取 https%3A%2F%2Fportal.contoso.com%2F

<!-- -->

-   为值 RPID=https%3A%2F%2Fportal.contoso.com%2F&RelayState=ReturnUrl%3D%2Fcontent%2Fsub-content%2F 编码

<!-- -->

-   以获取 RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

<!-- -->

-   预置 AD FS IdP 启动 SSO 路径以获取最终 URL

<!-- -->

-   https://adfs.contoso.com/adfs/ls/idpinitiatedsignon.aspx?RelayState=RPID%3Dhttps%253A%252F%252Fportal.contoso.com%252F%26RelayState%3DReturnUrl%253D%252Fcontent%252Fsub-content%252F

以下 [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] 脚本可用于构造 URL（保存到名为 Get-IdPInitiatedUrl.ps1 的文件）。

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

介绍 [!include[](../../../includes/pn-adfs-short.md)] 的上一章节也可以适用于 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD](https://msdn.microsoft.com/library/azure/mt168838.aspx)，因为 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 行为与标准 [SAML 2.0](https://msdn.microsoft.com/library/azure/dn195591.aspx)&ndash; 兼容 IdP 相似。 首先登录到 [[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] 管理门户](https://msdn.microsoft.com/library/azure/hh967611.aspx#bkmk_azureportal)并创建或选择现有目录。 提供目录时，按照说明[将应用程序添加](https://msdn.microsoft.com/library/azure/dn132599.aspx)到目录。  

1.  在目录的**应用程序**菜单下，选择**添加**。
2.  选择**添加我的组织正在开发的应用程序**。
3.  为应用程序指定自定义名称，然后选择类型 **Web 应用程序和/或 Web API**。
4.  对于**登录 URL** 和**应用程序 ID URI**，指定两个字段的门户的 URLhttps://portal.contoso.com/。
    这对应于 **ServiceProviderRealm** (Wtrealm) 网站设置值。
5. 此时，新应用程序创建。 在菜单中转至**配置**部分。

    在**单一登录**部分下，更新第一个**响应 URL** 条目以在 URL 中包含路径：https://portal.contoso.com/signin-azure-ad。

    这对应于 **AssertionConsumerServiceUrl** (Wreply) 网站设置值。

6. 在脚注菜单上，选择**查看终结点**并注意**联合元数据文档**字段。

这对应于 **MetadataAddress** 网站设置值。

-   在浏览器窗口中粘贴此 URL 以查看联合元数据 XML 并注释根元素的 **entityID** 属性。
-   这对应于 **AuthenticationType** 网站设置值。

> [!Note]
> 标准 [!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)] AD 配置只使用以下设置（使用示例值）：Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/MetadataAddress - <https://login.microsoftonline.com/01234567-89ab-cdef-0123-456789abcdef/federationmetadata/2007-06/federationmetadata.xml> 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AuthenticationType - <https://sts.windows.net/01234567-89ab-cdef-0123-456789abcdef/>  
> - 使用联合元数据的根元素中的 **entityID** 属性值（在是上方网站设置的浏览器中打开 **MetadataAddress URL**） 
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/ServiceProviderRealm - <https://portal.contoso.com/>  
> - Authentication/SAML2/[!INCLUDE[pn-azure-shortest](../../../includes/pn-azure-shortest.md)]AD/AssertionConsumerServiceUrl - <https://portal.contoso.com/signin-azure-ad>                                                                                   |

## <a name="shibboleth-identity-provider-3"></a>Shibboleth 身份提供程序 3

使用以下指南作为 IdP 服务正确配置 [Shibboleth 身份提供程序](https://wiki.shibboleth.net/confluence/display/IDP30/Home)。 以下假设 IdP 在域中托管：https://idp.contoso.com。  

联合元数据 URL 是 https://idp.contoso.com/idp/shibboleth

-   IdP 必须配置为生成/提供持久标识符。 根据说明启用[持久标识符生成](https://wiki.shibboleth.net/confluence/display/IDP30/NameIDGenerationConfiguration)。  

-   IdP 联合元数据 (&lt;IDPSSODescriptor&gt;) 必须配置为包括 [SSO 重定向绑定](https://shibboleth.net/about/advanced.html)。 [示例:](https://wiki.shibboleth.net/confluence/display/SHIB2/MetadataExample)。  

```
<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect"

Location=https://idp.contoso.com/idp/profile/SAML2/Redirect/SSO/>
```

通过设置 [metadata-providers.xml](https://wiki.shibboleth.net/confluence/display/IDP30/MetadataConfiguration) 配置服务提供程序（信赖方）。  

-   每个服务提供商联合元数据 (&lt;SPSSODescriptor&gt;) 必须包含声明使用者服务邮件绑定。 一个选项是使用 [FilesystemMetadataProvider](https://wiki.shibboleth.net/confluence/display/IDP30/FilesystemMetadataProvider) 并引用包含以下项的配置文件：  

```
<AssertionConsumerService index=1 isDefault=true

Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"

Location=https://portal.contoso.com/signin-saml2/>
```

位置属性对应于 **AssertionConsumerServiceUrl** (Wreply) 设置值。

-   服务提供商联合元数据应为对应 **AuthenticationType** 设置的 EntityDescriptor 指定 **entityID** 属性。

**&lt;EntityDescriptor entityID=<https://portal.local.contoso.com/&gt>;...**

> [!Note] 
> 标准 Shibbolet 配置仅使用以下设置（包含示例值）：   
> Authentication/SAML2/Shibboleth/MetadataAddress - https://idp.contoso.com/idp/shibboleth   
> -   Authentication/SAML2/Shibboleth/AuthenticationType - https://idp.contoso.com/idp/shibboleth 
> -   使用联合元数据的根元素中的 **entityID** 属性值（在是上方网站设置的浏览器中打开 **MetadataAddress URL**）  
> -   Authentication/SAML2/Shibboleth/ServiceProviderRealm - https://portal.contoso.com/ 
> -   Authentication/SAML2/Shibboleth/AssertionConsumerServiceUrl - https://portal.contoso.com/signin-saml2 

### <a name="idp-initiated-sign-in"></a>IdP 启动登录

Shibboleth 支持 SAML 2.0 [规范](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0-cd-02.html#5.1.4.IdP-Initiated%20SSO:%20POST%20Binding|outline)的 [IdP 启动 SSO](https://wiki.shibboleth.net/confluence/display/SHIB2/IdPUnsolicitedSSO) 配置文件。 为使门户（服务提供商）正确响应 IdP 启动的 SAML 请求，必须将 RelayState 参数正确编码。  

将编码到 SAML RelayState 参数的基本字符串值必须采用格式：**ReturnUrl=/content/sub-content/**，其中 **/content/sub-content/** 是在门户（服务提供商）中要访问的网页的路径。 路径可以由门户中的任何有效网页替换。 完整的 IdP 启动的 SSO URL 格式应为：<https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=&lt;URL> 编码的提供程序 ID&gt;&target=&lt;URL 编码的返回路径&gt;。

例如，指定服务提供程序路径 **/content/sub-content/** 和信赖方 ID **https://portal.contoso.com/**，最终 URL 是 https://idp.contoso.com/idp/profile/SAML2/Unsolicited/SSO?providerId=https%3A%2F%2Fportal.contoso.com%2F&target=ReturnUrl%3D%2Fcontent%2Fsub-content%2F

以下 [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] 脚本可用于构造 URL（保存到名为 Get-ShibbolethIdPInitiatedUrl.ps1 的文件）。

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

[!include[](../../../includes/pn-adfs-short.md)] 中的添加信赖方信任流程也可以通过在 [!include[](../../../includes/pn-adfs-short.md)] 服务器中运行以下 [!INCLUDE[pn-powershell-short](../../../includes/pn-powershell-short.md)] 脚本来执行（将内容保存到名为 Add-AdxPortalRelyingPartyTrustForSaml.ps1 的文件）。 在运行脚本后，继续配置门户网站设置。

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
[门户的 Open ID Connect 提供程序设置](configure-openid-settings.md)  
[门户的 WS 联合身份验证提供程序设置](configure-ws-federation-settings.md)  
