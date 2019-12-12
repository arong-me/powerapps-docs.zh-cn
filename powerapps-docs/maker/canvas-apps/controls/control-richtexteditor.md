---
title: RTF 编辑器控件：参考 | Microsoft Docs
description: 有关 RTF 编辑器控件的信息（包括属性和示例）
author: chmoncay
manager: kvivek
ms.service: powerapps
ms.topic: article
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 05/24/2018
ms.author: chmoncay
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 1c9bbfd724f588dce86c5ba2e620404f554d2bcd
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732086"
---
# <a name="rich-text-editor-control-in-power-apps"></a>Power Apps 中的富文本编辑器控件
允许最终用户设置所见即所得编辑区域内的文本格式。  输出格式为 HTML。

## <a name="description"></a>描述
“RTF 编辑器”控件为应用用户提供用于设置文本格式的 WYSIWYG 编辑区域。  控件的输入和输出格式为 HTML。

控件允许将复制的格式文本（例如， 从 Web 浏览器或 Word 中复制的格式文本）粘贴到控件。  

控件的预期用途是设置文本格式，但不保证保留输入 HTML 的完整性。  编辑器会删除所有脚本、样式、对象和其他可能有影响的标记。  这意味着，如果在 Power Apps 外部创建了丰富的文本，则该文本的外观可能与创建它的产品的外观不相同。

当前支持的功能包括：
- 粗体、斜体、下划线
- 文本颜色、突出显示颜色
- 文本大小
- 编号列表、项目符号列表
- 超链接
- 清除格式设置

若要使用窗体中的控件，选择“编辑多行文本”卡，并通过插入 RTE 控件自定义此卡。

## <a name="key-properties"></a>关键属性
**[默认](properties-core.md)** - 编辑器中显示的初始文本值的输入属性。

**HtmlText** - 所生成 HTML 格式格式文本的输出属性。


## <a name="additional-properties"></a>其他属性
**[AccessibleLabel](properties-accessibility.md)** – 屏幕阅读器标签。 应描述附件的用途。

[DisplayMode](properties-core.md) – 控件是允许添加和删除文件 (Edit)、仅显示数据 (View)，还是已禁用 (Disabled)。

**EnableSpellCheck** –是否启用浏览器拼写检查器。 请注意，此功能将仅以浏览器的默认语言提供拼写检查。  适用于 Windows 的 Power Apps 不支持此属性。

**[Height](properties-size-location.md)** – 控件上边缘和下边缘之间的距离。

**[TabIndex](properties-accessibility.md)** – 相对于其他控件的键盘导航顺序。

[Visible](properties-core.md) – 控件可见还是隐藏。

**[Width](properties-size-location.md)** – 控件左边缘和右边缘之间的距离。

[X](properties-size-location.md) – 控件左边缘与其父容器（如果没有父容器，则为屏幕）左边缘之间的距离。

[Y](properties-size-location.md) – 控件上边缘与其父容器（如果没有父容器，则为屏幕）上边缘之间的距离。


## <a name="accessibility-guidelines"></a>辅助功能准则
### <a name="screen-reader-support"></a>屏幕阅读器支持
* **[“AccessibleLabel”](properties-accessibility.md)** 必须存在。

### <a name="keyboard-support"></a>键盘支持
* **[“TabIndex”](properties-accessibility.md)** 必须为零或更大，以便键盘用户可以导航到它。

> [!TIP]
> 使用**Alt + 0**时，编辑器的重点是了解其他键盘快捷方式。
