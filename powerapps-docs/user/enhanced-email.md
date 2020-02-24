---
title: 预览：在模型驱动应用中使用增强的电子邮件体验发送电子邮件 | Microsoft Docs
description: 使用增强的电子邮件体验，无需离开正在处理的内容，即可撰写电子邮件。
ms.date: 02/03/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: shubhadaj
ms.author: shujoshi
manager: annbe
ms.openlocfilehash: 546f94f67608ab735d2c2eb6bb39f105335549f7
ms.sourcegitcommit: eda3382ade50efe66611518c8f36e3a2ada7a91d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/15/2020
ms.locfileid: "77282583"
---
# <a name="preview-send-email-using-the-enhanced-email-experience"></a>预览：使用增强的电子邮件体验发送电子邮件

使用增强的电子邮件体验发送电子邮件是一项抢先体验功能。 你可以提前选择加入，以在环境中启用这些功能。 这样即可测试这些功能，然后在环境中采用。 如需了解如何启用这些功能的信息，请参阅[选择加入 2020 版第 1 波更新](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates)。

通过模型驱动应用中增强的电子邮件体验，无需离开正在处理的记录即可撰写电子邮件。 使用增强的电子邮件体验，你可以：

- 导航到其他页面，而不会丢失电子邮件内容。
- 最小化电子邮件窗口以返回到正在处理的记录。
- 展开电子邮件编辑器弹出窗口，查看更多电子邮件选项。
- 同时打开三个电子邮件撰写弹出窗口。
- 搜索预定义的模板并将其应用于正在撰写的电子邮件。
- 将附件插入电子邮件。


> [!IMPORTANT]
> - 系统管理员必须先启用增强的电子邮件体验，然后用户才能使用这一功能。
> - [!INCLUDE[cc_preview_features_definition](../includes/cc-preview-features-definition.md)]  
> - [!INCLUDE[cc_preview_features_expect_changes](../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE[cc-preview-features-no-ms-support](../includes/cc-preview-features-no-ms-support.md)]

使用增强的体验撰写电子邮件：

1. 在记录（如“帐户”或“联系人”）的时间线部分中，选择“+”，然后在“活动”下，选择“电子邮件”     。

   此时将打开新的电子邮件弹出窗口。 

   > [!div class="mx-imgBorder"]
   > ![增强的电子邮件弹出窗口](media/enhanced-email-pop-up.png "增强的电子邮件弹出窗口")

   “发件人”和“收件人”字段根据原始记录的用户和帐户以及联系人自动填充   。

2. 从头开始撰写电子邮件，或者选择“插入模板”，搜索并应用模板  。 如需详细了解如何插入电子邮件模板，请参阅[插入电子邮件模板](insert-email-template.md)。

3. 如果要添加附件，请选择“附加文件”  。

4. 选择“插入签名”，搜索并添加签名  。

5. 完成此操作后，选择“发送”  。 

> [!IMPORTANT]
> - 增强的电子邮件体验仅适用于从模型驱动应用的“时间线”部分创建的电子邮件活动  。 
> - 仅当屏幕大小的高度和宽度不低于 400 x 650 像素时，增强的电子邮件弹出窗口才会打开。 如果低于这个标准，你将转到标准窗体，而不会转到增强的电子邮件体验。 

### <a name="see-also"></a>另请参阅

[设置增强的电子邮件](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[插入电子邮件模板](insert-email-template.md)
