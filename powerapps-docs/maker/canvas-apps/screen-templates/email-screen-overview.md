---
title: 电子邮件屏幕模板 |Microsoft Docs
description: 了解有关画布应用的电子邮件屏幕模板的工作原理，并扩展用例的屏幕
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/29/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: a1aad5ca9e8c7f8b55b1645b04d6c8dc0b9c707b
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61539202"
---
# <a name="overview-of-the-email-screen-template-for-canvas-apps"></a>画布应用的电子邮件屏幕模板的概述

在画布应用中，添加可让用户从其 Office 365 Outlook 帐户发送一封电子邮件的电子邮件屏幕。 用户可以搜索其组织中的收件人，并还添加外部电子邮件地址。 可以添加图像附件支持、 更改搜索库中显示的用户数据和进行其他自定义。

您还可以添加显示不同的数据，从 Office 365，如用户的其他基于模板的屏幕[日历](calendar-screen-overview.md)，[人](people-screen-overview.md)在组织中，并[可用性](meeting-screen-overview.md)的人们用户可能想要邀请参加会议。

本概述介绍了：
> [!div class="checklist"]
> * 如何使用默认电子邮件屏幕。
> * 如何对其进行修改。
> * 如何将其集成到应用。

此屏幕的默认功能的更深入了解，请参阅[电子邮件屏幕引用](email-screen-reference.md)。

## <a name="prerequisite"></a>先决条件

如何添加和配置屏幕和其他控件为您熟悉[在 PowerApps 中创建应用](../data-platform-create-app-scratch.md)。

## <a name="default-functionality"></a>默认功能

若要从模板中添加电子邮件的屏幕：

1. [登录](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 PowerApps，然后创建应用或在 PowerApps Studio 中打开现有应用程序。

    本主题显示手机应用，但概念同样适用于平板电脑应用。

1. 上**主页**选项卡的功能区中，选择**新屏幕** > **电子邮件**。

    默认情况下，查找类似于以下屏幕：

    ![电子邮件屏幕](media/email-screen/email-screen-full.png)

几个有用的说明：

* 若要搜索的用户在组织中，启动下面"收件人"的文本输入框中键入团队名称。
* 搜索的用户时，将返回的前 15 结果。
* 若要添加你的组织外部的电子邮件收件人的电子邮件地址，键入完整的有效电子邮件地址，并选择显示右侧的 + 图标。
* 必须将至少一个成员添加为收件人，并提供使用者发送一封电子邮件。
* 发送电子邮件后，主题行和消息正文以及收件人列表的内容将全部被清除。

## <a name="modify-the-screen"></a>修改屏幕

多种常见的方式，可以修改此屏幕的默认功能：

* [添加图像附件的支持](email-screen-overview.md#add-image-attachment-support)
* [显示不同的数据的人员](email-screen-overview.md#show-different-data-for-people)

如果你想要修改的屏幕进一步，使用[电子邮件屏幕引用](./email-screen-reference.md)作为指南。

> [!IMPORTANT]
> 以下步骤假定你已将只有一个电子邮件屏幕添加到应用。 如果你已添加多个控件名称 (如**iconMail1**) 将结束使用其他号码，并需要进行相应地调整公式。

### <a name="add-image-attachment-support"></a>添加图像附件的支持

这允许用户以附件形式发送其电子邮件包含的单一映像。

1. 上**插入**选项卡上，选择**媒体**，然后选择**添加图片**。
1. 设置新控件的**Y**属性设置为此表达式：

    `TextEmailMessage1.Y + TextEmailMessage1.Height + 20`
    
1. 与**AddMediaWithImage**插入控件，将设置为小于 210 窗体的高度。
1. 在控件树视图中，选择**AddMediaWithImage** > **...**  > **重新排列** > **置于底层**。
   这可以防止不必坐在前面的控件**PeopleBrowseGallery**控件。
1. 更改**高度**的属性**EmailPeopleGallery**为以下公式：

    ```powerapps-dot
    Min( 
        ( EmailPeopleGallery1.TemplateHeight + EmailPeopleGallery1.TemplatePadding * 2 ) *
            RoundUp( CountRows( EmailPeopleGallery1.AllItems ) / 2, 0 ), 
        304
    )
    ```

1. 设置**ShowScrollbar**的属性**EmailPeopleGallery**为以下表达式：

    ```EmailPeopleGallery1.Height >= 304```
    
    这可以防止将推送的最大高度**AddMediaWithImage**离开页面的控件。
    
1. 更改**OnSelect**的属性**iconMail**控制为以下公式：

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
    
    此公式检查上传的图像。 如果不存在，然后使用相同`Office365.SendEmail`像以前一样操作。 如果没有图像，则将它添加为 Attachments 表中的附件。
    发送电子邮件，附加后**重置**对其执行操作**AddMediaButton**删除上传的图像。
> [!NOTE]
> 若要添加多个电子邮件附件，请将记录添加到 Attachments 表。

### <a name="show-different-data-for-people"></a>显示不同的数据的人员

使用此屏幕[Office365Users.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser)搜索你组织中的用户的操作它还提供其他字段中将显示每个事件超过**PeopleBrowseGallery**控件。 添加或更改库中的字段很简单：

1. 在中**PeopleBrowseGallery**控件中，选择一个标签来修改 （或添加一个并使其选择用）。

1. 使用其**文本**属性处于选中状态，在公式栏中，使用的内容替换为 `ThisItem.`

    IntelliSense 显示可以选择的字段的列表。

1. 选择所需的字段。

    **文本**属性更新为`ThisItem.{FieldSelection}`。

## <a name="integrate-the-screen-into-an-app"></a>集成到应用的屏幕

电子邮件屏幕是功能强大的控件在自己的权限，但它通常作为更大、 更灵活的应用的一部分执行最佳。 可以将此屏幕集成到大型应用中通过多种方式，包括[将链接到日历屏幕](email-screen-overview.md#linking-to-the-calendar-screen)。

### <a name="linking-to-the-calendar-screen"></a>将链接到日历屏幕

按照的"显示事件的与会者"部分中所述的步骤[日历屏幕概述](./calendar-screen-overview.md#show-event-attendees)但是，在最后一步，设置**Navigate**函数以打开电子邮件屏幕。 完成这些步骤后**MyPeople**填充集合，它允许用户将电子邮件发送给参加所选的事件的人员。

> [!NOTE]
> 发送此电子邮件将发送单独的电子邮件从 Outlook 中的实际事件。

## <a name="next-steps"></a>后续步骤

* [查看此屏幕的参考文档](./email-screen-reference.md)。
* [了解有关 PowerApps 中的 Office 365 用户连接器的详细信息](../connections/connection-office365-users.md)。
* [请参阅在 PowerApps 中的所有可用连接](../connections-list.md)。