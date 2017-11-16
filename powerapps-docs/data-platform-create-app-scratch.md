---
title: "使用 Common Data Service 数据库从头开始创建应用 | Microsoft 文档"
description: "创建用于添加、更新和删除记录的应用。"
services: powerapps
documentationcenter: na
author: kfend
manager: kfend
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 12/06/2016
ms.author: kfend
ms.openlocfilehash: f3cc5a8116f84d61576d75b22a8e3197d6ec7e42
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="create-an-app-from-scratch-using-a-common-data-service-database"></a>使用 Common Data Service 数据库从头开始创建应用
生成一个应用，以使用（内置的）标准实体和/或（组织创建的）自定义实体来管理 Common Data Service 中存储的数据。

使用 Common Data Service 生成应用时，无需从 Microsoft PowerApps 建立连接，而处理 SharePoint、Dynamics 365 或 Salesforce 等数据源时则需要这样做。 只需指定要显示、管理或在应用中用于这两种活动的实体即可。

[!VIDEO nb:cid:UUID:5db63c4d-6aeb-45c5-9609-8f4bbdd37bc6]


1. 创建 Common Data Service 数据库。 有关详细信息，请参阅[创建 Common Data Service 数据库](create-database.md)。
2. 在 [powerapps.com](https://web.powerapps.com) 上的左侧导航窗格中，单击或点击“新应用”。
3. 在随即显示的对话框中，单击或点击“适用于 Web 的 PowerApps Studio”。 （也可以单击或点击“适用于 Windows 的 PowerApps Studio”，然后按说明操作，安装适用于 Windows 的 PowerApps Studio。 虽然接下来的说明使用的是适用于 Web 的 PowerApps Studio，但有关 Microsoft Windows 应用的说明也与之相似。）
4. 在“从空白画布或模板开始”下方，单击或点击“空白应用”磁贴上的“手机布局”。
5. 如果系统显示提示，请单击或点击“跳过”，跳过教程。
6. 单击或点击“内容”选项卡。
7. 单击或点击“数据源”。
8. 单击或点击右侧窗格中的“添加数据源”。
9. 单击或点击要使用的 Common Data Service。
10. 在实体列表中，选中要使用的一个或多个实体的复选框，然后单击或点击“连接”。

此时，指定的实体会显示在数据源列表中。可以按[从头开始创建应用](get-started-create-from-blank.md)中所述来生成应用了。

