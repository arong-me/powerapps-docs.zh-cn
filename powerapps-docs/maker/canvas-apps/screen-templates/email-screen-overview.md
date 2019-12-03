---
title: 电子邮件-屏幕模板 |Microsoft Docs
description: 了解 canvas 应用的电子邮件屏幕模板的工作原理，并为自己的用例扩展屏幕
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/29/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: ff3e2db1c0d02fda91215ae0e5cc6dd4ae712dd9
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675102"
---
# <a name="overview-of-the-email-screen-template-for-canvas-apps"></a>用于画布应用的电子邮件屏幕模板概述

在画布应用中，添加一个电子邮件屏幕，该屏幕允许用户从其 Office 365 Outlook 帐户发送电子邮件。 用户也可以在组织中搜索收件人并添加外部电子邮件地址。 你可以添加图像附件支持、更改搜索库中显示的用户数据，以及进行其他自定义。

你还可以添加其他基于模板的屏幕，这些屏幕显示 Office 365 的不同数据，如用户的[日历](calendar-screen-overview.md)、组织中的[人员](people-screen-overview.md)，以及用户可能想要邀请参加会议的人员的[可用性](meeting-screen-overview.md)。

本概述介绍了以下内容：
> [!div class="checklist"]
> * 如何使用默认电子邮件屏幕。
> * 如何修改它。
> * 如何将其集成到应用中。

若要深入了解此屏幕的默认功能，请参阅[电子邮件屏幕参考](email-screen-reference.md)。

## <a name="prerequisite"></a>先决条件

熟悉如何[在 PowerApps 中创建应用](../data-platform-create-app-scratch.md)时添加和配置屏幕和其他控件。

## <a name="default-functionality"></a>默认功能

从模板中添加电子邮件屏幕：

