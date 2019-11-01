---
title: PowerApps 门户中的已知问题 | Microsoft Docs
description: 了解 PowerApps 门户中的已知问题
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: null
ms.date: 07/18/2019
ms.author: shjais
ms.reviewer: null
---

# <a name="known-issues"></a>已知问题

[!include[cc-beta-prerelease-disclaimer](../../includes/cc-beta-prerelease-disclaimer.md)]

## <a name="general-issues"></a>常见问题

- 应用程序的**修改日期**可能不正确，因为这些应用程序是提前设置的应用程序，可能之前已经过设置。

- 门户负责人错误显示。 其显示为“系统”。

- 如果重复使用最近删除的门户的 URL 创建新门户，运行时可能要经过一段时间的延迟才会进行设置。 这是因为仍在清除之前的资源，可能需要 30 分钟到 1 个小时，才能在 azure 中设置新门户。

- 在 PowerApps 中切换环境时，**应用程序**或**最近应用程序**列表中可能不会立即显示环境内的门户。 特定是在与其租户不同的区域中创建的环境会发生这种情况。 解决方法是使用浏览器刷新，或等待一些时间，以便应用程序列表中显示门户。

- 从 PowerApps 门户管理中心成功重置门户之后，将显示以下错误：“您尝试访问的门户不属于您当前登录的租户。 请注销，然后登录正确租户。” 可访问 PowerApps 主页并创建新门户。 

## <a name="portal-designer-issues"></a>门户设计器问题

-   在文本框中选择文本时，格式工具栏中不显示所选文本的字体大小。

- 节中列的边距与网站中显示的边距不同。 将根据节内的内容调整边距。

- 区域无法加载中文内容。

- 采用了**带侧面导航的页面**模板的网页仅显示网页创建期间已存在的页面的链接。 可更新页面左侧的链接，方法是将页面模板更改为另一个模板，然后改回**带侧面导航的页面**。

- 如果删除网页，下次刷新区域之前，区域不反映更新后的菜单。

- 从重写页面（门户设计器中不支持的页面）创建子页时，必须从属性窗格手动选择模板，才能呈现页面。

- 如果页面名称太长，无法在**页面**窗格中完全显示，则不显示**省略号**按钮 (...)。 必须右键单击页面名称，才可以看到页面选项。

- 如果已经在页面中添加了停用的内容片段，将在门户设计器中显示该内容片段。 但是，实际网站中将隐藏已停用内容片段。

- 一些组件的占位符（如 Web 链接、Power BI、图表等）不可编辑。 但是同样还是可以编辑文本。 将不保存对占位符进行的更改。

- 门户设计器中仅支持英语的信息和相关操作，如组件名称。

- 仅支持英语的颜色选取器及其关联字符串。

- 员工自助服务门户中的一些模板页无法呈现正确的导航痕迹。

- 一些 Dynamics 365 门户模板没有按照其页面层次结构应该具有的菜单项。 但是，如果创建新页面，将相应创建这些菜单项。