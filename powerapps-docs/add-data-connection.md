---
title: "在应用中添加数据连接 | Microsoft 文档"
description: "在现有应用或空白应用中添加数据连接"
services: 
suite: powerapps
documentationcenter: na
author: archnair
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 10/02/2017
ms.author: archanan
ms.openlocfilehash: 3fe41ceddcce1ee8d1daa9b3532b4c92a94d8eee
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="add-a-data-connection-in-powerapps"></a>在 PowerApps 中添加数据连接
在 PowerApps 中，向现有应用或从头开始生成的应用添加数据连接。 本主题使用的是 PowerApps Studio，也可以使用 [powerapps.com](https://web.powerapps.com)，如[管理连接](add-manage-connections.md)主题所述。

应用中添加的数据连接可以连接 SharePoint、Salesforce、OneDrive 或[许多其他数据源之一](connections-list.md)。

阅读完本文的[后续步骤](#next-steps)是，在应用中显示和管理相应数据源中的数据，如下面这些示例所述：

* 连接到 OneDrive，并在应用中管理 Excel 工作簿中的数据。
* 连接到 Twilio，并从应用发送短信。
* 连接 SQL Server，然后通过应用更新表。

## <a name="prerequisites"></a>先决条件
[注册](signup-for-powerapps.md)、[安装](http://aka.ms/powerappsinstall) PowerApps，然后打开该程序，并提供注册所用的同一凭据进行登录。

## <a name="background-on-data-connections"></a>数据连接的背景知识
大多数 PowerApps 应用使用称为“数据源”的外部信息，此类信息存储在云服务中。 常见的例子是，OneDrive for Business 中存储的 Excel 文件中的表。 应用可以使用连接器访问这些数据源。

最常见的数据源是可用于检索和存储信息的表。 可以使用数据源连接器，在 Microsoft Excel 工作簿、SharePoint 列表、SQL 表和其他许多格式数据源中读取和写入数据，这些数据源可以存储在 OneDrive for Business、DropBox、SQL Server 等云服务中。

除表以外的其他数据源包括电子邮件、日历、Twitter 和通知。

使用“[库](controls/control-gallery.md)”、“[显示窗体](controls/control-form-detail.md)”和“[编辑窗体](controls/control-form-detail.md)”控件，可以轻松创建在数据源中读取和写入数据的应用。 若要开始，请阅读[了解数据窗体](working-with-forms.md)一文。

## <a name="add-a-connection"></a>添加连接
1. 单击或点击“文件”菜单（左边缘附近）上的“新建”。
   
    ![“文件”菜单上的“新建”选项](./media/add-data-connection/file-new.png)
2. 在“空白应用”磁贴上，单击或点击“手机布局”。
   
    ![从头开始创建应用](./media/add-data-connection/blank-app.png)
3. 在中心窗格中，单击或点击“连接到数据”。
4. 如果“数据”窗格中的连接列表包含要使用的连接，请单击或点击相应连接，将其添加到应用中。 否则，请跳到下一步。
   
    ![添加数据源](./media/add-data-connection/choose-existing-connections.png)
5. 单击或点击“新建连接”，查看连接器列表。
   
    ![添加连接](./media/add-data-connection/new-connection.png)
6. 滚动浏览连接器列表，直到发现要创建的连接类型（例如，Office 365 Outlook），然后单击或点击此类型。
   
    ![选择连接](./media/add-data-connection/choose-connection.png)
7. 单击或点击“创建”，创建连接并将其添加到应用中。
   
    某些连接器（如 Microsoft Translator）不需要执行额外步骤即可立即从中显示数据。 其他连接器将提示你提供凭据，指定一组特定的数据或执行其他步骤。 例如，[SharePoint](connections/connection-sharepoint-online.md) 和 [SQL Server](connections/connection-azure-sqldatabase.md) 需要在使用之前提供其他信息。

## <a name="view-or-change-a-data-source"></a>查看或更改数据源
如果正在更新应用，则可能需要确定或更改具有 Item 属性的库、窗体或其他控件中显示的数据源。 例如，你可能正在使用其他人创建的应用，或者你可能想要提醒自己你在不久前配置的数据源。

1. 选择想要为其标识数据源的控件。
   
    例如，通过在左边缘附近的屏幕和控件的层次结构列表中单击或点击一个库（而非库中的控件）来选择此库。
   
    数据源的名称在右侧窗格的“属性”选项卡上显示。
   
    ![“属性”选项卡上的数据源](./media/add-data-connection/properties-tab.png)
2. 若要显示此数据源的详细信息或更改它，请单击或点击右侧窗格中的“数据”。
   
    ![“数据”窗格](./media/add-data-connection/data-pane.png)
3. 若要更改该数据源，请单击或点击该数据源旁的向下箭头，然后选择或创建其他源。

## <a name="next-steps"></a>后续步骤
* 若要显示和更新数据源（如 Excel、SharePoint Online 或 SQL Server）中的数据，请先[添加库](add-gallery.md)，然后[添加窗体](add-form.md)。
* 对于其他源中的数据，请使用连接器特定的函数，例如，适用于 [Office 365 Outlook](connections/connection-office365-outlook.md)、[Twitter](connections/connection-twitter.md) 和 [Microsoft Translator](connections/connection-microsoft-translator.md) 的函数。

