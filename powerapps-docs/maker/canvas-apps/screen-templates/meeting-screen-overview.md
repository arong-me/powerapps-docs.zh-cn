---
title: 会议-屏幕模板 |Microsoft Docs
description: 了解 canvas 应用的会议屏幕模板的工作原理，并为自己的用例扩展屏幕
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
ms.openlocfilehash: ac6b75d60f41cd68ee1723c913766ea701bc6ca8
ms.sourcegitcommit: 6b27eae6dd8a53f224a8dc7d0aa00e334d6fed15
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74732529"
---
# <a name="overview-of-the-meeting-screen-template-for-canvas-apps"></a>画布应用的会议屏幕模板概述

在画布应用中，添加可让用户从其 Office 365 Outlook 帐户创建和发送会议请求的会议屏幕。 用户可以在其组织中搜索与会者并添加外部电子邮件地址。 如果你的租户有内置于 Outlook 的会议室，则用户也可以选择位置。

你还可以添加其他基于模板的屏幕，这些屏幕显示 Office 365 中的不同数据，如[电子邮件](email-screen-overview.md)、组织中的[人员](people-screen-overview.md)以及用户的[日历](calendar-screen-overview.md)。

本概述介绍屏幕的高级功能。

若要深入了解此屏幕的默认功能，请参阅[会议屏幕参考](meeting-screen-reference.md)。

## <a name="prerequisite"></a>先决条件

熟悉如何[在 Power Apps 中创建应用](../data-platform-create-app-scratch.md)时添加和配置屏幕和其他控件。

## <a name="default-functionality"></a>默认功能

从模板添加会议屏幕：

1. [登录](https://make.powerapps.com?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)到 power apps，然后在 Power apps Studio 中创建应用或打开现有应用。

    本主题演示了一个手机应用，但相同的概念也适用于平板电脑应用。

1. 在功能区的 "**主页**" 选项卡上，选择 "**新建屏幕** > **会议**"。

  填写时，会议屏幕的两个选项卡的外观如下所示：

  ![会议屏幕，两个选项卡](media/meeting-screen/meeting-screen-full-both.png)

一些有用的说明：

* 会议屏幕允许应用用户在 Outlook 中创建会议。
  用户可以搜索并添加与会者，还可以选择向会议添加会议室。
* 若要搜索你的组织中的用户，请在 "与会者" 下的文本输入框中键入其名称。
* 搜索用户时，只返回前15个结果。
* 若要为组织外的与会者添加电子邮件地址，请键入完整的有效电子邮件地址，并选择电子邮件地址右侧显示的 "+" 图标。
* 若要创建会议，你必须将至少一个人添加为与会者，提供主题，然后在 "**计划**" 选项卡中选择会议时间。
* 发送会议请求后，将清除该会议的所有信息。
* 发送图标的**OnSelect**语句（右上角）包含以下公式：
    ```powerapps-dot
    Set( _myCalendarName, 
        LookUp( 'Office365'.CalendarGetTables().value, DisplayName = "Calendar" ).Name 
    );
    ```
* 对于大多数 Office 用户的日历，"日历" 是默认的显示名称，但您的组织可能会有所不同。 如果是这样，则可以将 "日历" 更改为组织的相应术语。
* 如果你尝试计划过去发生的会议或向会议添加20多人，会收到错误。

## <a name="next-steps"></a>后续步骤

* [查看此屏幕的参考文档](./meeting-screen-reference.md)。
* [了解有关 Office 365 Outlook connector 的详细信息](../connections/connection-office365-outlook.md)。
* [了解有关 Office 365 用户连接器的详细信息](../connections/connection-office365-users.md)。
