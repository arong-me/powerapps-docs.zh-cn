---
title: 教程：借助 PowerApps 创建带组件的自定义实体 | Microsoft Docs
description: 本教程提供分步说明，介绍如何创建并配置实体以将其与 PowerApps 应用结合使用。
services: ''
suite: powerapps
documentationcenter: na
author: Mattp123
manager: bycho
editor: ''
tags: ''
ms.service: powerapps
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 03/21/2018
ms.author: matp
ms.openlocfilehash: 3fd8b262849fb1f6bf2a7ff70d9d9af8b082efac
ms.sourcegitcommit: 59785e9e82da8f5bd459dcb5da3d5c18064b0899
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-create-a-custom-entity-that-has-components-in-powerapps"></a>教程：在 PowerApps 中创建带组件的自定义实体

可借助 [!INCLUDE [powerapps](../../includes/powerapps.md)]，基于组织的行业、命名法和独特的业务流程量身定制应用。 [!INCLUDE [powerapps](../../includes/powerapps.md)] 应用开发包括添加“现成的”标准实体或创建自定义实体。 实体定义要跟踪的信息（采用记录的形式），通常包括公司名称、位置、产品、电子邮件和电话号码等属性。 

本教程创建一个实体并添加或自定义关键组件，例如字段、关系、视图和窗体。 了解如何：

- 创建自定义实体
- 将自定义字段添加到实体
- 添加实体关系
- 自定义视图 
- 自定义窗体

> [!IMPORTANT]
> [!INCLUDE [cc-preview-features-definition](../../includes/cc-preview-features-definition.md)]

本教程以 Contoso 公司为例，该公司是为狗和猫提供美容护理服务的宠物美容护理公司。 Contoso 需要一款供员工使用、用于客户和宠物跟踪且能够在多种设备上使用的应用。

## <a name="prerequisites"></a>先决条件

登录 [PowerApps](https://powerapps.microsoft.com/)。 如果尚不拥有 [!INCLUDE [powerapps](../../includes/powerapps.md)] 帐户，请从 [powerapps.com](https://web.powerapps.com) 中选择“免费开始使用”链接。

## <a name="create-a-custom-entity"></a>创建自定义实体

1. 在 Common Data Service 下的左侧导航窗格上选择“实体”，然后选择“新建实体”。
    ![新建实体](media/create-custom-entity/create-new-entity.png)
2. 在右侧窗格中，输入下列值，然后选择“下一步”。
  - **显示名称**：宠物 
  - **描述**：用于跟踪宠物服务的自定义实体
3. 选择“保存实体”。

## <a name="add-and-customize-fields"></a>添加和自定义字段

1. 在“字段”选项卡上选择“主要名称”字段。
2. 在右侧窗格中，对“主要名称”字段做出以下更改： 
  - 将“显示名称”从“主要名称”更改为“宠物名称”
  - 选中“可搜索”

    ![更改主要字段](media/create-custom-entity/primary-field.png)
3. 选择“完成”。
4. 在实体设计器工具栏上选择“添加”字段。 在“字段属性”窗格中输入或选择下列值和选项。
  - **显示名称**。 种类
  - **数据类型**。 选项集
  - **选项集**。 新
5. 创建选项集

  a. 选择“添加新项”。 
  
  b. 将“新选项”替换为“狗”。 
   
  c. 选择“添加新项”。 
    
  d.  将“新选项”替换为“猫”。 
    
  e. 选择“保存”。 

  ![新选项集](media/create-custom-entity/optionset-add-items.png)

6. 选中“可搜索”，然后选择“完成”。

7. 在实体设计器工具栏上选择“添加字段”。 在“字段属性”窗格中输入或选择下列值，然后选择“完成”。
  - **显示名称**。 品种
  - **数据类型**。 *文本*
  - **可搜索**。 是

8. 在实体设计器工具栏上选择“添加字段”。 

9. 在“字段属性”窗格中输入或选择下列值，然后选择“完成”。 
  - **显示名称**。 预约日期
  - **数据类型**。 日期和时间

10. 选择“保存实体”。

## <a name="add-a-relationship"></a>添加关系

1. 选择“关系”选项卡，然后在实体设计器工具栏上选择“添加关系”。 
2. 在右侧窗格上，在“相关实体”列表中选择“帐户”，然后选择“完成”。
3. 选择“保存实体”。

请注意，在添加关系时，会自动在字段选项卡上的字段列表中添加一个数据类型为“查找”的字段。![帐户查找字段](media/create-custom-entity/account-lookup-field.png)

## <a name="customize-a-view"></a>自定义视图

1. 选择“视图”选项卡，然后选择“活动宠物”视图。
2. 在视图设计器上选择“添加列”，选择以下列，然后选择“确定”。
  - 帐户
  - 预约日期 
  - 品种 
  - 种类
3. 选择“创建日期”列，选择“删除”，然后选择“确定”以确认删除此列。
4. 若要将这些列进行排列，选择要移动的列，然后使用 <- 和 -> 箭头按钮，直到视图如下显示为止。
    ![活动宠物视图](media/create-custom-entity/active-pets-view.png)
5. 在视图设计器工具栏上选择“保存并关闭”。  
6. 选择“保存实体”。

## <a name="model-driven-apps-only-customize-the-main-form"></a>仅限模型驱动应用：自定义主窗体

如果只想在画布应用中使用“宠物”实体，请跳过此步骤。 

1. 在 [!INCLUDE [powerapps](../../includes/powerapps.md)] 左侧导航窗格中，选择“模型驱动”。
2. 在左侧导航栏中，选择“高级”。
3. 在解决方案窗口的左侧导航窗格中，选择“实体”，展开“宠物”，然后选择“窗体”。
4. 选择“主要”窗体类型旁边的“信息”以打开窗体编辑器。
    ![编辑主窗体](media/create-custom-entity/main-form-edit.png)
5. 在窗体编辑器上，将字段资源管理器窗格上的“种类”、“品种”、“预约日期”和“帐户”字段拖放至窗体画布的“常规”部分，使窗体显示如下。
    ![为主窗体选择字段](media/create-custom-entity/main-form-edit2.png) 
6. 选择“保存并关闭”。
7. 在解决方案窗口中，选择“发布所有自定义项”。
    ![发布所有自定义项](media/create-custom-entity/publish-all-customizations.png)

## <a name="add-the-custom-entity-to-an-app"></a>将自定义实体添加到应用

现在实体已可用于构建画布应用或模型驱动应用了。 

## <a name="next-steps"></a>后续步骤

本教程介绍了如何创建可用于构建有用应用的实体。 若要了解如何创建画布应用，请参阅[从头开始创建应用](../canvas-apps/get-started-create-from-blank.md)。
