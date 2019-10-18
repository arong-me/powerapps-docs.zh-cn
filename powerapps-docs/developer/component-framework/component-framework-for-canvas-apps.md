---
title: 用于画布应用的 PowerApps 组件框架 |Microsoft Docs
description: 为画布应用创建代码组件
keywords: ''
ms.author: nabuthuk
author: Nkrb
manager: kvivek
ms.date: 08/31/2019
ms.service: powerapps
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5d100dc3-bd82-4b45-964c-d90eaebc0735
ms.openlocfilehash: e1c6b4bad1280bdabf8c27e30396b368276ff10b
ms.sourcegitcommit: 2a3430bb1b56dbf6c444afe2b8eecd0e499db0c3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2019
ms.locfileid: "72347213"
---
# <a name="powerapps-component-framework-for-canvas-apps"></a>用于画布应用的 PowerApps 组件框架

> [!IMPORTANT]
> 此功能在默认情况下仍处于实验和禁用状态。 有关详细信息，请参阅[实验性和预览功能](../../maker/canvas-apps/working-with-experimental.md)。

PowerApps 组件框架使应用程序开发人员能够创建可在应用程序中或应用程序中使用的代码组件。 详细信息： [PowerApps 组件框架概述](overview.md) 

在此实验性预览中，PowerApps 组件框架使应用开发人员能够使用 PowerApps CLI 工具创建代码组件、调试、导入和添加到画布应用。 此实验预览版仅支持特定的 Api。 建议你检查每个 API，以确定它是否支持画布应用。 

> [!WARNING]
> 代码组件包含可能不由 Microsoft 生成并且可能会访问安全令牌和数据的代码。 向应用程序添加代码组件时，请确保代码组件解决方案来自受信任的源。

## <a name="prerequisites"></a>必备组件

若要启用环境中的 PowerApps 组件功能，需要具有系统管理员特权。

> [!IMPORTANT]
> 默认情况下，对模型驱动应用启用 PowerApps 组件框架。

## <a name="enable-powerapps-component-framework-feature"></a>启用 PowerApps 组件框架功能

若要向应用程序添加代码组件，需要在要使用它们的每个环境中启用 PowerApps component framework 功能。 允许环境在其应用中使用代码组件：

1. 登录 [PowerApps](https://powerapps.microsoft.com/en-us/)。

2. 选择 "**设置**" 图标，然后选择 "**管理中心**"。
    
    ![设置和管理中心](media/select-admin-center-from-settings.png "设置与管理中心") 

3. 选择要在其中启用此功能的环境，选择省略号（ **...** ），然后选择 "**设置**"。

4. 在 "**产品**" 选项卡下，选择 "**功能**"。

   ![启用 powerapps 组件框架](media/enable-pcf-feature.png "启用 powerapps 组件框架")

5. 从可用功能列表中，在 "**用于画布的 PowerApps 组件框架**" 下，将开关设置为**On** 。

6. 现在，打开要在其中添加代码组件的应用程序，然后导航到 "**文件**"  >  "**应用程序设置**"，然后选择 "**高级设置**"。

   ![为]powerapps 组件框架启用组件为(media/enable-components-for-pcf.png "powerapps 组件框架启用组件")
   
7. 在**实验性功能**部分下，将**组件**切换到 **"打开**"。

## <a name="implementing-code-components"></a>实现代码组件

在您的环境中启用 PowerApps 组件框架功能后，可以开始实现代码组件的逻辑。 "[实现示例组件](implementing-controls-using-typescript.md)" 主题演示了创建代码组件以实现自定义逻辑和清单文件、运行调试过程、创建解决方案 zip 文件以及将解决方案导入常见的分步过程。数据服务。

> [!NOTE]
> 对于模型驱动的应用程序和画布应用程序，实现代码组件是相同的（实验预览版）。 唯一的区别是添加代码组件。 

## <a name="add-components-to-a-canvas-app"></a>将组件添加到画布应用

> [!NOTE]
> 若要将代码组件添加到模型驱动应用的字段或实体，请参阅[向模型驱动应用添加代码组件](add-custom-controls-to-a-field-or-entity.md)

向画布应用程序添加代码组件：

1. 导航到 PowerApps Studio。
2. 创建新的画布应用或编辑要添加代码组件的现有应用。

   > [!IMPORTANT]
   > 在继续下一步之前，请确保解决方案 zip 文件已[导入](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/import-update-export-solutions)Common Data Service。

3. 请参阅在**导入组件** > **插入** > **组件**。 
 
    ![插入组件](media/insert-components-import.png "插入组件")

4. 选择 "**代码（实验）** " 选项卡，从列表中添加组件，然后选择 "**导入**"。 这会在 "**组件**" 菜单中添加示例组件。

    ![导入示例组件](media/import-component-add-sample-component.png "导入示例组件")

5. 导航到 "**组件**"，然后选择要添加到应用的组件。

   ![添加示例组件](media/add-sample-component-from-list.png "添加示例组件")

## <a name="delete-a-code-component"></a>删除代码组件 

若要从画布应用中删除代码组件，请选择要删除的代码组件，然后选择菜单上的 "**删除**" 按钮。 从应用中删除代码组件时，所有代码组件元素都将从应用和应用包中删除。 

## <a name="update-existing-code-components"></a>更新现有代码组件

更新代码组件时，将在清单文件中指定*version*属性，以便在运行时中反映最新的更改。 对于画布应用，更新现有代码组件时，无需更新*版本*属性。 按照设计，画布应用选取最新的代码组件，并在运行时中显示它。 画布应用中只能存在同一组件的单个版本。

> [!NOTE]
> 仅当在 PowerApps Studio 关闭或重新打开应用程序时，才会更新现有代码组件。 当你重新打开应用程序时，它会要求你更新代码组件。 只需删除代码组件或将代码组件添加回应用程序，就不会更新组件。

## <a name="see-also"></a>另请参阅

[PowerApps 组件框架概述](overview.md)<br/>
[实现示例组件](implementing-controls-using-typescript.md)

