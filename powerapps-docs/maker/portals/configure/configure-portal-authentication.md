---
title: 配置门户身份验证 |MicrosoftDocs
description: 了解如何为门户配置身份验证。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: b285ce6e3a93efb72ed867149ce0740f7ee96579
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73542761"
---
# <a name="configure-portal-authentication"></a>配置门户身份验证

在门户应用程序中，经过身份验证的门户用户与联系人或系统用户关联。 默认门户配置为 "基于联系人"。 若要登录，联系人必须已配置相应的 web 身份验证信息。 门户用户必须分配到 web 角色才能获得未经身份验证的用户的权限。 若要配置 web 角色的权限，请配置其网页访问权限和网站访问控制规则。

最新的门户身份验证体验允许门户用户使用他们选择的本地联系人成员资格提供程序或基于[ASP.NET Identity](https://www.asp.net/identity)的外部帐户进行登录。   

- **本地身份验证**：本地身份验证是常见的基于窗体的身份验证，使用 Common Data Service 环境的联系人记录进行身份验证。 为了构建自定义身份验证体验，开发人员可以使用 ASP.Net 标识 API 来创建自定义登录页和工具。
- **外部身份验证**：外部身份验证由 ASP.NET Identity API 提供。 在这种情况下，帐户凭据和密码管理由第三方标识提供者处理。 这包括基于 OpenID 的提供程序，例如 Yahoo！ 和基于 Google 和 OAuth 2.0 的提供程序，如 Twitter、Facebook 和 [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]。 用户通过选择要注册到门户的外部标识注册到门户。 注册后，外部标识可以访问与本地帐户相同的功能。 

本地和外部帐户注册都可以使用邀请代码进行注册，还可以使用电子邮件确认工作流。 此外，门户管理员还可以选择通过门户网站设置启用或禁用身份验证选项的任意组合。

> [!NOTE]
> 门户用户必须具有唯一的电子邮件地址。 如果两个或更多个联系人记录（包括停用的联系人记录）具有相同的电子邮件地址，则联系人将无法在门户上进行身份验证。

## <a name="account-sign-up-registration"></a>帐户注册（注册）

门户管理员有几个选项可用于控制帐户注册的行为。 打开注册是限制最少的注册配置，其中门户允许用户帐户通过只提供用户标识来注册。 其他配置可能要求用户提供邀请代码或有效的电子邮件地址以便向门户注册。 不管注册配置如何，本地和外部帐户都在注册工作流中同等地加入。 也就是说，用户可以选择要注册的帐户类型。

## <a name="open-registration"></a>打开注册

注册过程中，用户可以选择创建本地帐户（提供用户名和密码），也可以从标识提供者列表中选择外部标识。 如果选择了外部标识，则用户需要通过所选的标识提供者登录，以证明他们拥有外部帐户。 在任一情况下，都会立即注册用户并通过门户进行身份验证。 注册时，将在 Common Data Service 环境中创建新的联系人记录。

启用打开注册后，用户无需提供邀请代码即可完成注册过程。

### <a name="see-also"></a>另请参阅

[设置门户的身份验证标识](set-authentication-identity.md)  
