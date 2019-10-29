---
title: 在门户中使用 OAuth 2.0 隐式授权流 |MicrosoftDocs
description: 了解如何通过在门户中使用 OAuth 隐式授予流，对外部 Api 进行客户端调用并对其进行保护。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 06db149e5f86696ecffae38fe05e23198d72ecb5
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72974497"
---
# <a name="use-oauth-20-implicit-grant-flow-within-your-portal"></a>在门户中使用 OAuth 2.0 隐式授权流 

此功能使客户能够通过使用 OAuth 隐式授予流，对外部 Api 进行客户端调用并对其进行保护。 它提供了一个终结点，用于获取安全访问令牌，这些令牌包含外部 Api 在 OAuth 2.0 隐式授权流中进行授权时要使用的用户标识信息。 已登录用户的标识信息将以安全的方式传递到外部 AJAX 调用。 这不仅有助于开发人员传递身份验证上下文，还可以帮助用户使用此机制来保护其 Api。

OAuth 2.0 隐式授权流支持客户端可以调用来获取 ID 令牌的终结点。 这两个终结点用于此目的：[授权](#authorize-endpoint-details)和[标记](#token-endpoint-details)。

## <a name="authorize-endpoint-details"></a>授权终结点详细信息 

授权终结点的 URL 为： `<portal_url>/_services/auth/authorize`。 授权终结点支持以下参数：

| 参数   | 必填？ | 描述                             |
|---------------|-----------|---------------------------------------|
| client_id      | 是       | 在调用授权终结点时传递的字符串。 你必须确保已在[门户中注册](#register-client-id-for-implicit-grant-flow)了客户端 ID。 否则，会显示错误。 客户端 ID 作为 `aud` 和 `appid` 参数添加到令牌中的声明中，并可供客户端用来验证返回的令牌是否适用于其应用。<br>最大长度为36个字符。 仅支持字母数字字符和连字符。 |
| redirect_uri      | 是       | 可发送和接收身份验证响应的门户 URL。 它必须针对在调用中使用的特定 `client_id` 进行注册，并且应与注册的值完全相同。            |
| 状态       | 否        | 请求中包含的值，也会在令牌响应中返回。 它可以是你想要使用的任何内容的字符串。 通常，随机生成的唯一值用于防止跨站点请求伪造攻击。<br>最大长度为20个字符。              |
| 现时   | 否        | 由客户端发送的一个字符串值，该字符串值作为声明包含在生成的 ID 令牌中。 然后，客户端可以验证此值，以减少令牌重放攻击。 最大长度为20个字符。      |
| response_type         | 否        | 此参数仅支持 `token` 作为值。 这允许应用立即从授权终结点接收访问令牌，而无需向授权终结点发出第二次请求。                               |
|||

### <a name="successful-response"></a>成功的响应

授权终结点以片段的形式返回响应 URL 中的以下值：

- **令牌**：令牌作为 JSON Web 令牌（JWT）返回，由门户的私钥进行数字签名。
- **状态**：如果请求中包含状态参数，则响应中应显示相同的值。 应用应该验证请求和响应中的状态值是否相同。
- **expires_in**：访问令牌有效的时间长度（以秒为单位）。

例如，成功的响应如下所示：

```
GET https://aadb2cplayground.azurewebsites.net/#token=eyJ0eXAiOiJKV1QiLCJhbGciOI1NisIng1dCI6Ik5HVEZ2ZEstZnl0aEV1Q&expires_in=3599&state=arbitrary_data_you_sent_earlier
```

### <a name="error-response"></a>错误响应

授权终结点中的错误将作为具有以下值的 JSON 文档返回：

- **错误 ID**：错误的唯一标识符。
- **错误消息**：一条特定的错误消息，可帮助你确定身份验证错误的根本原因。
- **相关 ID**：用于调试目的的 GUID。 如果已启用诊断日志记录，则会在服务器错误日志中显示相关 ID。
- **时间戳**：生成错误的日期和时间。

错误消息以登录用户的默认语言显示。 如果用户未登录，则会显示登录页供用户登录。 例如，错误响应如下所示：

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="token-endpoint-details"></a>令牌终结点详细信息

还可以通过向 `/token` 终结点发出请求来获取令牌。 它与授权终结点的不同之处在于，授权终结点在单独的页（redirect_uri）中处理令牌逻辑，而标记终结点处理同一页上的标记逻辑。 令牌终结点的 URL 为： `<portal_url>/_services/auth/token`。 令牌终结点支持以下参数：

| 参数   | 必填？ | 描述                             |
|---------------|-----------|---------------------------------------|
| client_id      | 否       | 在调用授权终结点时传递的字符串。 你必须确保已在[门户中注册](#register-client-id-for-implicit-grant-flow)了客户端 ID。 否则，会显示错误。 客户端 ID 作为 `aud` 和 `appid` 参数添加到令牌中的声明中，并可供客户端用来验证返回的令牌是否适用于其应用。<br>最大长度为36个字符。 仅支持字母数字字符和连字符。 |
| redirect_uri      | 否       | 可发送和接收身份验证响应的门户 URL。 它必须针对在调用中使用的特定 `client_id` 进行注册，并且应与注册的值完全相同。            |
| 状态       | 否        | 请求中包含的值，也会在令牌响应中返回。 它可以是你想要使用的任何内容的字符串。 通常，随机生成的唯一值用于防止跨站点请求伪造攻击。<br>最大长度为20个字符。              |
| 现时   | 否        | 由客户端发送的一个字符串值，该字符串值作为声明包含在生成的 ID 令牌中。 然后，客户端可以验证此值，以减少令牌重放攻击。 最大长度为20个字符。      |
| response_type         | 否        | 此参数仅支持 `token` 作为值。 这允许应用立即从授权终结点接收访问令牌，而无需向授权终结点发出第二次请求。                               |
|||

> [!NOTE]
> 尽管 `client_id`、`redirect_uri`、`state`和 `nonce` 参数是可选的，但建议使用它们以确保集成安全。

### <a name="successful-response"></a>成功的响应

令牌终结点在窗体正文中返回 state 和 expires_in 作为响应标头和标记。

### <a name="error-response"></a>错误响应

令牌终结点中的错误将作为具有以下值的 JSON 文档返回：

- **错误 ID**：错误的唯一标识符。
- **错误消息**：一条特定的错误消息，可帮助你确定身份验证错误的根本原因。
- **相关 ID**：用于调试目的的 GUID。 如果已启用诊断日志记录，则会在服务器错误日志中显示相关 ID。
- **时间戳**：生成错误的日期和时间。

错误消息以登录用户的默认语言显示。 如果用户未登录，则会显示登录页供用户登录。 例如，错误响应如下所示：

```
{"ErrorId": "PortalSTS0001", "ErrorMessage": "Client Id provided in the request is not a valid client Id registered for this portal. Please check the parameter and try again.", "Timestamp": "4/5/2019 10:02:11 AM", "CorrelationId": "7464eb01-71ab-44bc-93a1-f221479be847" }
```

## <a name="validate-id-token"></a>验证 ID 令牌

仅获取 ID 令牌并不足以对用户进行身份验证;还必须根据应用的要求验证令牌的签名并验证令牌中的声明。 公共令牌终结点提供门户的公钥，该公钥可用于验证门户提供的令牌签名。 公共令牌终结点的 URL 为： `<portal_url>/_services/auth/publickey`。

## <a name="turn-implicit-grant-flow-on-or-off"></a>启用或禁用隐式授权流

默认情况下，隐式授权流处于启用状态。 如果要关闭隐式授权流，请将 " **Connector/ImplicitGrantFlowEnabled**站点" 设置的值设置为 " **False**"。

如果门户中未提供此站点设置，则必须使用适当的值[创建新的站点设置](configure/configure-site-settings.md#manage-portal-site-settings)。

## <a name="configure-token-validity"></a>配置令牌有效性

默认情况下，该令牌的有效时间为15分钟。 如果要更改令牌的有效性，请将**ImplicitGrantFlow/TokenExpirationTime**站点设置的值设置为所需的值。 值必须以秒为单位指定。 最大值可以是1小时，最小值必须为1分钟。 如果指定了不正确的值（例如，字母数字字符），则使用默认值15分钟。 如果指定的值大于最大值或小于最小值，则默认情况下将分别使用最大值和最小值。

例如，若要将令牌有效期设置为30分钟，请将**ImplicitGrantFlow/TokenExpirationTime**站点设置的值设置为**1800**。 若要将令牌有效性设置为1小时，请将**ImplicitGrantFlow/TokenExpirationTime**站点设置的值设置为**3600**。

## <a name="register-client-id-for-implicit-grant-flow"></a>注册隐式授权流的客户端 ID

必须将客户端 ID 注册到允许此流的门户。 若要注册客户端 ID，必须创建以下网站设置：

|站点设置|Value|
|------|------|
|ImplicitGrantFlow/RegisteredClientId|此门户允许的有效客户端 ID 值。 必须用分号分隔值，并且可以包含字母数字字符和连字符。 最大长度为36个字符。|
|ImplicitGrantFlow/{ClientId}/RedirectUri|允许用于特定客户端 ID 的有效重定向 Uri。 值必须用分号分隔。 提供的 URL 必须是门户的有效网页。|
|||

## <a name="sample-code"></a>示例代码

可以使用以下示例代码开始使用适用于 PowerApps 门户 Api 的 OAuth 2.0 隐式授权。

### <a name="use-portal-oauth-token-with-an-external-web-api"></a>将门户 OAuth 令牌用于外部 Web API

此示例是一个基于 ASP.NET 的项目，用于验证 PowerApps 门户颁发的 ID 令牌。 可在此处找到完整示例：[将门户 OAuth 令牌用于外部 WEB API](https://github.com/microsoft/PowerApps-Samples/tree/master/portals/ExternalWebApiConsumingPortalOAuthTokenSample)。

### <a name="authorize-endpoint-sample"></a>授权终结点示例

此示例演示授权终结点如何以重定向 URL 中的片段的形式返回 ID 令牌。 它还介绍了隐性 Grant 中支持的状态验证。 可在以下位置找到该示例：[授权终结点示例](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/AuthorizeEndpoint.js)。

### <a name="token-endpoint-sample"></a>令牌终结点示例

此示例演示如何使用 getAuthenticationToken 函数在 PowerApps 门户中使用令牌终结点获取 ID 令牌。 可在以下位置找到该示例：[令牌终结点示例](https://github.com/microsoft/PowerApps-Samples/blob/master/portals/TokenEndpoint.js)。
