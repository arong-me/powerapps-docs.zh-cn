---
title: 门户的 Azure AD B2C 提供程序设置 |MicrosoftDocs
description: 有关为门户启用 Azure AD B2C 提供程序设置的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 5f902dd900e074c2e6b3f08f8848475dcd907ee4
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542824"
---
# <a name="azure-ad-b2c-provider-settings-for-portals"></a>门户的 Azure AD B2C 提供程序设置

[!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory （Azure AD）为员工或内部身份验证提供 Office 365 和 Dynamics 365 服务。 [!include[Azure](../../../includes/pn-azure-shortest.md)] Active Directory B2C 是对该身份验证模型的扩展，它允许外部客户登录通过本地凭据并使用各种常见社交标识提供者进行联合身份验证。

门户所有者可以将门户配置为接受 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 作为标识提供者。 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 支持开放 ID Connect 进行联合。

在将 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 配置为你的门户的标识提供程序的过程中，将生成多个值，你稍后会在配置门户时使用这些值。 可以在下表中记下这些值。 配置门户时，请将变量名称替换为此处说明的值。

| 变量名称     | Value | 描述                                                           |
|-------------------|-------|-----------------------------------------------------------------------|
| 应用程序名称  |       | 将门户表示为信赖方的应用程序的名称 |
| 应用程序 ID    |       | 与在 Azure Active Directory B2C 中创建的应用程序关联的应用程序 ID。  |
| 策略登录-URL |       | 在元数据终结点中定义的颁发者（iss） URL。                |
| 联合名称   |       | 标识联合身份验证提供程序（如 "B2C"）类型的唯一名称。 这将在站点设置名称中用于对此特定提供程序的配置设置进行分组。                                                                      |
| | | |

### <a name="use-azure-ad-b2c-as-an-identity-provider-for-your-portal"></a>使用 Azure AD B2C 作为门户的标识提供者

1. 登录到[Azure 门户](https://portal.azure.com/)。
2. [创建 Azure AD B2C 租户](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-get-started)。
3. 选择最左侧导航栏 **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C** 。
4. [创建 Azure 应用程序](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-app-registration#register-a-web-application)。

   > [!Note]
   > 必须在 "**允许隐式流**" 字段中选择 **"是**"，并在 "**回复 URL** " 字段中指定门户 URL。 "**回复 URL** " 字段中的值应采用 [门户域]/Signin-[Federation Name] 格式。 例如，`https://contosocommunity.microsoftcrmportals.com/signin-B2C`。

5. 复制应用程序名称，然后在上表中输入应用程序名称的值。
6. 复制 "应用程序 ID"，并将其输入为上表中的 "应用程序 ID" 的值。
7. [创建注册或登录策略](https://docs.microsoft.com/azure/active-directory-b2c/active-directory-b2c-reference-policies#create-a-sign-up-or-sign-in-policy)。
8. 选择策略，然后选择 "**编辑**"。
9. 选择**令牌、会话 & SSO config**。
10. 从 "**颁发者（iss）声明**" 列表中，选择其路径中包含 **/tfp**的 URL。
11. 保存策略。
12. 选择 "**此策略的元数据终结点**中的 URL" 字段。
13. 复制 "颁发者" 字段的值，并将其输入为上表中的 "策略登录 URL" 的值。 

## <a name="portal-configuration"></a>门户配置

在 [!include[Azure](../../../includes/pn-azure-shortest.md)]中创建和配置 B2C 租户之后，必须使用 Open ID Connect 协议将门户配置为与 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 进行联合。 必须为联合创建唯一的名称，以便 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C&mdash;例如，B2C&mdash;，并将其存储为上表中的*联合名称*变量的值。

### <a name="configure-your-portal"></a>配置门户
1. 打开门户管理应用。
2. 请参阅**门户** > **网站**。
3. 选择需要为其启用 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 的网站记录。
4. 中转到 "**站点设置**"。
5. 创建下列站点设置：
   -   **名称**： Authentication/OpenIdConnect/[Federation-Name]/Authority

       **值**： [策略登录-URL]
   -   **名称**： Authentication/OpenIdConnect/[Federation-Name]/ClientId

       **值**： [应用程序 ID]
   -   **名称**： Authentication/OpenIdConnect/[Federation-Name]/RedirectUri

       **值**： [门户域]/Signin-[联合名称]

       例如，`https://mysite.com/signin-b2c` 
6. 若要支持联合注销，请创建以下站点设置：
   - **名称**： Authentication/OpenIdConnect/[Federation-Name]/ExternalLogoutEnabled

     **值**： true
7. 若要将门户硬编码为单个标识提供者，请创建以下网站设置：
   - **名称**：身份验证/注册/LoginButtonAuthenticationType

     **值**： [策略登录-URL]

8. 若要支持密码重置，请创建[此处](#password-reset)所述的所需站点设置。
9. 若要支持声明映射，请创建[此处](#claims-mapping)所述的所需站点设置。

有关相关站点设置的完整列表，请参阅[此处](#related-site-settings)。

### <a name="password-reset"></a>密码重置

如果要支持 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 本地帐户进行密码重置，则需要以下站点设置：

| 站点设置                                                        | 描述                                                                                                          |
|---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Authentication/OpenIdConnect/[Federation-Name/PasswordResetPolicyId | 密码重置策略的 ID。                                                                                     |
| Authentication/OpenIdConnect/[Federation-Name]/ValidIssuers         | 以逗号分隔的颁发者列表，其中包括 [策略登录 URL] 和密码重置策略的颁发者。 |
|Authentication/OpenIdConnect/[Federation-Name]/DefaultPolicyId | 登录或注册策略的 ID。|
|||

### <a name="related-site-settings"></a>相关站点设置

你可以在门户中创建或配置以下站点设置，以支持 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 作为标识提供者：


| 站点设置                                                         | 描述                                                                                                                                                                                                                                                        |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Authentication/Registration/ProfileRedirectEnabled                   | 指定在成功登录后门户是否可以将用户重定向到配置文件页面。 默认情况下，它设置为 true。                                                                                                                                            |
| Authentication/Registration/EmailConfirmationEnabled                 | 指定是否需要电子邮件验证。 默认情况下，它设置为 true。                                                                                     |
| Authentication/Registration/LocalLoginEnabled                        | 指定是否需要本地登录。 默认情况下，它设置为 true。                                                                        |
| Authentication/Registration/ExternalLoginEnabled                     | 启用或禁用外部身份验证。       |
| Authentication/Registration/AzureADLoginEnabled                      | 启用或禁用 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD 作为外部标识提供者。 默认情况下，它设置为 true。                                                                                                                                                                      |
| Authentication/OpenIdConnect/[Federation-Name]/ExternalLogoutEnabled | 启用或禁用联合注销。如果设置为 true，则当用户从门户注销时，将重定向到联合注销用户体验。 如果设置为 "false"，则仅从门户中注销用户。 默认情况下，它设置为 false。               |
| Authentication/LoginTrackingEnabled                                  | 启用或禁用跟踪用户的上次登录。 当设置为 true 时，日期和时间显示在联系人记录上的 "**最后一次成功登录**" 字段中。 默认情况下，此值设置为 false。                                                            |
| Authentication/OpenIdConnect/[Federation-Name]/RegistrationEnabled   | 启用或禁用现有标识提供者的注册要求。 如果设置为 true，则仅当站点设置身份验证/注册/启用也设置为 true 时，才为现有提供程序启用注册。 默认情况下，它设置为 true。 |
|Authentication/OpenIdConnect/[Federation-Name]/PostLogoutRedirectUri |指定在用户注销后要重定向到的门户中的 URL。 |
| | |

### <a name="related-content-snippet"></a>相关内容代码片段

如果在用户兑换邀请之后为用户禁用注册，请使用以下内容片段显示消息：

**名称**： Account/Register/RegistrationDisabledMessage

**值**：注册已禁用。

## <a name="customize-the-includeazureincludespn-azure-shortestmd-ad-b2c-user-interface"></a>自定义 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 用户界面

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 支持用户界面自定义。 你可以自定义注册和登录方案的用户体验。

### <a name="step-1-create-a-web-template"></a>步骤1：创建 web 模板
使用以下值创建 web 模板：

**名称**： [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 自定义页

**源**：使用下面的 web 模板源 HTML 示例。

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
### <a name="step-2-create-a-page-template"></a>步骤2：创建页面模板

创建以下页面模板：
- **名称**： [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 自定义页
- **类型**： Web 模板
- **Web 模板**： [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 自定义页面
- **使用网站页眉和页脚**：清除此复选框

### <a name="step-3-create-a-webpage"></a>步骤3：创建网页

创建以下网页：
- **名称**：登录
- **父项**页面：主页
- **部分 Url**： azure ad-b2c-登录
- **页面模板**： [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 自定义页面
- **发布状态**：已发布

### <a name="step-4-create-site-settings"></a>步骤4：创建站点设置

站点设置需要配置跨域资源共享（CORS），以允许 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 请求自定义页面并注入登录或注册用户界面。 创建下列站点设置。

| 名称                              | Value                             |
|-----------------------------------|-----------------------------------|
| HTTP/访问控制-允许-方法 | 获取，选项                      |
| HTTP/访问控制-允许-源  | `https://login.microsoftonline.com` |
| | |

有关其他 CORS 设置的完整列表，请参阅[CORS 协议支持](../add-web-resource.md#cors-protocol-support)。

### <a name="step-5-includeazureincludespn-azure-shortestmd-configuration"></a>步骤5： [!include[Azure](../../../includes/pn-azure-shortest.md)] 配置

1. 登录到 [!include[Azure portal](../../../includes/pn-azure-portal.md)]。
2. 导航到 **[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 租户管理**边栏选项卡。
3. 导航到 "**设置**" > **注册或登录策略**。 将显示可用策略的列表。
4. 选择要编辑的策略。
5. 选择 "**编辑**"。
6.  > **统一注册或登录页**上，选择 "**编辑策略**" > **页面 UI 自定义**"
7. 将 "**使用自定义页**" 设置为 **"是"** 。
8. 将**自定义页面 URI**设置为在此过程的步骤3中创建的 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 自定义页面网页的 URL。 例如，`https://mydomain.com/azure-ad-b2c-sign-in`。
9. 选择“确定”。

## <a name="claims-mapping"></a>声明映射

用户首次登录时，或随后，联合标识提供者会根据用户登录的数据库提供声明。 这些声明可在标识提供者中进行配置。

### <a name="includeazureincludespn-azure-shortestmd-ad-b2c-email-claims"></a>[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 电子邮件声明

[!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 以集合形式发送电子邮件声明。 门户会将集合中提供的第一个电子邮件作为联系人的主电子邮件地址。

### <a name="claims-to-support-sign-up-scenarios"></a>支持注册方案的声明

如果预配了在 Common Data Service 中不存在的新客户，则可以使用入站声明来播种门户将创建的新联系人记录。 常见声明可以包括名字和姓氏、电子邮件地址和电话号码，但可对其进行配置。 以下站点设置是必需的：

**名称**： Authentication/OpenIdConnect/[Federation-Name]/RegistrationClaimsMapping

**说明**：要用于将声明值映射到注册期间创建的联系人记录中的属性的逻辑名称/声明对的列表。

**格式**： attribute1 = claim1，attribute2 = claim2，attribute3 = claim3

例如： firstname =<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle>

> [!NOTE]
> 确保将电子邮件地址映射到联系人的主电子邮件（emailaddress1）。 如果已将辅助电子邮件（emailaddress2）或备用电子邮件（emailaddress3）添加到联系人记录，并将其映射到电子邮件，则将不会向联系人添加标识信息，并将使用用于注册的电子邮件地址创建新的电子邮件地址主电子邮件（emailaddress1）。

### <a name="claims-to-support-sign-in-scenarios"></a>支持登录方案的声明

Common Data Service 和标识提供程序中的数据不是直接链接的，因此，数据可能会失去同步。门户应该具有要在 Common Data Service 中进行更新的任何登录事件接受的声明列表。 这些声明可以是来自登录方案的声明的子集（或等于）。 这必须与登录声明映射分开进行配置，因为你可能不希望覆盖某些关键门户属性。 以下站点设置是必需的：

**名称**： Authentication/OpenIdConnect/[Federation-Name]/LoginClaimsMapping

**描述**：要用于将声明值映射到登录后创建的联系人记录中的属性的逻辑名称/声明对的列表。

**格式**： attribute1 = claim1，attribute2 = claim2，attribute3 = claim3

例如： firstname =<https://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname,lastname=https://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname,jobtitle=jobTitle> 

声明名称是在 "登录策略" 应用程序声明中的特性旁边列出的声明类型字段。

### <a name="allow-auto-association-to-a-contact-record-based-on-email"></a>允许基于电子邮件自动关联到联系人记录 

使用关联的电子邮件的联系人记录的客户，然后启动一个网站，其外部用户会通过电子邮件验证机制在 [!include[Azure](../../../includes/pn-azure-shortest.md)] AD B2C 上进行登录。 新登录应与现有的联系人记录相关联，而不是创建重复记录。 此功能仅成功映射没有活动标识的联系人，并且电子邮件地址必须是唯一的（不与多个联系人记录相关）。 以下站点设置是必需的：

**名称**：身份验证/[协议]/[Provider]/AllowContactMappingWithEmail

**说明**：指定是否将联系人映射到相应的电子邮件。 当设置为 true 时，此设置将唯一的联系人记录与匹配的电子邮件地址相关联，然后在用户成功登录后，自动将外部标识提供者分配给该联系人。 默认情况下，它设置为 false。
