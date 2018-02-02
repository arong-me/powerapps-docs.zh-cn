---
title: "API 连接器概述 | Microsoft 文档"
description: "ISV 和 SaaS 服务所有者可以生成连接器，并提交给 Microsoft 进行验证。"
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
ms.openlocfilehash: 74bac3b0f5bad2b95ab9b6b312fc5209bf5da3a2
ms.sourcegitcommit: 68eee592c351688e5d0bd458f33a70be507fa53f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2018
---
# <a name="api-connector-overview-powerapps"></a>API 连接器概述 (PowerApps)
**API 连接器**是使用 REST API 的 OpenAPI (Swagger) 包装器，可方便基础服务与 [Microsoft Flow](https://flow.microsoft.com)、[PowerApps](https://powerapps.microsoft.com) 和[逻辑应用](https://docs.microsoft.com/azure/logic-apps/)进行通信。 这样一来，用户可以连接自己的帐户，并利用预生成的一组**触发器**和**操作**来生成应用和工作流。

作为**独立软件供应商 (ISV)** 或 **SaaS 服务所有者**，可以通过生成连接器为用户实现各种业务和高效工作情境。 连接器有助于跨越一组明确的集成，并扩大服务的覆盖面、公开范围和使用群。

## <a name="requirements"></a>要求
若要生成并提交连接器，你的服务必须满足以下要求：

* 非常适用于 Microsoft Flow、PowerApps 和逻辑应用的业务用户情境
* 具有稳定 REST API 的公开发布服务

## <a name="build-your-connector"></a>生成连接器
生成 API 连接器的第一步是生成功能完备的自定义连接器。 自定义连接器的运行方式与 API 连接器完全相同，不同之处在于前者仅限作者和作者租户内的特定用户使用。

连接器生成工作由多项步骤组成：

![API 连接器生成步骤](./media/api-connectors-overview/authoring-steps.png)

[详细了解](api-connector-dev.md)如何开发 API 连接器。

## <a name="submit-for-certification"></a>提交以供验证
生成连接器后，将其提交以供验证。 作为第三方验证流程中的一个环节，Microsoft 会先评审连接器，然后再进行发布。

此过程将验证连接器在 Microsoft Flow 和 PowerApps 中的功能，并检查技术和内容符合性。

[详细了解](api-connector-submission.md)如何提交连接器以供验证和发布。

## <a name="get-support"></a>获取支持
若要获取新手入门和开发支持，请发送电子邮件至 [condevhelp@microsoft.com](mailto:condevhelp@microsoft.com)。我们会不断监视和管理此帐户。 开发者查询和事件会被快速分配给相应的团队。

