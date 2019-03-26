---
title: 模型驱动示例应用程序
description: 了解如何获取、自定义和删除模型驱动示例应用程序。
documentationcenter: na
author: mr-dang-msft
manager: kvivek
ms.service: powerapps
ms.devlang: na
ms.topic: conceptual
ms.component: model
ms.date: 03/08/2018
ms.author: brdang
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="model-driven-sample-apps"></a>模型驱动示例应用程序

在 [powerapps.com](https://powerapps.com) 中，使用示例应用程序探索设计的可能性，在开发您自己的应用程序时发现您可以应用的概念。 每个示例应用程序使用虚构数据来演示真实的情形。 

请务必查看每个示例应用程序的特定文档来了解更多详细信息。 

![Fundraiser 示例应用程序](media/overview-model-driven-samples/fundraiser-app1.png)


## <a name="get-sample-apps"></a>获取示例应用程序

为了运行或编辑模型驱动示例应用程序，必须首先在 Common Data Service 数据库中设置应用程序。 请先创建试用环境和数据库，并务必选中**包含示例应用程序和数据**。

![创建数据库](media/overview-model-driven-samples/create-database1.png)


> [!IMPORTANT]
> 此选项在数据库中安装所有可用的示例应用程序。 示例应用程序用于培训和演示目的，我们不建议在生产数据库中安装它们。 

## <a name="customize-a-sample-app"></a>自定义示例应用程序

1. 登录到 [powerapps.com](https://powerapps.com)  

    

2. 在**创建**页中，将鼠标悬停在示例应用程序上并单击**制作此应用**。

![示例模型应用](media/overview-model-driven-samples/model-driven-create-page-sample.png)

3. 应用程序设计器将打开，其中提供用于自定义应用程序的多个选项。 
4. 要查看其他自定义选项，从门户的左侧导航单击**高级**。

## <a name="remove-sample-apps-and-data"></a>删除示例应用程序和数据 
- 删除示例应用程序需要删除相应的[托管解决方案](https://docs.microsoft.com/dynamics365/customer-engagement/developer/uninstall-delete-solution)。 
- 删除解决方案也会删除特定于应用程序的自定义实体的任何示例数据。
- 如果对示例应用程序进行了自定义，则可能存在[依赖项](https://docs.microsoft.com/dynamics365/customer-engagement/developer/dependency-tracking-solution-components)，其必须在删除解决方案之前删除。

### <a name="steps"></a>步骤
1. 登录到 [PowerApps 管理门户](https://admin.powerapps.com)。

2. 选择环境。

3. 单击 **Dynamics 365 Administration Center** 

    ![Dynamics 365 管理中心](media/overview-model-driven-samples/admin-center.png)

4. 从列表中选择您的数据库并单击**打开**。

    ![选择数据库](media/overview-model-driven-samples/select-database.png)

5. 导航到**设置/解决方案**。

6. 选择要删除的应用程序的解决方案并单击**删除**。

    ![删除解决方案](media/overview-model-driven-samples/delete-solution.png)

*或者通过单击制造者门户中的**高级**导航到解决方案列表，并删除 URL 中 .dynamics.com/ 后面的部分*

> [!IMPORTANT]
> 除非您了解影响，否则请不要删除其他系统解决方案。

## <a name="install-or-uninstall-sample-data"></a>安装或卸载示例数据
1. 按照上面的步骤 1-4 操作。
2. 导航到**设置/数据管理/示例数据**。
3. 如果示例数据已安装，删除选项将可用。 否则安装选项可用。 

    ![删除示例数据](media/overview-model-driven-samples/remove-sample-data.png)




