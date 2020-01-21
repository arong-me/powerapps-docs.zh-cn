---
title: API 限制概述 (Common Data Service) | Microsoft Docs
description: 了解 Common Data Service API 请求的限制。
ms.custom: ''
ms.date: 12/08/2019
ms.reviewer: kvivek
ms.service: powerapps
ms.topic: article
author: JimDaly
ms.author: jdaly
manager: ryjones
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: aee2a6b256c991c178506c68a38f4821c341b1b5
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "2909489"
---
# <a name="common-data-service-api-limits-overview"></a>Common Data Service API 限制概述

Common Data Service API 限制有助于确保服务级别、可用性和质量。 Common Data Service API 限制是 Power Platform 请求限制和分配的组成部分。 此主题介绍适用于 Dynamics 365 中的模型驱动应用（如 Dynamics 365 Sales 和 Dynamics 365 Customer Service）的 Common Data Service、Power Apps 和连接到 Dynamics 365 中的 Common Data Service/模型驱动应用的 Power Automate 特有的限制。 

有关 Power Platform 内所有区域的限制的信息，请参阅 [Power Platform 请求限制和分配](/power-platform/admin/api-request-limits-allocations)。

适用于 Common Data Service 的限制有两类：*权利*和*服务保护*限制。

## <a name="entitlement-limits"></a>权利限制

这些限制表示用户每天有权创建的请求数量。 分配的限制取决于分配给每位用户的许可证类型。

如果任何用户超出其请求权利，管理员将接到通知，并且可以为该用户分配 Power Apps 和 Power Automate 请求容量。 此时不阻止用户对偶然超额和合理超额使用应用。

对于 Common Data Service，API 请求中包含与实体记录交互的所有数据操作（在这些操作中创建、检索、更新或删除 (CRUD) 记录）。 包括*共享*和*分配*等特殊操作，因为这些操作被视为更新。 这些请求可以来自任何客户端或应用程序，并使用任何终结点。 包括但不限于插件、异步工作流、自定义控件和 $batch (ExecuteMultiple) 操作执行的操作。 不包含一小组系统内部操作，如登录、注销和系统元数据操作。

> [!IMPORTANT]
> Power Platform API 请求分配包括使用 Power Automate、AI Builder 和连接器 API。 通过连接器建立并生成 Common Data Service 请求的所有请求代表 1 个 Power Platform 请求。

有关这些权利限制的详细信息，请参阅[基于许可证的 Microsoft Power Platform 请求分配](/power-platform/admin/api-request-limits-allocations#microsoft-power-platform-requests-allocations-based-on-licenses)。

有关查看和分配容量附加产品的信息，请参阅[容量附加产品](/power-platform/admin/capacity-add-on)。

有关购买单个容量附加产品的信息，请参阅 [Power Apps 和 Power Automate 许可指南](https://go.microsoft.com/fwlink/?linkid=2085130)。 
<!-- There should be some help about purchasing these through the Portal -->


## <a name="service-protection-limits"></a>服务保护限制

为了保证所有人一致的可用性和性能，我们对 API 与 Common Data Service 如何结合使用实施一些限制。 服务保护 API 限制有助于基于资源限制确保运行应用程序的用户不会影响彼此。 这些限制不会影响平台的正常用户。 只有执行大量 API 请求的应用程序可能会受到影响。 这些限制将帮助提供一定程度的保护，防止请求卷出现威胁 Common Data Service 平台可用性和性能特性的任意和意想不到的激增。

我们限制每个用户帐户的并行连接数量、每个连接的 API 请求数量和可用于每个连接的执行时间量。 它们在五分钟滑动窗口内评估。 如果超出其中一个限制，平台将引发异常。

> [!NOTE]
> 服务保护限制适用于所有请求，不适用于对实体执行且占用权利限制的 CRUD 操作。
> 
> 由于插件和自定义工作流活动独立于已登录用户在服务器上执行，所以不对通过插件代码进行的 API 调用应用服务保护 API 限制。

由于通常只有执行大量数据操作的应用程序才会遇到服务保护限制，所以建议生成这些应用程序的开发人员在返回了这些异常时一段时间后对重试操作应用模式。 这样，应用程序就可以响应服务发送的异常和减少请求的总数，并达到最高的吞吐量。

有关可返回的特定错误和开发人员如何应用模式以响应这些错误的信息，请参阅[服务保护 API 限制](../../developer/common-data-service/api-limits.md)。


### <a name="see-also"></a>另请参阅

[管理 Power Platform / 许可和许可证管理 / 请求限制和分配](/power-platform/admin/api-request-limits-allocations)<br />
[管理员 / 使用代码处理数据 / 服务保护 API 限制](../../developer/common-data-service/api-limits.md)

