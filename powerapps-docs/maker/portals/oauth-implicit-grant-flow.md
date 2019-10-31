---
title: 在门户中使用 OAuth 2.0 隐式授权流 | MicrosoftDocs
description: 了解如何使用 Dynamics 365 门户中的 OAuth 隐式授权流向外部 API 发起客户端调用并保护它们。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 08/30/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="use-oauth-20-implicit-grant-flow-within-your-portal"></a>在门户中使用 OAuth 2.0 隐式授权流 

此功能可以让客户使用 OAuth 隐式授权流向外部 API 发起客户端调用并保护它们。 它提供了获取安全访问令牌（将包含供按照 OAuth 2.0 隐式授权流的外部授权 API 使用的用户身份信息）的终结点。 已登录用户的身份信息是以受保护的方式传递到外部 AJAX 调用。 这不仅有助于开发人员传递身份验证上下文，还会帮助用户使用此机制保护他们的 API。

OAuth 2.0 隐式授权流支持客户端可以调用来获取 ID 令牌的终结点。 有两个终结点用于此目的：[授权](#authorize-endpoint-details)和[令牌](#token-endpoint-details)。

## <a name="authorize-endpoint-details"></a>授权终结点详细信息 

授权终结点的 URL 为：`<portal_url>/_services/auth/authorize`。 授权终结点支持以下参数：

| 参数   | 是否必需? | 说明                             |
|---------------|-----------|---------------------------------------|
| client_id      | 是       | 在对授权终结点发起调用时传递的字符串。 必须确保客户端 ID 已[在门户中注册](#register-client-id-for-implicit-grant-flow)。 否则，将显示错误。 客户端 ID 在令牌的声明中添加为 `aud` 以及 `appid` 参数，其可供客户端用来验证返回的令牌是否适合其应用。<br>最大长度为 36 个字符。 仅支持字母数字字符和连字符。 |
| redirect_uri      | 是       | 发出身份验证响应的门户的 URL 可以发送和接收。 其必须针对调用中使用的特定 `client_id` 注册，并且应该与注册值完全相同。            |
| state       | 否        | 也会在令牌响应中返回的请求中包含的值。 它可以是要使用的任何内容的字符串。 通常是随机生成，唯一值用于阻止跨站点请求伪造攻击。<br>最大长度为 20 个字符。              |
| nonce   | 否        | 在生成的 ID 令牌中作为声明包含的客户端发送的字符串值。 客户随后可以验证此值来缓解令牌重放攻击。 最大长度为 20 个字符。      |
| response_type         | 否        | 此参数仅支持 `token` 作为值。 这允许您的应用立即从授权终结点接收访问令牌，而无需向授权终结点发起第二次请求。                               |
|||

### <a name="successful-response"></a>成功响应

授权终结点在响应 URL 中作为片段返回以下值：

- **令牌**：令牌作为门户的私钥数字签名的 JSON Web 令牌 (JWT) 返回。
- **状态**：如果状态参数包含在请求中，相同值应该显示在响应中。 应用应验证请求和响应中的状态值是否相同。
- **expires_in**：访问令牌有效的时间长度（秒）。

例如，成功的响应如下所示：

```
GET https://aadb2cplayground.azurewebsites.net/#token=eyJ0eXAiOiJKV1QiLCJhbGciOI1NisIng1dCI6Ik5HVEZ2ZEstZnl0aEV1Q&expires_in=3599&state=arbitrary_data_you_sent_earlier
```

### <a name="error-response"></a>错误响应

授权终结点中的错误返回为包含以下值的 JSON 文档：

- **错误 ID**：错误的唯一标识符。
- **错误消息**：可以帮助您确定身份验证错误的根本原因的特定错误消息。
- **相关性 ID**：用于调试目标的 GUID。 如果启用了诊断日志记录，相关性 ID 会位于服务器错误日志内。
- **时间戳**：生成错误的日期和时间。

错误消息将以已登录用户的默认语言显示。 如果用户尚未登录，登录页将向用户显示以登录。 例如，错误响应如下所示：

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="token-endpoint-details"></a>令牌终结点详细信息

您还可以通过向 `/token` 终结点发起请求来获取令牌。 它与授权终结点在单独页面 (redirect_uri) 中处理令牌逻辑的方式不同，而令牌终结点在同一页处理令牌逻辑。 令牌终结点的 URL 为：`<portal_url>/_services/auth/token`。 令牌终结点支持以下参数：

| 参数   | 是否必需? | 说明                             |
|---------------|-----------|---------------------------------------|
| client_id      | 否       | 在对授权终结点发起调用时传递的字符串。 必须确保客户端 ID 已[在门户中注册](#register-client-id-for-implicit-grant-flow)。 否则，将显示错误。 客户端 ID 在令牌的声明中添加为 `aud` 以及 `appid` 参数，其可供客户端用来验证返回的令牌是否适合其应用。<br>最大长度为 36 个字符。 仅支持字母数字字符和连字符。 |
| redirect_uri      | 否       | 发出身份验证响应的门户的 URL 可以发送和接收。 其必须针对调用中使用的特定 `client_id` 注册，并且应该与注册值完全相同。            |
| state       | 否        | 也会在令牌响应中返回的请求中包含的值。 它可以是要使用的任何内容的字符串。 通常是随机生成，唯一值用于阻止跨站点请求伪造攻击。<br>最大长度为 20 个字符。              |
| nonce   | 否        | 在生成的 ID 令牌中作为声明包含的客户端发送的字符串值。 客户随后可以验证此值来缓解令牌重放攻击。 最大长度为 20 个字符。      |
| response_type         | 否        | 此参数仅支持 `token` 作为值。 这允许您的应用立即从授权终结点接收访问令牌，而无需向授权终结点发起第二次请求。                               |
|||

> [!NOTE]
> 虽然 `client_id`、`redirect_uri`、`state` 和 `nonce` 参数是可选的，但建议使用它们以确保您的集成是安全的。

### <a name="successful-response"></a>成功响应

令牌终结点在窗体主体中返回 state 和 expires_in 作为响应标题并返回令牌。

### <a name="error-response"></a>错误响应

令牌终结点中的错误返回为包含以下值的 JSON 文档：

- **错误 ID**：错误的唯一标识符。
- **错误消息**：可以帮助您确定身份验证错误的根本原因的特定错误消息。
- **相关性 ID**：用于调试目标的 GUID。 如果启用了诊断日志记录，相关性 ID 会位于服务器错误日志内。
- **时间戳**：生成错误的日期和时间。

错误消息将以已登录用户的默认语言显示。 如果用户尚未登录，登录页将向用户显示以登录。 例如，错误响应如下所示：

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="validate-id-token"></a>验证 ID 令牌

只获取 ID 令牌对于对用户进行身份验证是不够的；您还必须基于您的应用的要求验证令牌的签名并验证令牌中的声明。 公共令牌终结点提供门户的公钥，其可用于验证门户提供的令牌的签名。 公共令牌终结点的 URL 为：`<portal_url>/_services/auth/publickey`。

## <a name="turn-implicit-grant-flow-on-or-off"></a>打开或关闭隐式授权流

默认情况下，隐式授权流是启用的。 如果要关闭隐式授权流，将 **Connector/ImplicitGrantFlowEnabled** 站点设置的值设置为 **False**。

如果此站点设置在您的门户中不可用，则必须使用合适的值[创建新站点设置](configure-site-settings.md#manage-portal-site-settings)。

## <a name="configure-token-validity"></a>配置令牌有效性

默认情况下，令牌在 15 分钟内有效。 如果要更改令牌的有效性，将 **ImplicitGrantFlow/TokenExpirationTime** 站点设置的值设置为所需的值。 值必须在几秒钟内指定。 最大值可以是 1 小时，最小值必须是 1 分钟。 如果指定了不正确的值（例如，字母数字字符），将使用默认值 15 分钟。 如果您指定的是大于最大值或小于最小值，默认将分别使用最大值和最小值。

例如，若要将令牌有效性设置为 30 分钟，请将 **ImplicitGrantFlow/TokenExpirationTime** 站点设置的值设置为 **1800**。 若要将令牌有效性设置为 1 小时，请将 **ImplicitGrantFlow/TokenExpirationTime** 站点设置的值设置为 **3600**。

## <a name="register-client-id-for-implicit-grant-flow"></a>为客户端 ID 注册隐式授权流

您必须在允许此流的门户中注册客户端 ID。 若要注册客户端 ID，您必须创建以下站点设置：

|站点设置|Value|
|------|------|
|ImplicitGrantFlow/RegisteredClientId|此门户允许的有效的客户端 ID 值。 值必须由分号分隔，可以包含字母数字字符和连字符。 最大长度为 36 个字符。|
|ImplicitGrantFlow/{ClientId}/RedirectUri|特定客户端 ID 允许的有效重定向 URI。 值必须由分号分隔。 提供的 URL 必须是有效的门户网页。|
|||

## <a name="sample-code"></a>示例代码

可使用以下示例代码开始对 Dynamics 365 门户 API 使用 OAuth 2.0 隐式授权。

### <a name="use-portal-oauth-token-with-an-external-web-api"></a>对外部 Web API 使用门户 OAuth 令牌

此示例是基于 ASP.NET 的项目，用于验证 Dynamics 365 门户颁发的 ID 令牌。 下面提供完整示例：[对外部 Web API 使用门户 OAuth 令牌](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/ExternalWebApiConsumingPortalOAuthTokenSample)。

### <a name="authorize-endpoint-sample"></a>授权终结点示例

此示例显示授权终结点如何将 ID 令牌显示为重定向的 URL 中的片段。 还介绍隐式授权中支持的状态验证。 下面提供此示例：[授权终结点示例](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/AuthorizeEndpoint.js)。

### <a name="token-endpoint-sample"></a>令牌终结点示例

此示例显示在 Dynamics 365 门户中如何使用 getAuthenticationToken 函数和令牌终结点访存 ID 令牌。 下面提供此示例：[令牌终结点示例](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/TokenEndpoint.js)。
