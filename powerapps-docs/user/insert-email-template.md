---
title: 在模型驱动应用中撰写电子邮件时插入电子邮件模板 |MicrosoftDocs
description: 撰写电子邮件时插入预设格式的电子邮件。
ms.date: 04/09/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: sbmjais
ms.author: shjais
manager: shujoshi
ms.openlocfilehash: 8f5b607375cccd03b3bcea2bd5d50664e7033ae4
ms.sourcegitcommit: 2484ebce6563cfd1c849e1e2f66dd2d29fdb7b64
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/10/2020
ms.locfileid: "81007976"
---
# <a name="insert-an-email-template"></a>插入电子邮件模板

你可以使用电子邮件模板（一种预设格式的电子邮件）快速创建和发送电子邮件。 可以在撰写电子邮件时通过选择命令行上的“插入模板”来插入模板  。 可用模板的列表显示在“电子邮件模板”窗口中  。 “最近使用的模板”部分会显示四个最近使用过的模板  。 “所有模板”部分会按字母顺序显示所有立即可用的电子邮件模板（全局和特定于实体）的列表  。 全局模板显示为“用户”类型。 如果创建了自定义电子邮件模板，可在此处查看。 有关创建自定义电子邮件模板的信息，请参阅 [创建电子邮件模板](https://docs.microsoft.com/power-platform/admin/create-templates-email)。

可以通过选择“语言”列表中的一种语言来查看特定语言的模板  。 可以搜索模板，也可以浏览列表然后再进行选择。 选择电子邮件模板时，窗口右侧会显示预览。 预览会显示内容，以便选择最符合需要的模板。 插入电子邮件模板后，可以根据需要修改内容，然后发送电子邮件。

> [!NOTE]
> 搜索不支持正则表达式，仅支持模板名称。

**插入电子邮件模板**

1.  在电子邮件编辑器中，选择命令栏上的“插入模板”  。

     > [!div class="mx-imgBorder"]
     > ![“插入模板”按钮](media/insert-email-template-button.png "“插入模板”按钮") 

    “电子邮件模板”窗口会打开  。

2.  要查看各种区域设置的模板，请从“语言”列表中选择一种语言  。 模板按所选语言加载。    

3.  浏览所需模板。 选择模板，然后预览模板内容。

4.  （可选）你可以选择模板名称上的向下箭头，查看其内容说明。

5.  选择“应用模板”，将内容插入电子邮件  。

     > [!div class="mx-imgBorder"]
     > ![“电子邮件模板”窗口](media/email-templates-window.png "“电子邮件模板”窗口")

如果尝试在屏幕较小的设备上插入电子邮件模板，则只能看到用于搜索和选择模板的选项。

> [!div class="mx-imgBorder"]
> ![搜索模板](media/search-template.png "搜索模板") 

### <a name="see-also"></a>另请参阅

[设置增强的电子邮件](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[使用增强的电子邮件体验撰写和发送电子邮件](enhanced-email.md)
