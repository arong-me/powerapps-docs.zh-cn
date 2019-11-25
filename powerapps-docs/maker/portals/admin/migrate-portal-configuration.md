---
title: 迁移门户配置 | MicrosoftDocs
description: 了解如何迁移门户配置。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 0aa057594b500c7019a4d645c70cafcfff183608
ms.sourcegitcommit: d9cecdd5a35279d78aa1b6c9fc642e36a4e4612c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/04/2019
ms.locfileid: "2755980"
---
# <a name="migrate-portal-configuration"></a>迁移门户配置

门户开发涉及多个配置和自定义来实现所需的门户最终用户体验。

在完成了您的门户实例的开发或配置后，您可能想要将您最新的门户配置从开发环境中迁移到测试或生产环境中。 迁移涉及从源 Common Data Service 环境中导出您现有的配置，然后再将其导入目标 Common Data Service 环境。

若要导出配置数据，您需要使用配置迁移工具和门户特定的配置架构文件。 有关此工具的详细信息，请参阅[管理配置数据 ](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-configuration-data)。

> [!NOTE]
> - 建议您使用配置迁移工具的最新版本。 可以从 NuGet 下载配置迁移工具。 有关下载工具的更多信息：[从 NuGet 下载工具](https://docs.microsoft.com/dynamics365/customer-engagement/developer/download-tools-nuget)。
> - 用于配置迁移的架构文件支持的门户的最低解决方案版本为 8.4.0.275。 但是，建议您使用解决方案的最新版本。

架构文件可用于以下门户类型：
- [社区门户](https://go.microsoft.com/fwlink/p/?linkid=2019704)
- [客户自助服务门户](https://go.microsoft.com/fwlink/p/?linkid=2019705)
- [合作伙伴门户](https://go.microsoft.com/fwlink/p/?linkid=2019803)
- [员工自助服务门户](https://go.microsoft.com/fwlink/p/?linkid=2019802)
- [自定义门户](https://go.microsoft.com/fwlink/p/?linkid=2019804)

默认的架构文件包含有关门户实体、关系和每个实体唯一性定义的信息。 详细信息：[导出门户配置数据](#export-portal-configuration-data)

导出配置数据后，必须将其导入目标环境。 详细信息：[导入门户配置数据](#import-portal-configuration-data)

> [!NOTE]
> 提供架构文件是为了减少从头构建架构所需的工作。 可以使用工具提供的标准方法针对您的实施定制架构。 可以在配置迁移工具中加载架构文件，并可以进行更改来添加、移除和修改实体、属性等。

## <a name="export-portal-configuration-data"></a>导出门户配置数据

可以使用门户特定的配置架构文件从源系统中导出门户配置数据。

1.  下载配置迁移工具并提取到所需的文件夹。

2.  使用上方为您的门户类型提供的链接下载门户配置架构。

3.  双击 `<your_folder>\Tools\ConfigurationMigration` 文件夹中的 **DataMigrationUtility.exe** 文件运行配置迁移工具，选择主屏幕中的**导出数据**，然后选择**继续**。
    
    > [!div class=mx-imgBorder]
    > ![导出配置数据](../media/export-config-data.png "导出配置数据")

4.  在**登录**屏幕上，请提供身份验证详细信息，以便从要导出数据的地方连接到您的 Common Data Service 环境。 如果您在要导出数据的 Common Data Service 环境中有多个组织，请选中**显示可用组织的列表**复选框，然后选择**登录**。

    > [!div class=mx-imgBorder]
    > ![提供身份验证详细信息以连接到要从其中导出数据的 Common Data Service 环境](../media/export-config-login.png "提供身份验证详细信息以连接到要从其中导出数据的 Common Data Service 环境")

5.  如果您有多个组织，并在上一步中选择了**显示可用的组织列表**复选框，下一个屏幕将让您选择您想连接上的组织。 选择要连接的 Common Data Service 环境。 

    > [!NOTE]
    > 如果没有多个组织，此屏幕不会显示。

6.  在**架构文件**中，浏览并选择要用于数据导出的门户特定配置架构文件。

7.  在**保存到数据文件**中，指定将导出的数据文件的名称和位置。

    > [!div class=mx-imgBorder]
    > ![指定架构和目标文件](../media/export-config-file-name.png "指定架构和目标文件")

8.  选择**导出数据**。 一旦该导出完成，在此屏幕底部显示导出进度状态和导出文件的位置。

    > [!div class=mx-imgBorder]
    > ![配置数据导出进度](../media/export-config-status.png "配置数据导出进度")

    > [!IMPORTANT]
    > 配置迁移工具不支持在实体中筛选记录。 默认情况下，将导出所选实体中的所有记录。 因此，如果您创建了多个网站记录，所有网站记录都将导出。

9.  选择**退出**关闭工具。

## <a name="import-portal-configuration-data"></a>导入门户配置数据

1.  运行配置迁移工具并在主屏幕中选择**导入数据**，然后选择**继续**。

    > [!div class=mx-imgBorder]
    > ![导入配置数据](../media/import-config-data.png "导入配置数据")

2.  在**登录**屏幕上，请提供身份验证详细信息，以便从要导出数据的地方连接到您的 Common Data Service 环境。 如果您在要导出数据的 Common Data Service 环境中有多个组织，请选中**显示可用组织的列表**复选框，然后选择**登录**。

3.  如果您有多个组织，并在上一步中选择了**显示可用的组织列表**复选框，下一个屏幕将让您选择您想连接上的组织。 选择要连接的 Common Data Service 环境。 

    > [!NOTE]
    > - 如果没有多个组织，此屏幕不会显示。
    > - 确保已为您计划要导入配置的组织安装门户解决方案。

4.  下一屏幕提示您提供要导入的数据文件 (.zip)。 浏览数据文件，选择该文件，然后选择**导入数据**。 

    > [!div class=mx-imgBorder]
    > ![配置数据导入进度](../media/import-config-status.png "配置数据导入进度")

5.  下一屏幕将显示您的导入状态记录。 数据导入分多个步骤完成，首先导入基础数据，同时队列化从属数据，然后在后续步骤中导入从属数据，以处理所有数据的从属或链接。 这可以保证导入的数据干净且一致。 

6.  选择**退出**关闭工具。 
