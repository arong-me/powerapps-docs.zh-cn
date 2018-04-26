---
title: 模型驱动示例应用
description: 了解如何获取、自定义并删除模型驱动示例应用。
documentationcenter: na
author: caburk
manager: kfile
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/08/2018
ms.author: caburk
ms.openlocfilehash: c9525827c7e8e48c0f5e68e3608c9b6b9f630121
ms.sourcegitcommit: 8bd4c700969d0fd42950581e03fd5ccbb5273584
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="model-driven-sample-apps"></a>模型驱动示例应用

在 [powerapps.com](https://powerapps.com) 中，使用示例应用探究设计的可能性，并发现在开发自己的应用时可以应用的概念。 每个示例应用均使用虚拟数据展示实际场景。 

为了获得更多细节，请务必查看每个特定示例应用的文档。 

![募捐者示例应用](media/overview-model-driven-samples/fundraiser-app1.png)


## <a name="get-sample-apps"></a>获取示例应用

若要播放或编辑模型驱动示例应用，必须首先在 Common Data Service 数据库中预配应用。 首先创建试用环境和数据库，并确保选中“包括示例应用和数据”。

![创建数据库](media/overview-model-driven-samples/create-database1.png)


> [!IMPORTANT]
> 此选项会在数据库中安装所有可用示例应用。 示例应用适用于教育和演示目的，我们不建议在生产数据库中安装它们。 

## <a name="customize-a-sample-app"></a>自定义示例应用

1. 登录到 [powerapps.com](https://powerapps.com) 并选择“模型驱动”设计模式。 

    ![选择设计模式](media/overview-model-driven-samples/choose-design-mode.png)

2. 从主页中，将鼠标悬停在示例应用上并单击“自定义”。
3. 此时将打开应用设计器，为自定义应用提供多个选项。 
4. 有关其他自定义选项，请单击门户中左侧导航上的“高级”。

## <a name="remove-sample-apps-and-data"></a>删除示例应用和数据 
- 删除示例应用需要删除相应的[托管解决方案](https://docs.microsoft.com/dynamics365/customer-engagement/developer/uninstall-delete-solution)。 
- 删除解决方案还会删除特定于应用的自定义实体的任何示例数据。
- 如果对示例应用进行了自定义，则可能存在[依赖关系](https://docs.microsoft.com/dynamics365/customer-engagement/developer/dependency-tracking-solution-components)，必须在删除解决方案之前删除该依赖关系。

### <a name="steps"></a>步骤
1. 登录到 [PowerApps 管理门户](https://admin.powerapps.com)。

2. 选择环境。

3. 单击“Dynamics 365 管理中心” 

    ![Dynamics 365 管理中心](media/overview-model-driven-samples/admin-center.png)

4. 从列表中选择数据库，然后单击“打开”。

    ![选择数据库](media/overview-model-driven-samples/select-database.png)

5. 导航到“设置/解决方案”。

6. 为要删除的应用选择解决方案，然后单击“删除”。

    ![删除解决方案](media/overview-model-driven-samples/delete-solution.png)

或者通过单击创建者门户中的“高级”导航到解决方案列表，然后删除 URL 中 .Dynamics.com/ 后的所有内容**

> [!IMPORTANT]
> 除非了解所造成的影响，否则不要删除其他系统解决方案。

## <a name="install-or-uninstall-sample-data"></a>安装或卸载示例数据
1. 按照以上步骤 1-4 进行操作。
2. 导航到“设置/数据管理/示例数据”。
3. 如果安装了示例数据，则删除选项可用。 否则，安装选项可用。 

    ![删除示例数据](media/overview-model-driven-samples/remove-sample-data.png)




