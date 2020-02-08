---
title: 预览版在模型驱动应用中使用增强的电子邮件体验发送电子邮件 |MicrosoftDocs
description: 使用增强的电子邮件体验来撰写电子邮件，而无需离开正在处理的内容。
ms.date: 02/03/2020
ms.service:
- dynamics-365-sales
ms.topic: article
author: shubhadaj
ms.author: shujoshi
manager: annbe
ms.openlocfilehash: 6f3c603284e5f5d53380f5caa932cafac11e2d7a
ms.sourcegitcommit: 68a31e3fa4d1635ccf4cd8bd9da5fba1bfecefa4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051927"
---
# <a name="preview-send-email-using-the-enhanced-email-experience"></a>预览：使用增强的电子邮件体验发送电子邮件

使用增强的电子邮件体验发送电子邮件是一项早期访问功能。 你可以提前选择在你的环境中启用这些功能。 这样，你就可以测试这些功能，然后在你的环境中采用它们。 有关如何启用这些功能的信息，请参阅[选择加入 2020 release wave 1 更新](https://docs.microsoft.com/power-platform/admin/opt-in-early-access-updates)。

模型驱动应用中增强的电子邮件体验允许您撰写电子邮件，而无需离开正在处理的记录。 利用增强的电子邮件体验，你可以：

- 导航到不同的页面，而不会丢失电子邮件内容。
- 最小化电子邮件窗口以返回到你正在处理的记录。
- 展开电子邮件编辑器弹出窗口，查看更多电子邮件选项。
- 同时打开三个电子邮件撰写弹出窗口。
- 搜索并将预定义的模板应用于要撰写的电子邮件。
- 将附件插入电子邮件。


> [!IMPORTANT]
> - 系统管理员必须先启用增强的电子邮件体验，然后才能使用。
> - [!INCLUDE[cc_preview_features_definition](../includes/cc-preview-features-definition.md)]  
> - [!INCLUDE[cc_preview_features_expect_changes](../includes/cc-preview-features-expect-changes.md)]
> - [!INCLUDE[cc-preview-features-no-ms-support](../includes/cc-preview-features-no-ms-support.md)]

使用增强的体验撰写电子邮件：

1. 在记录（如 "帐户" 或 "联系人"）的 "**时间线**" 部分中，**选择 "** **+** "，然后在 "**活动**"

   此时将打开一个新的电子邮件弹出窗口。 

   > [!div class="mx-imgBorder"]
   > ![增强的电子邮件弹出窗口](media/enhanced-email-pop-up.png "增强的电子邮件弹出窗口")

   "**从**" 和 "**到**" 字段基于原始记录的用户和帐户和联系人自动填充。

2. 从头开始编写电子邮件，或者选择 "**插入模板**" 以搜索和应用模板。 有关插入电子邮件模板的详细信息，请参阅[插入电子邮件模板](insert-email-template.md)。

3. 如果要添加附件，请选择**附加文件**。

4. 选择 "**插入签名**" 搜索并添加签名。

5. 完成后，选择 "**发送**"。 

> [!IMPORTANT]
> - 增强的电子邮件体验仅适用于从模型驱动应用的**时间线**部分创建的电子邮件活动。 
> - 仅当屏幕大小的高度和宽度至少为 400 x 650 像素或更大时，"增强型电子邮件" 弹出窗口才会打开。 如果较低，你将转到标准表单，而不是增强的电子邮件体验。 

### <a name="see-also"></a>另请参阅

[设置增强型电子邮件](https://docs.microsoft.com/power-platform/admin/system-settings-dialog-box-email-tab)<br>
[插入电子邮件模板](insert-email-template.md)
