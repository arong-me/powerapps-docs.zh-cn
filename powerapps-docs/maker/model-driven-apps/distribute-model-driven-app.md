---
title: 使用解决方案分发模型驱动应用程序 | MicrosoftDocs
description: 了解如何使用解决方案分发模型驱动应用程序
keywords: ''
ms.date: 08/06/2018
ms.service: powerapps
ms.custom: ''
ms.topic: article
applies_to:
- Dynamics 365 (online)
- Dynamics 365 Version 9.x
- powerapps
ms.assetid: e82e7f64-37ad-41e5-acd7-16309881c6a2
author: Mattp123
ms.author: matp
manager: kvivek
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
caps.latest.revision: 9
topic-status: Drafting
search.audienceType:
- maker
search.app:
- PowerApps
- D365CE
ms.openlocfilehash: 2d9c6692f26e16b03872696b094ccd14a649299f
ms.sourcegitcommit: 861ba8e719fa16899d14e4a628f9087b47206993
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "2873165"
---
# <a name="distribute-a-model-driven-app-using-a-solution"></a>使用解决方案分发模型驱动应用程序

模型驱动应用作为解决方案组件分发。 创建模型驱动应用后，可将其提供给其他环境使用，方法是将应用打包为解决方案，然后导出到 zip 文件中。 在目标环境中成功导入解决方案（.zip 文件）后，即可使用打包的应用。 
  
## <a name="add-an-app-to-a-solution"></a>向解决方案中添加应用程序
为了分发应用程序，您创建解决方案，以可以打包应用程序以供导出。

1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

2. 选择**解决方案**，然后选择**新建解决方案**。
3. 在**新建解决方案**页上填写字段，然后选择**保存**。 详细信息：[创建解决方案](../common-data-service/create-solution.md)
4. **解决方案**页将显示。 选择**添加现有**，选择**应用程序**，选择要添加到解决方案的应用程序，然后选择**确定**。 

    ![选择解决方案组件](media/select-solution-components.png)

5. 如果**缺少必需组件**页显示，建议您选择**是，包含必需组件**添加必要的组件，如属于应用程序一部分的实体、视图、窗体、图表和站点地图。 选择**确定**。
6. 在**解决方案**页上，选择**保存并关闭**。

## <a name="export-a-solution"></a>导出解决方案
若要分发应用程序以便可以将其导入到其他环境，或让其在 [Microsoft AppSource](https://appsource.microsoft.com/) 中可用，将解决方案导出到 zip 文件。 然后，包含应用程序和组件的 zip 文件可以导入到其他环境中。

1. 打开[解决方案页](advanced-navigation.md#solutions)。 
2. 选择要导出的解决方案，然后在工具栏上选择**导出**。 
3. 在**发布自定义项**页上，选择**下一步**。
4. 如果**缺少必需组件**页显示，选择**下一步**。 
5. 在**导出系统设置**页，选择您要包括的可选功能，然后选择**下一步**。 
6. 在**包类型**页上，选择**非托管**或**托管**，然后选择**导出**。 有关解决方案包类型的详细信息，请参阅[解决方案概述](../common-data-service/solutions-overview.md)。
7. 根据您的浏览器和设置，.zip 包文件建立并复制到默认下载文件夹。 包的文件名基于后面追加有下划线和解决方案版本号的解决方案的唯一名称。

    > [!NOTE]
    > 在使用解决方案导出应用时，应用 URL 不导出。
  
## <a name="import-a-solution"></a>导入解决方案  
收到包含要导入的应用的解决方案 zip 文件时，请打开解决方案组件页，然后导入解决方案。 成功导入解决方案后，应用程序将在您的环境中可用。

1. 登录到 [Power Apps](https://make.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。

2. 选择**解决方案**，然后在工具栏上选择**导入**。
3. 浏览到要导入的文件，然后选择**下一步**。
4. 选择**导入**。

## <a name="see-also"></a>另请参阅
[更改解决方案发布商前缀](../common-data-service/change-solution-publisher-prefix.md)
