---
title: "在环境和租户之间迁移应用 | Microsoft 文档"
description: "在环境和租户之间迁移应用"
services: 
suite: powerapps
documentationcenter: na
author: jamesol-msft
manager: anneta
editor: 
tags: 
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 07/28/2017
ms.author: jamesol
ms.openlocfilehash: 2d25e6ddbaf15991655ffa94bbf9578946504f0e
ms.sourcegitcommit: 43be6a4e08849d522aabb6f767a81c092419babc
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2017
---
# <a name="environment-and-tenant-app-migration-through-packaging"></a>通过打包进行环境和租户应用迁移
了解如何通过打包将资源从一个环境迁移到另一个环境。 这些环境可以位于同一租户中，也可以跨不同的租户。

## <a name="the-scenario"></a>场景
可能需要迁移资源的一种常见场景是，你有一个测试或开发环境，同时又有一个生产环境。 开发人员和测试人员对其环境中的应用进行访问时，其权限很宽松。 但将新应用迁移到生产环境中时，对更新和更改权限的控制会很严格。

另一场景是，每个客户都有其自己的环境和数据， 添加新客户时，将为其创建新环境，然后再将应用迁移到环境中。

## <a name="which-resources-can-i-migrate-through-packaging"></a>可以通过打包迁移哪些资源？
导出应用时，应用的从属资源也会导出到包中。  最初仅支持所有可能的资源类型的子集，如下表所示。

| 资源类型 | 受支持 | 导入选项 |
| --- | --- | --- |
| 应用 |是 |有两个选项可用于将应用导入到环境： <ol><li><b>新建</b> – 在导入包的环境中将此应用创建为新应用。</li> <li><b>更新</b> - 环境中已存在此应用，导入此包后将更新此应用。</li></ol> |
| 流 |是 |有两个选项可用于将流导入到环境： <ol><li><b>新建</b> – 在导入包的环境中将此流创建为新流。</li> <li><b>更新</b> - 环境中已存在此流，导入此包后将更新此流。</li></ol> <div> <i>注意：流依赖的所有资源也会包含在导出的应用包内，并需要使用导入的包进行配置。</i> |
| CDS 实体自定义项和选择列表 |是 |有两个选项可用于将 CDS 实体或选择列表导入环境： <ol><li><b>覆盖</b> - 如果有使用相同名称的资源，导入后将替换此资源。 如果没有匹配的资源，将创建新资源。 <li><b>合并</b> – 如果有使用相同名称的实体或选择列表，则会添加新字段或实体，但不会删除缺失的字段或条目。</li></ol> |
| 自定义连接器 |否 |应用依赖自定义连接器时，当前不<b></b>支持将连接器导出为包的一部分。 <p></p> 如果应用依赖自定义连接器，目前唯一的选择是在目标环境中手动重新创建或更新该连接器，并在导入包时选择该连接器。 |
| 连接 |否 |应用依赖连接（例如带凭据的 SQL 连接）时，当前不支持将连接或凭据导出为包的一部分。 <p></p> 如果应用依赖共享连接（例如 SQL），目前唯一的选择是，使用相应的凭据在目标环境中手动重新创建该连接，并在导入包时选择该连接。 |
| CDS 自定义角色和权限集 |否 |当前不支持导出自定义 CDS 角色和/或权限集，因此目前唯一的选择是在目标环境中手动重新创建这些实体。 |
| 网关 |否 |网关仅在默认（和 {租户名称}（预览版提供））环境中受支持，因此不能导出/迁移。 |
| CDS 数据行 |否 |当前不支持导出 CDS 实体中的行，因此目前唯一的选择是，在新环境中应用 CDS 架构更改后，手动[导出和导入](data-platform-export-data.md)数据。 |

## <a name="how-do-i-get-access-to-packaging-for-my-app"></a>如何获取打包应用的权限？
拥有应用“编辑”权限的所有用户均可导出应用。

拥有目标环境的“环境制作”权限的所有用户均可导入应用。

用户必须拥有 PowerApps 计划 2 或 PowerApps 计划 2 试用版许可证才能导出或导入任何应用。

注意：虽然打包功能目前处于预览状态，但是所有拥有 PowerApps 有效许可证的用户均可在他们的应用和环境上试用打包功能。

## <a name="exporting-an-app"></a>导出应用
1. 在 http://web.powerapps.com 中，单击或点击“应用”，选择省略号以找到想要迁移的应用，然后选择“导出(预览)”。
   
    ![选择导出](./media/environment-and-tenant-migration/select-export.png)
2. 导出包页打开后，为包输入“名称”和“说明”。
   
    ![查看包详细信息](./media/environment-and-tenant-migration/package-details.png)
3. 在“审阅包内容”部分中，可以选择添加评论或备注，或更改包导入期间将每个资源导入到目标环境的方式的设置。
   
    ![配置包内容](./media/environment-and-tenant-migration/export-package-content.png)
4. 选择“导出”后，将在几秒内开始下载包文件。

## <a name="importing-an-app"></a>导入应用
1. 在 http://web.powerapps.com 中，单击或点击“应用”，然后选择“导入包(预览)”。
   
    ![选择导入](./media/environment-and-tenant-migration/select-import.png)
2. 选择“上传”，然后选择要导入的应用包文件。
   
    ![选择包文件](./media/environment-and-tenant-migration/select-file.png)
3. 上传包后，需要查看包内容并需要为标有红色图标的所有项输入其他内容（选择各个项的扳手图标并输入所需信息）。
   
    ![查看包内容](./media/environment-and-tenant-migration/import-package-content.png)
4. 提供所有所需信息后，选择“导入”。
   
    ![更新的打包内容](./media/environment-and-tenant-migration/import-package-content-dirty.png)
5. 导入完成后，将自动重定向到一个页面（如下所示），提示导入操作是否已成功。
   
    ![查看导入结果](./media/environment-and-tenant-migration/import-results.png)

> 注意：如果在导入应用时选择了“更新”现有应用，新更改内容将被保存为此应用程序的草稿。  需要[发布](http://powerapps.microsoft.com/tutorials/save-publish-app/#publish-an-app)这些更改才能让此应用程序的所有其他用户获取这些更改。
> 
> 

## <a name="known-limitations"></a>已知的限制
| 限制 | 状态 |
| --- | --- |
| 根据报告，导入的应用包包含 3 个以上的资源时，需要几分钟的时间才能完成。 |这是一个已知问题，即将推出修复程序。 |

