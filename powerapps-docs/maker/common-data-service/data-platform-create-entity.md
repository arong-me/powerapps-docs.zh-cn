---
title: 创建自定义实体的快速入门 | Microsoft Docs
description: 本快速入门介绍了如何在 PowerApps 中创建自定义实体。
author: SKjerland
manager: kfile
ms.service: powerapps
ms.component: cds
ms.topic: quickstart
ms.date: 05/01/2018
ms.author: sharik
ms.openlocfilehash: 55ebd94fb0c895a64323e948d421c758c6af7cc8
ms.sourcegitcommit: b3b6118790d6b7b4285dbcb5736e55f6e450125c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2018
---
# <a name="quickstart-create-a-custom-entity"></a>快速入门：创建自定义实体
在 PowerApps 中，实体定义要跟踪的信息（采用记录的形式），通常包括公司名称、位置、产品、电子邮件和电话号码等属性。 然后可通过开发引用该实体的应用来演示该数据。 PowerApps 提供标准的“现成可用”实体，包含组织内的典型方案（例如跟踪约会），但有时需要创建自定义实体才能存储特定于组织的数据。

此快速入门中介绍了如何创建名为“产品审核”的自定义实体，可使用该实体创建应用，显示公司所销售产品的评分和评论。

## <a name="prerequisites"></a>先决条件
若要按照本快速入门教程，则需要以下项目：
* PowerApps 计划 2 或 Microsoft Flow 计划 2 许可证。 此外，也可以注册 [PowerApps 计划 2 免费试用版](https://web.powerapps.com/signup?redirect=marketing&email=)。
* Common Data Service for Apps 中的系统管理员或系统定制员安全角色。

## <a name="sign-in-to-powerapps"></a>登录到 PowerApps
在 [https://web.powerapps.com]([https://web.powerapps.com) 上登录到 PowerApps。

## <a name="create-an-entity"></a>创建实体
1. 在导航窗格中，单击或点击“数据”将其展开，然后单击或点击“实体”。

    ![实体及其详细信息列表](./media/data-platform-cds-create-entity/entitylist.png "实体列表")

2. 在命令栏中，单击或点击“新建实体”。

    在创建实体之前，请查看[实体引用](../../developer/common-data-service/reference/about-entity-reference.md)，获取有关可用标准实体的说明。 这些实体包含典型方案。 如果有符合你要求或仅需稍加更改的实体，可使用该实体以节省时间。 

3. 在“新建实体”面板的“显示名称”框中，输入“产品审核”，然后可选择性地输入说明（如果其他人要使用此实体，相关说明会很有帮助）。 面板中的其他字段将会自动填充，如下所述。 完成时，请单击“下一步”。

    * 复数显示名称 - 当输入显示名称时，此字段会自动填充，但可以根据需要进行更改。 复数显示名称是 Common Data Service WebAPI 中实体的名称，可用于从 PowerApps 或 Flow 中与此实体交互。
    * 名称 - 当输入显示名称时，此字段也会自动填充。 在创建环境时设置前缀，确保所创建的实体可以在其他环境中导出和导入，而不会与其他实体名称发生冲突。 要更改此前缀，可为 Common Data Service 默认解决方案更新发布服务器上的前缀。 为了防止现有应用中断，保存实体后不得更改名称。
     
    ![新建实体](./media/data-platform-cds-create-entity/newentitypanel.png "新建实体面板")

4. 在实体详细信息页上，单击或点击“主要名称”字段，打开“主要名称”面板，然后在“显示名称”框中，将“主要名称”替换为“产品审核”。 在“名称”框中，将“主要名称”替换为“产品审核”，然后单击或点击“完成”。
 
    默认情况下，每个实体都会包含“主要名称”字段，在与其他实体建立关系时，查找字段会使用该字段。 “主要名称”字段通常会存储实体中所存储数据的名称或主描述。 在第一次保存实体之前，可以更新“主要名称”字段的名称和显示名称。

    ![实体详细信息](./media/data-platform-cds-create-entity/newentitydetails.png "新实体详细信息")

5. 要将字段添加到实体，请执行以下操作：
 
    a. 在命令栏中，单击或点击“添加字段”，打开“字段属性”面板。

    b. 在“显示名称”框中，输入“审核日期”。

    c. 从“数据类型”下拉列表中，选择“仅日期”。

    d. 单击或点击“必填”复选框。
    
    e. 单击或点击“完成”。
     
    有关详细信息，请参阅 [管理实体中的字段](data-platform-manage-fields.md)。

    ![新字段](./media/data-platform-cds-create-entity/newfieldpanel-2.png "新字段面板")

6. 重复上一步，再添加三个具有以下配置的字段：
    * 显示名称 = 产品评分；数据类型 = 整数；单击或点击“必填”复选框
    * 显示名称 = 审核者姓名；数据类型 = 文本
    * 显示名称 = 审核者评论；数据类型 = 文本

    完成时，在实体详细信息页上应该列出五个字段。

    ![字段列表](./media/data-platform-cds-create-entity/addedfields.png "字段列表")

    请注意，所有实体都具有只读系统字段。 默认情况下，系统字段不会显示在字段列表中，即使它们存在于实体中。 要查看所有字段，可以在命令栏上将筛选器从“默认”更改为“所有”。 要详细了解与实体相关的元数据，请参阅[实体元数据](../../developer/common-data-service/entity-metadata.md)。

7. 单击“保存实体”以保存实体并使它在应用中可用。

    “产品审核”实体应显示在数据库的实体列表中。 如果没有显示，可以在命令栏中将筛选器从“默认”更改为“自定义”。

    ![筛选器](./media/data-platform-cds-create-entity/filter.png "筛选器选择")

## <a name="next-steps"></a>后续步骤
在此快速入门中，你已了解到如何创建名为“产品审核”的自定义实体，使用该实体可以创建应用，显示特定公司销售的每个产品的评分和评论。 接下来，可了解如何定义实体之间的关系（在本例中是标准产品实体与自定义“产品审核”实体之间的关系），以便将每个产品与其接收到的审核和评论关联。

> [!div class="nextstepaction"]
> [创建关系](data-platform-entity-lookup.md)

## <a name="privacy-notice"></a>隐私声明
通过 Microsoft PowerApps 通用数据模型，Microsoft 可收集自定义实体和字段名称，并将其存储在诊断系统中。 我们利用这一知识来改进我们客户的通用数据模型。 应用创建者创建的实体和字段名称帮助我们了解 Microsoft PowerApps 社区中的常见方案，并确定服务标准实体范围中的缺口，如与组织相关的架构。 Microsoft 无法访问或使用数据库表中与这些实体相关联的数据，此类数据也无法在预配了数据库的区域之外进行复制。 不过，请注意，自定义实体和字段名称可能可以进行跨区域复制，并根据我们的数据保留策略进行删除。 Microsoft 致力于保护你的隐私安全，我们的[信任中心](https://www.microsoft.com/trustcenter/Privacy/default.aspx)对此进行了详述。
