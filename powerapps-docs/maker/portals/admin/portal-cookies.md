---
title: Power Apps 门户中的 Cookie | MicrosoftDocs
description: 了解 Power Apps 门户使用的 Cookie。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 03/10/2020
ms.author: nenandw
ms.reviewer: tapanm
ms.openlocfilehash: 13730a4faa284890136cc04d2f56ff50c46d42e2
ms.sourcegitcommit: cf492063eca27fdf73459ff2f9134f2ca04ee766
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/17/2020
ms.locfileid: "3136641"
---
# <a name="cookies-in-power-apps-portals"></a>Power Apps 门户中的 Cookie

Cookie 是浏览器从网站发送到访问者设备的一个小文件。 一个 Web 会话可以使用多个 Cookie。

Power Apps 门户还使用 Cookie 来存储用于各种用途的信息。 以下一节内容列出并介绍了 Power Apps 门户使用的 Cookie：

## <a name="names-and-descriptions-of-cookies-used-by-portals"></a>门户使用的 Cookie 的名称和说明

#### <a name="arraffinity"></a>ARRAffinity

由 Azure 网站自动添加，确保不同站点之间的请求负载均衡。 不存储任何用户信息。

####  <a name="aspnet-session-id"></a>ASP.Net 会话 ID

用于维持已登录用户的会话，以避免重复登录。 此 Cookie 不是永久性的，将在会话关闭后删除。

#### <a name="dynamics-365-portal-analytics"></a>Dynamics 365 门户分析

关键服务 Cookie，用于匿名分析服务使用情况并进行汇总以用于统计目的。

#### <a name="contextlanguagecode"></a>ContextLanguageCode

存储会话中和跨网页访问门户的用户的默认语言。 此 Cookie 在会话关闭后删除。

#### <a name="aspnetapplicationcookie"></a>.AspNet.ApplicationCookie

用于标识用户会话。 当用户首次浏览门户时，用户会话开始。 在会话关闭时结束。 [身份验证站点设置](https://docs.microsoft.com/powerapps/maker/portals/configure/set-authentication-identity)可以用于更改会话过期时间跨度。

#### <a name="__requestverificationtoken"></a>__RequestVerificationToken 

由 [antiforgery](https://docs.microsoft.com/dotnet/api/system.web.helpers.antiforgeryconfig.cookiename) 系统使用。

#### <a name="adxpreviewunpublishedentities"></a>adxPreviewUnpublishedEntities

为门户管理员保留在经典 CMS 系统中使用的预览**开/关**模式。

#### <a name="adx-notification"></a>adx-notification

在实体窗体操作中用于存储要在重定向中显示的警报消息。

#### <a name="timezonecode"></a>timezoneCode

保留当前时区的 *CRM timezonedefinition* 实体的 *timezonecode* 字段值。

#### <a name="timezoneoffset"></a>timezoneoffset

保留 UTC 与当地浏览器时间之间的[时区差异](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getTimezoneOffset)。

#### <a name="isdstsupport"></a>isDSTSupport

指示指定的日期和时间是否在夏令时范围内。

#### <a name="isdstobserved"></a>isDSTObserved

存储指示当前时间是否是夏令时的值。

### <a name="see-also"></a>另请参阅

[Cookie 身份验证网站设置](https://docs.microsoft.com/powerapps/maker/portals/configure/set-authentication-identity#cookie-authentication-site-settings)

