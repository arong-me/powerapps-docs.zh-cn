---
title: 门户的 Azure AD B2C 提供程序设置 | MicrosoftDocs
description: 为门户启用 Azure AD B2C 提供程序设置的说明。
author: sbmjais
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/03/2020
ms.author: shjais
ms.reviewer: tapanm
ms.openlocfilehash: e8275fa256b00736501990c3abf127777097d938
ms.sourcegitcommit: 82eec5da9c97fcb6ed50ae8e582f326af9278aa7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "2935192"
---
# <a name="azure-ad-b2c-provider-settings-for-portals"></a>门户的 Azure AD B2C 提供程序设置

[!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory (Azure AD) 为员工提供 Office 365 和 Dynamics 365 服务或内部身份验证。 [!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory B2C 是通过本地凭据和不同常见社交身份提供程序的联合启用外部客户登录的身份验证模式的扩展。

门户负责人可以配置门户以接受 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 为身份提供程序。 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 支持用于联合的 Open ID Connect。

在配置 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 为您的门户的身份提供程序的过程中，生成您稍后在配置门户时将使用的多个值。 您可以记下下表中的这些值。 在配置门户时，请使用您在此处记下的值替换该变量名称。

| 变量名称     | 值 | 说明                                                           |
|-------------------|-------|-----------------------------------------------------------------------|
| 应用程序名称  |       | 作为信赖方表示门户的应用程序的名称 |
| 应用程序 ID    |       | 在 Azure Active Directory B2C 中创建的与应用程序有关的应用程序商店 ID。  |
| Policy-Signin-URL |       | 在元数据端点中定义的颁发者 (iss) URL。                |
| Federation-Name   |       | 用于标识联合提供程序类型的唯一名称，例如“B2C”。 这将用于在站点设置名称中对此特定提供程序的配置设置分组。                                                                      |
| | | |

### <a name="use-azure-ad-b2c-as-an-identity-provider-for-your-portal"></a>使用 Azure AD B2C 作为您的门户的身份提供程序

1. 登录到您的 [Azure 门户](https://portal.azure.com/)。
2. [创建 Azure AD B2C 租户](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-get-started)。
3. 选择最左侧导航栏上的 **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C**。
4. [创建 Azure 应用程序](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-app-registration#register-a-web-application)。

   > [!Note]
   > 您必须为**允许隐式流程**字段选择**是**，并在**回复 URL** 字段中指定您的门户 URL。 **回复 URL** 字段中的值应使用 [门户域]/登录-[联合-名称] 格式。 例如，`https://contosocommunity.microsoftcrmportals.com/signin-B2C`。

5. 复制应用程序名称，然后输入为上表中的应用程序-名称的值。
6. 复制应用程序 ID，然后输入为上表中的应用程序-ID 的值。
7. [创建注册或登录策略](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-reference-policies#create-a-sign-up-or-sign-in-policy)。
8. 选择策略，然后选择 **编辑**。
9. 选择**令牌、会话和 SSO 配置**。
10. 从**颁发者 (iss) 声明**列表中，选择路径中有 **/tfp** 的 URL。
11. 保存策略。
12. 选择**此策略的元数据端点**字段中的 URL。
13. 复制颁发者字段的值并作为上表中的策略-登录-URL 的值输入。 

## <a name="portal-configuration"></a>门户配置

在 [!include[Azure](../../../includes/pn-azure-shortest.md)] 中创建和配置 B2C 租户后，您必须配置您的门户以使用 Open ID Connect 协议与 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 联合。 您必须为联合到 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 创建一个唯一名称&mdash;例如 B2C&mdash;然后将其存储为上表中的*联合名称*变量的值。

### <a name="configure-your-portal"></a>配置您的门户
1. 打开“门户管理”应用。
2. 转到**门户** > **网站**。
3. 选择需要对其启用 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 的网站记录。
4. 转到**站点设置**。
5. 创建以下站点设置：
   -   **名称**：身份验证/OpenIdConnect/[联合-名称]/机构

       **值**：[策略-登录-URL]
   -   **名称**：身份验证/OpenIdConnect/[联合-名称]/ClientId

       **值**：[应用程序-ID]
   -   **名称**：身份验证/OpenIdConnect/[联合-名称]/RedirectUri

       **值**：[门户域]/登录-[联合-名称]

       例如，`https://mysite.com/signin-b2c` 
6. 若要支持联合注销，请创建以下站点设置：
   - **名称**：身份验证/OpenIdConnect/[联合-名称]/ExternalLogoutEnabled

     **值**：true
7. 若要将您的门户硬编码到一个身份提供程序，请创建以下站点设置：
   - **名称**：Authentication/Registration/LoginButtonAuthenticationType

     **值**：[策略-登录-URL]

8. 若要支持密码重置，请创建[此处](#password-reset) 描述的所需站点设置。
9. 若要支持声明映射，请创建[此处](#claims-mapping) 描述的所需站点设置。

有关相关站点设置的完整列表，请参阅[此处](#related-site-settings)。

### <a name="password-reset"></a>重置密码

如果您要支持使用 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 本地帐户进行密码重置，需要以下站点设置：

| 站点设置                                                        | 说明                                                                                                          |
|---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| 身份验证/OpenIdConnect/[联合-名称]/PasswordResetPolicyId | 密码重置策略的 ID。                                                                                     |
| 身份验证/OpenIdConnect/[联合-名称]/ValidIssuers         | 包括 [策略-登录-URL] 的颁发者和密码重置策略的颁发者的逗号分隔的列表。 |
|身份验证/OpenIdConnect/[联合-名称]/DefaultPolicyId | 登录或注册 ID 策略。|
|||

### <a name="related-site-settings"></a>相关站点设置

您可以在门户中创建或配置以下站点设置以支持 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 作为身份提供程序：


| 站点设置                                                         | 说明                                                                                                                                                                                                                                                        |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ProfileRedirectEnabled                   | 指定门户是否可以在用户成功登录后将用户重定向到个人资料页面。 默认情况下，它设置为 true。                                                                                                                                            |
| Authentication/Registration/EmailConfirmationEnabled                 | 指定是否需要进行电子邮件验证。 默认情况下，它设置为 true。                                                                                     |
| Authentication/Registration/LocalLoginEnabled                        | 指定是否需要本地登录。 默认情况下，它设置为 true。                                                                        |
| Authentication/Registration/ExternalLoginEnabled                     | 启用或禁用外部身份验证。       |
| Authentication/Registration/AzureADLoginEnabled                      | 启用或禁用 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD 作为外部身份提供程序。 默认情况下，它设置为 true。                                                                                                                                                                      |
| 身份验证/OpenIdConnect/[联合-名称]/ExternalLogoutEnabled | 启用或禁用联合注销。当设置为 true 时，用户从门户注销后被重定向到联合注销用户体验。 当设置为 false 是，用户仅从门户注销。 默认情况下，它设置为 false。               |
| 身份验证/LoginTrackingEnabled                                  | 启用或禁用跟踪用户的上一次登录。 如果设置为 true，则在联系人记录的**上次成功登录**字段中显示日期和时间。 默认情况下，该值设置为 false。                                                            |
| 身份验证/OpenIdConnect/[联合-名称]/RegistrationEnabled   | 启用或禁用现有身份提供程序的注册需要。 当设置为 true 时，仅当站点设置身份验证/注册/启用也设置为 true 时才对现有提供程序启用注册。 默认情况下，它设置为 true。 |
|身份验证/OpenIdConnect/[联合-名称]/PostLogoutRedirectUri |指定在用户注销后要重定向到的门户中的 URL。 |
| | |

### <a name="related-content-snippet"></a>相关内容片段

如果在用户兑现邀请后对用户禁用注册，则使用以下内容片段显示消息：

**名称**：帐户/注册/RegistrationDisabledMessage

**值**：注册已被禁用。

## <a name="customize-the-includeazureincludespn-azure-shortestmd-ad-b2c-user-interface"></a>自定义 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 用户界面

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 支持用户界面自定义。 您可以自定义注册和登录方案的用户体验。

### <a name="step-1-create-a-web-template"></a>步骤 1：创建 Web 模板
使用以下值创建 Web 模板：

**名称**：[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 自定义页

**源**：使用以下示例 Web 模板源 HTML。

```html
<!DOCTYPE html>
<html lang=en-US>
  <head>
    <meta charset=utf-8>
    <meta name=viewport content=width=device-width, initial-scale=1.0>
    <meta http-equiv=X-UA-Compatible content=IE=edge>
    <title>
      {{ page.title | h }}
    </title>
                        <link href={{ request.url | base }}/bootstrap.min.css rel=stylesheet>
                        <link href={{ request.url | base }}/theme.css rel=stylesheet>
                        <style>
                          .page-heading {
            padding-top: 20px;
      }
      .page-copy {
            margin-bottom: 40px;
      }
      .highlightError {
        border: 1px solid #cb2027!important;
        background-color: #fce8e8!important;
      }
      .attrEntry .error.itemLevel {
        display: none;
        color: #cb2027;
        font-size: .9em;
      }
      .error {
        color: #cb2027;
      }
      .entry {
        padding-top: 8px;
        padding-bottom: 0!important;
      }
      .entry-item {
        margin-bottom: 20px;
      }
      .intro {
        display: inline;
        margin-bottom: 5px;
      }
      .pageLevel {
          width: 293px;
          text-align: center;
          margin-top: 5px;
          padding: 5px;
          font-size: 1.1em;
          height: auto;
      }
      #panel, .pageLevel, .panel li, label {
          display: block;
      }
      #forgotPassword {
          font-size: .75em;
          padding-left: 5px;
      }
      #createAccount {
          margin-left: 5px;
      }
      .working {
          display: none;
          background: url(data:image/gif;base64,R0lGODlhbgAKAPMAALy6vNze3PTy9MTCxOTm5Pz6/Ly+vNTS1Pz+/�N0Jp6BUJ9EBIISAQAh+QQJCQAKACxRAAIABgAGAAAEE1ClYU4RIIMTdCaegVCfRASCEgEAOw==) no-repeat;
          height: 10px;
          width: auto;
      }
      .divider {
        margin-top: 20px;
        margin-bottom: 10px;
      }
      .divider h2 {
        display: table;
        white-space: nowrap;
        font-size: 1em;
        font-weight: 700;
      }
      .buttons {
        margin-top: 10px;
      }
      button {
            width:auto;
            min-width:50px;
            height:32px;
            margin-top:2px;
            -moz-border-radius:0;
            -webkit-border-radius:0;
            border-radius:0;
            background:#2672E6;
            border:1px solid #FFF;
            color:#fff;
            transition:background 1s ease 0s;
            font-size:100%;
            padding:0 2px
      }

      button:hover {
            background:#0F3E83;
            border:1px solid #3079ed;
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0
      }
      .password-label label {
        display: inline-block;
        vertical-align: baseline;
      }
      img {
            border:0
      }
      .divider {
            margin-top:20px;
            margin-bottom:10px
      }
      .divider h2 {
            display:table;
            white-space:nowrap;
            font-size:1em;
            font-weight:700
      }
      .divider h2:after,.divider h2:before {
            border-top:1px solid #B8B8B8;
            content:'';
            display:table-cell;
            position:relative;
            top:.7em;
            width:50%
      }
      .divider h2:before {
            right:1.8%
      }
      .divider h2:after {
            left:1.8%
      }
      .verificationErrorText {
            color:#D63301
      }
      .options div {
            display:inline-block;
            vertical-align:top;
            margin-top:7px
      }
      .accountButton,.accountButton:hover {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAh1BMVEX///9QUFBOTk5LS0tERERCQkI/Pz9ISEg6OjpGRkZNTU08PDyAgID09PSlpaWWlpZxcXFgYGBZWVlUVFT6+vrx8fHt7e3s7Ozo6Oji4uLJycnGxsa4uLiqqqqgoKCNjY2JiYmGhoZra2tmZmb7+/vu7u7d3d3U1NTNzc2+vr67u7usrKx7e3vprNQnAAAA8klEQVQ4y63Q127DMAxAUZpDwyMeSdqsNqu7/f/va6zahgGJKAr0vgk6DyQh+6V/BiTOOeNRA9zuAWBdM6WBlPDTvaUUoAuMrT0mgNvA1IJjQB3MKjACvp6DK0WAH+agtH8H9jQHLUUgz7Uhx8xOXzNESxirLCYA2mw8tacI5FyIYXq8A9ge2Qs6oTnw2e2ruho2rjBcXJ4ADh3jBOQLQnVhRFx2gNDZ4ACogbHXj/ft9Dj5AcgbJFu5AThQWuYBIGmgtAFQo4EFB+CPGthJAPypgY3BHsheA5UNwLyAvsYNoDyroKUe4EoFTQ/yDtTONvsGUJ8KTUYyH+UAAAAASUVORK5CYII=);
            background-repeat:no-repeat
      }
      .accountButton {
            border:1px solid #FFF;
            color:#FFF;
            margin-left:0;
            margin-right:2px;
            transition:background-color 1s ease 0s;
            -moz-border-radius:0;
            -webkit-border-radius:0;
            border-radius:0;
            text-align:center;
            word-wrap:break-word;
            height:34px;
            width:158px;
            padding-left:30px;
            background-color:#505050;
      }
      .accountButton:hover {
            background-color:#B9B9B9;
            border:1px solid #FFF;
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0
      }
      .accountButton:focus {
            outline:gold solid 1px
      }
      #MicrosoftAccountExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAPFBMVEU1pe/////t+v4uoe5btvNixPVVwfUsoe9tyfXU7/y95vu24vrd9f5NtfLH6/ys3/o/sPE6qfD2/f+f2vnAysuQAAAAaElEQVQ4y93SORKAIAwFUEGCsoT1/nd1JkkDFhY24qt+8VMkk20lu6DAaVBOBsVKsuO8aYo08IqlYyxoRTQExfyKheRIgu5Yl4KoVhSUgNOhoiYRsmb5g2u+LtzXDNOhjKgoAZ9/8k8uZWsGqcIav5wAAAAASUVORK5CYII=);
            background-color:#33A7F2
      }
      #MicrosoftAccountExchange:hover {
            background-color:#ADDBF9
      }
      #GoogleExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAb1BMVEXcTkH////cTD/bSj3ZQDLYOyzaRDbeV0vbSDrZPS/66Obyv7rsnpfpkorjcWfgZlvXOCr++Pj5393haFz88/L88fD67Or319T1zsv1zsrxuLPuqaLuqKLoi4LlfXTgYlbWMyTWMiPwtrHwta/fXVH/sCIIAAAAmElEQVQ4y+2RyQ7DIBBDMcwAIXvovqXb/39jRaX0AEmr5px3tSV7PGLhX6TVRFpN61l9zPNS6kn9gDcXO67zDnCnO2BCiNIyMtgKKJgyY2zQ68JEDtqju0nFTcOsxPUMw1GDDUqt+tY51/YNVlhvacTgEfCDIY0Q/lkBSg4RaUmmDo4/JdMzHy1Q2ejMeCj6PrXQP5+1MI8X0Y4HL4c826EAAAAASUVORK5CYII=);
            background-color:#DC4E41
      }
      #GoogleExchange:hover {
            background-color:#F1B8B3
      }
      #TwitterExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAdVBMVEVgqd3///9Ypdtdp9xaptxSotpQodlNn9lWo9pUo9rX6Pa+2vGTw+iLvuZlqt79/P7K4PO62O+y0+6hyutysuD2+fzi7vne6/fT5PTE3fKs0O2lzeuZx+l7tuJqrd71+Pzz9vzn8PnQ4/SCueSAueNsrt9InNh7sQwBAAAAwklEQVQ4y92PRw6EMAwAXeIkdBbY3uv/n7gSAoLDD5hbPCPZgZVihEgYgNSUpmfS7bfbtHS2nReyL2Qoc+yp8ZRAwCEWjgGAPQ7sssKoAGsWBrrgyMZCwD77Uel+59E3Tt14xZ7qlY7BRf1CDgeMKMw8sBXGlKxWtLGvHCgkQ80m0YHpjjq4sQ74pn1mISLJVSAMiwJO98l/TWSNF1eGKzqKfZ7Vj0mnHHwodpP+WIYlZP373DTtVWxYr2FD3pOBdfIHhOAHYHQI9VgAAAAASUVORK5CYII=);
            background-color:#60A9DD
      }
      #TwitterExchange:hover {
            background-color:#BFDCF1
      }
      #FacebookExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAaVBMVEU7W5z///85Wps3WJsiRo8xU5fw8vYyUpY0VZiAj70pS5OBkb0vUpb7+fwsTpTR1ud6irllerBPaqX09fnx8vfs7fSQoMZxg7VsgLNGY6FCX58ZP4v++/7r7vTZ3OupstGIlsFWcalDYaCK3qwDAAAAnklEQVQ4y+XQyw7CIBAFUBgc5VUoWGtb3/7/RyoYkyZAiSsXvdt7kstA/hRg/B0GpZ6byQ3Dw0NBaH+lMYRle3T0kwayACRdBrr/gnN+QtpQWv8cR4DswiUAjozlz4RdF8AmlnmwjaDQImoZwQkRedoToUS7D+ColGoTwQidx8oEQDMHN1MBva5MOL70SCHuE1TOhOpHrRt0FWAOP4IX8PsG2qEOR30AAAAASUVORK5CYII=);
            background-color:#3B5B9C
      }
      #FacebookExchange:hover {
            background-color:#B0BDD7
      }
      #LinkedInExchange {
            background-image:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACAAAAAgCAMAAABEpIrGAAAAb1BMVEUAe7b///8AdrMklscAc7EAeLUAcbB5ttifzeMqmckAdLIAaqz7+/6PxeAShr0CgLkAba4nmMctksTv9Puw1eij0OWGvNtfrNJNo80YjMAeib/D4vGt3Oy82+yfzOOCvtyJvdx3tddirtI/ncoxmMj9KsrQAAAAw0lEQVQ4y9WSVw7DIAxAG8CkjJDVzO5x/zMWk0RNJaB/kfo+sGUeCMvstgI4J7F9aS5NxSLnTWLpZVDgexTqIiycUNBhgTxRyCKPYJ3dl7sITCkO+FyLXaWU310DscASOesf3ahWChGJ5cb4ASO5Joiu2EegWEmZa1c3yUwOHmHNuQgJup4CgF8YlKpcMhKvkNmb1REz6hdetsyziIBldv8lpH8ouGm28zQFCu2SOSAXlJYGYCgpFThEMFPm/zCryja8Acy7CRfMrcKPAAAAAElFTkSuQmCC);
            background-color:#0077B5
      }
      #LinkedInExchange:hover {
            background-color:#99CAE1
      }
      #AmazonExchange {
            background-image:url(https://images-na.ssl-images-amazon.com/images/G/01/lwa/btnLWA_gold_156x32.png);
            background-color:#FFF;
            color:transparent
      }

      #next {
            -moz-user-select:none;
            user-select:none;
            cursor:pointer;
            width:auto;
            padding-left:10px;
            padding-right:10px;
            height:30.5px;
            -moz-border-radius:0;
           -webkit-border-radius:0;
            border-radius:0;
            background:#2672E6;
            border:1px solid #FFF;
            color:#fff;
            transition:background 1s ease 0s;
            font-size:100%
      }
      #next:hover {
            background:#0F3E83;
            border:1px solid #FFF;
            box-shadow:0 0 0
      }
      #next:hover,.accountButton:hover {
            -moz-box-shadow:0 0 0;
            -webkit-box-shadow:0 0 0;
            box-shadow:0 0 0;
      }
                        </style>
  </head>
  <body>
    <div class=navbar navbar-inverse navbar-static-top role=navigation>
      <div class=container>
        <div class=navbar-header>
          <div class=visible-xs-block>
            {{ snippets[Mobile Header] }}
          </div>
          <div class=visible-sm-block visible-md-block visible-lg-block navbar-brand>
            {{ snippets[Navbar Left] }}
          </div>
        </div>
      </div>
    </div>
    <div class=container>
      <div class=page-heading>
        <ul class=breadcrumb>
          <li>
            <a href={{ request.url | base }} title=Home>Home</a>
          </li>
          <li class=active>{{ page.title | h}}</li>
        </ul>
        {% include 'Page Header' %}
     </div>
     <div class=row>
      <div class=col-md-12>
        {% include 'Page Copy' %}
        <div id=api></div>
      </div>
     </div>
    </div>
    <footer role=contentinfo>
      <div class=footer-top hidden-print>
        <div class=container>
          <div class=row>
            <div class=col-md-6 col-sm-12 col-xs-12 text-left>
               {{ snippets[About Footer] }}
            </div>
            <div class=col-md-6 col-sm-12 col-xs-12 text-right>
              <ul class=list-social-links>
                <li><a href=#><span class=sprite sprite-facebook_icon></span></a></li>
                <li><a href=#><span class=sprite sprite-twitter_icon></span></a></li>
                <li><a href=#><span class=sprite sprite-email_icon></span></a></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class=footer-bottom hidden-print>
        <div class=container>
          <div class=row>
            <div class=col-md-4 col-sm-12 col-xs-12 text-left>
               {{ snippets[Footer] | liquid }}
            </div>
            <div class=col-md-8 col-sm-12 col-xs-12 text-left >
            </div>   
          </div>
        </div>
      </div>
    </footer>
  </body>
</html>
```
### <a name="step-2-create-a-page-template"></a>步骤 2：创建页面模板

创建以下页面模板：
- **名称**：[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 自定义页
- **类型**：Web 模板
- **Web 模板**：[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 自定义页
- **使用网站页眉和页脚**：清除此复选框

### <a name="step-3-create-a-webpage"></a>步骤 3：创建网页

创建以下网页：
- **名称**：登录
- **父**页：主页
- **部分 Url**：azure-ad-b2c-sign-in
- **页面模板**：[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 自定义页
- **发布状态**：已发布

### <a name="step-4-create-site-settings"></a>步骤 4：创建站点设置

需要通过站点设置配置跨源资源共享 (CORS) 以允许 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 请求自定义页和注入登录或注册用户界面。 创建以下站点设置。

| 名称                              | 值                             |
|-----------------------------------|-----------------------------------|
| HTTP/Access-Control-Allow-Methods | GET，选项                      |
| HTTP/Access-Control-Allow-Origin  | `https://login.microsoftonline.com` |
| | |

有关其他 CORS 设置的完整列表，请参阅 [CORS 协议支持](../add-web-resource.md#cors-protocol-support)。

### <a name="step-5-includeazureincludespn-azure-shortestmd-configuration"></a>步骤 5：[!include[Azure](../../../includes/pn-azure-shortest.md)] 配置

1. 登录到你的 [!include[Azure portal](../../../includes/pn-azure-portal.md)]。
2. 导航到 **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 租户管理**边栏选项卡。
3. 导航到**设置** > **注册或登录策略**。 显示可用策略的列表。
4. 选择要编辑的策略。
5. 选择**编辑**。
6. 选择**编辑策略** > **页面 UI 自定义** > **统一注册或登录页**
7. 将**使用自定义页**设置为**是**。
8. 将**自定义页 URI** 设置为在此过程步骤 3 中创建的 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 自定义页网页中的 URL。 例如，`https://mydomain.com/azure-ad-b2c-sign-in`。
9. 选择**确定**。

## <a name="claims-mapping"></a>声明映射

当用户首次登录或后续时，联合身份提供程序提供基于用户登录相关数据库的声明。 这些声明可在身份提供程序中进行配置。

### <a name="includeazureincludespn-azure-shortestmd-ad-b2c-email-claims"></a>[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 电子邮件声明

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 将电子邮件声明作为集合发送。 门户接受在集合中提供的第一封电子邮件作为联系人的主要电子邮件地址。

### <a name="claims-to-support-sign-up-scenarios"></a>支持注册方案的声明

如果配置在 Common Data Service 中不存在的新客户，可使用入站声明播种门户将要创建的新联系人记录。 常见声明包括姓名、电子邮件地址和电话号码，但它们是可以配置的。 需要以下站点设置：

**名称**：身份验证/OpenIdConnect/[联合-名称]/RegistrationClaimsMapping

**说明**：用于将声明值映射到在注册期间创建的联系人记录中的属性的逻辑名称/声明对的列表。

**格式**：attribute1=claim1,attribute2=claim2,attribute3=claim3

例如：firstname=<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle>

> [!NOTE]
> 确保将电子邮件地址映射到联系人的主要电子邮件 (emailaddress1)。 如果已向联系人记录添加了次要电子邮件 (emailaddress2) 或备用电子邮件 (emailaddress3) 并将其映射到了该电子邮件，将不向该联系人添加身份信息，而是使用用于主要电子邮件 (emailaddress1) 中设置的注册的电子邮件地址新建一个。

### <a name="claims-to-support-sign-in-scenarios"></a>支持登录方案的声明

Common Data Service 中和身份提供程序中的数据不直接关联，因此数据可能不会保持同步。门户应具有您要从任何登录事件接受的在 Common Data Service 中更新的声明的列表。 这些声明可以是来自登录方案的声明的子集或相等。 这必须与登录声明映射单独配置，因为您可能不希望覆盖某些关键门户属性。 需要以下站点设置：

**名称**：身份验证/OpenIdConnect/[联合-名称]/LoginClaimsMapping

**说明**：用于将声明值映射到在登录后创建的联系人记录中的属性的逻辑名称/声明对的列表。

**格式**：attribute1=claim1, attribute2=claim2, attribute3=claim3

例如：firstname=<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle> 

声明名称是在登录策略应用程序声明中的属性旁边列出的“声明类型”字段。

### <a name="allow-auto-association-to-a-contact-record-based-on-email"></a>允许基于电子邮件自动关联到联系人记录 

具有与电子邮件关联的联系人记录的客户之后启动网站，其外部用户将使用 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 通过电子邮件验证机制登录。 新登录将与现有的联系人记录关联，而不是创建重复记录。 此功能只成功映射没有活动身份的联系人，且电子邮件地址必须是唯一的（不与多个联系人记录关联）。 需要以下站点设置：

**名称**：身份验证/[协议]/[提供程序]/AllowContactMappingWithEmail

**说明**：指定联系人是否映射到相应的电子邮件。 当设置为 true 时，此设置将唯一的联系人记录与匹配的电子邮件地址关联，然后在用户成功登录后自动将外部身份提供程序分配到联系人。 默认情况下，它设置为 *false*。

**名称**：Authentication/UserManager/UserValidator/RequireUniqueEmail

**描述**：指定验证用户是否需要唯一电子邮件地址。 使用现有联系人电子邮件地址登录时，必须将此设置设置为 false。 默认情况下设置为 *true*，可能导致已有电子邮件地址的联系人记录的登录尝试失败。
