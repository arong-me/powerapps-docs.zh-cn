---
title: 配置门户的重定向步骤类型 | MicrosoftDocs
description: 有关如何添加和配置门户的重定向步骤的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: e82d19a7adb43bcb8fddaeac88a5e238ee96eae1
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2979589"
---
# <a name="add-a-redirect-step-type"></a>添加重定向步骤类型

重定向步骤类型允许用户的浏览器会话重定向到门户中的其他页面或外部 URL。 这对无缝定向流非常有用。

| 客户                                                            | 说明                                                                                                                                                                                  |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 外部 URL                                                    | 需要对重定向进行操作成功设置。 指定 Web 中外部资源的 URL。                                                                                                       |
| 或网页                                                     | 需要对重定向进行操作成功设置。 从当前网站中选择网页。                                                                                                             |
| 追加现有查询字符串                                    | 需要对重定向进行操作成功设置。 选中后，现有查询字符串参数将在重定向之前添加到目标 URL。                                                 |
| 将记录 ID 追加到查询字符串                                | 需要对重定向进行操作成功设置。 选中后，创建的记录 ID 将追加到重定向到的 URL 的查询字符串。                                               |
| 记录 ID 查询字符串参数名称                           | 需要对重定向进行操作成功设置。 重定向到的 URL 的查询字符串中 ID 参数的名称。                                                                        |
| 追加自定义查询字符串                                      | 需要对重定向进行操作成功设置。 可追加到重定向 URL 的现有查询字符串的自定义字符串。                                                                  |
| 将属性值追加到查询字符串 - 参数名称         | 需要对重定向进行操作成功设置。 给予与目标实体中属性值相关的参数的名称，该实体追加到重定向 URL 的查询字符串。 |
| 向查询字符串追加属性值 - 属性逻辑名称 | 需要对重定向进行操作成功设置。 将值追加到重定向 URL 的查询字符串的目标实体中属性的逻辑名称。                            |

### <a name="see-also"></a>另请参阅

[配置门户](configure-portal.md)  
[定义实体窗体](entity-forms.md)  
[门户的 Web 窗体步骤](web-form-steps.md)  
[加载窗体/加载选项卡步骤类型](load-form-step.md)  
[条件步骤类型](add-conditional-step.md)  
[添加自定义 JavaScript](add-custom-javascript.md)  

