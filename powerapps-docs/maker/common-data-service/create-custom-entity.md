---
title: 使用 PowerApps 创建包含组件的自定义实体 | Microsoft Docs
description: 包含创建和配置实体以使用 PowerApps 应用的分步说明的主题。
author: Mattp123
manager: kvivek
ms.service: powerapps
ms.component: cds
ms.topic: tutorial
ms.date: 01/23/2019
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-a-custom-entity-that-has-components-in-powerapps"></a>在 PowerApps 中创建包含组件的自定义实体

使用 PowerApps，您可以定制您的应用程序使之适合您组织的行业、命名法和特定业务过程。 PowerApps 应用开发包括添加“现成”的标准实体或创建自定义实体。 实体定义您要以记录形式跟踪的信息，通常包括公司名称、地点、产品、电子邮件和电话等属性。 

在本主题中，您创建实体，然后添加或自定义关键组件（如字段、关系、视图和窗体）。 您了解如何：

- 创建自定义实体。
- 向您的实体添加自定义字段
- 添加实体关系
- 自定义视图 
- 自定义窗体

本主题将以公司 Contoso 为例，这是一家打理狗和猫造型的宠物美容公司。 Contoso 需要一个可由员工跨各种设备使用的客户和宠物跟踪应用程序。

## <a name="prerequisites"></a>必备条件 

登录到 [PowerApps](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc)。 如果还没有 PowerApps 帐户，请从 [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 选择**免费开始**链接。

## <a name="create-a-custom-entity"></a>创建自定义实体。

1. 在左侧导航窗格上，展开**数据**，选择**实体**，然后选择**新建实体**。
    > [!div class="mx-imgBorder"] 
    > ![新建实体](media/create-custom-entity/create-new-entity.png)
2. 在右侧窗格中，输入以下值，然后选择**下一步**。
  - **显示名称**：*宠物* 
  - **描述**：*跟踪宠物服务的自定义实体*
3. 选择**保存实体**。

## <a name="add-and-customize-fields"></a>添加和自定义字段
 
1. 在实体列表中，选择在前面部分创建的**宠物**实体。
2. 在**字段**选项卡上，选择**宠物**字段。
3. 在右侧窗格中，对**显示名称**字段进行以下更改： 
  - 将**显示名称**从**宠物**更改为*宠物名称*
  - 选择**可搜索**  
  
    > [!div class="mx-imgBorder"] 
    > ![更改主要字段](media/create-custom-entity/primary-field.png)
3. 选择**无**。
4. 在实体设计器工具栏的**字段**选项卡上，选择**添加字段**。 在**字段属性**窗格上，输入或选择下列值和选项。
  - **显示名称**。 *种类*
  - **数据类型**。 *选项集*
  - **选项集**。 *新建选项集*
5. 创建选项集

  a. 选择**添加新项**。 
  
  b. 使用*狗*替换**新选项**。 
   
  c. 选择**添加新项**。 
    
  d.  使用*猫*替换**新选项**。 
    
  e. 选择**保存**。 

  > [!div class="mx-imgBorder"] 
  > ![新建选项集](media/create-custom-entity/optionset-add-items.png)

6. 选择**可搜索**，然后选择**完成**。

7. 在实体设计器工具栏上，选择**添加字段**。 在**字段属性**窗格上，输入或选择下列值，然后选择**完成**。
  - **显示名称**。 *品种*
  - **数据类型**。 *文本*
  - **可搜索**。 *是*

8. 在实体设计器工具栏上，选择**添加字段**。 

9. 在**字段属性**窗格上，输入或选择下列值，然后选择**完成**。 
  - **显示名称**。 *预约日期*
  - **数据类型**。 *日期和时间*

10. 选择**保存实体**。

## <a name="add-a-relationship"></a>添加关系

1. 选择**关系**选项卡，在实体设计器工具栏上，选择**添加关系**，然后选择**多对一**。 
2. 在右侧窗格中，在**相关**列表中选择**客户**。
3. 选择**无**。
4. 选择**保存实体**。

  请注意，在添加多对一关系时，数据类型为**查找**的**客户**字段将被自动添加到**字段**选项卡上的字段列表中。
  > [!div class="mx-imgBorder"]
  > ![客户查找字段](media/create-custom-entity/account-lookup-field.png)

## <a name="customize-a-view"></a>自定义视图

1. 选择**视图**选项卡，然后选择**有效宠物**视图。 如果看不到**活动宠物**视图，选择**移除筛选器**。
2. 在视图设计器中选择**添加列**，选择以下列，然后选择**确定**。
  - 客户
  - 预约日期 
  - 品种 
  - 种类
3. 选择**创建日期**列，选择**删除**，然后选择**确定**确认列删除。
4. 若要安排列，选择要移动的列，然后使用 <- 和 -> 箭头按钮，直到您的视图如下所示。
    > [!div class="mx-imgBorder"] 
    > ![有效宠物视图](media/create-custom-entity/active-pets-view.png)
5. 在视图设计器工具栏中，选择**保存并关闭**。  

## <a name="model-driven-apps-only-customize-the-main-form"></a>模型驱动应用程序仅：自定义主窗体

如果您要在画布应用程序中使用“宠物”实体，请跳过此步骤。 

1. 在左侧导航窗格上，展开**数据**，选择**实体**，然后选择**宠物**。
2. 选择**窗体**选项卡，然后选择**主**窗体类型旁边的**信息**以打开窗体编辑器。
    > [!div class="mx-imgBorder"] 
    > ![编辑主窗体](media/create-custom-entity/main-form-edit.png)
3. 在窗体编辑器中，将位于“字段资源管理器”窗格上的**种类**、**品种**、**预约日期**和**客户**字段拖放到窗体画布的“常规”部分，直到窗体如下所示。
    > [!div class="mx-imgBorder"] 
    > ![选择主窗体的字段](media/create-custom-entity/main-form-edit2.png) 
4. 选择**保存**。
5. 选择**发布**。
6. 选择**保存并关闭**以关闭窗体设计器。

## <a name="add-the-custom-entity-to-an-app"></a>将自定义实体添加到应用程序

现在，您的实体已经可以用于构建画布或模型驱动应用程序了。 

## <a name="next-steps"></a>后续步骤

在本主题中，您了解了如何创建可用于创建有用应用的实体。 
- 若要了解如何创建模型驱动应用程序，请参阅[构建您的第一个模型驱动应用程序](../model-driven-apps/build-first-model-driven-app.md)。
- 若要了解如何创建画布应用程序，请参阅[从头创建应用程序](../canvas-apps/get-started-create-from-blank.md)。
