---
title: 人们屏幕模板 |Microsoft Docs
description: 了解画布应用的人屏幕模板的工作原理以及如何扩展用例的屏幕
author: emcoope-msft
manager: kvivek
ms.service: powerapps
ms.topic: conceptual
ms.custom: canvas
ms.reviewer: anneta
ms.date: 12/30/2018
ms.author: emcoope
search.audienceType:
- maker
search.app:
- PowerApps
ms.openlocfilehash: 85da6f5414cc25d1145f0fa8910e8c78bfb74533
ms.sourcegitcommit: 4042388fa5e7ef50bc59f9e35df330613fea29ae
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61536086"
---
# <a name="overview-of-the-people-screen-template-for-canvas-apps"></a>画布应用的人屏幕模板的概述

在画布应用中，添加可让用户搜索其组织内部人员的人屏幕。 用户可以搜索、 选择，并将用户添加到集合。 您可以更改哪些类型的数据显示在搜索结果库中，使用你的用户选择发送一封电子邮件，并进行其他自定义。

您还可以添加其他基于模板的屏幕，如显示不同的数据从 Office 365[电子邮件](email-screen-overview.md)，用户的[日历](calendar-screen-overview.md)，并[可用性](meeting-screen-overview.md)人的用户可能会想要邀请参加会议。

本概述介绍了：
> [!div class="checklist"]
> * 如何使用默认用户屏幕。
> * 如何修改屏幕。
> * 如何将屏幕集成到应用。

此屏幕的默认功能的更深入了解，请参阅[人屏幕引用](people-screen-reference.md)。

## <a name="prerequisite"></a>先决条件

如何添加和配置屏幕和其他控件为您熟悉[在 PowerApps 中创建应用](../data-platform-create-app-scratch.md)。

## <a name="default-functionality"></a>默认功能

若要从模板中添加一个人的屏幕：

1. [登录](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 PowerApps，然后创建应用或在 PowerApps Studio 中打开现有应用程序。

    本主题显示手机应用，但概念同样适用于平板电脑应用。

1. 上**主页**选项卡的功能区中，选择**新屏幕** > **人**。

    默认情况下，查找类似于以下屏幕：

    ![初始用户屏幕上的状态](media/people-screen/people-screen-empty.png)

1. 若要开始搜索的用户，选择顶部的文本输入的框并开始键入对同事的名称。 在输入文本框下方显示搜索结果：

    ![人们屏幕搜索状态](media/people-screen/people-browse-gall-full.png)

1. 从搜索结果中选择个人，当它们添加到**MyPeople**集合。 搜索栏输入值重置，则显示所选的人的集合：

    ![人们屏幕集合结果](media/people-screen/people-people-gall-full.png)

## <a name="modify-the-screen"></a>修改屏幕

可以修改的默认功能，通过此屏幕的[显示不同的数据的人员](people-screen-overview.md#show-different-data-for-people)。

如果你想要修改的屏幕进一步，使用[人屏幕引用](./people-screen-reference.md)作为指南。

### <a name="show-different-data-for-people"></a>显示不同的数据的人员

使用此屏幕[Office365Users.SearchUser](https://docs.microsoft.com/connectors/office365users/#searchuser)搜索你组织中的用户的操作它还提供其他字段中将显示每个事件超过**UserBrowseGallery**控件。 添加或更改库中的字段是一个简单的过程：

1. 在中**UserBrowseGallery**，选择一个标签来修改 （或添加一个并使其选择用）。

1. 使用其**文本**属性处于选中状态，在公式栏中，使用的内容替换为 `ThisItem.`

    IntelliSense 显示可以选择的字段的列表。

1. 选择所需的字段。

    **文本**属性应更新到`ThisItem.{FieldSelection}`。

## <a name="integrate-the-screen-into-an-app"></a>集成到应用的屏幕

人们屏幕是一功能强大的控件在自己的权限，但它通常作为更大、 更灵活的应用的一部分执行最佳。 可以将此屏幕集成到大型应用中通过多种方式，包括[使用缓存的人员列表](people-screen-overview.md#use-your-cached-list-of-people)。

### <a name="use-your-cached-list-of-people"></a>使用缓存的人员列表

人们屏幕缓存中的人选择**MyPeople**集合。 应为用户查找调用您的业务方案，你将需要知道如何使用此集合。 在这里，您将演练如何连接到一个尚不完善的电子邮件的屏幕的此屏幕中向用户发送电子邮件**MyPeople**集合。 你还将深入了解到如何[电子邮件屏幕](./email-screen-overview.md)工作原理。

1. 将 Office 365 Outlook 数据源添加到您的应用程序，通过选择**视图**选项卡上，选择**数据源** > **添加数据源**，然后查找 Office365 outlook 连接器。 可能需要选择**新的连接**找到它。
1. 插入后人屏幕，插入一个新的空白屏幕。 在该屏幕中，添加一个后退箭头图标、 两个文本输入框中和一个发送图标。
1. 重命名屏幕**EmailScreen**的后退箭头图标**BackIcon**，一个文本输入框**SubjectLine**，则其他到**MessageBody**，并为发送图标**SendIcon**。
1. 设置**OnSelect**的属性**BackIcon**到`Back()`。
1. 设置**OnSelect**的属性**SendIcon**为以下公式：

    ```powerapps-dot
    Office365.SendEmail( 
        Concat( MyPeople, UserPrincipalName & ";" ), 
        SubjectLine.Text, 
        MessageBody.Text 
    )
    ```
    
    在这里，使用 Outlook 连接器发送一封电子邮件。 将其传递`Concat(MyPeople, UserPrincipalName & ";")`的收件人列表。 此公式将串联中的电子邮件地址的所有**MyPeople**用分号分隔的方式为一个字符串集合。 这是与写出的您喜爱的电子邮件的客户端的"收件人"行中的以分号分隔的电子邮件地址字符串没有什么不同。
    * 您传递`SubjectLine.Text`作为该消息，主题和`MessageBody.Text`作为消息的正文。
1. 在用户屏幕上，在右上角中，插入**邮件**图标。
   将图标颜色更改为任何适合你。
1. 设置**OnSelect**的属性**SendIcon**到`Navigate( EmailScreen, None )`。

    现可在其中可以选择用户、 撰写电子邮件到它们，然后将其发送的两个屏应用。 尽情地测试一下，但务必谨慎，因为应用程序发送电子邮件发送给每个人都您将添加到**MyPeople**集合。

## <a name="next-steps"></a>后续步骤

* [查看此屏幕的参考文档](./people-screen-reference.md)。
* [了解有关 Office 365 Outlook 连接器的详细信息](../connections/connection-office365-outlook.md)。
* [了解有关 Office 365 用户连接器的详细](../connections/connection-office365-users.md)。
