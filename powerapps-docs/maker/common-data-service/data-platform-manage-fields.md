---
title: 管理实体中的自定义字段 | Microsoft Docs
description: 如何在面向应用程序的 Common Data Service (CDS) 中创建、读取、更新和删除实体内的自定义字段的演练。
author: clwesene
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: conceptual
ms.date: 03/21/2018
ms.author: clwesene
search.audienceType:
  - maker
search.app:
  - PowerApps
  - D365CE
---

# <a name="manage-custom-fields-in-an-entity"></a>管理实体中的自定义字段
您可以创建和更新任何实体中的一个或多个自定义字段。 在创建自定义字段时，可以指定一组属性，如字段名、其显示名称和它将包含的数据的类型。 有关详细信息，请参阅[实体属性元数据](../../developer/common-data-service/entity-attribute-metadata.md)。

> [!NOTE]
> 每个实体都有系统字段，如指示记录上次更新时间以及更新人的字段。 此外，标准实体具有标准（默认）字段。 无法修改或删除系统字段或标准字段。 如果创建自定义字段，它应在这些内置字段的顶部提供功能。

## <a name="create-a-field"></a>创建字段
1. 在 [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开**数据**部分并单击或点按左侧导航窗格中的**实体**。

    ![实体详细信息](./media/data-platform-cds-create-entity/entitylist.png "实体列表")

2. 单击或点按现有实体或[创建新实体](data-platform-create-entity.md)

3. 单击**添加字段**向实体添加新字段。

4. 在“新建字段”面板中，为您的字段输入**显示名称**，**名称**将自动填充并用作字段的唯一名称。 **显示名称**在将此字段呈现给您的用户时使用，**名称**在生成应用程序时使用，使用表达式和公式形式。

    > [!NOTE]
    > **显示名称**字段可以随时更新以在您的应用程序中有不同显示，**名称**字段无法在保存实体后更改，因为这可能导致现有应用程序中断。

    > [!div class="mx-imgBorder"] 
    > ![新建字段](./media/data-platform-cds-create-entity/newfieldpanel.png "新建字段面板")

5. 选择您的字段的**数据类型**，这将控制信息的存储方式以及它如何在应用程序中呈现。 例如，文本的存储与十进制数或 URL 不同。 有关可用的数据类型的详细信息，请参阅[实体属性元数据](../../developer/common-data-service/entity-attribute-metadata.md)。

    如果看到提示，请为您指定的数据类型指定其他信息。 根据数据类型，将呈现不同字段。 如果创建类型为“选项集”或“多选选项集”的字段，您可以选择**新建选项集**在创建字段时创建新选项集。 有关详细信息，请参阅[创建选项集](custom-picklists.md)

    > [!div class="mx-imgBorder"] 
    > ![新建字段](./media/data-platform-cds-create-entity/newfieldpanel-2.png "新建字段面板")


7. 在**必填**下，如果您想要建议此字段在您的应用程序中为必填字段，则选择此复选框。 这不通过所有 Common Data Service 连接提供硬实施。 如果您需要确认字段已填充，则创建[业务规则](data-platform-create-business-rule.md)

8. 在**可搜索**下，如果需要此字段在“视图”、“图表”、“仪表板”和“高级查找”中提供，则选中此复选框。 大多数情况下会选中此复选框。

9. 单击或点按**完成**关闭“字段”面板并返回到实体。 您可以对其他每个字段重复步骤 3-9。
   
    > [!IMPORTANT]
    > 在您将更改保存到实体前，字段未保存和创建。

10. 单击或点按**保存实体**完成所做更改并将它们保存到 Common Data Service。

    当操作成功完成时您将收到通知。 如果操作未成功，错误消息指示出现问题以及您如何修复。

## <a name="create-a-calculated-or-roll-up-field"></a>创建计算字段或汇总字段
计算字段可以将您的业务流程中使用的手动计算自动化。 例如，推销员可能想知道商机的加权收入，这基于商机与概率乘积得到的预计收入。 或者，如果订单大于 500 美元，他们想要自动使用一个折扣。 计算字段可以包含简单数学运算或条件运算（如大于或 if - else 等）产生的值。 计算字段可以使用以下数据类型创建：

* 单行文本
* 选项集
* 两个选项
* 整数
* 十进制数
* 货币
* 日期和时间

有关支持的表达式类型的更多详细信息和示例，请参阅[定义计算字段](/dynamics365/customer-engagement/customize/define-calculated-fields)

## <a name="update-or-delete-a-field"></a>更新或删除字段
1. 在 [powerapps.com](https://web.powerapps.com/?utm_source=padocs&utm_medium=linkinadoc&utm_campaign=referralsfromdoc) 上，展开**数据**部分并单击或点按左侧导航窗格中的**实体**，然后单击或点按实体。
2. 在所选实体的字段列表中，单击或点按字段，然后按照以下步骤之一操作：
   
   * 更改字段的一个或多个属性。
   * 通过单击或点按字段右边缘附近的省略号 (...)，然后单击或点按**删除**来删除字段。

3. 单击或点按**保存实体**提交您的更改。
   
    > [!IMPORTANT]
    > 如果在浏览器中打开其他页面或退出浏览器前不保存更改，所作更改将丢失。

    当操作成功完成时您将收到通知。 如果操作未成功，错误消息指示出现问题以及您如何修复。

## <a name="best-practices-and-restrictions"></a>最佳实践和限制
在创建和修改字段时，请牢记以下几点：

* 无法修改或删除系统字段或它们的值。
* 在标准实体中，无法修改或删除标准（默认）字段，添加需要数据的字段，或进行可能会中断依赖于该实体的应用程序的任何其他更改。
* 在自定义实体中，您应该确保所做更改不会中断依赖于该实体的任何应用程序。
* 您必须为每个自定义字段提供在实体中是唯一的名称，而且在创建字段后无法对其重命名。

## <a name="next-steps"></a>后续步骤
* [定义实体之间的关系](data-platform-entity-lookup.md)
* [创建业务规则](data-platform-create-business-rule.md)
* [使用实体创建应用程序](../canvas-apps/data-platform-create-app.md)
* [使用 Common Data Service 数据库从头创建应用程序](../canvas-apps/data-platform-create-app-scratch.md)

## <a name="privacy-notice"></a>隐私声明
通过 Microsoft PowerApps 通用数据模型，我们收集并在我们的诊断系统中存储自定义实体和字段名称。  我们使用此知识来改进我们客户的通用数据模型。 创建者创建的实体和字段名称帮助我们了解 Microsoft PowerApps 社区常见的情形，以及服务的标准实体功能存在的确定空白区，如与组织相关的架构。 与这些实体关联的数据库表中的数据不由 Microsoft 访问或使用，也不会在数据库配置地区以外复制。 但是，请注意，自定义实体和字段名称可以跨地区复制，并根据我们的数据保留策略删除。 Microsoft 承诺保护您的隐私，如我们的[信任中心](https://www.microsoft.com/trustcenter/Privacy/default.aspx)的详细叙述。

