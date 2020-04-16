---
title: 更新解决方案 | MicrosoftDocs
description: 了解如何在 Power Apps 中更新或升级解决方案
ms.custom: ''
ms.date: 03/18/2020
ms.reviewer: ''
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
author: Mattp123
ms.assetid: ''
ms.author: matp
manager: kvivek
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 0bebbc9eeead8fb4f02c4bf958c33b79c0d9cc1c
ms.sourcegitcommit: 48414442a10210d49911c3eda8b49f68db85f684
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2020
ms.locfileid: "3151162"
---
# <a name="upgrade-or-update-a-solution"></a>升级或更新解决方案  
有时，您需要更新现有托管解决方案。 若要更新解决方案，请执行以下步骤： 

1.  在开发环境中打开非托管解决方案，新建组件或添加、删除所需的现有组件。 
2.  在将解决方案作为托管解决方案导出时，递增版本号。 详细信息：[了解更新的版本号](#understanding-version-numbers-for-updates) 

    > [!div class="mx-imgBorder"] 
    > ![更新解决方案版本](media/update-solution-version.png)
3. [在目标环境中应用升级或更新](#apply-the-upgrade-or-update-in-the-target-environment)

## <a name="apply-the-upgrade-or-update-in-the-target-environment"></a>在目标环境中应用升级或更新
导入更新的解决方案的过程类似于安装新的托管解决方案，但是会遇到一些不同的选项。 如果您要更新从其他人那里获取的解决方案，则应从解决方案发布商那里获取有关应选择哪些选项的指导。  

1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)，选择所需的目标环境，然后从左侧导航中选择**解决方案**。  

2. 在命令栏上选择**导入**。  

3. 在**选择解决方案包**页中，选择**浏览**找到包含要更新的解决方案的压缩（.zip 或 .cab）文件。  

4. 选择**下一步**。  

5. 在您选择**下一步**前可以查看关于解决方案的信息。 该页面将无法显示一个黄色条，指示**此解决方案包中包含已安装的解决方案的更新** 。  

6. 在以下解决方案操作选项中进行选择：  
   - **升级(推荐)** 此选项将您的解决方案升级到最新版本，并通过一个步骤汇总之前的所有修补程序。  将删除与上一个解决方案版本关联，但较高解决方案版本中不包含的所有组件。 这是推荐选项，因为可以确保生成的配置状态与正在导入的解决方案一致，包括删除解决方案中不再包含的组件。
        
   - **升级对应的阶段** 此选项会将您的解决方案升级到更高版本，但会推迟删除先前版本和任何相关的修补程序，直到您稍后应用解决方案升级。  仅当要同时在系统中安装新旧解决方案，以便在完成解决方案升级之前执行一些数据迁移，才应选择此选项。 这将删除旧解决方案和新解决方案中不包含的所有组件。
        
   - **更新(不推荐)** 此选项将把您的解决方案替换为此版本。  不在较新解决方案中的组件将不会被删除，仍将保留在系统中。  不推荐使用此选项，因为目标环境的配置将与源环境的配置不同，并且可能导致难以重现和诊断的问题。
        
7. 可从以下自定义选项中选择：

   - **维护自定义项（推荐）**  

        选择此选项将保留对组件执行的所有非托管自定义项，但也表示此解决方案中包含的某些更新将不会生效。  

   - **覆盖自定义(不推荐)**  

        选择此选项会覆盖或删除包括在此解决方案中的之前对组件执行的任何非托管的自定义项。 此选项不影响支持合并行为的组件（窗体、站点地图、功能区、应用程序模块）。  在要替换的现有解决方案顶部具有其他托管解决方案的组件仍然留在顶部，不受此选项影响。  

8. 决定是否为导入后操作启用以下选项：
   - **启用解决方案中包含的任何 SDK 消息处理步骤**  
        选择此选项将启用解决方案中不包含的插件和工作流。
        
9. 选择**下一步**。  

10. 在完成解决方案导入期间，可能需要等待一会儿。 若此不成功，则您可以查看结果并选择**关闭**。  

   如果导入了需要发布的任何更改，则这些自定义项只有在发布之后才可用。 

**完成解决方案升级** 如果选择升级对应的阶段，或者如果在完成升级时系统出错，您将发现您的原始解决方案和与基础解决方案同名，但带有后缀 \_Upgrade 的新解决方案仍然安装在您的系统中。  若要完成升级，在解决方案列表中选择基础解决方案，然后选择**应用解决方案升级**。  这将卸载所有之前修补程序和基础解决方案，然后将 \_Upgrade 解决方案重命名为与上一个基础解决方案同名。  此过程中，将删除原始解决方案中的所有组件，以及 \_Upgrade 解决方案中不包含的修补程序。

## <a name="understanding-version-numbers-for-updates"></a>了解更新的版本号
解决方案的版本具有以下格式：major.minor.build.revision。 更新必须具有比父解决方案更高的主要、次要、内部版本号或修订号。 例如，对于基本解决方案版本 3.1.5.7，一个小更新可以是版本 3.1.5.8，或者一个稍大的更新可以是版本 3.1.7.0。 非常重大的更新可以是版本 3.2.0.0。


### <a name="see-also"></a>另请参阅
[添加解决方案组件](create-solution.md#add-solution-components) <br />
[导出解决方案](export-solutions.md) <br />
[导入解决方案](import-update-export-solutions.md)