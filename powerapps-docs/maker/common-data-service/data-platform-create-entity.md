---
title: 创建自定义实体 | Microsoft Docs
description: 了解如何在 PowerApps 中创建自定义实体。
author: Mattp123
ms.service: powerapps
ms.component: cds
ms.topic: quickstart
ms.date: 05/01/2018
ms.author: matp
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="create-a-custom-entity"></a>创建自定义实体。
在 PowerApps 中，*实体*定义您要以记录形式跟踪的信息，通常包括公司名称、地点、产品、电子邮件和电话等属性。 然后您可以通过开发引用该实体的应用程序来显示该数据。 PowerApps 提供标准的“现成”实体来覆盖组织内的典型情形（如跟踪约会），但是有时您可能需要创建自定义实体来存储特定于组织的数据。

在本主题中，您将了解如何创建名为“产品审核”的自定义实体，您可以用它来创建显示您的公司所销售的产品的评分和评论的应用程序。

## <a name="prerequisites"></a>必备条件 
若要按照此过程操作，需要以下项目：
* PowerApps 计划 2 或 Microsoft Flow 计划 2 许可证。 或者，可以注册[免费的 PowerApps 计划 2 试用版](https://web.powerapps.com/signup?redirect=marketing&email=)。
* 面向应用的 Common Data Service 内的系统管理员或系统定制员安全角色。

## <a name="sign-in-to-powerapps"></a>登录到 PowerApps
在 [https://web.powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 登录到 PowerApps

## <a name="create-an-entity"></a>创建实体
1. 在导航窗格中，单击或点按**数据**以展开它，然后单击或点按**实体**。

    ![实体及其详细信息的列表](./media/data-platform-cds-create-entity/entitylist.png "实体列表")

2. 在命令栏中，单击或点按**新建实体**。

    在创建实体之前，查看[实体参考信息](../../developer/common-data-service/reference/about-entity-reference.md)了解可用标准实体的说明。 这些实体覆盖典型情形。 如果这些实体之一本身或在轻微更改后满足您的要求，您可以使用此实体开始以节省时间。 

3. 在**新建实体**面板中，在**显示名称**框中，输入**产品审核**，然后可以选择输入说明（如果其他人员将使用此实体，说明会有帮助）。 此页面中的其他字段将自动填充，如下所述。 完成后，请单击**下一步**。

    * **复数显示名称** - 此字段在您输入显示名称时自动填充，如果需要，您也可以更改它。 复数显示名称是 Common Data Service WebAPI 中实体的名称，在从 PowerApps 或 Flow 与此实体交互时使用。
    * **名称** - 此字段在您输入显示名称时也会自动填充。 当创建环境时会设置前缀，并确保您创建的实体可以在其他环境中导出和导入，且不会与其他实体名称冲突。 您可以通过更新 Common Data Service 默认解决方案的发布商的前缀来更改此前缀。 为了防止现有应用程序中断，在保存实体后您无法更改名称。

       > [!NOTE]
       > 若要让实体名称支持 [Dynamics 365 for Customer Service 嵌入式知识搜索](/dynamics365/customer-engagement/customer-service/set-up-knowledge-management-embedded-knowledge-search)，含发布者前缀的实体名称最大长度不能超过 24 个字符。
     
    ![新建实体](./media/data-platform-cds-create-entity/newentitypanel.png "新建实体面板")

4. 在实体详细信息页上，单击或点按**主要名称**字段打开**主要名称**面板，然后在**显示名称**框中，使用**产品审核**替换**主要名称**。 在**名称**框中，使用 **ProductReview** 替换 **PrimaryName**，然后单击或点按**完成**。
 
    默认情况下，每个实体均包含“主要名称”字段，其在建立与其他实体的关系时由查找字段使用。 通常，“主要名称”字段存储在实体中存储的数据的名称或主要说明。 您可以在首次保存实体之前更新“主要名称”字段的名称和显示名称。

    ![实体详细信息](./media/data-platform-cds-create-entity/newentitydetails.png "新实体详细信息")

5. 若要向实体添加字段，请执行以下操作：
 
    a. 在命令栏中，单击或点按**添加字段**打开**字段属性**面板。

    b. 在**显示名称**框中，输入**审核日期**。

    c. 从**数据类型**下拉列表，选择**仅限日期**。

    d. 单击或点按**必填**复选框。
    
    e. 单击或点按**完成**。
     
    有关详细信息，请参阅[管理实体中的字段](data-platform-manage-fields.md)。

    > [!div class="mx-imgBorder"] 
    > ![新建字段](./media/data-platform-cds-create-entity/newfieldpanel-2.png "新建字段面板")

6. 重复上一步骤添加具有以下配置下的另外三个字段：
    * **显示名称** = 产品评分；**数据类型** = 整数；单击或点按**必填**复选框
    * **显示名称** = 审核人姓名；**数据类型** = 文本
    * **显示名称** = 审核人评论；**数据类型** = 文本

    完成后，您应该在实体详细信息页有五个列出的字段。

    ![字段列表](./media/data-platform-cds-create-entity/addedfields.png "字段列表")

    请注意，所有实体均有只读的系统字段。 默认情况下，系统字段不显示在字段列表中，即使它们在实体中存在。 若要查看所有字段，将命令栏上的筛选器从**默认**更改为**所有**。 有关与实体相关的元数据的详细信息，请参阅[实体元数据](../../developer/common-data-service/entity-metadata.md)。

7. 单击**保存实体**保存您的实体并使它可在应用程序中使用。

    “产品审核”实体应显示在数据库中实体的列表中。 如果您没有看到它，请将命令栏上的筛选器从**默认**更改为**自定义**。

    > [!div class="mx-imgBorder"] 
    > ![筛选器](./media/data-platform-cds-create-entity/filter.png "筛选器选择")

## <a name="next-steps"></a>后续步骤
在本主题中，您了解了如何创建名为“产品审核”的自定义实体，它可以用于创建显示某家公司所销售的每个产品的评分和评论的应用程序。 接下来，了解如何定义实体间的关系（在本例中，是标准产品实体与您的自定义产品审核实体），以便您可以将每个产品与其收到的审核和评论关联起来。

> [!div class="nextstepaction"]
> [创建关系](data-platform-entity-lookup.md)

## <a name="privacy-notice"></a>隐私声明
通过 Microsoft PowerApps 通用数据模型，Microsoft 收集并在我们的诊断系统中存储自定义实体和字段名称。 我们使用此知识来改进我们客户的通用数据模型。 应用程序创建者创建的实体和字段名称帮助我们了解 Microsoft PowerApps 社区常见的情形，以及服务的标准实体功能存在的确定空白区，如与组织相关的架构。 与这些实体关联的数据库表中的数据不由 Microsoft 访问或使用，也不会在数据库配置地区以外复制。 但是，请注意，自定义实体和字段名称可以跨地区复制，并根据我们的数据保留策略删除。 Microsoft 承诺保护您的隐私，如我们的[信任中心](https://www.microsoft.com/trustcenter/Privacy/default.aspx)的详细叙述。
