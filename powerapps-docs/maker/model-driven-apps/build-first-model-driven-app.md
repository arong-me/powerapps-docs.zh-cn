---
title: 使用 PowerApps 从头开始构建第一个模型驱动应用 | Microsoft Docs
description: 了解如何构建简单的模型驱动应用
documentationcenter: ''
author: Mattp123
manager: kvivek
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 04/18/2018
ms.author: matp
ms.openlocfilehash: 36e189c75ef4c53ac97805fae38094e25c2c4804
ms.sourcegitcommit: aba996b1773ecdf62758e06b34eaf57bede29e08
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39663938"
---
# <a name="build-your-first-model-driven-app-from-scratch"></a>从头开始构建第一个模型驱动应用
模型驱动应用设计是一种侧重于组件的应用开发方法。 在本主题中，可使用 PowerApps 环境中提供的一个标准实体来简化模型驱动应用的构建方式。

> [!TIP]
> 要全面了解如何构建模型驱动应用，请先参阅[了解模型驱动应用组件](model-driven-app-components.md)。 

## <a name="sign-in-to-powerapps"></a>登录到 PowerApps
登录 [PowerApps](https://web.powerapps.com/)。 如果还没有 [!INCLUDE [powerapps](../../includes/powerapps.md)] 帐户，请选择“开始免费使用”链接。 

## <a name="create-your-model-driven-app"></a>创建模型驱动应用

1.  选择所需的环境，或转到 [PowerApps 管理中心](https://admin.powerapps.com/)创建一个新环境。
2.  从左侧导航窗格，选择“模型驱动”。 

    ![模型驱动](media/build-first-model-driven-app/choose-design-mode.png)

  > [!IMPORTANT]
  > 如果“模型驱动”设计模式不可用，则可能需要[创建环境](https://docs.microsoft.com/powerapps/administrator/create-environment)。   

3. 从左窗格选择“应用”，然后选择“创建应用”。

4.  在“创建新应用”页上，输入以下详细信息，然后选择“完成”： 
  - 名称：输入应用名称，如“Myfirstapp”。 
  - 说明：键入应用是什么或其功能的简短说明，如“这是我的第一个应用”。
有关其他应用属性的信息，请参阅[创建应用](https://docs.microsoft.com/dynamics365/customer-engagement/customize/create-edit-app#create-an-app)。
 
    ![Create-new-app](media/build-first-model-driven-app/create-new-app.png)

## <a name="add-components-to-your-app"></a>将组件添加到应用
从应用程序设计器中，可以将组件添加到你的应用。
1.  选择“打开站点地图设计器”箭头以打开站点地图设计器。 

    ![Create-new-sitemap](media/build-first-model-driven-app/new-sitemap.png)

2.  在站点地图设计器上选择“新子区域”，在右窗格中选择“属性”选项卡，然后选择以下属性。
  - 类型：实体
  - 实体：帐户

    ![将组件添加到站点地图](media/build-first-model-driven-app/sitemap.png)

3.  选择“保存并关闭”。
4.  在应用程序设计器画布中选择“表单”，然后在“主表单”组下的右窗格中，选择“帐户”表单。

    ![帐户主表单](media/build-first-model-driven-app/main-form.png)

5.  在应用程序设计器画布中选择“视图”，然后选择“活动帐户”、“所有帐户”，和“我的活动帐户”视图。

    ![帐户视图](media/build-first-model-driven-app/views.png)

6. 在应用程序设计器画布中选择“图表”，然后选择“按行业划分的帐户”图表。
7. 在视图设计器工具栏上选择“保存”。

    ![应用程序设计器工具栏保存](media/build-first-model-driven-app/app-designer-toolbar.png)
 
<!-- ##  Validate your app
This step checks for component dependencies that are required for the app to work, but haven't yet been added to the app. 

1. On the app designer canvas, select the component that indicates a dependency, such as the **Forms** component. Then, on the right-pane select the **Required** tab, expand **Entity Dependencies** and then select all required dependencies. 

    ![Add dependencies](media/build-first-model-driven-app/resolve-dependencies.png)

2. Select **Add Dependencies**.
3. On the app designer toolbar, select **Save**.  -->

## <a name="publish-your-app"></a>发布你的应用
在视图设计器工具栏上选择“发布”。

在发布应用后，它将可供你运行或与其他人共享。

![简单帐户实体应用](media/build-first-model-driven-app/accounts-quickstart-app.png)

## <a name="next-steps"></a>后续步骤
在本主题中，你构建了一个简单的模型驱动应用。 
- 要查看应用运行时的效果，请参阅[在移动设备上运行模型驱动应用](../../user/run-app-client-model-driven.md)。
- 要了解如何共享应用，请参阅[共享模型驱动应用](share-model-driven-app.md)。
- 要开始体验并全面了解如何构建模型驱动应用，请参阅[了解模型驱动应用组件](model-driven-app-components.md)
