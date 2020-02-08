---
title: 在模型驱动的应用中撰写电子邮件时插入电子邮件模板 |MicrosoftDocs
description: 撰写电子邮件时插入预设格式的电子邮件。
ms.date: 02/03/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: sbmjais
ms.author: shjais
manager: shujoshi
ms.openlocfilehash: abbef00f3b93809dadf617c4180b52a1372e625a
ms.sourcegitcommit: 68a31e3fa4d1635ccf4cd8bd9da5fba1bfecefa4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051835"
---
# <a name="preview-insert-an-email-template"></a>预览：插入电子邮件模板

插入电子邮件模板是一项早期访问功能。 你可以提前选择在你的环境中启用这些功能。 这样，你就可以测试这些功能，然后在你的环境中采用它们。 有关如何启用这些功能的信息，请参阅[选择加入 2020 release wave 1 更新](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates)。

你可以使用电子邮件模板（一种预设格式的电子邮件）快速创建和发送电子邮件。 可以通过在命令栏上选择 "**插入模板**" 来插入模板，同时编写电子邮件。 可用模板的列表显示在 "**电子邮件模板**" 窗口中。 在 "**最近使用**" 部分中，会显示四个最近使用的模板。 "**所有模板**" 部分以字母顺序显示所有现成电子邮件模板的列表（全局和实体特定）。 全局模板显示为 "用户" 类型。 如果已创建自定义电子邮件模板，还可以在此处查看。 有关创建自定义电子邮件模板的信息，请参阅[创建电子邮件模板](https://docs.microsoft.com/power-platform/admin/create-templates-email)。

您可以通过从 "**语言**" 列表中选择一种语言来查看特定语言的模板。 可以搜索模板，也可以浏览列表并选择它。 选择电子邮件模板时，预览将显示在窗口的右侧。 预览会显示内容，以便选择最能满足需要的模板。 插入电子邮件模板之后，可以根据需要修改内容，然后发送电子邮件。

> [!NOTE]
> 搜索不支持正则表达式，它仅适用于模板名称。

**插入电子邮件模板**

1.  在电子邮件编辑器的命令栏中选择 "**插入模板**"。

     > [!div class="mx-imgBorder"]
     > !["插入模板" 按钮](media/insert-email-template-button.png ""插入模板" 按钮") 

    此时将打开 "**电子邮件模板**" 窗口。

2.  若要查看不同区域设置的模板，请从 "**语言**" 列表中选择一种语言。 模板按所选语言加载。    

3.  浏览所需的模板。 选择模板，预览模板的内容。

4.  （可选）可以选择模板名称上的向下箭头，以查看其内容的说明。

5.  选择 "**应用模板**" 以在电子邮件中插入内容。

     > [!div class="mx-imgBorder"]
     > ![电子邮件模板窗口](media/email-templates-window.png "电子邮件模板窗口")

如果尝试在屏幕大小较小的设备上插入电子邮件模板，则只能看到用于搜索和选择模板的选项。

> [!div class="mx-imgBorder"]
> ![搜索模板](media/search-template.png "搜索模板") 

### <a name="see-also"></a>另请参阅

[设置增强型电子邮件](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[使用增强的电子邮件体验撰写和发送电子邮件](enhanced-email.md)
