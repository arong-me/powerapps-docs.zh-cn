---
title: 迁移门户配置 |MicrosoftDocs
description: 了解如何迁移门户配置。
author: sbmjais
manager: shujoshi
ms.service: powerapps
ms.topic: conceptual
ms.custom: ''
ms.date: 10/07/2019
ms.author: shjais
ms.reviewer: ''
ms.openlocfilehash: 585f8e6c3ad1efcb047e2cbb0a516c3662c1a3eb
ms.sourcegitcommit: 5338e01d2591f76d71f09b1fb229d405657a0c1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/11/2019
ms.locfileid: "72975762"
---
# <a name="migrate-portal-configuration"></a>迁移门户配置

门户开发涉及多个配置和自定义，以获得门户最终用户所需的体验。

完成门户实例的开发或配置后，你可能需要将最新的门户配置从开发迁移到测试或生产环境。 迁移涉及从源 Common Data Service 环境导出现有配置，然后将其导入目标 Common Data Service 环境。

若要导出配置数据，则需要使用配置迁移工具和特定于门户的配置架构文件。 有关此工具的详细信息，请参阅[管理配置数据](https://docs.microsoft.com/dynamics365/customer-engagement/admin/manage-configuration-data)。

> [!NOTE]
> - 建议使用最新版本的配置迁移工具。 可以从 NuGet 下载配置迁移工具。 有关下载工具的详细信息：[从 NuGet 下载工具](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/download-tools-nuget)。
> - 用于配置迁移的架构文件支持的门户最低解决方案版本为8.4.0.275。 但是，我们建议使用最新的解决方案版本。

架构文件可用于以下门户类型：
- [社区门户](https://go.microsoft.com/fwlink/p/?linkid=2019704)
- [客户自助服务门户](https://go.microsoft.com/fwlink/p/?linkid=2019705)
- [合作伙伴门户](https://go.microsoft.com/fwlink/p/?linkid=2019803)
- [员工自助服务门户](https://go.microsoft.com/fwlink/p/?linkid=2019802)
- [自定义门户](https://go.microsoft.com/fwlink/p/?linkid=2019804)

默认架构文件包含有关每个实体的门户实体、关系和唯一性定义的信息。 详细信息：[导出门户配置数据](#export-portal-configuration-data)

导出配置数据后，必须将其导入到目标环境中。 详细信息：[导入门户配置数据](#import-portal-configuration-data)

> [!NOTE]
> 提供架构文件是为了减少从头开始生成架构所需的工作量。 可以使用工具提供的标准方法为实现定制架构。 可以在配置迁移工具中加载架构文件，并将其更改为添加、删除和修改实体、属性等。

## <a name="export-portal-configuration-data"></a>导出门户配置数据

你可以通过使用特定于门户的配置架构文件从源系统中导出门户配置数据。

1.  下载配置迁移工具并提取到所需的文件夹。

2.  使用上面为门户类型提供的链接下载门户配置架构文件。

3.  双击 `<your_folder>\Tools\ConfigurationMigration` 文件夹中的**DataMigrationUtility**文件以运行配置迁移工具，选择主屏幕中的 "**导出数据**"，然后选择 "**继续**"。
    
    > [!div class=mx-imgBorder]
    > ![导出配置数据](../media/export-config-data.png "导出配置数据")

4.  在**登录**屏幕上，提供身份验证详细信息以连接到要从中导出数据的 Common Data Service 环境。 如果在 Common Data Service 环境中有多个组织从何处导出数据，请选中 "**显示可用组织的列表**" 复选框，然后选择 "**登录**"。

    > [!div class=mx-imgBorder]
    > ![提供身份验证详细信息以连接到要从中导出数据的 Common Data Service 环境]，(../media/export-config-login.png "提供身份验证详细信息以连接到要从中导出数据的 Common Data Service 环境")

5.  如果你有多个组织，并且已在上一步中选中了 "**可用组织的显示列表**" 复选框，则下一屏幕将允许你选择要连接到的组织。 选择要连接到的 Common Data Service 环境。 

    > [!NOTE]
    > 如果没有多个组织，则不会显示此屏幕。

6.  在 "**架构文件**" 中，浏览并选择要用于数据导出的特定于门户的配置架构文件。

7.  在 "**保存到数据文件**" 中，指定要导出的数据文件的名称和位置。

    > [!div class=mx-imgBorder]
    > ![指定架构和目标文件](../media/export-config-file-name.png "指定架构和目标文件")

8.  选择 "**导出数据**"。 导出完成后，屏幕将显示导出进度状态以及导出文件在屏幕底部的位置。

    > [!div class=mx-imgBorder]
    > 配置数据导出(../media/export-config-status.png "进度的")![配置]数据导出进度

    > [!IMPORTANT]
    > 配置迁移工具不支持筛选实体中的记录。 默认情况下，将导出所选实体中的所有记录。 因此，如果你创建了多个网站记录，将导出所有网站记录。

9.  选择 "**退出**" 以关闭工具。

## <a name="import-portal-configuration-data"></a>导入门户配置数据

1.  运行配置迁移工具，并选择主屏幕中的 "**导入数据**"，然后选择 "**继续**"。

    > [!div class=mx-imgBorder]
    > ![导入配置数据](../media/import-config-data.png "导入配置数据")

2.  在**登录**屏幕上，提供身份验证详细信息以连接到要从中导出数据的 Common Data Service 环境。 如果在 Common Data Service 环境中有多个组织从何处导出数据，请选中 "**显示可用组织的列表**" 复选框，然后选择 "**登录**"。

3.  如果你有多个组织，并且已在上一步中选中了 "**可用组织的显示列表**" 复选框，则下一屏幕将允许你选择要连接到的组织。 选择要连接到的 Common Data Service 环境。 

    > [!NOTE]
    > - 如果没有多个组织，则不会显示此屏幕。
    > - 请确保已为计划导入配置的组织安装门户解决方案。

4.  下一个屏幕会提示你提供要导入的数据文件（.zip）。 浏览到数据文件，选择它，然后选择 "**导入数据**"。 

    > [!div class=mx-imgBorder]
    > 配置数据导入的![配置数据导]入(../media/import-config-status.png "进度")进度

5.  下一屏幕显示记录的导入状态。 数据导入是在多个阶段中完成的，以便在排队依赖数据时首先导入基础数据，然后导入后续传递中的相关数据来处理任何数据依赖关系或链接。 这可确保数据导入干净和一致。 

6.  选择 "**退出**" 以关闭工具。 
