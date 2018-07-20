---
title: RTF 编辑器控件：参考 | Microsoft Docs
description: 有关 RTF 编辑器控件的信息（包括属性和示例）
author: fikaradz
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: anneta
ms.date: 05/24/2018
ms.author: fikaradz
ms.openlocfilehash: 604b48a70f54a011e803342191e51dda12cbca3a
ms.sourcegitcommit: dfa0e1a7981814e15e6ca4720e2a5f930e859db1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/13/2018
ms.locfileid: "39016136"
---
# <a name="rich-text-editor-control-experimental-in-powerapps"></a>PowerApps 中的 RTF 编辑器控件（实验性）
允许最终用户在 WYSIWYG 编辑区域中设置文本格式的实验性控件。  输出格式为 HTML。

## <a name="description"></a>描述
“RTF 编辑器”控件为应用用户提供用于设置文本格式的 WYSIWYG 编辑区域。  控件的输入和输出格式为 HTML。

控件允许将复制的格式文本（例如， 从 Web 浏览器或 Word 中复制的格式文本）粘贴到控件。  

控件的预期用途是设置文本格式，但不保证保留输入 HTML 的完整性。  编辑器会删除所有脚本、样式、对象和其他可能有影响的标记。  这意味着，如果格式文本是在 PowerApps 外部创建的，则该文本看起来可能会与在创建它的产品中所有不同。

当前支持的功能包括：
- 粗体、斜体、下划线
- 文本颜色、突出显示颜色
- 文本大小
- 编号列表、项目符号列表
- 超链接
- 清除格式设置

若要使用窗体中的控件，选择“编辑多行文本”卡，并通过插入 RTE 控件自定义此卡。

## <a name="limitations"></a>限制
由于以下临时限制，控件的当前版本为实验性版本：
- 控件具有用于设置文本格式的有限功能。  

- 此控件主要用于大屏幕上的浏览器中。  在手机上使用此控件的体验可能不佳。

- 使用 Windows Studio 或 Microsoft Edge 浏览器时，创作体验中的已知问题。  当前建议在 Chrome 中使用 Web studio。


## <a name="key-properties"></a>关键属性
**[默认](properties-core.md)** - 编辑器中显示的初始文本值的输入属性。

**HtmlText** - 所生成 HTML 格式格式文本的输出属性。



## <a name="additional-properties"></a>其他属性
**[AccessibleLabel](properties-accessibility.md)** – 屏幕阅读器标签。 应描述附件的用途。

[DisplayMode](properties-core.md) – 控件是允许添加和删除文件 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

[Visible](properties-core.md) – 控件可见还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

[Y](properties-size-location.md) – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。