---
title: 用户-屏幕模板 |Microsoft Docs
description: 了解 canvas 应用的人员屏幕模板的工作原理，以及如何为自己的用例扩展屏幕
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: tapanm
ms.date: 12/30/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 4f54a2f6d3bfa7c843b7b095f999050602e063b0
ms.sourcegitcommit: dd2a8a0362a8e1b64a1dac7b9f98d43da8d0bd87
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/02/2019
ms.locfileid: "74675022"
---
# <a name="overview-of-the-people-screen-template-for-canvas-apps"></a>用于画布应用的人员屏幕模板概述

在画布应用中，添加允许用户在其组织内搜索人员的人员屏幕。 用户可以搜索、选择并向集合添加人员。 您可以更改搜索结果库中显示的数据类型、使用用户选择发送电子邮件以及进行其他自定义。

你还可以添加其他基于模板的屏幕，这些屏幕显示 Office 365 的不同数据，如[电子邮件](email-screen-overview.md)、用户的[日历](calendar-screen-overview.md)，以及用户可能想要邀请参加会议的人员的[可用性](meeting-screen-overview.md)。

本概述介绍了以下内容：
> [!div class="checklist"]
> * 如何使用默认人屏幕。
> * 如何修改屏幕。
> * 如何将屏幕集成到应用中。

若要深入了解此屏幕的默认功能，请参阅[用户界面参考](people-screen-reference.md)。

## <a name="prerequisite"></a>先决条件

熟悉如何[在 PowerApps 中创建应用](../data-platform-create-app-scratch.md)时添加和配置屏幕和其他控件。

## <a name="default-functionality"></a>默认功能

从模板添加人员屏幕：

1. [登录](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 power apps，然后在 Power apps Studio 中创建应用或打开现有应用。

    本主题演示了一个手机应用，但相同的概念也适用于平板电脑应用。

1. 在功能区的 "**主页**" 选项卡上，选择 "**新屏幕** > **人员**"。

    默认情况下，屏幕的外观如下所示：

    ![初始人员屏幕状态](media/people-screen/people-screen-empty.png)

1. 若要开始搜索用户，请选择顶部的文本输入框，然后键入同事的名称。 搜索结果显示在文本输入框下方：

    ![人员屏幕搜索状态](media/people-screen/people-browse-gall-full.png)

1. 从搜索结果中选择个人时，它们将被添加到**MyPeople**集合。 将重置搜索栏输入值，显示所选人员的集合：

    ![人员屏幕收集结果](media/people-screen/people-people-gall-full.png)

## <a name="modify-the-screen"></a>修改屏幕

您可以通过[显示用户的不同数据](people-screen-overview.md#show-different-data-for-people)来修改此屏幕的默认功能。

如果你想要进一步修改屏幕，请使用[人脉参考](./people-screen-reference.md)作为指导。

### <a name="show-different-data-for-people"></a>显示人员的不同数据

此屏幕使用[Office365Users. SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser)操作在你的组织中搜索用户。它为每个事件提供了**UserBrowseGallery**控件中显示的其他字段。 添加或更改库中的字段是一个简单的过程：

1. 在**UserBrowseGallery**中，选择要修改的标签（或添加一个标签，并将其保留为选中状态）。

1. 选中其**Text**属性后，在编辑栏中，将内容替换 `ThisItem.`

    IntelliSense 显示您可以选择的字段列表。

1. 选择所需的字段。

    **Text**属性应更新为 `ThisItem.{FieldSelection}`。

## <a name="integrate-the-screen-into-an-app"></a>将屏幕集成到应用中

人员屏幕是一种功能强大的控件绑定，但它通常作为更大、更通用的应用程序的一部分执行。 可以通过多种方式将此屏幕集成到较大的应用程序中，包括[使用缓存的人员列表](people-screen-overview.md#use-your-cached-list-of-people)。

### <a name="use-your-cached-list-of-people"></a>使用缓存的人员列表

人员屏幕缓存用户在**MyPeople**集合中的选择。 如果你的业务方案调用人员查找，你将需要了解如何使用此集合。 在这里，你将演练如何将此屏幕连接到基本的电子邮件屏幕，并向**MyPeople**集合中的用户发送电子邮件。 你还将深入了解[电子邮件屏幕](./email-screen-overview.md)的工作方式。

1. 通过选择 "**视图**" 选项卡，选择 "**数据源**" > "**添加数据源**"，并查找 Office 365 Outlook connector，将 Office 365 outlook 数据源添加到应用。 可能需要选择 "**新建连接**" 才能找到它。
1. 插入人脉屏幕后，插入新的空白屏幕。 在该屏幕中，添加一个后退箭头图标、两个文本输入框和一个发送图标。
1. 将屏幕重命名为 " **EmailScreen**"，将 "向后箭头" 图标更改为 " **SubjectLine**"，将 " **BackIcon**" 的一个文本输入框重命名为 " **MessageBody**"，将 "发送" 图标更改为**SendIcon**
1. 将**BackIcon**的**OnSelect**属性设置为 `Back()`。
1. 将**SendIcon**的**OnSelect**属性设置为以下公式：

    ```powerapps-dot
    Office365.SendEmail( 
        Concat( MyPeople, UserPrincipalName & ";" ), 
        SubjectLine.Text, 
        MessageBody.Text 
    )
    ```
    
    此时，你将使用 Outlook connector 发送电子邮件。 将其作为收件人列表传递 `Concat(MyPeople, UserPrincipalName & ";")`。 此公式将**MyPeople**集合中的所有电子邮件地址连接到单个字符串，并用分号分隔它们。 这与在你喜爱的电子邮件客户端的 "发件人" 行中用分号分隔的电子邮件地址不相同。
    * 您将 `SubjectLine.Text` 作为消息的主题传递，并将 `MessageBody.Text` 为消息正文。
1. 在 "人脉" 屏幕的右上角，插入 "**邮件**" 图标。
   将图标颜色更改为你适合的任何颜色。
1. 将**SendIcon**的**OnSelect**属性设置为 `Navigate( EmailScreen, None )`。

    现在，你有了一个两个屏幕的应用，你可以在其中选择用户、撰写电子邮件消息，然后发送电子邮件。 请随意测试，但请务必小心，因为应用会向添加到**MyPeople**集合中的每个人发送电子邮件。

## <a name="next-steps"></a>后续步骤

* [查看此屏幕的参考文档](./people-screen-reference.md)。
* [了解有关 Office 365 Outlook connector 的详细信息](../connections/connection-office365-outlook.md)。
* [了解有关 Office 365 用户连接器的详细信息](../connections/connection-office365-users.md)。
