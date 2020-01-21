---
title: 更新解决方案 | MicrosoftDocs
description: 了解如何在 Power Apps 中更新解决方案
ms.custom: ''
ms.date: 09/30/2019
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
ms.openlocfilehash: 534c4d986cec688723e6d3351135bca2692d020f
ms.sourcegitcommit: 212bd841595db0d6f41002f7ff9a1c8eb33a0724
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/20/2019
ms.locfileid: "2914307"
---
# <a name="update-solutions"></a>更新解决方案  

有时，您可能需要安装对现有托管解决方案的更新。 该过程类似于安装新的托管解决方案，但是会遇到一些不同的选项。 如果您要更新从其他人那里获取的解决方案，则应从解决方案发布商那里获取有关应选择哪些选项的指导。  
  
1.  在左侧导航中选择**解决方案**。
  
2.  在解决方案列表菜单，选择**导入**。  
  
3.  在**导入解决方案**对话框的**选择解决方案包**步骤中，选择**选择文件**并浏览找到包含要更新的解决方案的压缩（.zip 或 .cab）文件。

4.  选择**下一步**。  
  
5.  查看有关解决方案的信息，然后选择**下一步**。 该页面将无法显示一个黄色条，指示**此解决方案包中包含已安装的解决方案的更新** 。  
  
6.  您将具有以下选项：  
  
    - **维护自定义项（推荐）**  
  
         选择此选项将保留对组件执行的所有非托管自定义项，但也表示此解决方案中包含的某些更新将不会生效。  
  
    - **覆盖自定义项**  
  
         选择此选项会覆盖包括在此解决方案中的之前对组件执行的任何非托管的自定义项。 包括在此解决方案中的所有更新都将生效。  
  
     选择适合的选项，然后选择**下一步**。  
  
7.  在完成导入期间，可能需要等待一会儿。 查看结果，然后选择**关闭**。  
  
 如果导入了需要发布的任何更改，则这些自定义项只有在发布之后才可用。 
  
 解决方案发布商可能会要求您导入现有的非托管自定义项，使用该选项更新其托管解决方案来覆盖自定义项，然后重新导入您的非托管自定义项。 这将有助于确保应用他们预期的更改，同时保留您的自定义项。  
  
<a name="BKMK_ExportSolutions"></a>   

### <a name="see-also"></a>另请参阅
[导出解决方案](export-solutions.md) <br />
[分发解决方案和修补程序](use-segmented-solutions-patches-simplify-updates.md) <br />
[导入解决方案](import-update-export-solutions.md)