1. [登录](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 power apps，然后在 Power apps Studio 中创建应用或打开现有应用。

    本主题演示了一个手机应用，但相同的概念也适用于平板电脑应用。

1. 在功能区的 "**主页**" 选项卡上，选择 "**新屏幕** > **电子邮件**"。

    默认情况下，屏幕的外观如下所示：

    ![电子邮件屏幕](media/email-screen/email-screen-full.png)

一些有用的说明：

* 若要搜索你的组织中的用户，请在 "到" 下方的文本输入框中键入其名称。
* 搜索人员时，将只返回前15个结果。
* 若要添加组织外电子邮件收件人的电子邮件地址，请键入完整的有效电子邮件地址，然后选择显示在其右侧的 "+" 图标。
* 必须将至少一个人添加为收件人，并提供发送电子邮件的主题。
* 发送电子邮件后，主题行和邮件正文以及收件人列表的内容都将被清除。

## <a name="modify-the-screen"></a>修改屏幕

您可以通过几种常见方法修改此屏幕的默认功能：

* [添加图像-附件支持](email-screen-overview.md#add-image-attachment-support)
* [显示人员的不同数据](email-screen-overview.md#show-different-data-for-people)

如果要进一步修改屏幕，请使用[电子邮件屏幕参考](./email-screen-reference.md)作为指南。

> [!IMPORTANT]
> 以下步骤假定你已将一个电子邮件屏幕添加到应用。 如果您添加了多个控件名称（如**iconMail1**），则会以不同数字结束，并且您需要相应地调整公式。

### <a name="add-image-attachment-support"></a>添加图像-附件支持

这允许用户以电子邮件附件的形式发送单个映像。

1. 在 "**插入**" 选项卡上，选择 "**媒体**"，然后选择 "**添加图片**"。
1. 将新控件的**Y**属性设置为以下表达式：

    `TextEmailMessage1.Y + TextEmailMessage1.Height + 20`
    
1. 插入**AddMediaWithImage**控件后，将其高度设置为小于210。
1. 在控件树视图中，选择 " **AddMediaWithImage** >  **...** " > **重新排序** > "**发送到后**"。
   这可以防止控件位于**PeopleBrowseGallery**控件前面。
1. 将**EmailPeopleGallery**的**Height**属性更改为以下公式：

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery1.TemplateHeight + EmailPeopleGallery1.TemplatePadding * 2 ) *
            RoundUp( CountRows( EmailPeopleGallery1.AllItems ) / 2, 0 ), 
        304
    )
    ```

1. 将**EmailPeopleGallery**的**ShowScrollbar**属性设置为以下表达式：

    ```EmailPeopleGallery1.Height >= 304```
    
    这会阻止最大高度从页面推送**AddMediaWithImage**控件。
    
1. 将**iconMail**控件的**OnSelect**属性更改为以下公式：

    ```powerapps-dot
    Set( _emailRecipientString, Concat(MyPeople, Mail & ";") );
    If( IsBlank( UploadedImage1 ),
        'Office365'.SendEmail( _emailRecipientString, 
            TextEmailSubject1.Text, 
            TextEmailMessage1.Text, 
            { Importance: "Normal" }
        ),
        'Office365'.SendEmail( _emailRecipientString, 
            TextEmailSubject1.Text, 
            TextEmailMessage1.Text, 
            {
                Importance: "Normal",
                Attachments: Table(
                    {
                        Name: "Image.jpg", 
                        ContentBytes: UploadedImage1.Image
                    }
                )
            }
        )
    );
    Reset( TextEmailSubject1 );
    Reset( TextEmailMessage1 );
    Reset( AddMediaButton1 );
    Clear( MyPeople )
    ```
    
    此公式检查上传的图像。 如果没有，则使用与之前相同的 `Office365.SendEmail` 操作。 如果有图像，则会将其作为附件添加到附件表中。
    发送电子邮件后，在**AddMediaButton**上执行其他**重置**操作以删除上传的映像。
> [!NOTE]
> 若要将多个附件添加到电子邮件中，请将记录添加到附件表中。

### <a name="show-different-data-for-people"></a>显示人员的不同数据

此屏幕使用[Office365Users. SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser)操作在你的组织中搜索用户。它为每个事件提供了**PeopleBrowseGallery**控件中显示的其他字段。 添加或更改库中的字段非常简单：

1. 在**PeopleBrowseGallery**控件中，选择要修改的标签（或添加一个标签，并将其保留为选中状态）。

1. 选中其**Text**属性后，在编辑栏中，将内容替换 `ThisItem.`

    IntelliSense 显示您可以选择的字段列表。

1. 选择所需的字段。

    **Text**属性更新为 `ThisItem.{FieldSelection}`。

## <a name="integrate-the-screen-into-an-app"></a>将屏幕集成到应用中

电子邮件屏幕是一种功能强大的控件绑定，但它通常作为更大、更通用的应用程序的一部分执行。 您可以通过多种方式将此屏幕集成到较大的应用程序中，包括[链接到日历屏幕](email-screen-overview.md#linking-to-the-calendar-screen)。

### <a name="linking-to-the-calendar-screen"></a>链接到日历屏幕

按照[Calendar screen 概述](./calendar-screen-overview.md#show-event-attendees)的 "显示事件与会者" 一节中所述的步骤进行操作，但在最后一个步骤中，将 "**导航**" 功能设置为打开 "电子邮件" 屏幕。 完成这些步骤后，将填充**MyPeople**集合，该集合允许用户向出席所选事件的人员发送电子邮件。

> [!NOTE]
> 发送此电子邮件将在 Outlook 中发送与实际事件不同的电子邮件。

## <a name="next-steps"></a>后续步骤

* [查看此屏幕的参考文档](./email-screen-reference.md)。
* [详细了解 PowerApps 中的 Office 365 用户连接器](../connections/connection-office365-users.md)。
* [查看 PowerApps 中的所有可用连接](../connections-list.md)。