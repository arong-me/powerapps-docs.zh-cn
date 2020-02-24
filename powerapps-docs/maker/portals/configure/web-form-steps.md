---
title: 为门户配置 Web 窗体步骤 | MicrosoftDocs
description: 有关如何为门户中的 Web 窗体创建 Web 窗体步骤的说明。
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 11/04/2019
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 618a0d83fbdb851b7b30b46e021654b003b4d63b
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2980161"
---
# <a name="define-web-form-steps-for-portals"></a>定义门户的 Web 窗体步骤

Web 窗体步骤提供窗体的用户体验的流程逻辑，例如步骤和条件分支。 还提供了与窗体和其他行为的呈现相关的详细信息。

> [!NOTE]
> Web 窗体保留用户在 Web 窗体会话实体上的对象中进行访问的步骤的历史记录。 如果已修改 Web 窗体的步骤，则以前创建的历史记录数据现在可能已过时。 步骤发生更改时，推荐您删除所有 Web 窗体会话记录，以消除历史记录中的步骤顺序与当前顺序不符的情况。

每个 Web 窗体将在门户中显示一个或多个步骤。 这些步骤共享一些常见属性，如下所示。 每个步骤包含下一个步骤的指针（查找），最终步骤除外。 最终步骤没有下一步，因而是 Web 窗体的最后一个步骤（由于条件分支，可以存在多个最终步骤）

![创建 Web 窗体的步骤](../media/web-form-creation-steps.png "创建 Web 窗体的步骤")  

| 名称     | 说明                                    |
|----------|------------------------------------------------|
| 名称     | 用于引用的标题。                    |
| Web 窗体 | Web 窗体与当前步骤关联。 |
|Type|以下版本之一：<br>[加载窗体/加载选项卡步骤类型](load-form-step.md)：显示窗体的属性。 <ul><li>[加载窗体/加载选项卡步骤类型](load-form-step.md)：显示选项卡的属性。</li><li>[条件步骤类型](add-conditional-step.md)：显示用于指定条件分支将计算的表达式的属性。 </li><li>[重定向步骤类型](add-redirect-step.md)：显示适合配置网站重定向的设置。</li></ul><br>有关这些 Web 窗体步骤类型设置的更多详细信息，请参阅下述相应部分。<br>**注意**：第一步不能是“条件”类型。|
| 后续步骤                  | 紧跟当前步骤的步骤。 这对于单个步骤单个窗体为空白。                                                                                                            |
| 目标实体逻辑名称 | 与窗体关联的实体的逻辑名称。                                                                                                                                               |
| 允许回到上一步骤    | 指示用户是否可以选择在多步骤 Web 窗体中导航到上一步骤。 默认值为 true。 取消选中此项可阻止用户移到上一步骤。 |
||

### <a name="see-also"></a>另请参阅

[配置门户](configure-portal.md)  
[定义实体](entity-forms.md)  
[加载窗体/加载选项卡步骤类型](load-form-step.md)  
[重定向步骤类型](add-redirect-step.md)  
[条件步骤类型](add-conditional-step.md)  
[添加自定义 JavaScript](add-custom-javascript.md)  

