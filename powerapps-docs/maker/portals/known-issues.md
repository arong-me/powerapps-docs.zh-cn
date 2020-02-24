---
title: Power Apps 门户中的已知问题 | Microsoft Docs
description: 了解 Power Apps 门户中的已知问题
author: tapanm-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 01/17/2020
ms.author: tapanm
ms.reviewer: ''
ms.openlocfilehash: 4c7f5aaa46acd255f15e0a040f44710a608d34a2
ms.sourcegitcommit: a0d069f63d2ce9496d578f81e65cd32bec2faa4d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2020
ms.locfileid: "2977345"
---
# <a name="known-issues"></a>已知问题


## <a name="general-issues"></a>常见问题

- 更新后的 Yahoo YDN OAuth 提供商终结点与 Power Apps 门户之间的现有兼容性问题导致用户暂时不可以通过 [Yahoo 身份提供程序](./configure/configure-oauth2-settings.md#yahoo-ydn-app-settings)的身份验证。

- 应用程序的**修改日期**可能不正确，因为这些应用程序是提前设置的应用程序，可能之前已经过设置。

- 随起点门户一起创建环境时，门户的负责人未正确显示。 其显示为“系统”。

- 如果重复使用最近删除的门户的 URL 创建新门户，运行时可能要经过一段时间的延迟才会进行设置。 这是因为仍在清除之前的资源，可能需要 30 分钟到 1 个小时，才能在 Azure 中设置新门户。 门户在此期间也将无法编辑，并且在 Studio 中启动进行编辑时可能会显示错误。

- 在 Power Apps 中切换环境时，**应用程序**或**最近应用程序**列表中可能不会立即显示环境内的门户。 特定是在与其租户不同的区域中创建的环境会发生这种情况。 解决方法是使用浏览器刷新，或等待一些时间，以便应用程序列表中显示门户。

- 如果从 Power Apps 门户管理中心重置门户时，在 Power Apps 主页中保持门户设置窗格处于打开状态，则由于门户不可用，用户将在门户设置窗格中看到“出错了”错误消息。

- 在某些情况下，当您创建门户时，样式无法正确地应用到门户，并且通过**浏览网站**打开时，显示的网站没有样式。 这种情况很少发生，可以通过从 Power Apps 门户管理中心重新启动门户来恢复样式。

## <a name="power-apps-portals-studio-issues"></a>Power Apps 门户 Studio 问题

- 如果门户的页面层次结构超过三个级别，则 Power Apps 门户 Studio 中不会显示第四个级别以后的页面。

- 仅当有专门为该文本定义的字体大小时，才会显示所选文本的字体大小。 如果它是标准 HTML 标记（如 p、H1、H2、H3 等）的一部分，Power Apps 门户 Studio 将不会显示字体大小。

- 采用了**带侧面导航的页面**模板的网页仅显示网页创建期间已存在的页面的链接。 可更新页面左侧的链接，方法是将页面模板更改为另一个模板，然后改回**带侧面导航的页面**。

- 如果删除网页，下次刷新区域之前，区域不反映更新后的菜单。

- 仅支持英语的颜色选取器及其关联字符串。

- 员工自助服务门户中的一些模板页无法呈现正确的导航痕迹。

- 一些 Power Apps 门户模板，尤其是绑定到 Dynamics 365 中模型驱动应用的模板，没有按其页面层次结构设置的默认菜单项。 原因是在全部或少数网页中没有可用的页面顺序。 没有网页显示顺序的任何门户都会出现此问题。

- 当页面内容（页面副本）超过其限制 65536 个字符并且页面摘要超过其默认限制 2000 个字符时，将显示一条错误消息。

- 导航菜单仅在分辨率达最小宽度 1600px 的画布上可见。

- 在页面上上载的图像成为页面的子级。 如果删除页面，并在其他页面上使用该图像，则图像将不会在 Power Apps 门户 Studio 和网站上呈现。

- Power Apps 门户 Studio 当前不支持窗体呈现。 添加窗体时，您必须选择**浏览网站**才能打开网站并验证窗体。

- 在文本或部分背景上，如果将颜色更改为**无颜色**，Power Apps 门户 Studio 不会删除相关属性，例如背景色或字体颜色，而是将值设置为 null。

- 在以下情况下，Power Apps 门户 Studio 停止加载并显示“很抱歉，连接已断开”错误：
    - 如果门户的主页被删除或禁用。
    - 如果与主页或任何页面相关的页面模板被禁用或删除。

- Power Apps 门户 Studio 将无法加载未在 Common Data Service 中分配语言的那些内容片段的源代码。

- 在某些情况下，无论通过 Power Apps 门户 Studio 的 WYSIWYG 体验还是通过代码编辑器，对页眉和页脚的更改都不会立即反映出来。

- 如果在 Power Apps 门户 Studio 中为网页分配了搜索模板，它将显示一个带有加载程序的简单页面。 为了让此功能生效，您必须为该页面创建一个适当的站点标记。

- 一旦在 Power Apps 门户 Studio 中使用了新页面，默认 Studio 模板还将在页面模板中显示为选项。 另外，此模板仅以英语插入，并且不支持基于默认 Common Data Service 或门户语言的本地化。

- 不能通过 Power Apps 门户 Studio 配置作为日历控件或地图呈现的列表。

- 页面属性中的“部分 URL”字段不接受特殊字符，并且会中断画布中的呈现一段时间。 

- 在 CSS 文件名包含特殊字符或文件名中包含空格的情况下，上载 CSS 可能会失败。

- 未发布的网页不在 Power Apps 门户 Studio 的画布中呈现。

- 使用 Power Apps 门户 Studio 时，如果您的门户基本语言与浏览器的语言不同，则使用默认 Studio 模板创建的新网页将以浏览器语言而非门户语言插入虚拟内容。

- **主题**窗格中仅显示在根页面上应用的 CSS。 但是，如果您尝试上载与门户中可用的任何其他 CSS 文件同名的 CSS 文件，Power Apps 门户 Studio 会要求您替换该文件。

- Mac 操作系统中的 Safari 当前不支持 Power Apps 门户 Studio，并且存在以下问题：
    - 组件选择不正确，将鼠标悬停在组件上会提供错误的目标指示。
    - 两到三列的部分在 Power Apps 门户 Studio 中无法正确呈现，但在网站上可以正常工作。

