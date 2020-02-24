---
title: 配置门户身份验证 | MicrosoftDocs
description: 了解如何为门户配置身份验证。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/18/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: acae3e962ed23e9cdff9cf74c1b6c5b7706c23be
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979149"
---
# <a name="configure-portal-authentication"></a>配置门户身份验证

在门户应用程序中，已通过身份验证的门户用户与联系人或系统用户关联。 默认门户配置基于联系人。 若要登录，联系人必须已配置适当的 Web 身份验证信息。 门户用户必须分配到 Web 角色，才能获得超越尚未通过身份验证的用户的权限。 若要配置 Web 角色的权限，请配置其网页访问和网站访问控制规则。

最新的门户身份验证体验允许门户用户使用其所选的基于本地联系人成员资格提供程序的帐户或基于 [ASP.NET Identity](https://www.asp.net/identity) 的外部帐户进行登录 。   

- **本地身份验证**：本地身份验证是使用 Common Data Service 环境的联系人记录进行身份验证的常见的基于表单的身份验证。 若要构建自定义身份验证体验，开发人员可以使用 ASP.Net 标识 API 创建自定义登录页和工具。
- **外部身份验证：** 外部身份验证由 ASP.NET Identity API 提供。 在这种情况下，帐户凭据和密码管理由第三方身份提供程序处理。 这包括基于 OpenID 的提供程序（例如 Yahoo!） 和基于 Google 和 OAuth 2.0 的提供程序（例如 Twitter、Facebook 和 [!INCLUDE[cc-microsoft](../../../includes/cc-microsoft.md)]）。 用户可通过选择外部身份登录门户，以注册到该门户。 注册后，外部身份便可与本地帐户访问相同功能。 

本地和外部帐户注册均可利用邀请代码注册以及电子邮件确认工作流。 此外，门户管理员可以选择通过门户网站设置启用或禁用身份验证选项的任意组合。

> [!NOTE]
> 门户用户必须具有唯一的电子邮件地址。 如果两个或多个联系人记录（包括已停用的联系人记录）具有相同的电子邮件地址，则联系人将无法在门户上进行身份验证。

## <a name="account-sign-up-registration"></a>帐户注册（注册）

门户管理员拥有几个选项来控制帐户注册行为。 开放式注册是限制最少的注册配置，在此情况下，门户允许用户帐户只需提供用户标识便可注册。 替代配置可能需要用户提供邀请代码或有效的电子邮件地址来注册门户。 无论注册配置如何，本地和外部帐户均可同等地加入注册工作流。 即，用户可以选择希望注册的帐户类型。

## <a name="open-registration"></a>开放式注册

在注册期间，用户可以选择创建本地帐户（提供用户名和密码）或从身份提供程序列表中选择外部身份。 如果选择外部身份，则用户需要通过所选身份提供程序登录，以证明他们拥有外部帐户。 在任一情况下，用户均可使用门户立即注册并进行身份验证。 注册时，将在 Common Data Service 环境中创建新联系人记录。

启用开放式注册时，用户无需提供邀请代码来完成注册流程。

### <a name="see-also"></a>另请参阅

[设置门户的身份验证标识](set-authentication-identity.md)  
