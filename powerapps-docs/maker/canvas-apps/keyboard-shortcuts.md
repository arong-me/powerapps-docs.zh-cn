---
title: 画布应用的键盘快捷方式 |Microsoft Docs
description: 画布应用的键盘快捷方式
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: ''
ms.date: 02/09/2020
ms.author: tapanm
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 6c6f033027fb9ce29ba443efab2b5c14ec5ea013
ms.sourcegitcommit: ee1960fe32136a621e653d6ff2f13d87017830a2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/11/2020
ms.locfileid: "77145367"
---
# <a name="keyboard-shortcuts-for-canvas-apps"></a>画布应用的键盘快捷方式

> [!NOTE]
> 快捷方式可能因键盘布局而异。

## <a name="file"></a>文件

| 快捷方式 | 操作 |
|--|--|
| Ctrl + O （或 Alt + F） | 打开文件。 |
| Ctrl + Shift + S （或 Alt + P） | 使用其他名称保存应用。 |
| Ctrl+S | 用相同的名称或首次保存应用。 |
| F12 | 下载应用文件（. project-requests-app.msapp）。 |
| Alt+F | 打开 "**文件**" 菜单。 |

## <a name="ribbon"></a>功能区

| 快捷方式 | 操作 |
|--|--|
| 输入 | 运行所选的命令。 |
| Tab | 在所选选项卡上的命令之间移动，然后在下一个选项卡之间移动。 |
| Ctrl+F6 | 导航到下一个路标。 |
| Ctrl + Shift + F6 | 导航到上一个路标。 |
| Alt + I | 选择 "**插入**" 选项卡。 |

## <a name="editing"></a>编辑

| 快捷方式 | 操作 |
|--|--|
| Ctrl + A | 全选。 |
| Ctrl+X | 剪贴. |
| Ctrl+C | 复制。 |
| Ctrl+V | 粘贴。 |
| Ctrl+Z | Undo 命令。 |
| Ctrl+Y | Redo 命令。 |
| Ctrl+M | 添加一个屏幕。 |
| Ctrl + = 或 Ctrl + Shift + = | 放大。 |
| Ctrl +-或 Ctrl + Shift +- | 缩小。 |
| Ctrl + 0 | 使画布适合页面。 |
| Shift + Enter | 在公式中换行。 |

## <a name="preview"></a>预览

| 快捷方式 | 操作 |
|--|--|
| F5 | 打开预览模式。 |
| Esc | 关闭预览模式、对话框或弹出窗口。|

## <a name="canvas"></a>画布

| 快捷方式 | 操作 |
|--|--|
| Tab | 选择下一个控件。 |
| 按住 Ctrl 并单击或 Shift 并单击 | 同时选择多个对象。 |
| 向右键 | 向右微移选定的控件。 |
| 向左箭头 | 将所选控件向左移动。 |
| 向上键 | 向上微移选定的控件。 |
| 向下键 | 向下微移选定的控件。 |

## <a name="tree-view"></a>树视图

> [!NOTE]
> 这些快捷键要求 "**树视图**" 窗格具有焦点。

| 快捷方式 | 操作 |
|--|--|
| F2 | 重命名控件。 |
| Esc | 取消重命名控件。 |
| Ctrl+G | 对控件进行分组/取消分组。 |
| Ctrl +] | 使控件向前移动。 |
| Ctrl + [ | 向后发送控件。 |
| Ctrl + Shift +] | 置于顶层。 |
| Ctrl + Shift + [ | 置于底层。 |

## <a name="resize"></a>调节

| 快捷方式 | 操作 |
|--|--|
| Shift + 向左键 | 减小宽度。 |
| Ctrl + Shift + 向左键 | 稍微减小宽度。 |
| Shift + 向下键 | 减小高度。 |
| Ctrl + Shift + 向下键 | 稍微降低高度。 |
| Shift + 向右键 | 增加宽度。 |
| Ctrl + Shift + 向右键 | 稍微增加宽度。 |
| Shift + 向上键 | 增加高度。 |
| Ctrl + Shift + 向上键 | 稍微增加高度。 |

## <a name="text-format"></a>文本格式

| 快捷方式 | 操作 |
|--|--|
| Ctrl + B  | 循环级别为粗体。 |
| Ctrl+I | 打开或关闭斜体。 |
| Ctrl+U | 添加或删除下划线。 |

## <a name="alternate-behavior"></a>备用行为

| 快捷方式 | 操作 |
|--|--|
| Alt 或 Ctrl + Shift | 1. 选择控件之前，隐藏设计元素，以便与应用程序的用户进行交互。<br>2. 启动控件的大小调整或重定位后，按下这些键将覆盖所有的对齐点。 |

与 Excel 电子表格一样，画布应用程序处于活动和运行（即使正在编辑它们）。  无需更改为预览模式便可执行应用程序，使编辑和测试循环的速度更快。  但这会带来一个问题：我们如何区分选择按钮控件，以便可以通过选择按钮控件调整其大小，以在应用程序中执行逻辑。

处于设计模式时，默认情况下，选择对象进行编辑：移动、重设大小、更改属性，并以其他方式配置对象。  此默认值可通过*在启动所*选内容时按住 Alt 或 Ctrl + Shift 键进行重写，以将所选内容视为应用程序的用户完成。  

在下面的动画中，首先选择了一个按钮控件进行编辑。  装饰器出现在控件的周围，编辑栏会显示**OnSelect**属性，可以进行编辑。  然后释放该按钮。  *使用 Alt 键先*按下，按钮控件再次被选中，但此时将计算**OnSelect**属性并显示通知，就像在正在运行的应用程序中选择了该按钮一样。  

![动画显示：按住 alt 键的同时选择按钮控件](media/keyboard-shortcuts/alt-select.gif)

选择控件*后*，还可以使用 Alt 键来覆盖用于移动和调整大小的对齐点。  下一个动画显示 "[**编辑窗体**](controls/control-form-detail.md)" 控件内数据卡的大小调整。  最初，大小限制仅限于特定的对齐点。  稍后，如果*不释放 mouses 按钮*，则除了鼠标按钮外，还会按 Alt 键。 添加 Alt 键将覆盖对齐点，并且可以用鼠标获得任何宽度。 

![显示将 alt 键添加到数据卡的大小的效果的动画](media/keyboard-shortcuts/alt-fine-control.gif)

## <a name="other"></a>其他

| 快捷方式 | 操作 |
|--|--|
| F1 | 打开文档。 |
| Shift+F10 | 打开中的快捷菜单，例如 "**树视图**"。 |


 