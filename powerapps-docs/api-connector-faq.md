---
title: "API 连接器常见问题解答 | Microsoft 文档"
description: "查看有关要求、触发器和其他方面的常见问题解答。"
services: 
suite: powerapps
documentationcenter: na
author: asavaritayal
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/06/2017
ms.author: astay
ms.openlocfilehash: b945f2775e26327557255a75f18e87a638a9fe66
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="api-connector-faq-powerapps"></a>API 连接器 FAQ (PowerApps)
## <a name="requirements"></a>要求
**问：**如果我不是 ISV，能否仍生成连接器？

**答：**根据我们的要求，必须拥有基础服务或明确拥有使用 API 的权限，才能公开发布连接器。

**问：**能否在不使用 REST API 的情况下生成连接器？

**答：**不能。 你的服务必须支持稳定 HTTP REST API，才能生成 API 连接器。

**问：**支持哪些身份验证类型？

**答：**我们支持以下身份验证标准：

* OAuth2.0（包括 Azure Active Directory）
* API 密钥
* 基本身份验证

## <a name="triggers"></a>触发器
**问：**能否在不使用 webhook 的情况下生成触发器？ 

**答：**Microsoft Flow 和逻辑应用 API 连接器只允许生成基于 webhook 的触发器。 若要申请采用其他实现形式，请联系 [condevhelp@microsoft.com](mailto:condevhelp@microsoft.com)，并随附 API 的详细信息。

## <a name="miscellaneous"></a>其他
**问：**我的 API 使用动态主机。 如何在 OpenAPI 中实现此操作？

**答：**API 连接器功能不支持动态主机。 请使用静态主机进行开发和测试。 提交时，请就动态实现问题咨询你的 Microsoft 联系人。

**问：**是否支持 Postman 集合 V2？

**答：**否，暂不支持 Postman V2。

**问：**是否支持 OpenAPI 3.0？

**答：**否，目前仅支持 OpenAPI 2.0。

