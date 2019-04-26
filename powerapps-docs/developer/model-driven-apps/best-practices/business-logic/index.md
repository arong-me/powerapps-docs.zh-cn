---
title: 开发人员：针对模型驱动应用的客户端脚本编写指南和最佳做法 | Microsoft Docs
description: PowerApps 中针对模型驱动应用开发人员的客户端脚本编写指南和最佳做法。
services: ''
suite: powerapps
documentationcenter: na
author: jowells
manager: austinj
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/12/2018
ms.author: jowells
search.audienceType:
- developer
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: e2b43178882cb66abba2305f65f78855915591ed
ms.sourcegitcommit: 4ed29d83e90a2ecbb2f5e9ec5578e47a293a55ab
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "63317688"
---
# <a name="best-practices-and-guidance-of-client-side-scripting-for-model-driven-apps"></a>针对模型驱动应用的客户端脚本编写指南和最佳做法

下表中包含针对模型驱动应用客户端脚本编写的所有指南和最佳做法。

|最佳做法  |描述  |
|---------|---------|
|[避免使用 window.top](avoid-window-top.md)     |介绍如何避免与在 JavaScript 自定义中使用 window.top 相关联的脚本错误和不当应用程序行为。         |
|[建议在以编程方式打开实体窗体或视图时禁用 NavBar](consider-disabling-navbar-programmatically-opening-entity-forms-views.md)|如果导航栏 (NavBar) 已启用，使用 URL 打开实体窗体或视图可能会导致高延迟网络上的客户端性能变慢。|
|[最佳做法：模型驱动应用中的客户端脚本编写](../../clientapi/client-scripting-best-practices.md)     |一些你可在为模型驱动应用编写 JavaScript 代码时参考的最佳做法提示。         |
|[与 HTTP 和 HTTPS 资源异步交互](interact-http-https-resources-asynchronously.md)     |在为模型驱动应用编写 JavaScript 客户端扩展时，应与 HTTP 和 HTTPS 资源异步交互。         |
|[删除已停用或已禁用的自定义项](remove-deactivated-disabled-configurations.md)     |应从解决方案中删除已禁用或已禁用的自定义项，从而提升解决方案管理效果并减少用户使用或管理过期组件的风险。         |

# <a name="see-also"></a>另请参阅
[通过客户端脚本编写来应用业务逻辑](../../client-scripting.md) <br />
 