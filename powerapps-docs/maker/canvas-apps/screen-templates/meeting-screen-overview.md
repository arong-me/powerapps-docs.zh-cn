---
title: 会议屏幕模板 |Microsoft Docs
description: 了解有关画布应用的会议屏幕模板的工作原理，并扩展用例的屏幕
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
ms.openlocfilehash: 24f04ff9ce95f603f5f7d4dc7d217146b9eebef8
ms.sourcegitcommit: 5e15a1033a68289781f8092fb65c57432501f911
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54459389"
---
# <a name="overview-of-the-meeting-screen-template-for-canvas-apps"></a>画布应用的会议屏幕模板的概述

在画布应用中，添加一个会议屏幕，使用户能够创建和从其 Office 365 Outlook 帐户发送会议请求。 用户可以在其组织中的与会者搜索并添加外部电子邮件地址。 如果你的租户有内置在 Outlook 的会议室，用户可以选择的位置以及。

您还可以添加其他基于模板的屏幕，如显示不同的数据从 Office 365[电子邮件](email-screen-overview.md)，[人](people-screen-overview.md)组织和用户的中[日历](calendar-screen-overview.md)。

本概述介绍了有关在屏幕的高级功能。

此屏幕的默认功能的更深入了解，请参阅[会议屏幕引用](meeting-screen-reference.md)。

## <a name="prerequisite"></a>先决条件

如何添加和配置屏幕和其他控件为您熟悉[在 PowerApps 中创建应用](../data-platform-create-app-scratch.md)。

## <a name="default-functionality"></a>默认功能

若要从模板添加会议屏幕：

1. [登录](http://web.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 PowerApps，然后创建应用或在 PowerApps Studio 中打开现有应用程序。

    本主题显示手机应用，但概念同样适用于平板电脑应用。

1. 上**主页**选项卡的功能区中，选择**新屏幕** > **会议**。

  填写会议屏幕的两个选项卡时类似于此：

  ![会议屏幕中，两个选项卡](media/meeting-screen/meeting-screen-full-both.png)

几个有用的说明：

* 会议屏幕允许应用用户在 Outlook 中创建会议。
  用户可以搜索和添加与会者和，（可选） 添加到会议的会议室。
* 若要搜索的组织中的用户，请启动"与会者"下的文本输入框中键入团队名称。
* 当搜索用户时，将返回的前 15 结果。
* 若要添加你的组织外部的与会者电子邮件地址，键入完整的有效电子邮件地址，并选择电子邮件地址的右侧显示的 + 图标。
* 若要创建一个会议，必须将至少一个成员添加为某个出席者，提供一个主题，并选择中的会议时间**计划**选项卡。
* 发送会议请求后，会清除该会议的所有信息。
* **OnSelect**语句的发送图标 （右上角） 包含以下公式：
    ```powerapps-dot
    Set( _myCalendarName, 
        LookUp( 'Office365'.CalendarGetTables().value, DisplayName = "Calendar" ).Name 
    );
    ```
* "日历"是默认的显示名称为大多数 Office 用户的日历，但你的组织可能会不同。 如果是这样，您可以将"日历"更改为你组织的相应术语
* 如果你尝试计划发生在过去的会议收到一个错误，或将超过 20 个人员添加到会议。

## <a name="next-steps"></a>后续步骤

* [查看此屏幕的参考文档](./meeting-screen-reference.md)。
* [了解有关 Office 365 Outlook 连接器的详细信息](../connections/connection-office365-outlook.md)。
* [了解有关 Office 365 用户连接器的详细](../connections/connection-office365-users.md)。
