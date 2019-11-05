---
title: 为门户配置重定向步骤类型 |MicrosoftDocs
description: 有关为门户添加和配置重定向步骤的说明。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 3cf76cccfd247bdcfb4ee32e99682d2b9e95e139
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73553500"
---
# <a name="add-a-redirect-step-type"></a>添加重定向步骤类型

重定向步骤类型允许将用户的浏览器会话重定向到门户中的另一页或外部 URL。 这适用于无缝定向流。

| 名称                                                            | 描述                                                                                                                                                                                  |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 外部 URL                                                    | 在成功设置重定向时要求。 指定指向 web 上的外部资源的 URL。                                                                                                       |
| 或网页                                                     | 在成功设置重定向时要求。 选择当前网站中的网页。                                                                                                             |
| 追加现有查询字符串                                    | 在成功设置重定向时要求。 选中后，将在重定向之前将现有查询字符串参数添加到目标 URL。                                                 |
| 将记录 ID 追加到查询字符串                                | 在成功设置重定向时要求。 选中时，创建的记录的 ID 将追加到正在重定向到的 URL 的查询字符串中。                                               |
| 记录 ID 查询字符串参数名称                           | 在成功设置重定向时要求。 要重定向到的 URL 的查询字符串中的 ID 参数的名称。                                                                        |
| 追加自定义查询字符串                                      | 在成功设置重定向时要求。 可追加到重定向 URL 的现有查询字符串的自定义字符串。                                                                  |
| 将属性值追加到查询字符串参数名称         | 在成功设置重定向时要求。 要给予参数的名称，该参数与附加到重定向 URL 的查询字符串的目标实体上的属性值关联。 |
| 将属性值追加到查询字符串-属性逻辑名称 | 在成功设置重定向时要求。 目标实体上的属性的逻辑名称，用于获取要追加到重定向 URL 的查询字符串的值。                            |

### <a name="see-also"></a>另请参阅

[配置门户](configure-portal.md)  
[定义实体窗体](entity-forms.md)  
[门户的 Web 窗体步骤](web-form-steps.md)  
[加载窗体/加载选项卡步骤类型](load-form-step.md)  
[条件步骤类型](add-conditional-step.md)  
[添加自定义 JavaScript](add-custom-javascript.md)  

