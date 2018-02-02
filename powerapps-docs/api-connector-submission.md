---
title: "提交 API 连接器以供验证 | Microsoft 文档"
description: "经过验证的连接器可供 Microsoft Flow、PowerApps 和逻辑应用的所有用户使用。"
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
ms.openlocfilehash: 265fde7b8ce5d5521c53af35a2274409523282fe
ms.sourcegitcommit: 68eee592c351688e5d0bd458f33a70be507fa53f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2018
---
# <a name="submit-for-certification-as-an-api-connector-powerapps"></a>提交 API 连接器以供验证 (PowerApps)
作为第三方验证流程中的一个环节，我们会先评审你的连接器，然后再进行发布。 经过验证的连接器可供 Microsoft Flow、PowerApps 和逻辑应用的所有用户使用。 下面介绍了验证条件和步骤。

## <a name="criteria"></a>条件
| 功能 | 详细信息 | 必需或推荐 |
| --- | --- | --- |
| 服务型软件 (SaaS) 业务应用 |非常适用于 Microsoft Flow、PowerApps 和逻辑应用的业务用户情境 |需要 |
| 身份验证类型 |API 必须支持 OAuth2、API 密钥或基本身份验证 |需要 |
| 支持 |必须提供支持联系人，以便客户可以向其寻求帮助 |需要 |
| 可用性/运行时间 |应用的运行时间至少应为 99.9% |推荐 |

## <a name="submitting-your-connector"></a>提交连接器
通过以下简单三步，即可针对 Microsoft Flow、PowerApps 和逻辑应用验证应用：

1. **提名**
   
   * [提交提名](https://go.microsoft.com/fwlink/?linkid=848754)
   * 你会收到双向保密协议和合作伙伴协议。 必须签署这些合同，才能继续操作。
   * 我们会检查你的应用是否符合这些条件。 一经批准，我们便会立即通知你，并随附新手入门说明。
2. **评审**
   
    向提名联系人提交以下信息，以供评审。 如果需要其他信息，我们会与你联系来获取更多详情。
   
   * 用于描述 API 的 OpenAPI 文件
   * icon.png 文件（位于 230 像素方形内的约 160 像素徽标，首选彩色背景白色徽标）
   * 十六进制的品牌颜色（与图标文件中的彩色背景相匹配）
   * 供验证时使用的测试帐户
   * 支持联系人
3. **发布**
   
    验证连接器的功能和内容后，我们便会发布连接器，以供跨所有产品和区域进行部署。 
   
    默认情况下，所有连接器均发布为“高级”。 如果应用是在 Azure 上生成的，可以申请将连接器列为面向 Office 365 企业版计划所有用户的“标准”连接器。 请咨询你的提名联系人，了解更多详细信息。

