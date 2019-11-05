---
title: 为门户配置 web 窗体步骤 |MicrosoftDocs
description: 介绍如何在门户中创建 web 窗体的 web 窗体步骤。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: c81cddb771c98ccecf2be206ab45a8271ff3559d
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "73551223"
---
# <a name="define-web-form-steps-for-portals"></a>定义门户的 web 窗体步骤

Web 窗体步骤提供表单的用户体验（例如步骤和条件分支）的流逻辑。 它还提供了有关表单渲染和其他行为的详细信息。

> [!NOTE]
> Web 窗体保留用户在 Web 窗体会话实体上的对象中访问的步骤历史记录。 如果修改了 Web 窗体的步骤，则以前创建的历史记录数据现在可能已过时。 如果更改了任何步骤，则建议你删除所有 Web 窗体会话记录，以消除记录在历史记录和当前序列中的步骤顺序的不匹配。

门户中将显示每个 Web 窗体，其中包含一个或多个步骤。 这些步骤共享一些常见属性，如下所述。 每个步骤都包含指向下一步骤的指针（一个查找），但有一些终端步骤除外。 终端步骤没有下一次，因此是 Web 窗体的最后一步（由于条件分支，可能有多个终端步骤）

![创建 web 窗体的步骤](../media/web-form-creation-steps.png "创建 web 窗体的步骤")  

| 名称     | 描述                                    |
|----------|------------------------------------------------|
| 名称     | 用于引用的标题。                    |
| Web 窗体 | 与当前步骤关联的 Web 窗体。 |
|类型|拥有下列一种应用：<br>[加载窗体/加载选项卡步骤类型](load-form-step.md)：显示窗体的属性。 <ul><li>[加载窗体/加载选项卡步骤类型](load-form-step.md)：显示选项卡的属性。</li><li>[条件步骤类型](add-conditional-step.md)：显示用于指定要为条件分支计算的表达式的属性。 </li><li>[重定向步骤类型](add-redirect-step.md)：显示适用于配置网站重定向的设置。</li></ul><br>有关这些 web 窗体步骤类型的设置的更多详细信息，请参阅以下相应部分。<br>**注意**：第一步的类型不能是 "Condition"。|
| 下一步                  | 将遵循当前步骤的步骤。 对于单步单一窗体，此参数为空白。                                                                                                            |
| 目标实体逻辑名称 | 与窗体关联的实体的逻辑名称。                                                                                                                                               |
| 移动上一个允许的    | 指示是否向用户提供一个在多步骤 web 窗体中导航到上一步骤的选项。 默认值为 true。 取消选中此项可防止用户转到上一步。 |
||

### <a name="see-also"></a>另请参阅

[配置门户](configure-portal.md)  
[定义实体](entity-forms.md)  
[加载窗体/加载选项卡步骤类型](load-form-step.md)  
[重定向步骤类型](add-redirect-step.md)  
[条件步骤类型](add-conditional-step.md)  
[添加自定义 JavaScript](add-custom-javascript.md)  

